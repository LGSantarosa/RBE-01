# 001 — Cinemática: diferencial com rodas no meio e omni na frente e atrás

**Data:** 2026-11-05
**Estado:** aceita (decisão do dono). Os detalhes de suspensão estão em aberto.

## Contexto

O robô convive com crianças e precisa andar entre mesas e mochilas, girar sem
"varrer" ninguém e parar com precisão na frente de uma mesa. O corpo vai ser
gordinho, com **~70 cm de altura e ~50 cm de largura**, e **pesado de propósito**,
pra uma criança não conseguir tombar.

O conceito visual (`docs/conceito/`) mostra as rodas grandes **no meio da
lateral** do corpo.

## Opções consideradas

| Opção | Prós | Contras | Resultado |
|---|---|---|---|
| **A. 2 motoras na frente + 1 omni atrás** (como o robô 3) | 3 pontos: sempre apoia no chão; simples | o centro de giro fica na frente, então a traseira varre um arco ao girar; o triângulo de apoio tomba fácil na linha roda–omni | **descartada** |
| **B. 2 motoras no meio + omni na frente e atrás** | gira **em torno do próprio centro** (pegada circular, ótimo pro Nav2 e perto de criança); apoio largo nos 4 lados, resiste a tombamento; bate com o conceito visual | 4 pontos de apoio num chassi rígido é hiperestático: num desnível uma roda motora perde contato | **escolhida** |
| C. Skid-steer de 4 rodas (robô 1) | robusto | é a fonte dos problemas do robô 1 (giro, zona morta, patinagem) | descartada de cara |
| D. Boba (caster giratório) em vez de omni | barata | arrasto e "shopping cart" ao inverter; o robô 3 só ficou bom com omni | descartada (lição do robô 3) |

O dono trocou a ideia inicial (A, "parecido com o robô 3") pela B quando viu que
o próprio modelo já tinha as rodas no meio: "fica interessante".

## Decisão

- **Diferencial**: 2 rodas motoras no eixo central, uma de cada lado.
- **Omni fixa na frente e omni fixa atrás**, no eixo longitudinal.
- Robô **gira no lugar** em torno do centro geométrico.

## Consequências e pontos em aberto

- **Suspensão obrigatória**: sem ela, com 4 pontos rígidos, um desnível tira uma
  roda motora do chão e ela patina. Análise completa na
  [010](010-chassi-proposta.md): a recomendação atual é **rodas motoras fixas e
  mola com batente nas omnis**. A gangorra pura nas omnis não funciona nesta
  geometria (pivô em linha com o eixo, então o chassi cabeceia).
- **Chão**: liso dentro da sala; fora dela há **tapete** e **corrediça de porta**
  que ele precisa passar quando necessário. Por isso a roda precisa ter
  diâmetro razoável (≥ ~14–15 cm) e as omnis não podem ser minúsculas.
- **Centro de massa baixo**: baterias no fundo do chassi (proposta).
- **LiDAR**: as rodas, ao lado, vão tapar parte do campo de visão do LD06. Ver a
  [005](005-navegacao-nav2-ld06-imu.md).
