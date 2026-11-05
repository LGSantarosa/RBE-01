# 003 — Energia: duas baterias iguais (tração / computação)

**Data:** 2026-11-05
**Estado:** aceita no conceito (decisão do dono). A química, o modelo e a
capacidade estão em aberto.

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

## Em aberto

- Química (Li-ion vs LiFePO4: LiFePO4 é mais segura perto de criança e dura mais
  ciclos, mas pesa mais, o que aqui **não é problema**). Preferência a discutir.
- Modelo/fornecedor; BMS; como medir a tensão e corrente de cada uma no ROS.
- Como a estação de carga carrega **as duas** (ver [004](004-estacao-de-carga-autonoma.md)).
- Corte geral e botão de emergência.
