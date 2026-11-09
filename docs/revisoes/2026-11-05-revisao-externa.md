# Revisão externa da apresentação (2026-11-05)

Revisão das 21 páginas do PDF "RBE-01 — Base móvel", trazida pelo dono. Abaixo
está a triagem do assistente: o que procede, o que já estava coberto e o que
fazer com cada ponto.

**Veredito da revisão:** a arquitetura é coerente (diferencial central, cubos,
massa embaixo, rodas fixas com omnis suspensas), mas não está pronta pra fabricar
5 unidades. Recomenda fazer um protótipo ("muleto") primeiro. **Concordo.**

| # | Ponto | Procede? | Ação |
|---|---|---|---|
| 1 | **Tombamento errado**: os apoios formam um losango (rodas a ±21 cm, omnis a ±13 cm); a borda mais próxima fica a 13·21/√(13²+21²) ≈ **11 cm**, não 22. Pior caso (diagonal, 35 kg, topo a 70 cm): **≈ 5,5 kgf**, não 11 | **Sim, erro meu** | ✅ Corrigido nos slides 7 e 20 e na 010. Falta decidir **como alargar o apoio** (ver abaixo) |
| 2 | E-stop: botão visível e acessível (não escondido), segundo acionamento na frente ou no topo, circuito NF com rearme manual, contator DC dimensionado pro pico, entrada de desabilitação segura do driver, para-choque físico, limite de corrente e aceleração, distância de parada medida; watchdog de 200 ms = 8 cm a 0,4 m/s antes de reagir; análise de risco ISO 12100 (verificar ISO 13482 e NR-12) | Sim | Decisão do dono. Liga com a pendência do freio na 007 |
| 3 | LiDAR "numa fresta" pode ficar muito bloqueado por casco e rodas; anel de visão livre a 15–20 cm, ou LiDAR externo protegido, ou campo limitado + sensores traseiros + para-choque. LiDAR não pode ser a única proteção | Sim | ✅ Decidido na 014: LD06 no topo da cabeça (360° livres) + câmera de profundidade no peito; para-choque proposto como proteção de contato |
| 4 | Rodízio de portão não caracterizado: "0,5 a 8 kg" não dá N/mm; travar o giro com solda pode travar o curso ou criar folga; não foi feito pra carga lateral de omni; 276 mm ocupa espaço. Medir força × deslocamento, atrito e folga; guia antirrotação; amortecimento desde o início; batente de compressão e extensão | Sim | Mantém o teste de bancada com 2 unidades. Critério de aprovação nesses itens; o módulo próprio é o plano B |
| 5 | Velocidade: 100 rpm em roda de 140 mm ≈ 0,73 m/s; 0,4 m/s ≈ 55 rpm | Parcial: os 80–100 rpm eram pros 0,6 m/s de corredor, e os 100 rpm são o exemplo do manual | ✅ Slides 4 e 5 esclarecidos; limite no driver (`2008h`) registrado na 006 |
| 6 | Bateria por energia: Wh, consumo médio e de pico, recarga, degradação, baixa tensão; 29,2 V cheia; **regeneração com BMS bloqueando a carga = sobretensão no barramento** | Parcial: os Wh estão na 008, mas não na apresentação. Regeneração é ponto novo e bom | ✅ Registrado na 008: checar regeneração do ZLAC, corrente de carga do BMS e sobretensão do barramento |
| 7 | Estação de carga: duas baterias, contatos protegidos, polaridade impossível de inverter, pré-carga, intertravamento (não andar carregando), tolerância, sensor de encaixe, estratégia de retentativa; compatibilizar com o e-stop atrás | Sim | Em aberto (004) |
| 8 | Chassi pra 5 unidades: **chapa dobrada cortada a laser** em vez de muito metalon (repetível, menos empeno, furos de referência); se for metalon, gabarito. Faltam furos, tolerâncias, cabos, retenção das baterias, manutenção, ventilação, pontos de içamento. MDF e acrílico só no protótipo | Sim | Considerar chapa dobrada (serviço de corte e dobra) |
| 9 | IMU perto de aço, ímãs e corrente: não confiar no magnetômetro; calibrar raio e bitola por robô | Já coberto na 009 (modo IMU, sem magnetômetro) | ✅ Calibração de raio e bitola por unidade acrescentada na 009 |
| 10 | Requisitos mensuráveis: altura da corrediça, tapete, inclinação, dBA, distância de parada, força mínima de tombamento, temperaturas, carga útil, vão livre, autonomia com ciclo definido, sucesso da docagem, vida útil | Sim | Criar matriz requisito → solução → ensaio |

## Como alargar o apoio (ponto 1, decisão do dono)

Força pra tombar empurrando no topo, a 70 cm, com 35 kg (estimativas):

| Opção | Menor distância até a borda | Força no pior caso |
|---|---|---|
| Hoje: losango (omnis a ±13 cm) | ~11 cm | ~5,5 kgf |
| Omnis mais pra fora (±20 cm) | ~14,5 cm | ~7,3 kgf |
| 4 omnis nos cantos (±18, ±18) + rodas centrais | ~18 cm | ~9 kgf |
| **Batentes antitombo nos 4 cantos** (±22 cm, 1–1,5 cm acima do chão) | ~21 cm | **~10,5 kgf** |

Os batentes antitombo são passivos e baratos, e não mexem na suspensão. O
cuidado é a altura: eles não podem raspar na corrediça nem no tapete.

## Ensaios propostos antes de replicar

1. Carga em cada roda, com balanças
2. Curva e amortecimento da suspensão
3. Corrediça e tapete em vários ângulos
4. Tombamento frontal, lateral e diagonal
5. Parada normal, por watchdog e por e-stop
6. Desligar USB/RS485 e travar o software de propósito
7. 4 h rodando, medindo corrente e temperatura
8. Docagem repetida
9. Impacto, esmagamento de pé e pontos de beliscão
10. Durabilidade antes da série
