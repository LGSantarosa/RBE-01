# 003 — Energia: duas baterias iguais (tração / computação)

**Data:** 2026-11-05
**Estado:** aceita no conceito (decisão do dono). Química e capacidade fechadas
na [008](008-baterias-lifepo4.md) (LiFePO4 8S ~10 Ah); modelo em aberto.

## Requisitos (do dono)

- **4 horas seguidas** de operação.
- **2 horas** pra recarregar e voltar à ativa.
- **Duas baterias iguais**, como no robô 1: uma alimenta a **tração** e a outra o
  **PC e os sensores**.

## Decisão

- **Bateria 1 → tração**: driver ZLAC8015D + motores.
- **Bateria 2 → computação**: NUC, LD06, IMU e, no futuro, o corpo (tela, som,
  câmera, braços).
- **Iguais** (mesmo modelo): uma peça de reposição serve pros dois lados, e o
  carregador também é um só.

Por que separar: ruído e queda de tensão nos motores não derrubam o PC, e o
problema de "a bateria da percepção não tem canal na pilha ROS" (robô 3) tem que
ser resolvido aqui desde o início. **As duas tensões precisam ser monitoradas.**

## Dimensionamento (estimativa do assistente, a refinar)

| Consumidor | Média estimada | 4 h |
|---|---|---|
| NUC + LD06 + IMU | 15–30 W | 60–120 Wh |
| Tração (andando parte do tempo) | 15–40 W | 60–160 Wh |
| Corpo (futuro: tela, som, câmera) | ? | reserva |

Proposta: **24 V nominal, ~200 Wh cada** (ex.: Li-ion 7S ou LiFePO4 8S de
~8–10 Ah). A margem cobre o corpo e o envelhecimento. Recarga em 2 h ≈ 0,5 C,
o que é tranquilo pra essas químicas.

24 V porque é a tensão nominal do motor ZLTECH e simplifica a tração (sem
conversor). O lado da computação precisa de conversor DC-DC pro NUC (a
tensão de entrada depende do modelo).

### Conversores de tensão (2026-11-10)

- **Tração: sem conversor.** O ZLAC8015D aceita 20–48 V (manual V2.00) e
  controla a velocidade do motor de 24 V sozinho, então a 8S (20–29,2 V) entra
  direto. Um conversor ali teria que aguentar ~40 A de pico e bloquearia a
  energia da frenagem. O relé de 24 V do e-stop também aceita 29 V (relé
  automotivo de 24 V é feito pra sistema de ~28 V).
- **Computação: conversor DC-DC obrigatório pro NUC.** A bateria varia de 20 a
  29,2 V e o NUC pede tensão fixa (12 ou 19 V, conforme o modelo, ainda em
  aberto na 005). Perto de vazia a bateria chega a ~20 V, então um *buck* só
  abaixando não segura 19 V: usar saída de **12 V** (se o NUC aceitar) ou um
  **buck-boost** de 19 V. Dimensionar pelo pico do NUC (~65–90 W, a confirmar
  com o modelo), com folga.
- LD06, câmera e IMU vêm pelo USB do NUC: sem conversor próprio. O corpo
  (tela, som) vai pedir os seus (12 V / 5 V), a definir.

## Em aberto

- Modelo/fornecedor; BMS; como medir a tensão e corrente de cada uma no ROS.
- Como a estação de carga carrega **as duas** (ver [004](004-estacao-de-carga-autonoma.md)).
- Detalhar corte geral e integrar o circuito de emergência já decidido na
  [007](007-eletrica-e-emergencia.md).
