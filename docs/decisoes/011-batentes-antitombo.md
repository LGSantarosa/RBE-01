# 011 — Batentes antitombo nos quatro cantos

**Data:** 2026-11-05
**Estado:** aceita (escolha do dono, depois da [revisão externa](../revisoes/2026-11-05-revisao-externa.md)).
**Corrige:** a conta do tombamento da [010](010-chassi-proposta.md).

## Contexto

Com rodas motoras a ±21 cm e omnis a ±13 cm, os apoios formam um losango, e a
borda mais próxima fica a ~11 cm do centro. Empurrando na diagonal no topo, um
robô de 35 kg tomba com **~5,5 kgf**. Lastro ajuda pouco.

## Opções

| Opção | Pior caso (35 kg) | Resultado |
|---|---|---|
| Nada (losango) | ~5,5 kgf | descartada |
| Omnis mais pra fora (±20 cm) | ~7,3 kgf | descartada: ganha pouco |
| 4 omnis suspensas nos cantos | ~9 kgf | descartada: 4 suspensões pra regular, mais ruído e resistência no giro |
| **Batentes antitombo nos cantos** | **~10,5 kgf** (estimativa geométrica) | **escolhida** |
| Roletes antitombo nos cantos | ~10,5 kgf | segunda escolha, se as sapatas raspar na corrediça |

## Decisão

- As **duas omnis continuam** só pra apoio e suspensão. Cinemática e odometria
  não mudam.
- **4 sapatas deslizantes arredondadas**, presas direto na bandeja de aço, perto
  do limite do corpo (**±21–22 cm**).
- Material: **UHMW, nylon** ou similar. **Face de baixo inclinada** pra não
  agarrar na corrediça. **Trocáveis por parafuso**. Dimensionadas pra aguentar o
  peso do robô inteiro com impacto.
- **Folga = maior obstáculo medido no piso + tolerância de fabricação e flexão.**
  Não é um número fixo. Com uma corrediça de 10 mm, a bancada começa com
  **13–15 mm**. Quanto menor a folga, menos o robô inclina antes de o batente
  entrar.

## Critérios de aprovação no protótipo

- Não raspa nos obstáculos definidos (passagem reta, diagonal e durante o giro).
- Não agarra durante o giro.
- **Força de tombamento medida ≥ 10 kgf em qualquer direção.** Os ~10,5 kgf são
  estimativa geométrica: com a folga, o robô inclina antes do contato e o centro
  de massa se desloca.
- Batente sem deformação permanente depois do ensaio.

Se as sapatas não passarem na corrediça, a troca é por **roletes antitombo**.
Não colocar 4 omnis suspensas antes de testar a solução passiva.
