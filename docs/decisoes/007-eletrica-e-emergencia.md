# 007 — Elétrica, botão de emergência e (sem) microcontrolador

**Data:** 2026-11-05
**Estado:** aceita no conceito (decisão do dono). O esquema elétrico está em
aberto.

## Decisão (do dono)

- **Elétrica parecida com a do robô 1**: duas baterias, cada uma com seu circuito.
- **Botão de emergência na traseira** do robô.
- O botão **derruba só a elétrica das rodas**. O NUC e os sensores continuam
  ligados (não perdem mapa nem posição).
- **Sem LED** de sinalização na base.

## Consequência: robô sem microcontrolador (proposta, aceita implicitamente)

No robô 1, a MEGA existia pra tração, IMU, LEDs, relé e botão. Aqui:

| Função | Robô 1 | RBE-01 |
|---|---|---|
| Tração | MEGA → placas hover | NUC → RS485 → ZLAC8015D |
| IMU | MEGA (I²C) | **IMU USB direto no NUC** (modelo a escolher) |
| LEDs / relé | MEGA | **não tem** |
| Botão | MEGA | e-stop elétrico + entrada X0 do ZLAC |
| LiDAR | USB | USB |

Portanto **nenhum microcontrolador** na base. Quando o corpo vier, o estado
(carregando, bateria baixa, emergência) aparece na tela do visor.

## Propostas do assistente (a validar)

- **Botão cogumelo com trava** (aperta e trava; destrava girando). Se uma criança
  apertar por brincadeira, só um adulto libera.
- O botão faz duas coisas:
  1. **Corta a alimentação da tração** no hardware, sem depender de software.
     Como a corrente de pico dos dois motores pode passar do que o contato do
     botão aguenta em DC, o botão comanda um **relé/contator automotivo de 24 V**
     (barato, ~40 A) em vez de passar a corrente por ele. No robô 1 a contatora
     industrial foi descartada pelo preço; o relé automotivo resolve isso.
  2. **Sinaliza o driver e o NUC** (contato auxiliar NF na entrada X0 do ZLAC,
     que já vem como "parada rápida"; o NUC lê o estado em `2003h`). Assim o
     software sabe que foi o botão, não falha, e **não volta a andar sozinho**
     quando destravam: precisa de um comando de rearme.
- **Chave geral por bateria** + **fusível** em cada saída.
- Como o driver perde energia no e-stop, a hardware interface precisa tratar a
  volta (reconfigurar modo velocidade, habilitar) depois do rearme.

## Lição do robô 1 que vale aqui

O BMS do hoverboard desarmava sob rotor travado (39 V → 6 V). No RBE-01, o ZLAC
tem proteção de sobrecorrente e sobrecarga própria, e o BMS da bateria de tração
precisa ser escolhido com corrente de pico acima do que o driver pede.

## Em aberto

- Esquema elétrico completo (chaves, fusíveis, relé, conversor DC-DC do NUC).
- Como a estação de carga entra nesse circuito ([004](004-estacao-de-carga-autonoma.md)).
- Modelo da IMU USB.
