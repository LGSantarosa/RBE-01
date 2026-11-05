# 005 — Navegação: Nav2 + LiDAR 2D LD06 + IMU, mini PC tipo NUC

**Data:** 2026-11-05
**Estado:** aceita (decisão do dono). O modelo da IMU e o do PC estão em aberto.

## Decisão (do dono)

- **Nav2** pra navegação, como no robô 1.
- **LiDAR 2D LDROBOT LD06**, o mesmo do robô 1 ("muito bom e barato").
- **IMU** pra dar firmeza no rumo e nas curvas, como no robô 1.
- **Mini PC tipo NUC** (não Raspberry Pi).

## Velocidade (proposta do assistente)

- **~0,4 m/s no máximo perto de criança**, que é o passo lento de uma pessoa.
- Um pouco mais (~0,6 m/s) no corredor vazio, se for útil.

## Descartado

- **Raspberry Pi**: o dono escolheu NUC. A Pi 4 do robô 1 vivia no limite (colcon
  com 2 workers etc.), e o corpo vai pedir visão (reconhecer a criança).
- **LiDAR 3D (Livox)**: é do robô 3; caro e desnecessário pra sala.
- **Optical flow (PMW3901)**: deu problema demais no robô 1 e foi removido.

## Em aberto

- **Posição do LD06**: baixo, numa fresta em volta da base (proposta). As rodas
  laterais vão tapar uma parte do campo; é preciso medir e mascarar esses
  ângulos. Também é preciso ver se ele enxerga perna de cadeira e mochila no
  chão.
- **Qual IMU** e onde ela é lida (direto no NUC por USB, ou por um micro). Ver o
  próximo tema: IMU, LEDs, botões e se ainda precisa de microcontrolador.
- **Parar de frente pra mesa** com precisão: pose final com yaw (o robô 1 não
  fazia giro final de yaw).
- Modelo do NUC (CPU/RAM pensando na visão futura).
