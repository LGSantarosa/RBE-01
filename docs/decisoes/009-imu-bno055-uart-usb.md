# 009 — IMU: BNO055 em modo UART, por adaptador USB-serial direto no NUC

**Data:** 2026-11-05
**Estado:** aceita (o dono escolheu a BNO055 e sugeriu ligar por USB).

## Contexto

No robô 1 passaram três IMUs: MPU6050, MPU6500 (vendida como "MPU9250") e
BNO055. Segundo o dono, **a BNO055 foi a melhor** ("meio carinha, mas dá pra
usar"). Como a base não tem microcontrolador ([007](007-eletrica-e-emergencia.md)),
a IMU precisa falar direto com o NUC.

## Decisão

- **BNO055** (Bosch, 9 eixos, com fusão de sensores no chip).
- **Modo UART** nativo do chip (pino **PS1 em 3,3 V**; conferir os jumpers de
  cada breakout, pois o GY-BNO055 tem relatos de lógica invertida).
- **Adaptador USB-serial de 3,3 V** (CP2102/CP2104/FTDI) → USB do NUC.
  Fiação: o TX/RX do adaptador vão nos pinos marcados SDA/SCL da placa (em modo
  UART eles viram RX/TX).
- **Driver ROS 2 pronto**: pacote `bno055` (flynneva), disponível pro **Jazzy**,
  com `connection_type: uart`, porta padrão `/dev/ttyUSB0`, 115200 baud.
  Usar regra udev pra dar nome fixo (`/dev/imu`).

## ⚠️ Magnetômetro: não usar pro rumo (proposta)

Os motores de cubo têm **ímãs permanentes grandes** a poucos centímetros, e o
robô vai passar perto de estrutura metálica de mesa. O magnetômetro vai ser
puxado por eles (no robô 1 já existia a flag `use_imu2_heading:=false` por causa
de EMI). Portanto:

- usar o modo de fusão **IMU** do BNO055 (giroscópio + acelerômetro, rumo
  relativo), **não o NDOF** (que usa o magnetômetro);
- o rumo absoluto vem do mapa (AMCL/LiDAR), não da bússola;
- montar a IMU **no centro, presa firme e plana**, o mais longe possível dos
  motores e dos cabos de potência.

## Calibração por robô

O raio efetivo das rodas e a bitola efetiva variam com pneu, carga e fabricação.
Calibrar **raio e bitola em cada unidade**, comparar odometria com deslocamento e
giro medidos e guardar os parâmetros por número de série. A IMU e o LiDAR servem
para validar a calibração, não para esconder erro sistemático da cinemática.

## Descartado

- **MPU6050 / MPU6500**: sem fusão no chip, I²C (precisaria de micro), histórico
  ruim no robô 1.
- **BNO055 por I²C**: exigiria microcontrolador ou adaptador USB-I²C; a UART
  nativa é mais simples.
- Trocar por BNO085 ou IMU USB comercial: possível no futuro, mas sem motivo
  agora; a BNO055 já foi validada pelo time.

## Fontes

- Pacote `bno055` Jazzy (conectores UART/I²C): https://docs.ros.org/en/ros2_packages/jazzy/api/bno055/bno055.connectors.html
- Índice ROS: https://index.ros.org/p/bno055/
- Notas de fiação UART/CP2104: https://github.com/whyscience/bno055
