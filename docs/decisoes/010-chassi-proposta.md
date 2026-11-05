# 010 — Chassi: aço embaixo, alumínio em cima, MDF/acrílico nos decks

**Data:** 2026-11-05
**Estado:** **proposta em discussão**. Vai ser apresentada ao time pra opinião;
nada aqui está aceito ainda.

Apresentação: https://claude.ai/artifact/4GiDdu8DLxx7WZ58rTv9yL

## Restrições

- **Ferramentas da casa** (dono): impressão 3D, **corte a laser de MDF e
  acrílico** (não corta metal) e solda simples.
- O dono acha o chassi "a parte mais embaçada": material e como fazer.
- Tem que segurar: ~30–35 kg com massa embaixo, suspensão nas rodas motoras
  ([001](001-cinematica-diferencial-rodas-centrais.md)), LD06 enxergando,
  e-stop e contatos de carga na traseira, base pra um corpo de 70 cm, e dar pra
  repetir 5 vezes.

## A conta do tombamento

Empurrão estático no topo: `F = m · d / h`, com `d` ≈ 0,22 m (centro até a
borda do apoio) e `h` = 0,70 m.

| Massa | Força pra tombar |
|---|---|
| 30 kg | ~9 kgf |
| 35 kg | ~11 kgf |
| 40 kg (com 10 kg de lastro) | ~13 kgf |

A altura do centro de massa não entra no empurrão estático (ela pesa em rampa,
frenagem e batida). **Só massa e largura de apoio aumentam a força**, então o
chassi pode ser o lastro. O par de motores aceita até 60 kg.

## Opções

| Opção | Como é | Prós | Contras | Resultado |
|---|---|---|---|---|
| **A** | bandeja de **metalon soldado** + **colunas de perfil de alumínio** + **decks de MDF/acrílico** no laser | o peso fica onde deve (o aço é o lastro); robusto; usa solda e laser da casa; em cima continua ajustável | solda tem que sair no esquadro; mexer na bandeja depois dá trabalho | **recomendada** |
| B | tudo em **perfil de alumínio V-slot** parafusado + chapas MDF/acrílico + lastro de aço | sem solda; fácil de ajustar e repetir; bom pro 1º protótipo | leve, precisa de lastro; perfis e conexões custam mais | alternativa |
| C | tudo em **MDF/compensado** cortado a laser, em camadas | mais barato e rápido | MDF não segura suporte de motor nem pancada, sofre com umidade, não dura em 5 robôs | descartada (no máximo maquete) |

## Proposta A em detalhe

Alturas a partir do chão (medidas são proposta):

| Camada | Altura | O que leva |
|---|---|---|
| Bandeja de aço | 4–13 cm | motores + suspensão, omnis, 2 baterias, driver, relé, fusíveis, IMU no centro |
| LD06 | ~15 cm, na frente, numa fresta do casco | — |
| Deck MDF/acrílico | ~26 cm | NUC, conversores |
| Colunas de alumínio | até ~50 cm | fixação do casco e da cabeça |

Vista de cima: base 50 × 50 cm, bitola ~42 cm, omnis a ±13 cm do centro, uma
bateria de cada lado do eixo pra equilibrar, e-stop e contatos de carga na
traseira.

### Suspensão

Braço oscilante de **chapa de aço 4–5 mm**, pivô com bucha ou rolamento e
**mola de compressão** (ou amortecedor de RC/bike) entre a bandeja e o braço.
Curso de ~1–1,5 cm. A alternativa é a gangorra nas omnis.

### Fabricação

| Peça | Material | Como | Quem |
|---|---|---|---|
| Bandeja | metalon 20×20 / 30×20 + chapa 2 mm | serra e solda | nós |
| Suportes do motor e braços | chapa de aço 4–5 mm | corte a laser de chapa terceirizado (DXF) ou barra chata furada | fora / nós |
| Colunas | perfil de alumínio 20×20 | serra + cantoneiras | nós |
| Decks e tampas | MDF 9 mm ou acrílico 5 mm | laser | nós |
| Suportes de LiDAR, IMU e cabos | PETG/ABS | impressão 3D | nós |
| Lastro | chapa/barra de aço | parafusado na bandeja | nós |
| Casco | a definir | fase seguinte | — |

### Peso estimado

Motores 4,0 · driver/relé/fusíveis 1,0 · baterias 5,5 · bandeja 7,0 ·
omnis/suspensão 2,0 · colunas/decks 3,0 · NUC/sensores/cabos 2,0 ·
casco/cabeça 6,0 → **~30 kg**.

## Perguntas levadas ao time

1. Chassi A ou B?
2. Suspensão: mola nas rodas motoras ou gangorra nas omnis?
3. LiDAR baixo, na fresta (vê obstáculo baixo, mas as rodas tapam um pedaço), ou
   acima das rodas (vê 360°, mas perde o que é baixo)?
4. Lastro até ~40 kg vale a pena?
5. Experiência com estação de carga autônoma?
6. O que preocupa nessa base?
