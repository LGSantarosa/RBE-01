# 002 — Tração: cubo servo AGV ZLTECH 5,5" + driver ZLAC8015D

**Data:** 2026-11-05
**Estado:** aceita (o dono aprovou: "me parece bom"). Falta a cotação e a
confirmação de 2 itens da ficha.

## Requisitos

- **Silencioso**: é sala de aula. O dono **não quer chiado** de redução.
- **Andar devagar com precisão**: parar de frente pra mesa. Nada de arranque aos
  trancos nem zona morta (que foi o problema do robô 1).
- **Sem exagero**: o motor de hoverboard (350 W) foi considerado forte e pesado
  demais pro uso.
- **Reposição e escala**: dá pra fazer **5 robôs** iguais e repor peça.

### Conta de dimensionamento (estimativa do assistente)

Premissas: robô completo com **30–35 kg**, roda de ~14–15 cm, aceleração
suave (~0,5 m/s²), tapete e corrediça com margem 2×.

- Força total ≈ m·(a + g·Crr) × 2 ≈ 60 N → **~30 N por roda**
- Torque por roda ≈ 30 N × 0,07 m ≈ **2–3 N·m contínuo**
- Velocidade: 0,6 m/s em roda de 14 cm → **~80–100 rpm**
- Potência ≈ **20 W por roda** em uso normal (longe dos 350 W do hover)

## Opções consideradas

| Opção | Prós | Contras | Resultado |
|---|---|---|---|
| **Motorredutor DC 24 V planetário + encoder** (ex.: anúncio do Mercado Livre "motor redução encoder 24 V") | leve, barato, encoder com muita resolução | **chiado da redução**; precisa de driver + micro fazendo PID | **descartada** (barulho) |
| **Cubo servo AGV + driver dedicado** (ZLTECH) | **sem engrenagem = mudo**; feito pra andar devagar com precisão; driver fecha malha de velocidade; RS485/CAN | importado; mais caro | **escolhida** |
| Motor de passo com malha fechada | preciso, comando simples | barulho, esquenta parado | descartada |
| Redução por **correia dentada** (motor pequeno + GT2) | quase mudo, leve, barato | mais peça mecânica pra montar e ajustar | descartada (ficou como plano B) |
| **Hoverboard com a placa do robô 1** (firmware NiklasFauth hack) | barato, o time domina | firmware antigo (não é FOC), devagar fica grosseiro; volta a MEGA; **a placa varia entre hoverboards e o hack só roda numa versão**, então 5 robôs iguais e reposição viram loteria | descartada |
| Cubo BLDC 74 mm (AliExpress, R$ 51, "M0603B_222") | barato, sem engrenagem | é roda de robô aspirador; torque pra poucos kg; 74 mm não passa corrediça; sem driver | descartada |
| Cubo de patinete 8" 350 W com freio a tambor (AliExpress, R$ 185 + **R$ 714 de frete**) | robusto | é um hover maior: feito pra 25 km/h, devagar dá trancos; freio inútil; frete inviável | descartada |
| Controlador BLDC 36 V 350 W 2 motores + controle remoto (Mercado Livre) | barato | quase certamente é comando por acelerador/rádio, sem feedback de velocidade nem malha fechada (não deu pra abrir o anúncio) | descartada |

## Decisão

- **Motor**: ZLTECH (Shenzhen Zhongling) **ZLLG55ASM150**, cubo servo 5,5",
  24 V, 150 W.
  - ~3–3,2 N·m nominal, ~6,4–9 N·m pico (varia entre fontes/versões)
  - encoder interno (4096 linhas segundo uma listagem), ~2 kg por motor
  - Ø 130–140 mm (V2.0 vs V2.07, **confirmar a versão**)
  - carga recomendada **< 60 kg no par** (robô fica em 30–35 kg)
  - eixo de um lado só (roda em balanço, preso por suporte, sem garfo)
- **Driver**: **ZLAC8015D**, um driver para os dois motores. Modo velocidade,
  Modbus RTU por RS485 (115200), também tem CAN. Detalhes em
  [`../hardware/zlac8015d.md`](../hardware/zlac8015d.md).
- **Compra**: **6 kits** (5 robôs + 1 reserva), **numa cotação só, do mesmo
  lote**, direto da fábrica (loja ZLTECH na Alibaba).

## Por que o peso do cubo não é problema aqui

O hover foi rejeitado por "peso extra". Mas o robô **precisa** ser pesado pra
não tombar, e o motor no cubo é a massa mais baixa possível do robô. Aqui o peso
**ajuda**.

## Disponibilidade e riscos

- **Não foi encontrado distribuidor no Brasil**: tudo é importado (~3–6 semanas
  mais impostos). Reposição = **estoque de reserva em casa**.
- Existem **fabricantes similares** (3X Motion, Eriksen) com cubos 5,5" de
  3 N·m. Plano B se a ZLTECH sumir, mas o driver muda.
- Mitigação: o suporte da roda e a interface de software ficam **isolados**,
  então trocar de marca mexe numa peça mecânica e num driver de software.

## Custos (estimativas, a cotar)

- Motor: ~US$ 85–105 cada (Alibaba) → 12 motores ≈ US$ 1.000–1.300
- Kit 2 motores + driver: US$ 556 no eBay (preço de varejo)
- Ordem de grandeza por robô, com imposto: **R$ 4–5 mil** (chute do assistente)

## A confirmar antes de comprar

1. ~~Faixa de tensão de alimentação do ZLAC8015D~~ **Resolvido:** 20–48 V,
   subtensão em 16 V (manual V2.00; ver [`../hardware/zlac8015d.md`](../hardware/zlac8015d.md)).
   A 8S LiFePO4 cabe inteira.
2. **Largura** do motor (estimativa 5–6 cm) e versão (V2.0/V2.07).
3. Se o kit vem com cabos (fases + encoder) no comprimento necessário.

## Fontes

- Alibaba ZLLG55ASM150: https://www.alibaba.com/product-detail/Low-speed-high-torque-5-5inch_1600466113721.html
- Ficha ZLLG55-ASM150 V2.0: https://aifitlab.com/products/zhongling-zllg55-asm150-v2-0-motor
- Kit eBay: https://www.ebay.com/itm/395679398909
- Loja ZLTECH: https://cnzltech.en.alibaba.com/
- 3X Motion 5,5" 3 N·m: https://datasheets.globalspec.com/ds/3X-Motion-Technologies/5-5-inch-3n-m/6ea784af-bae0-4e4c-ab83-fab0db5bcb2f
- Manual RS485 ZLAC8015D v1.04: [`../referencias/ZLAC8015D_RS485_v1.04.pdf`](../referencias/ZLAC8015D_RS485_v1.04.pdf)
