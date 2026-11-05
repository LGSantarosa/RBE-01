# Diário

## 2026-11-05 — Nascimento do projeto: idealização da base

Conversa de idealização entre o dono e o assistente.

- **Ponto de partida:** criar uma base de 2 rodas motoras + roda de apoio, "parecida
  com o robô 3", mas como continuação do robô 1 e **solta dos outros dois**.
- **Uso:** sala de aula com crianças e professor. Ele vai até a mesa de uma
  criança, identifica, para de frente e conversa. Essa interação fica pra depois.
- **Lição do robô 3** (dono): ele só ficou bom com **roda omni** atrás, sem arrasto.
- **Corpo:** ~70 × 50 cm, gordinho, pesado de propósito. O conceito (`RBE-01.skp`)
  tem as rodas **no meio** da lateral, então a cinemática mudou pra rodas centrais
  + omni na frente e atrás (dono: "fica interessante").
- **Chão:** liso na sala, tapete e corrediça fora dela.
- **Bateria:** 4 h de uso, 2 h de recarga, duas iguais. Carga em **estação
  autônoma**.
- **Motor:** o hover foi rejeitado (forte e pesado demais). O motorredutor DC
  foi rejeitado por **chiado**. Três anúncios avaliados e descartados (cubo de
  aspirador de 74 mm, cubo de patinete 8" 350 W, controlador BLDC com controle
  remoto). O hover com a placa do robô 1 voltou como opção barata, mas perdeu
  pela **reprodutibilidade em 5 robôs** (a placa varia, e o hack só roda numa).
  **Escolhido o cubo servo AGV ZLTECH 5,5" + ZLAC8015D.**
- **Integração verificada no manual RS485 v1.04:** modo velocidade, escrita
  síncrona das duas rodas em rpm, feedback de posição e velocidade, watchdog de
  comunicação, entrada X0 = parada rápida. Sem micro na tração.
- **Disponibilidade:** sem distribuidor no Brasil; comprar 6 kits do mesmo lote.

- **Elétrica:** parecida com o robô 1. **Botão de emergência na traseira** que
  derruba só as rodas; **sem LED**. Com isso a base fica **sem nenhum
  microcontrolador** (IMU por USB direto no NUC).

- **Relé automotivo** do e-stop aprovado.
- **Baterias LiFePO4** (proposta aceita): 8S ~10 Ah, BMS ≥ 30 A / 60 A pico pra
  "aguentar as paradas". Condição: confirmar que o ZLAC8015D aceita ~20 V.

Próximo: modelo da IMU, depois o esquema elétrico.
