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

- **IMU:** BNO055, a melhor do robô 1 segundo o dono, em **modo UART** com
  adaptador USB-serial (ideia do dono). Existe driver ROS 2 Jazzy pronto. Sem
  magnetômetro no rumo por causa dos ímãs dos motores de cubo.

- **Chassi:** ferramentas da casa são impressão 3D, laser de MDF/acrílico e solda
  simples. Proposta A (aço soldado embaixo como lastro, colunas de alumínio,
  decks MDF/acrílico, suspensão de braço com mola) contra B (só alumínio) e
  C (só MDF, descartada). Montada uma apresentação de 17 slides pro time opinar.

- **Apresentação revisada** (pedido do dono): saíram os slides de cenário,
  lições, perguntas e próximos passos (ficou com 16). A suspensão virou 4 slides:
  o problema, a mola nas motoras, a gangorra e o recomendado. Achado: **a gangorra
  pura cabeceia** no losango (rodas e pivô na mesma linha). Recomendação nova:
  **rodas motoras fixas, mola com batente nas omnis**.

- **Suspensão por dentro:** slides novos explicando por que a mola nas omnis
  resolve e a "janela" da mola. Mola revisada pra ~8 N/mm (faixa 6–12) +
  amortecedor a óleo (sem ele, ~2 Hz de balanço). Pesquisa: não existe omni
  com suspensão pronta; o padrão de AGV leve é guia vertical + mola. Proposta:
  hastes de 8 mm + LM8UU + coilover RC 1/8 + batente de PU; omni de alumínio
  ≥ 40 kg.
- **Achado:** o e-stop cortando o driver tira o freio (o robô rola 30–50 cm).
  Pendente com o dono (ver 007).
- **Slide "RBE-01 por dentro":** o astronauta translúcido com toda a base
  desenhada por dentro, no fim da apresentação (19 slides).

Próximo: trazer a opinião do time sobre o chassi; o dono decide o freio do e-stop.
