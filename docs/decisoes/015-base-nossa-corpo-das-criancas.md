# 015 — A base é nossa, o corpo é das crianças

**Data:** 2026-11-10
**Estado:** aceita (escolha do dono e do time). As medidas e os limites são
proposta do assistente e ainda precisam ser validados.
**Muda:** a parte de cima do chassi da [010](010-chassi-proposta.md) e a
montagem dos sensores da [014](014-percepcao-lidar-topo-camera-peito.md).
**Apresentação:** https://claude.ai/artifact/XmZhHhXqM3zNK3EUs9yJVv

## Contexto

O time gostou da apresentação e propôs que **as crianças criem e decorem o
corpo do robô**, como projeto delas na sala criativa. Nós fazemos a base móvel e
a estrutura, e elas fazem o resto. O robô tem que **funcionar com qualquer corpo**
que elas fizerem, e as posições já decididas podem mudar pra isso.

O medo do dono é o corpo das crianças fazer o robô parar de funcionar: tapar um
sensor, ficar pesado demais, ficar largo demais ou alguém mexer na elétrica.

## Princípio

> **Regra no papel, criança não segue. Barreira física segue.**

Tudo o que faz o robô funcionar fica numa **área nossa e fechada**, e o corpo
das crianças não tem como alcançar. O que não dá pra barrar fisicamente, como
tapar o sensor com a mão, o **software detecta, e o robô para**.

## Decisão

### 1. Base fechada (nossa)

- Tudo o que é elétrico e de controle fica **dentro de uma caixa fechada**:
  rodas, rodízios, baterias, driver, relé, fusíveis, IMU, **NUC e conversores**,
  e-stop, contatos de carga, para-choque, batentes e para-lamas.
- **Muda a 010:** o NUC e os conversores saem do deck de ~30 cm, que era área
  aberta, e ficam dentro da base. A base fecha em **~20 cm** (atualizado em
  2026-11-10; antes era ~30–35 cm por causa da torre de 276 mm do rodízio de
  portão).
- **Módulo próprio da omni** no lugar do rodízio de portão: suporte fixo em
  cima, **2 hastes Ø8** descendo ao lado da roda, **buchas LM8UU** nas placas do
  garfo, **molas** entre bucha e suporte (~4 N/mm cada, pré-carga ~2 kg, curso
  ~10 mm), anel embaixo limita a descida. Omni reta, sem giro, **~13 cm** de
  altura. Rodas motoras internas, como na 010–012.
- A **placa de interface fica em cima da base e é fixa**: faz parte da
  estrutura, segura o mastro e o corpo, e nunca sai. Tem furos ou trilhos em
  posições padrão, onde o corpo é fixado. A criança constrói sobre a placa e
  nunca fura a base.
- **Acesso à elétrica pelos painéis da frente e de trás** da base (dono,
  2026-11-10: mexer na elétrica não pode exigir desmontar o corpo delas). Os
  painéis saem sem tocar no corpo e fecham com **fecho que pede chave ou
  ferramenta**: o adulto abre em segundos, a criança não. O que se mexe mais
  (fusíveis, portas do NUC, conectores do driver e das baterias) fica **perto do
  painel de trás**. E-stop, contatos de carga, para-choque e batentes ficam na
  parte fixa, não nos painéis.
- **Botão de emergência na parede de trás da base** (dono, 2026-11-10): no meio
  da moldura fixa, acima do painel, virado pra trás, com **anel de proteção**
  contra toque sem querer. Nada fica saindo pra cima da placa, e o corpo das
  crianças não chega perto. Fica a ~30 cm do chão (o adulto se abaixa um pouco). Alternativa, se o layout pedir: o NUC e o driver
  numa **gaveta** que desliza pela traseira.
- Ventilação do NUC, e-stop e contatos de carga ficam na base, abaixo da placa,
  fora da área das crianças.

### 2. Mastro de sensores (nosso)

- Uma **coluna rígida** que sai do centro da base e atravessa o corpo.
- **LD06 no topo do mastro** (~70 cm, como na 014). Ele **pode fazer parte da
  cabeça das crianças**, como o topinho dela (dono, 2026-11-10): a cabeça sobe
  até a base do sensor, com o topo caindo pras bordas pra o laser não raspar
  quando o robô inclina. O datasheet pede a **janela óptica exposta**: qualquer anteparo na frente
  dela prejudica a medição. Por isso, **nada nosso nem delas na altura da
  janela**, nem anteparo transparente.
- **Câmera de profundidade presa no mastro, na altura do peito** (dono,
  2026-11-10), olhando por um **furo no peito do corpo delas**, sem nada na
  frente. Presa no mastro, a TF continua estática seja qual for o corpo. A
  primeira ideia, um "nariz" saindo pra fora do corpo, foi trocada pelo peito.
