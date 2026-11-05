# 000 — Projeto independente, continuação do robô 1

**Data:** 2026-11-05
**Estado:** aceita (decisão do dono)

## Contexto

Existem dois robôs anteriores no workspace:

- **Robô 1, `Controle_robo_web`**: protótipo do robô educativo da sala criativa.
  É um skid-steer de 4 rodas de hoverboard, com duas placas hover e uma Arduino
  MEGA no meio, Raspberry Pi, LD06, IMU, Nav2 com click-to-go e uma cara web
  (`face_web`). Ele começou com 2 rodas motoras e passou pra 4. Com o tempo foi
  acumulando camadas pra compensar o hardware: um `path_follower` próprio, o
  `unstuck_supervisor`, o `motion_guard`, uma zona morta de giro de 1,7 rad/s,
  patinagem no point-turn e sensores que entravam e saíam (PMW3901, MPU9250/6500).
- **Robô 3, `Controle_robo_livox_robo3`**: diferencial, com 2 rodas de hover na
  frente e uma roda traseira. Usa `ros2_control` falando direto com a placa hover,
  sem micro no meio, mais Livox Mid-360 e NUC. Projeto de pesquisa (PIBIT).

## Decisão

O RBE-01 é a **continuação do robô 1**, porque é o mesmo propósito: o robô
educativo da sala criativa. Mas é um projeto **completamente solto** dos outros
dois:

- é um repositório novo, **sem histórico herdado** (não é clone nem fork);
- **nenhum código copiado** por padrão. Se algo for reaproveitado, ele entra como
  decisão explícita neste diretório;
- não tem pacote ROS, launch nem configuração compartilhada com os outros robôs.

## O que herdamos (só lições)

| Lição | De onde veio |
|---|---|
| Skid-steer de 4 rodas briga com o giro: zona morta, patinagem, arco que não funciona | robô 1 |
| Microcontrolador no meio da tração = mais um protocolo, mais um firmware, mais um ponto de falha | robô 1 (MEGA) |
| Velocidade em **unidades SI** direto no controlador, sem escada de ganhos entre nós | robô 3 (decisão 003 de lá) |
| Roda traseira **boba que arrasta** deixa o rumo instável; com **omni fixa** (sem arrasto) o robô 3 ficou bom de verdade | robô 3 (relato do dono) |
| Yaw tem que vir da IMU, não da roda; no sim, inclusive | robô 1 (2026-08-26) |
| LD06 é bom e barato | robô 1 |
| Duas baterias separadas (tração / computação) | robô 1 e robô 3 |

## Descartado

- **Fork do robô 1** e ir limpando: traria junto todo o acúmulo de remendo, que é
  exatamente o que este projeto quer evitar.
- **Partir do robô 3**: o propósito é outro (pesquisa com LiDAR 3D) e o hardware
  também.
