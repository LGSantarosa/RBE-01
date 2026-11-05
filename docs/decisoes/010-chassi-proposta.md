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
| Bandeja de aço | 4–13 cm | motores (fixos), omnis com mola, 2 baterias, driver, relé, fusíveis, IMU no centro |
| LD06 | ~15 cm, na frente, numa fresta do casco | — |
| Deck MDF/acrílico | ~26 cm | NUC, conversores |
| Colunas de alumínio | até ~50 cm | fixação do casco e da cabeça |

Vista de cima: base 50 × 50 cm, bitola ~42 cm, omnis a ±13 cm do centro, uma
bateria de cada lado do eixo pra equilibrar, e-stop e contatos de carga na
traseira.

### Suspensão (revisada em 2026-11-05)

**O problema:** com 4 apoios num chassi rígido, só 3 tocam o chão. No losango
(rodas motoras nas laterais, omnis na linha do meio), quando uma omni passa
num desnível o chassi tomba de lado sobre a linha das omnis e **uma roda motora
sai do chão**: ela patina e o robô sai do rumo. Poucos milímetros de corrediça
bastam.

| Caminho | Como | Avaliação |
|---|---|---|
| 1. Mola nas rodas motoras | braço oscilante com pivô + mola empurrando a roda; omnis fixas | funciona, mas **a tração passa a depender da pré-carga da mola** (ela precisa segurar ~12 kg por roda); o braço carrega o motor de 2 kg e o cabo; folga no pivô desalinha a roda e o robô puxa pro lado |
| 2. Gangorra nas omnis | viga ligando omni da frente e de trás, com pivô no centro do chassi | **sozinha não funciona nesta geometria**: as duas rodas motoras e o pivô ficam na mesma linha (o eixo), então nada segura o chassi de girar em volta dela e ele **cabeceia** como um robô de 2 rodas. Precisa de molas de centragem, e aí vira o caminho 3 com as omnis acopladas. A gangorra pura só funciona com apoios fora de linha (ex.: rodas motoras atrás + gangorra na frente, como o eixo pendular de trator) |
| **3. Rodas motoras fixas, mola nas omnis** | motor de cubo parafusado direto na bandeja; cada omni numa mola curta com **batente** (~10 mm de curso) | **recomendado**: tração vem do peso (CG em cima do eixo, baterias uma de cada lado); omni carrega pouco, então a mola é pequena, barata e com pouca pré-carga; sem braço, sem folga, sem desalinhar; com alguém empurrando, a omni encosta no batente e vira apoio rígido (a conta do tombamento continua valendo) |

**Por que o caminho 3 resolve:** no chassi rígido, as quatro rodas estão
travadas umas nas outras, então a omni subir na corrediça obriga o chassi a
inclinar, e uma roda motora sai do chão. No caminho 3, quem define a altura e a
posição do chassi são as **duas rodas motoras**, presas direto nele. As omnis só
acompanham o chão, com uma mola entre elas e o chassi. A omni sobe, a mola
encolhe alguns milímetros, e o chassi continua reto.

**A janela da mola** (estimativas, a confirmar na bancada; robô de ~30 kg com o
CG em cima do eixo e pré-carga de ~2 kg por omni):

| | Chão liso | Omni numa corrediça de 10 mm |
|---|---|---|
| 2 rodas motoras | ~26 kg | ~21 kg |
| Omni da frente | ~2 kg | ~7 kg |
| Omni de trás | ~2 kg | ~2 kg |

- **Mole demais:** cabeceia ao frear e bate no batente; o LiDAR balança junto.
- **Dura demais:** a omni levanta o chassi como se fosse rígida, e volta o
  problema.
- **Na medida: ~5 N/mm, 10 mm de curso.** Na frenagem de 0,5 m/s² com o CG a
  ~25 cm, o momento é 30 × 0,5 × 0,25 ≈ 3,75 N·m, ou ~29 N na omni (a 0,13 m),
  ou seja ~6 mm de afundamento, dentro do batente. Na corrediça de 10 mm, a mola
  pega ~50 N (~5 kg) das rodas motoras, que continuam com ~21 kg: tração de
  sobra.

