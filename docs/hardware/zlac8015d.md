# ZLAC8015D — notas de integração

Fonte: *ZLAC8015D Servo Driver RS485 Communication Instruction v1.04*
(Shenzhen ZhongLing Technology), em [`../referencias/ZLAC8015D_RS485_v1.04.pdf`](../referencias/ZLAC8015D_RS485_v1.04.pdf).
Conferido registrador por registrador em 2026-11-05.

## Ligação

```
NUC ──USB──► adaptador USB-RS485 ──par trançado A/B (+GND)──► ZLAC8015D ──► motor E / motor D
                                                                  ▲
                                                     bateria de tração 24 V
botão de emergência ──► entrada X0 (de fábrica = "quick stop")
```

- Terminação de 120 Ω no fim do barramento (a lib `zlac_ros2` menciona chave de
  terminação no driver).

## Serial

- **Modbus RTU**, endereço 1 por padrão (faixa 1–127; o dicionário lista o
  default de `2001h` como 4, então **conferir na bancada**).
- **115200** 8N1 por padrão; também 9600 … 256000 (`2002h`).
- Funções: `0x03` ler, `0x06` escrever 1, `0x10` escrever vários.
- Também tem **CAN** (`200Ah` nó, `200Bh` baud, 500 kbit/s padrão).

## Modo velocidade (o que vamos usar)

| Reg. | Nome | Valor / unidade |
|---|---|---|
| `200Dh` | Modo de controle | `3` = velocidade (1/2 posição, 4 torque) |
| `200Eh` | Palavra de controle | `0x08` habilita, `0x07` para, `0x05` parada rápida, `0x06` limpa falha |
| `2080h/2081h` | Tempo de aceleração E/D | ms, 0–32767 (padrão 500) |
| `2082h/2083h` | Tempo de desaceleração E/D | ms (padrão 500) |
| `2088h/2089h` | Velocidade alvo E/D | **rpm inteiro**, I16, ±3000 |
| `20ABh/20ACh` | Velocidade real E/D | **0,1 rpm**, I16 |
| `20A7h–20AAh` | Posição real E/D (alta/baixa) | contagens, 32 bits |
| `2008h` | Velocidade máxima | rpm, 1–1000 (padrão 1000) |

Escrita **síncrona** das duas rodas (exemplo do manual, 100 rpm nas duas):
`01 10 20 88 00 02 04 00 64 00 64 23 9C`

Sequência de init do manual: modo 3 → acel/desacel → `200Eh = 0x08`.

## Segurança e diagnóstico

| Reg. | Nome | Nota |
|---|---|---|
| `2000h` | Tempo de comunicação offline | ms, padrão **1000**. Se o host para de falar, o driver para. **Baixar pra ~200 ms.** |
| `2011h` | Ação da parada rápida | 5 parar / 6 com desacel / 7 sem desacel |
| `2016h–2018h` | Entradas X0/X1 | nível e função; **X0 de fábrica = 9, parada rápida** |
| `2019h–201Bh` | Saídas Y0/Y1 | função **freio** disponível |
| `20A1h` | Tensão DC | 0,01 V |
| `20A4h` | Temperatura do motor | 1 °C |
| `20A5h/20A6h` | Código de erro E/D | bits: sobretensão, subtensão, sobrecorrente, sobrecarga, erro de seguimento de corrente/posição/velocidade, EEPROM, hall, sobretemperatura |
| `2010h` | Salvar registradores na EEPROM | `1` salva |

## Implicações pro projeto

- **Resolução do comando é 1 rpm.** Com roda de 14 cm, 1 rpm ≈ **7,3 mm/s**. Em
  0,4 m/s (~55 rpm) cada degrau vale ~1,8 %. É suficiente pro Nav2, mas o
  `diff_drive_controller` vai arredondar e isso precisa estar no sim.
- Um ciclo (escrita síncrona + leitura de 6 registradores) leva ~2–3 ms a
  115200: 50 Hz com folga. Dá pra subir o baud se precisar.
- **Faixa de tensão de alimentação NÃO está neste manual.** Confirmar no manual
  de hardware.
