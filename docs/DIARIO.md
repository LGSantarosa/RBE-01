# Diário

## 2026-11-05 — Nascimento do projeto: idealização da base

Conversa de idealização entre o dono e o assistente.

- **Ponto de partida:** criar uma base de 2 rodas motoras + roda de apoio, "parecida
  com o robô 3", mas como continuação do robô 1 e **solta dos outros dois**.
- **Uso:** sala de aula com crianças e professor. Ele vai até a mesa de uma
  criança, identifica, para de frente e conversa. Essa interação fica pra depois.
- **Lição do robô 3** (dono): ele só ficou bom com **roda omni** atrás, sem arrasto.
- **Corpo:** ~70 × 50 cm, gordinho, pesado de propósito. O conceito (`RBE-01.skp`)
  tem as rodas **no meio** da lateral, então a cinemática mudou pra rodas centrais
  + omni na frente e atrás (dono: "fica interessante").
- **Chão:** liso na sala, tapete e corrediça fora dela.
- **Bateria:** 4 h de uso, 2 h de recarga, duas iguais. Carga em **estação
  autônoma**.
- **Motor:** o hover foi rejeitado (forte e pesado demais). O motorredutor DC
  foi rejeitado por **chiado**. Três anúncios avaliados e descartados (cubo de
  aspirador de 74 mm, cubo de patinete 8" 350 W, controlador BLDC com controle
  remoto). O hover com a placa do robô 1 voltou como opção barata, mas perdeu
  pela **reprodutibilidade em 5 robôs** (a placa varia, e o hack só roda numa).
  **Escolhido o cubo servo AGV ZLTECH 5,5" + ZLAC8015D.**
- **Integração verificada no manual RS485 v1.04:** modo velocidade, escrita
  síncrona das duas rodas em rpm, feedback de posição e velocidade, watchdog de
  comunicação, entrada X0 = parada rápida. Sem micro na tração.
- **Disponibilidade:** sem distribuidor no Brasil; comprar 6 kits do mesmo lote.

- **Elétrica:** parecida com o robô 1. **Botão de emergência na traseira** que
  derruba só as rodas; **sem LED**. Com isso a base fica **sem nenhum
  microcontrolador** (IMU por USB direto no NUC).

- **Relé automotivo** do e-stop aprovado.
- **Baterias LiFePO4** (proposta aceita): 8S ~10 Ah, BMS ≥ 30 A / 60 A pico pra
  "aguentar as paradas". Condição: confirmar que o ZLAC8015D aceita ~20 V.

- **IMU:** BNO055, a melhor do robô 1 segundo o dono, em **modo UART** com
  adaptador USB-serial (ideia do dono). Existe driver ROS 2 Jazzy pronto. Sem
  magnetômetro no rumo por causa dos ímãs dos motores de cubo.

- **Chassi:** a equipe tem impressão 3D e laser de MDF/acrílico, mas não solda
  metalon nem corta aço. A proposta A (aço soldado embaixo como lastro, colunas
  de alumínio, decks MDF/acrílico, suspensão de braço com mola) depende de
  serviço externo de solda e corte; a B (só alumínio) evita a solda; e a C (só
  MDF) foi descartada. Montada uma apresentação de 17 slides pro time opinar.

- **Apresentação revisada** (pedido do dono): saíram os slides de cenário,
  lições, perguntas e próximos passos (ficou com 16). A suspensão virou 4 slides:
  o problema, a mola nas motoras, a gangorra e o recomendado. Achado: **a gangorra
  pura cabeceia** no losango (rodas e pivô na mesma linha). Recomendação nova:
  **rodas motoras fixas, mola com batente nas omnis**.

- **Suspensão por dentro:** slides novos explicando por que a mola nas omnis
  resolve e a "janela" da mola. Mola revisada pra ~8 N/mm (faixa 6–12) +
  amortecedor a óleo (sem ele, ~2 Hz de balanço). Pesquisa: não existe omni
  com suspensão pronta; o padrão de AGV leve é guia vertical + mola. Proposta:
  hastes de 8 mm + LM8UU + coilover RC 1/8 + batente de PU; omni de alumínio
  ≥ 40 kg.
