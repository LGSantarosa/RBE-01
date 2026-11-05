# Design — Base móvel do RBE-01

**Data:** 2026-11-05
**Estado:** **em construção**. A conversa de idealização ainda não terminou; a
tração está fechada, e o resto da base segue em discussão (ver "Em aberto").

> Convenção deste documento: **(dono)** = decidido pelo Luiz; **(proposta)** =
> palpite/sugestão do assistente, ainda não confirmado.

## 1. Intenção

Um robô educativo pra **sala de educação criativa**, no meio de crianças e do
professor. Ele interage com as crianças usando o conteúdo da sala. O cenário-alvo
(dono): ele **vai até a mesa de uma criança, identifica quem é, para de frente e
conversa com ela**.

A interação (reconhecer, conversar, braços, visor) **fica pra depois**. Agora o
objetivo é uma **base móvel que se move bem**: confiável, silenciosa, segura perto
de criança, precisa pra parar de frente pra uma mesa e autônoma até pra
recarregar.

É a continuação do robô 1 (`Controle_robo_web`) feita "do jeito que deveria ser":
**simples e confiável desde o começo**, sem as camadas de compensação que o robô 1
foi acumulando ([000](../decisoes/000-projeto-independente.md)).

## 2. Objetivos

- Andar pela sala e **chegar a uma pose** (posição + rumo) de frente pra uma mesa.
- **4 h de operação seguida**, **2 h de recarga** (dono).
- **Ir sozinho pra estação de carga e encaixar** (dono).
- Passar **tapete** e **corrediça de porta** quando precisar (dono).
- **Não tombar** com criança empurrando ou se apoiando (dono: "tem que ser mais
  pesado mesmo").
- **Silencioso** (dono: sem chiado).
- **Reproduzível em 5 unidades**, com reposição possível (dono).

## 3. Não-objetivos (por agora)

- Reconhecimento da criança, conversa, visão, braços, visor/cara.
- Velocidade alta: não é trekking nem competição.
- Ambientes externos.

## 4. Anti-objetivos (seria fracasso mesmo funcionando)

- Repetir o robô 1: ganhar comportamento à base de remendo (supervisor de
  desencalhe, zona morta compensada, nós de cinemática caseiros, escada de ganhos).
- Um robô que assusta criança: barulhento, aos trancos, rápido ou que varre gente
  ao girar.
- Hardware que não dá pra repetir em 5 robôs.

## 5. Restrições

- **Corpo:** gordinho, **~70 cm de altura, ~50 cm de largura** (dono). Conceito em
  `docs/conceito/` (capacete/visor, barra de câmera no peito, braços, rodas
  grandes no meio da lateral).
- **Massa:** 30–35 kg estimada (proposta), concentrada embaixo.
- **Chão:** liso na sala, com tapete e corrediça fora dela (dono).

## 6. Decidido

| Tema | Decisão | Doc |
|---|---|---|
| Cinemática | diferencial, rodas motoras no **meio**, **omni fixa na frente e atrás**, gira no próprio centro (dono) | [001](../decisoes/001-cinematica-diferencial-rodas-centrais.md) |
| Motor | **ZLTECH ZLLG55ASM150**, cubo servo 5,5", 24 V, ~3 N·m, sem engrenagem (dono aprovou) | [002](../decisoes/002-tracao-zltech-hub-servo.md) |
| Driver | **ZLAC8015D**, modo velocidade, Modbus RTU/RS485 (dono aprovou) | [002](../decisoes/002-tracao-zltech-hub-servo.md), [notas](../hardware/zlac8015d.md) |
| Compra | 6 kits, mesmo lote, direto da fábrica (proposta) | [002](../decisoes/002-tracao-zltech-hub-servo.md) |
| Energia | **2 baterias iguais**: tração / computação (dono) | [003](../decisoes/003-energia-duas-baterias.md) |
| Baterias | **LiFePO4 8S (25,6 V) ~10 Ah** cada, BMS ≥ 30 A / 60 A pico (dono aceitou a proposta) | [008](../decisoes/008-baterias-lifepo4.md) |
| Carga | **estação autônoma**, ele encaixa sozinho (dono) | [004](../decisoes/004-estacao-de-carga-autonoma.md) |
| Navegação | **Nav2 + LD06 + IMU**, **mini PC tipo NUC** (dono) | [005](../decisoes/005-navegacao-nav2-ld06-imu.md) |
| Elétrica | como o robô 1; **e-stop na traseira** derruba só as rodas; **sem LED**; base **sem microcontrolador** (dono + consequência) | [007](../decisoes/007-eletrica-e-emergencia.md) |
| IMU | **BNO055 em modo UART** + adaptador USB-serial no NUC, driver `bno055` Jazzy; modo de fusão IMU, sem magnetômetro (dono + proposta) | [009](../decisoes/009-imu-bno055-uart-usb.md) |
| Software da tração | `ros2_control` direto no driver + `diff_drive_controller`, sem micro na tração, SI ponta a ponta (proposta, aceita com a tração) | [006](../decisoes/006-software-ros2control-direto.md) |

## 7. Propostas ainda não confirmadas

- Velocidade máx. **~0,4 m/s** perto de criança, ~0,6 m/s em corredor.
- **Suspensão de mola** nas rodas motoras (alternativa: gangorra nas omnis).
- Baterias no fundo do chassi.
- **Contatos de carga na traseira**, entrando de ré; alvo em V pro LiDAR.
- LD06 **baixo, numa fresta em volta da base**, com os ângulos das rodas mascarados.
- E-stop **cogumelo com trava**, acionando **relé automotivo** que corta a tração, mais contato na **entrada X0** do driver.
- ROS 2 **Jazzy**.

## 8. Em aberto (próximos temas da idealização)

1. ~~IMU~~ → [009](../decisoes/009-imu-bno055-uart-usb.md). **Esquema elétrico**: chaves, fusíveis, relé do e-stop, DC-DC do NUC.
2. **Baterias**: modelo/fornecedor, monitoramento das duas no ROS. **Depende da
   faixa de tensão do ZLAC8015D.**
3. **Suspensão e omnis**: tipo, diâmetro da omni, curso.
4. **Chassi**: material, layout interno (baterias, NUC, driver), pontos de fixação
   do corpo.
5. **LD06**: altura, campo cego das rodas, o que precisa enxergar.
6. **Estação de carga**: contatos, detecção de encaixe, carga das duas baterias.
7. **Segurança**: e-stop, corte geral, limites de velocidade/aceleração perto de
   pessoa, para-choque/detecção de contato?
8. **NUC**: modelo e alimentação.
9. Confirmações de ficha do ZLTECH/ZLAC (tensão de alimentação, largura, versão).
