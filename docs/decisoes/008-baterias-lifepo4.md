# 008 — Baterias: duas LiFePO4 8S (25,6 V), ~10 Ah

**Data:** 2026-11-05
**Estado:** aceita (o dono topou LiFePO4 "se ela é melhor pra esse caso"). Faixa
de tensão do driver confirmada (2026-11-10); falta a regeneração e fechar o modelo.

Complementa a [003](003-energia-duas-baterias.md) (duas baterias iguais,
tração / computação).

## Requisito do dono

"Ela só tem que aguentar as paradas": suportar os picos de corrente (arrancadas,
frenagens, giro no lugar) sem o BMS desarmar, que era o problema do robô 1
(BMS do hover caindo de 39 V pra 6 V sob rotor travado).

## Opções consideradas

| Química | Prós | Contras | Resultado |
|---|---|---|---|
| **LiFePO4** | muito mais difícil de entrar em fuga térmica (perto de criança é o que pesa); 2000+ ciclos; curva de tensão plana | mais pesada e maior por Wh | **escolhida** |
| Li-ion (NMC, 7S 18650/21700) | leve, compacta, barata | risco térmico maior; ~500–1000 ciclos | descartada |
| Chumbo-ácido selada | barata, robusta | pesadíssima, poucos ciclos, recarga lenta (não fecha as 2 h) | descartada |

O peso a mais da LiFePO4 **ajuda** aqui (o robô precisa ser pesado e com massa
embaixo).

## Dimensionamento

| Item | Valor |
|---|---|
| Configuração | **8S LiFePO4**, 25,6 V nominal (≈ 20–29,2 V de vazia a cheia) |
| Capacidade | **~10 Ah ≈ 256 Wh** cada (cobre os 60–160 Wh de cada lado em 4 h, com margem pro corpo e envelhecimento) |
| Massa | ~2,5–3 kg cada (estimativa) |
| Recarga | carregador de ~5 A (0,5 C) → **~2 h** |

### "Aguentar as paradas": corrente

- Tração: 2 motores de 150 W a 24 V ≈ 6 A cada, **~12 A contínuo** no máximo;
  pico de torque (~3× o nominal) por instantes → **~35–40 A de pico**.
- Computação: NUC + LD06 + IMU ≈ 1–2 A, picos ~4 A.
- **Exigência pro BMS** (igual nas duas, já que são iguais): **≥ 30 A contínuo
  e ≥ 60 A de pico** por alguns segundos. Dá pra configurar as rampas do driver
  (`2080h–2083h`) e a velocidade máxima pra nunca chegar perto disso.

## ⚠️ Condição pra fechar

**Faixa de tensão: resolvida (2026-11-10).** O *ZLAC8015 Servo Driver Manual
V2.00* dá entrada de **20 V mín. / 36 V típ. / 48 V máx.**, subtensão em **16 V**
e sobretensão em **75 V** (o texto do manual diz "24V–48V", a tabela diz 20 V).
A 8S vai de ~20 V a 29,2 V, então fica dentro. Mesmo no pior caso (mínimo de
24 V = 3,0 V/célula), a LiFePO4 passa quase toda a descarga no patamar de
3,2–3,3 V/célula (25,6–26,4 V) e perde só uma fração pequena (estimativa
~5–10 %). A 8S está mantida. Detalhes em [`../hardware/zlac8015d.md`](../hardware/zlac8015d.md).

Na frenagem, confirmar se o ZLAC **regenera para o barramento** e como limita a
tensão. Se o BMS bloquear corrente de carga — especialmente com a bateria cheia
— a tensão do barramento pode subir até uma falha de sobretensão. A combinação
ZLAC + bateria/BMS precisa aceitar a energia regenerada ou ter uma forma
dimensionada de dissipá-la. **O manual V2.00 não fala de regeneração**:
perguntar à ZLTECH ou medir na bancada. **Não comprar bateria antes disso**
(muda a corrente de carga que o BMS precisa aceitar).

## Em aberto

- Modelo/fornecedor (pack pronto com BMS vs montar com células prismáticas).
- Corrente de carga aceita pelo BMS durante a frenagem, sobretensão do barramento
  e eventual necessidade de resistor/circuito de frenagem.
- Como medir a tensão e a corrente de cada bateria no ROS (a tensão da tração
  vem do `20A1h` do driver; a da computação precisa de um sensor).
- Carregador e integração com a estação de carga ([004](004-estacao-de-carga-autonoma.md)).