**Mola revisada (8 N/mm, faixa 6–12) e amortecimento.** A primeira conta (5 N/mm)
exagerava o risco da mola dura: pra acelerar a 0,5 m/s² o robô precisa de só
~2 kgf de tração, e com 8 N/mm as rodas motoras ainda ficam com ~18 kg (30 kg)
ou ~28 kg (40 kg) numa corrediça de 10 mm. Frenagem: ~4 mm (30 kg) / ~5 mm
(40 kg) de afundamento. Só mola daria um balanço de ~2 Hz depois de cada
frenagem, então **precisa de amortecedor a óleo**.

**Hardware da suspensão (proposta):**
- **Não existe omni com suspensão pronta pra comprar** (pesquisa de 2026-11-05).
  O que existe pronto não serve: rodízio giratório com mola (é a roda boba) e
  rodízio fixo com mola (não desliza de lado no giro).
- O padrão de AGV de carga leve é **guia vertical com mola**: duas hastes,
  buchas lineares e mola, curso de ~±10 mm. Proposta: **2 hastes de 8 mm +
  buchas LM8UU** (peças de impressora 3D) segurando o garfo da omni, com um
  **coilover de RC 1/8** (mola + óleo, anel de pré-carga) no centro e **batente
  de poliuretano** em 10 mm.
- **Omni de alumínio com roletes de PU, 100 mm, carga ≥ 40 kg** (com alguém se
  apoiando na frente, a omni encosta no batente e carrega 30 kg ou mais; a
  Nexus de aço de 100 mm aguenta só ~10 kg). Alternativa: omni dupla.
- Alternativa ao coilover: braço arrastado de 8–10 cm, onde a posição do
  coilover no braço ajusta a dureza.

**✅ Escolha do dono (2026-11-05): rodízio de portão com mola, comprado pronto.**
"Esse negócio já pronto me faz mais feliz do que criar um." O módulo próprio
abaixo fica como **plano B**.

- Peça: *Light Duty Sprung Gate Castor (60 kg)*, Castors Online (Reino Unido),
  https://www.castors-online.co.uk/product/light-duty-sprung-gate-castor-60kg-4692
- Ficha: mola que **começa em 0,5 kg e fecha em 8 kg** (a faixa da nossa omni; o
  fechamento faz as vezes de batente), carga 60 kg, roda 100 × 27 mm de borracha,
  altura **276 mm**, aço prensado zincado, fixação por **placa lateral** de
  102 × 25 mm com furos **M10 a 57 mm**, £ 21,09 sem imposto / £ 25,31 com.
- Adaptação: **tirar a roda de borracha e montar a omni no garfo** (espaçadores
  se precisar). Fixar a placa num **suporte soldado na bandeja**.
- Consequências: com 276 mm de altura, o **deck do NUC sobe pra ~30 cm**. Sem
  amortecedor: se balançar, entra um **amortecedor de RC do lado**.
- **Mola mais macia que o ideal** (estimativa: curso de ~25 mm, o que dá ~3 N/mm,
  contra 6–12 ideal). Tração de sobra (rodas com ~23 kg na corrediça), mas afunda
  ~10 mm numa frenagem de 0,5 m/s² (~6 mm a 0,3 m/s²). Mitigação: rampa de
  frenagem suave no driver.
- **⚠️ Pelas fotos e pelo desenho técnico da loja, o garfo é de rodízio GIRATÓRIO**
  (rolamento de giro de Ø48 e deslocamento de 75 mm). O "fixed" do texto se refere
  ao suporte. O mecanismo é um **suporte em "C"** (102 mm entre os braços) com um
  **eixo vertical que desliza pelos dois braços e a mola exposta entre eles**, e
  não um tubo fechado. Placa de 25 mm com furos de Ø11 a 57 mm. Garfo de 123 mm
  de altura, roda Ø100 × 27.
  **Precisa travar o giro do garfo e do eixo** (pino ou ponto de solda); sem isso,
  volta o problema da roda boba do robô 3.
