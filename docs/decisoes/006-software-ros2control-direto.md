# 006 — Software da tração: `ros2_control` falando direto com o ZLAC8015D

**Data:** 2026-11-05
**Estado:** proposta do assistente, aceita junto com a tração ("me parece bom").
A distro ROS e a biblioteca exata estão em aberto.

## Decisão

```
Nav2 ──/cmd_vel (SI)──► diff_drive_controller ──► hardware interface ZLAC (nossa)
                                                     │  Modbus RTU, 50 Hz
NUC ──USB──► adaptador USB-RS485 ──A/B──► ZLAC8015D ─┴─► motor E / motor D
```

- **Sem microcontrolador na tração** (diferente do robô 1, onde era a MEGA). O
  NUC fala direto com o driver.
- Uma **interface de hardware `ros2_control`** que, a cada ciclo (~50 Hz):
  - escreve as duas velocidades numa escrita só (`0x10` em `2088h/2089h`, rpm);
  - lê posição (`20A7h–20AAh`, contagens) e velocidade (`20ABh/20ACh`, 0,1 rpm);
  - lê, com menos frequência, tensão, temperatura e falhas.
- **`diff_drive_controller`** padrão faz a cinemática e a odometria das rodas.
- Velocidade em **unidades SI** ponta a ponta, **sem escada de ganhos** entre
  nós (lição do robô 3).
- O próprio driver garante a malha de velocidade, a rampa e o **watchdog** de
  comunicação (`2000h`, baixar de 1000 ms pra ~200 ms).

## Referência de código existente

- [`JosefGst/zlac_ros2`](https://github.com/JosefGst/zlac_ros2): biblioteca C++
  de comunicação com o ZLAC8015 pra ser usada dentro de uma hardware interface.
  CI lista foxy/humble/iron/rolling (**não lista Jazzy**). Usar como referência ou
  dependência, a decidir na hora do plano.

## Descartado

- **MEGA/micro na tração** (robô 1): mais um firmware e mais um protocolo, sem
  ganho, já que o driver fecha a malha sozinho.
- **Nós Python caseiros de cinemática** (`cmd_vel_to_wheels` do robô 1).

## Em aberto

- Distro: **ROS 2 Jazzy** (a mesma dos outros robôs) é o palpite padrão.
- Ainda pode existir um micro pra **LEDs, botões e IMU**. Esse é o próximo tema.