- **Achado:** o e-stop cortando o driver tira o freio (o robô rola 30–50 cm).
  Pendente com o dono (ver 007).
- **Slide "RBE-01 por dentro":** o astronauta translúcido com toda a base
  desenhada por dentro, no fim da apresentação (19 slides).

- **Módulo da omni em corte** (slide 20): fica dentro do casco, num bolso da
  bandeja; torre de ~20 cm por causa do coilover, então o LiDAR vai na frente.
  Lista de peças numerada na 010.

- **Suspensão da omni: rodízio de portão com mola, pronto** (escolha do dono).
  Mola de 0,5 a 8 kg, na faixa da omni. Tira a roda de borracha e põe a omni.
  O módulo próprio virou plano B. Comprar 2 pra bancada.
  Pelas fotos da loja: o garfo é **giratório** (precisa travar) e a mola fica
  exposta num suporte em C. Fotos e desenho com as medidas no slide 17.

- **Revisão externa** da apresentação (em `docs/revisoes/`). Achou um **erro
  meu no tombamento**: o apoio é um losango e a borda fica a ~11 cm, não 22, então
  são ~5,5 kgf na diagonal, não 11. Corrigido nos slides 7 e 20 e na 010. Os
  outros pontos foram triados na revisão.

- **Antitombo decidido:** sapatas de UHMW/nylon nos 4 cantos (011), com folga
  = obstáculo medido + tolerância; critério de ≥ 10 kgf medido em qualquer
  direção. Slide 21 novo, e os batentes entraram na vista de cima.

- **Para-lama nas rodas** (dono): proteção em cima pra criança não enfiar a mão
  (012). Batentes e para-lamas entraram no slide "por dentro".

Próximo: medir a corrediça e o tapete; comprar 2 rodízios e medir; trazer a opinião do time; o dono decide o
freio do e-stop.

## 2026-11-09 — Consolidação da revisão externa

- Corrigidos os textos antigos que ainda tratavam como abertas decisões já
  fechadas sobre suspensão, bateria, IMU e ausência de microcontrolador.
- O deck do NUC subiu de ~26 cm para **~30 cm**, acima do rodízio de portão de
  276 mm.
- O limite de velocidade passou a ser configurado também no driver (`2008h`):
  ponto de partida de **~55 rpm / 0,4 m/s** perto de crianças; o perfil de
  corredor (~82 rpm / 0,6 m/s) depende de validação de segurança.
- Registrada na 008 a verificação da **regeneração do ZLAC com o BMS**, incluindo
  o risco de sobretensão no barramento durante a frenagem.
- Registrada a calibração de raio e bitola por unidade e reformulada a pergunta
  ao time: a suspensão está escolhida; agora é preciso avaliar os riscos da
  adaptação do rodízio (trava do giro, carga lateral, folga e amortecimento).
- Revisão externa: pontos **1, 5, 6 e 9 resolvidos**; continuam abertos **2, 3,
  4, 7, 8 e 10**.

Próximo: decidir o freio do e-stop; validar campo de visão do LiDAR e rodízios;
detalhar docagem, fabricação e matriz de requisitos.

- **Percepção (014):** o rodízio da frente tapava o LD06 baixo. Fresta no corpo
  e janela transparente foram descartadas pelo dono. Ficou **LD06 no topo da
  cabeça** (cabeça fixa, 360° livres) pra mapa e localização, e **câmera de
  profundidade no peito** pro que é baixo (mochila, pé, mesa). Para-choque na
  X1 do ZLAC ficou como proposta. Falta medir as mesas da sala e escolher a
  câmera. Revisão externa: ponto 3 resolvido.

- **Rodízio com a omni reta** (dono): a omni fica alinhada embaixo do eixo, sem
  o deslocamento do garfo giratório. Travar o giro não basta; o garfo precisa
  ser trocado ou adaptado. Registrado na 010 e na pendência da bancada.
  Desenho do slide 9 corrigido.
