# Estado do Projeto — RBE-01

> Documento vivo. O que está decidido, o que está aberto e o que vem a seguir.
> Atualizado em **2026-11-05**.

## Fase

**Idealização da base móvel.** Não existe código nem hardware ainda. As decisões
estão em `docs/decisoes/`, e o design consolidado (em construção) em
`docs/design/2026-11-05-base-movel.md`.

## Decidido

- 000 Projeto independente, continuação do robô 1
- 001 Diferencial, rodas no meio, omni na frente e atrás
- 002 Tração ZLTECH 5,5" + ZLAC8015D
- 003 Duas baterias iguais (tração / computação)
- 004 Estação de carga autônoma
- 005 Nav2 + LD06 + IMU, NUC
- 006 `ros2_control` direto no driver

## Próximo tema da conversa

**IMU, LEDs e botões**, e se ainda precisa de um microcontrolador pra eles.

## Pendências de compra/verificação

- [ ] Cotação de **6 kits** ZLTECH (ZLLG55ASM150 + ZLAC8015D), mesmo lote
- [ ] Faixa de tensão de alimentação do ZLAC8015D (manual de hardware)
- [ ] Largura e versão (V2.0/V2.07) do motor; cabos inclusos

## Em aberto

Ver a §8 do design.
