# Estado do Projeto — RBE-01

> Documento vivo. O que está decidido, o que está aberto e o que vem a seguir.
> Atualizado em **2026-11-10**.

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
- 007 Elétrica como o robô 1, e-stop traseiro só nas rodas, sem LED, sem micro
- 008 Baterias LiFePO4 8S ~10 Ah (tensão do driver ok; falta checar a regeneração)
- 009 IMU BNO055 por UART/USB, modo IMU (sem magnetômetro)
- 011 Batentes antitombo nos 4 cantos
- 012 Para-lama cobrindo o topo das rodas motoras (requisito)
- 014 LD06 no topo da cabeça + câmera de profundidade no peito
- 015 A base é nossa, o corpo é das crianças: base fechada + mastro de sensores + vigias no software

## Em discussão

- 010 Chassi: proposta A (aço embaixo, alumínio em cima, MDF/acrílico). Apresentação pro time: https://claude.ai/artifact/4GiDdu8DLxx7WZ58rTv9yL

## Próximo tema da conversa

O time aprovou a apresentação e as crianças vão fazer o corpo (015). Próximo:
apresentar a 015 ao time (https://claude.ai/artifact/XmZhHhXqM3zNK3EUs9yJVv), definir a placa de interface e o mastro, e o
"manual do construtor" das crianças. Ainda faltam as respostas do chassi A/B.
Depois: esquema elétrico completo.

## Pendências de compra/verificação

- [ ] Cotação de **6 kits** ZLTECH (ZLLG55ASM150 + ZLAC8015D), mesmo lote
- [x] **Faixa de tensão do ZLAC8015D**: 20–48 V, subtensão 16 V (manual V2.00). A 8S cabe (008)
- [ ] **Regeneração do ZLAC8015D na frenagem** (manual não fala): perguntar à ZLTECH ou medir. Bloqueia a compra da bateria (008)
- [ ] Largura e versão (V2.0/V2.07) do motor; cabos inclusos
- [ ] **2 rodízios de portão com mola** (Castors Online, £ 25) pra bancada: giro já confirmado; travar o giro, **garfo reto com a omni embaixo do eixo** (trocar ou adaptar o garfo), curso e rigidez da mola, folga, se a omni cabe, entrega pro Brasil
- [ ] Decidir o freio do e-stop (ver 007)
- [ ] **Medir a altura das mesas e cadeiras da sala** (o LD06 a ~70 cm não pode ficar no plano do tampo, 014)
- [ ] Escolher a câmera de profundidade do peito (014)
- [ ] Medir a **janela óptica do LD06** no sensor real (015)
- [ ] Saber a **faixa de idade** das crianças da sala criativa (define a fixação do corpo, 015)
- [ ] Refazer o tombamento com o **corpo das crianças** em cima e fechar o peso máximo (015)
- [ ] Se o chassi A for escolhido, encontrar serviço externo de **solda de
  metalon e corte de chapa de aço**; a opção B evita a solda (010)
- [x] **Tombamento**: decidido, batentes antitombo nos cantos (011). Falta medir o maior obstáculo do piso pra definir a folga
- [ ] Concluir as ações da revisão externa: pontos **1, 3, 5, 6 e 9 resolvidos**;
  faltam **2, 4, 7, 8 e 10** (e-stop, rodízio, docagem, fabricação e matriz de
  requisitos)

## Em aberto

Ver a §8 do design.

## Orçamento (2026-11-10)

[docs/orcamento.md](docs/orcamento.md): R$ 11–19 mil por robô, R$ 58–100 mil nos 5 + kit de tração reserva (NUC Gigantec já temos). Base de ~20 cm com módulo próprio da omni (015).
