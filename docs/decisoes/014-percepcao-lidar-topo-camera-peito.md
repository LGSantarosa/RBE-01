# 014 — Percepção: LD06 no topo da cabeça + câmera de profundidade no peito

**Data:** 2026-11-09
**Estado:** aceita (escolha do dono). O modelo da câmera e a altura exata estão
em aberto.
**Substitui:** a posição do LD06 "baixo, numa fresta da base" proposta na
[005](005-navegacao-nav2-ld06-imu.md) e na [010](010-chassi-proposta.md).

## Contexto

Com o LD06 baixo (~15 cm, na frente), a torre do rodízio da omni da frente
(276 mm, [010](010-chassi-proposta.md)) e as rodas motoras tapariam boa parte do
campo. A [revisão externa](../revisoes/2026-11-05-revisao-externa.md) (ponto 3)
já apontava o risco da fresta e lembrava que o LiDAR não pode ser a única
proteção.

## Opções consideradas

| Opção | Resultado |
|---|---|
| LD06 baixo, numa fresta da base | descartada: rodízio e rodas tapam o campo |
| LD06 no meio do corpo, com fresta de 360° (o "cinto") | descartada pelo dono |
| LD06 no meio do corpo, atrás de janela transparente | descartada: reflexo da janela vira ponto falso; risco e sujeira |
| Dois LD06 (topo + meio do corpo) | descartada: o do meio cai num dos casos acima |
| **LD06 no topo da cabeça + câmera de profundidade no peito** | **escolhida** |

## Decisão (do dono)

- **LD06 no topo da cabeça** (~70 cm). Nada fica acima dele: 360° livres, sem
  máscara de rodas nem de rodízio. A cabeça **não se mexe**, então ele fica fixo
  no robô (TF estática).
- **Câmera de profundidade na barra do peito**, olhando pra frente e pra baixo,
  pra enxergar o que fica abaixo do plano do LiDAR: mochila, pé, perna de cadeira,
  criança sentada no chão e a borda da mesa. Entra no costmap do Nav2 como nuvem
  de pontos (camada de voxel), por USB no NUC.

Papéis:

| Sensor | Uso |
|---|---|
| LD06 (topo) | mapa e localização (AMCL/SLAM); obstáculos na altura dele |
| Câmera (peito) | obstáculos baixos à frente; aproximação da mesa |

## Por que funciona

- A 70 cm o LD06 fica acima da bagunça de cadeiras e mochilas e vê paredes e
  móveis: localização mais estável.
- **Cabeceio:** com a mola macia do rodízio, uma frenagem inclina o robô ~4°.
  A 15 cm o plano do laser tocaria o chão a ~2 m; a 70 cm, a ~9 m.
- O robô gira no próprio centro e só anda de lado se girar antes; a câmera vê o
  que está à frente antes de ele ir pra lá, e a camada de voxel guarda o que já
  foi visto durante o giro.

## Consequências e cuidados

- **Mesas no plano do laser:** mesa infantil tem ~55–65 cm. Se as mesas da sala
  estiverem perto de 70 cm, o laser raspa no tampo e a leitura fica instável.
  **Medir as mesas e cadeiras da sala** antes de fixar a altura.
- **Docagem de ré:** os contatos ficam na traseira ([004](004-estacao-de-carga-autonoma.md))
  e a câmera olha pra frente. O alinhamento final usa o LD06, então o **alvo da
  estação precisa ficar na altura do LiDAR** (~70 cm).
- **Traseira sem visão baixa:** a ré só acontece na docagem. Fica coberta pelo
  para-choque (abaixo) e pela manobra curta e lenta.
- **Abaixo do plano, dos lados e atrás**, a única proteção é o contato. O
  LiDAR e a câmera não são proteção de segurança sozinhos.

## Proposta do assistente (a validar)

- **Para-choque físico** na saia da base, com chave ligada na **entrada X1 do
  ZLAC8015D** como parada rápida: para sem micro e sem software. É a proteção de
  último recurso pedida na revisão (ponto 2). Precisa ser decidido junto com o
  freio do e-stop ([007](007-eletrica-e-emergencia.md)).

## Em aberto

- **Modelo da câmera:** USB no NUC, alcance mínimo curto (ver o pé perto do
  robô), campo que pegue o chão desde perto da base, driver ROS 2 Jazzy, dar pra
  comprar 6 iguais. Vale ver se a mesma câmera serve depois pro reconhecimento
  da criança.
- Altura e inclinação da câmera no peito (que distância do chão ela cobre).
- Altura final do LD06, depois de medir as mesas.
- Desenho do topo da cabeça pra nada do capacete cruzar o plano do laser.