- **Comprar 2 pra bancada e conferir:** se é fixo (a página se contradiz entre
  "fixed" e "swivel"), curso e dureza da mola, se a omni cabe no garfo de 27 mm,
  diâmetro do eixo, entrega pro Brasil.
- Parecidos: Caujolle (França), mola macia e 70 mm de curso
  (https://www.caujolle.fr/en/gate-wheels-and-accessories/1922-fixed-gate-wheel-with-soft-spring-diameter-100-mm-load-75kg-to-15kg-with-70mm-travel.html);
  Keypak 57 kg na B&Q, mola não informada. Rodízios com mola comuns (RS PRO
  75 kg, R4089 100–200 kg) têm mola dura demais e ficariam rígidos.

**Plano B: módulo próprio da omni (medidas estimadas):** fica **dentro do
casco**, num **bolso recortado na bandeja**; por fora só aparece a parte de baixo
da omni. De baixo pra cima:

| # | Peça | Especificação |
|---|---|---|
| 1 | Omni | Ø100, alumínio + PU, ≥ 40 kg |
| 11 | Eixo + rolamentos | Ø8, 2× 608ZZ, no garfo |
| 8 | Mesa móvel + garfo | aço 3 mm |
| 6 | 2 batentes | anel de PU, 5 mm (curso de 10 mm pra cima) |
| 3 | 2 hastes | Ø8 retificada, ~80 mm, presas na mesa móvel |
| 4 | 2 buchas lineares | LM8UU, na mesa fixa |
| 7 | Mesa fixa | aço 3 mm, parafusada na bandeja |
| 5 | 2 anéis-trava | no alto das hastes: limitam a descida |
| 2 | Coilover RC | 1/10–1/8, óleo regulável; o anel dele acerta a pré-carga (~2 kg) |
| 9 | Ponte + espaçadores | seguram o topo do coilover |
| 10 | Bandeja | bolso recortado pro módulo |

- Altura da torre: **~205 mm** (com coilover 1/8). O **LiDAR vai na frente dela**.
  Um coilover 1/10, mais curto, baixa uns 3 cm. **Ponto a pensar.**
- Vão livre da bandeja: 40 mm.

Fontes: comparativo de suspensões de AGV
(https://blog.csdn.net/qq_38880380/article/details/122716428), patente com omni
em guia + rolamento linear + mola (US 11519112), rodízios de AGV com mola
(https://www.keystonecastors.co.uk/castors/agv-castors/shock-absorbing-dual-wheel-agv-castors/).

Cuidados do caminho 3: o centro de massa tem que ficar em cima do eixo, e a mola
tem que ser firme o bastante pra o robô não cabecear ao frear (o plano do LiDAR
inclina pouco). Rigidez e curso se acertam na bancada.

Isso **substitui** a primeira ideia (mola nas rodas motoras), que era proposta
do assistente.

### Fabricação

| Peça | Material | Como | Quem |
|---|---|---|---|
| Bandeja | metalon 20×20 / 30×20 + chapa 2 mm | serra e solda | nós |
| Suportes do motor e das omnis | chapa de aço 4–5 mm | corte a laser de chapa terceirizado (DXF) ou barra chata furada | fora / nós |
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
2. Suspensão: rodas motoras fixas com mola nas omnis (recomendado), mola nas rodas motoras ou gangorra com molas?
3. LiDAR baixo, na fresta (vê obstáculo baixo, mas as rodas tapam um pedaço), ou
   acima das rodas (vê 360°, mas perde o que é baixo)?
4. Lastro até ~40 kg vale a pena?
5. Experiência com estação de carga autônoma?
6. O que preocupa nessa base?
