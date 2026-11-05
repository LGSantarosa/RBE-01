# 004 — Estação de carga autônoma

**Data:** 2026-11-05
**Estado:** aceita no conceito (decisão do dono). O desenho está em aberto.

## Decisão (do dono)

O robô **vai sozinho até a estação de carga e encaixa**. Ninguém liga cabo na mão.

## Opções consideradas

| Opção | Resultado |
|---|---|
| Cabo na mão | descartada pelo dono |
| **Estação com contatos, encaixe autônomo** | **escolhida** |

## Propostas do assistente (a validar)

- **Contatos na traseira**: ele entra de ré e a frente (câmera, cara) fica
  livre pra sala.
- **Alvo pro LiDAR na estação** (formato em V ou padrão refletivo) pro
  alinhamento final. O Nav2 leva até perto e uma manobra curta de docking
  encaixa (existe o `opennav_docking` no Nav2 pra isso).
- Os contatos e o encaixe precisam ser **seguros pra criança**: sem tensão
  exposta quando o robô não está encaixado (contatos energizados só quando
  detecta robô).
- A estação precisa carregar **as duas baterias** (dois carregadores, ou um com
  chaveamento). A definir junto com a [003](003-energia-duas-baterias.md).

## Em aberto

- Lado dos contatos, tipo de contato (mola/pogo, lâminas), corrente de carga.
- Como detectar que encaixou (tensão nos contatos, corrente, chave).
- Se o PC fica ligado durante a carga (provavelmente sim).