- O LD06 é uma caixinha fechada (38,59 × 38,59 × 33,30 mm, IPX4), então ninguém
  segura o rotor. O risco é **tapar a janela**, e isso é tratado no software
  (item 4). O que sobra de físico: **fixação firme** do LD06 e **cabo preso**
  no mastro, pra não arrancar num puxão.

### 3. Corpo (das crianças)

Elas fazem o que quiserem, dentro de um envelope:

| Regra | Valor proposto (a validar) | Por quê |
|---|---|---|
| Largura | dentro da projeção da base (50 × 50 cm) | o footprint do Nav2 é fixo |
| Cabeça | sobe até a base do LD06, topo caindo pras bordas; a janela fica livre | cabeceio de ~4° na frenagem não pode fazer o laser raspar |
| Peso | até ~3 kg | tombamento ([010](010-chassi-proposta.md), [011](011-batentes-antitombo.md)) e energia de batida |
| Câmera | furo no peito, cone de visão aberto | sem acrílico na frente: reflexo vira ponto falso (014) |
| Nada pendurado | fita, tecido ou antena que balance | entra no plano do laser, na câmera ou na roda |
| Material | leve e sem ponta | criança e robô juntos na sala |
| Fixação | só na placa de interface, com fixação rápida | tira o corpo e a base continua andando |
| Saia | o corpo não desce pelas laterais da base | os painéis de acesso ficam livres |

### 4. Vigias no software (NUC)

Pro Nav2, um sensor tapado **não parece obstáculo**: pontos a 2–5 cm caem dentro
do contorno do robô e o costmap descarta. O robô andaria cego. Por isso há um
vigia separado, que trata isso como **sensor cego**:

| O que ele vê | Significado | Ação |
|---|---|---|
| Muitos pontos do LD06 colados (dentro do raio do mastro) num setor | mão, adesivo ou enfeite tapando | **para e avisa** |
| Setor sem retorno ou com intensidade muito baixa | janela coberta ou suja | **para e avisa** |
| Velocidade de giro fora da faixa, scan parado ou erro de CRC | sensor com problema | **para** |
| Imagem da câmera quase toda colada ou sem profundidade | câmera tapada | **para e avisa** |
| Tudo normal de novo | destapou | volta a andar |

O mesmo vigia faz o **autoteste ao ligar**. Se o corpo estiver encostando no
plano do laser ou entrando no cone da câmera, ele acusa antes de o robô sair.

### 5. Porta de acessório (proposta, a validar)

As crianças vão querer luz e som. Em vez de abrirem a base, a placa de interface
tem **uma porta USB de 5 V com fusível próprio**. A [007](007-eletrica-e-emergencia.md)
continua valendo: a base em si não tem LED.

## Para a sala criativa

As regras viram parte do projeto delas, como num projeto de engenharia de
verdade:

- **Mapa de cores** pintado na base e no mastro: **vermelho** não pode tapar,
  **amarelo** pede cuidado, **verde** está livre.
- **Gabarito físico** do envelope: se o corpo cabe no gabarito, a largura e a
  altura estão aprovadas.
- **Balança**: o corpo é pesado antes de montar.
- **Inspeção**: passa no gabarito, passa na balança, e o robô liga e passa no
  autoteste. Elas mesmas aprovam o robô delas.
- Fazemos um **corpo de referência** nosso, pra testar a base e servir de
  exemplo.

## Opções consideradas

| Opção | Resultado |
|---|---|
| Sensores no corpo, com regras pras crianças | descartada: o corpo muda, a TF muda, e regra no papel falha |
| LiDAR baixo, numa faixa livre entre a base e o corpo | descartada: volta no "cinto" da 014, as colunas do corpo tapariam o laser e perde a vantagem dos 70 cm |
| Chapéu com pilares em cima do LD06 | descartada: o LD06 é fechado (ninguém trava o rotor) e os pilares tapariam a janela |
| **Base fechada + mastro de sensores + corpo livre + vigias** | **escolhida** |

## Em aberto

- Altura da base fechada e desenho da placa de interface (padrão de furos ou
  trilho, tipo de fixação rápida).
- Painéis de acesso: tipo de fecho, e se as baterias saem pelos painéis ou
  precisam de gaveta.
- Perfil do mastro, rigidez (o LD06 não pode balançar) e passagem dos cabos.
- Peso máximo do corpo: refazer a conta do tombamento com o corpo em cima.
- Altura da janela do LD06 no sensor real e altura final (medir as mesas, 014).
- Modelo da câmera, altura no peito e tamanho do furo (014).
- Limites do vigia (raio, tamanho do setor, tempos), ajustados na bancada.
- Faixa de idade das crianças: define a fixação (parafuso borboleta, ímã ou encaixe).

Fonte: [datasheet do LDROBOT LD06](https://enacrobotique.github.io/doc/datasheets/LDROBOT_LD06_Datasheet.pdf)
(seção 3, "Optical Windows and Mechanical Dimensions").
