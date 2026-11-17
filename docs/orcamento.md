# Orçamento do RBE-01

**Data:** 2026-11-17 · revisão 2 (média de cotações) ·
apresentação: https://claude.ai/artslide-15 (slides 12–19)

## Como foi feito

- Cada item tem **pelo menos 2 cotações públicas com link**. O preço usado é a
  **média simples** das cotações, já convertidas pra real.
- Preço com faixa (ex.: US$ 99–104) entra pelo meio da faixa.
- **Câmbio:** US$ 1 = **R$ 5,51** (Cepea) · € 1 = **R$ 6,17** (taxa do BCE de 09/11/2026: 6,1748, publicada pelo Banca d'Italia).
- **Importado = 2× o preço convertido** (II de 60% com dedução de US$ 30 +
  ICMS de 17–20% por dentro). Vale pra compra dos 5 robôs junta, acima de
  US$ 50. Regra de 2026 a confirmar na Receita.
- Preço no Brasil entra como está (preço de tabela, sem desconto de Pix).
- **Estimativa** = item sem cotação pública. Está marcado e precisa de orçamento.
- **Contingência de 10%** sobre o subtotal: frete, perdas, variação de câmbio.
- **NUC (Gigantec) já temos:** custo 0 (assumido pros 5 robôs, a confirmar).
- A câmera ainda não foi escolhida (014), então o total sai em 3 cenários.

## Resumo

| Por robô | Astra Pro Plus | Gemini 336 | RealSense D435i |
|---|---:|---:|---:|
| Tração e elétrica | 3.880 | 3.880 | 3.880 |
| Energia | 3.786 | 3.786 | 3.786 |
| Sensores (sem câmera) | 1.037 | 1.037 | 1.037 |
| Câmera | 1.860 | 3.528 | 6.561 |
| Mecânica | 3.231 | 3.231 | 3.231 |
| Subtotal | 13.795 | 15.462 | 18.496 |
| Contingência 10% | 1.379 | 1.546 | 1.850 |
| **Total por robô (R$)** | **15.174** | **17.009** | **20.346** |
| **Frota: 5 robôs + 1 kit de tração reserva (R$)** | **79.760** | **88.932** | **105.617** |

Kit de tração reserva = 2 motores + 1 driver + 10% = R$ 3.889.

## Tração e elétrica

| Item | Qtd | Cotação 1 | Cotação 2 | Cotação 3 | Média un. (R$) | Por robô (R$) |
|---|---:|---|---|---|---:|---:|
| [Motor ZLTECH ZLLG55 5,5"][m1] | 2 | [Made-in-China (fábrica)][m1]: US$ 99–104 → 1.119 | [AIFitLab][m2]: US$ 110 → 1.212 | [China.org.ru][m3]: US$ 89,50–105 → 1.072 | 1.134 | 2.268 |
| [Driver ZLAC8015D][d1] | 1 | [Alibaba][d1]: US$ 115 → 1.267 | [Made-in-China][d2]: US$ 115 → 1.267 | — | 1.267 | 1.267 |
| [Botão de emergência 22 mm com trava][b1] | 1 | [Maqpart (Lukma)][b1]: R$ 17,40 | [Loja Elétrica (P20AKR-R-1B; a loja cita Metaltex e Margirius)][b2]: R$ 20,67 | [Sartori (WEG CSW-BEG)][b3]: R$ 59,48 | 32,52 | 33 |
| [Relé 24 V 40 A (bobina 24 V)][r1] | 1 | [Injepel][r1]: R$ 13,06 | [Conexão Elétrica (DNI 0211)][r2]: R$ 10,24 | [Via Peças (DNI 0216, 24 V 40/30 A, 5 terminais com suporte; 40 un. em estoque)][r3]: R$ 13,05 | 12,12 | 12 |
| Fusíveis, chaves, cabos, conectores, adaptador USB | — | estimativa | | | | 300 |
| **Subtotal** | | | | | | **3.880** |

## Energia

| Item | Qtd | Cotação 1 | Cotação 2 | Cotação 3 | Média un. (R$) | Por robô (R$) |
|---|---:|---|---|---|---:|---:|
| [Bateria LiFePO4 24 V 10 Ah (Unipower UPLFP2410)][e1] | 2 | [Braspower][e1]: R$ 1.187,50 | [Mercado Livre][e2]: R$ 1.179,90 | [Neosolar (sem estoque)][e3]: R$ 899,00 | 1.089 | 2.178 |
| [Conversor DC-DC 24 → 19 V 5 A (NUC)][c1] | 1 | [ATO (ATOWG-24S1905)][c1]: US$ 48,79 → 538 | [Mad Hornets][c2]: US$ 14,88 → 164 | — | 351 | 351 |
| [Carregador LiFePO4 24 V 5 A][k1] | 2 | [ExpertPower EPC245 (sem estoque)][k1]: US$ 46,99 → 518 | [Aegis (CRF-02405P)][k2]: US$ 48,99 → 540 | — | 529 | 1.058 |
| Contatos e suporte da estação | 1 | estimativa | | | | 200 |
| **Subtotal** | | | | | | **3.786** |

> **Conferir:** a corrente do BMS da Unipower. A tração precisa de ≥ 30 A contínuo (008).

## Sensores

| Item | Qtd | Cotação 1 | Cotação 2 | Cotação 3 | Média un. (R$) | Por robô (R$) |
|---|---:|---|---|---|---:|---:|
| [LiDAR LD06 (ou substituto STL-06P)][l1] | 1 | [AliExpress (LD06-LD)][l1]: US$ 28–31 → 325 | [Sensorlidar (LD06)][l2]: US$ 69 → 760 | [Sensorlidar (STL-06P)][l3]: US$ 99 → 1.091 | 725 | 725 |
| [IMU BNO055][i2] | 1 | [Adafruit (2472)][i2]: US$ 34,95 → 385 | [Mercado Livre (CJMCU-055)][i3]: R$ 299,00 | [Saravati (sem estoque)][i1]: R$ 249,90 | 311 | 311 |
| NUC (Gigantec) | 1 | já temos | | | | 0 |
| **Subtotal sem câmera** | | | | | | **1.037** |

**Câmera (escolher uma):**

| Câmera | Cotação 1 | Cotação 2 | Cotação 3 | Média (R$) |
|---|---|---|---|---:|
| [Orbbec Astra Pro Plus][a1] | [youyeetoo][a1]: US$ 79 → 871 | [MyBotShop (DE)][a2]: € 230,95 → 2.850 | — | **1.860** |
| [Orbbec Gemini 336][g1] | [Loja Orbbec][g1]: US$ 284 → 3.130 | [RobotShop US][g2]: US$ 392,40 → 4.324 | [Robotics Center][g3]: US$ 284 → 3.130 | **3.528** |
| [Intel RealSense D435i (fim de linha)][x1] | [Aztek][x1]: US$ 686,25 → 7.562 | [Robotics Center][x2]: US$ 550 → 6.061 | [AIFitLab (sem estoque)][x3]: US$ 550 → 6.061 | **6.561** |

> A Astra Pro Plus economiza ~R$ 1.700 por robô sobre a Gemini 336 (~R$ 8 mil
> na frota), mas a Orbbec anunciou o fim de linha dela. A D435i subiu: a Aztek cobra hoje US$ 686. Falta ver se o alcance mínimo dela enxerga o pé perto do robô (014).

## Mecânica

| Item | Qtd | Cotação 1 | Cotação 2 | Cotação 3 | Média un. (R$) | Por robô (R$) |
|---|---:|---|---|---|---:|---:|
| [Roda omni Ø100 alumínio dupla (Nexus 14054)][o1] | 2 | [RobotShop US][o1]: US$ 64,50 → 711 | [OZ Robotics][o2]: US$ 54,40 → 599 | — | 655 | 1.310 |
| [Bucha linear LM8UU][u1] | 8 | [Impacto CNC][u1]: R$ 5,25 | [AutoCore][u2]: R$ 7,90 | [Marino Store][u3]: R$ 6,00 | 6,38 | 51 |
| [Eixo retificado Ø8 × 300 mm][h1] | 4 | [Smart Projects][h1]: R$ 24,50 | [Saravati (sem estoque)][h2]: R$ 29,90 | — | 27,20 | 109 |
| [Perfil 20×20 V-slot (por metro)][p1] | 3 m (estimado) | [Leroy Merlin (1 m)][p1]: R$ 37,14 | [Amazon BR (0,6 m)][p2]: R$ 36,95/m | — | 37,05 | 111 |
| Molas, anéis e chapa do módulo da omni | — | estimativa | | | | 150 |
| Chassi: bandeja soldada, corte de chapa, painéis, peças 3D, batentes | — | estimativa | | | | 1.500 |
| **Subtotal** | | | | | | **3.231** |

> A omni Nexus aguenta 30 kg e a 010 pede ≥ 40 kg. Achar uma mais forte ou usar dupla.

## Em aberto

- Chassi e módulo da omni: pedir orçamento a 3 oficinas com o DXF (hoje é estimativa).
- Conferir se o BMS da Unipower dá ≥ 30 A contínuo (008).
- Carregador Aegis CRF-02405P: a Aegis recomenda bateria de 25 Ah ou mais; a nossa é de 10 Ah (5 A = 0,5 C). Confirmar com a Aegis antes de comprar.
- LiDAR do AliExpress é o "LD06-LD", anunciado como substituto do LD06: confirmar com o vendedor se é LDROBOT original.
- A omni de 30 kg fica abaixo dos ≥ 40 kg pedidos (010).
- LD06 parece descontinuado: LD06-LD ou STL-06P; conferir driver ROS 2.
- Câmera: escolher o modelo (014). Conferir alcance mínimo da Astra Pro Plus.
- Tensão de entrada do NUC Gigantec define o DC-DC (003).
- O NUC Gigantec cobre os 5 robôs?
- Kit ZLTECH pode passar de US$ 3.000 por remessa (muda o regime).
- Cotar frete internacional (hoje está dentro da contingência de 10%).

## Fontes (consultadas em 2026-11-17)

**Câmbio e imposto**

- Cepea: dólar comercial — <https://www.cepea.org.br/br/serie-de-preco/dolar.aspx>
- Banca d'Italia: taxas de referência do BCE em 09/11/2026 — <https://www.bancaditalia.it/compiti/operazioni-cambi/cambio/cambi_rif_20261109>
- Econet: Portaria MF 1.342/2026 — <https://blog.econeteditora.com.br/remessa-conforme-o-que-muda-com-a-portaria-mf-1-342-2026/>
- Forbes: compras internacionais — <https://forbes.com.br/forbes-money/2026/09/taxa-das-blusinhas-veja-como-ficam-as-compras-internacionais/>
- ICMS nas compras internacionais — <https://amdjus.com.br/icms-sobre-compras-internacionais-permanece-mesmo-sem-taxa-das-blusinhas/>

**Itens** (os links das tabelas)

[m1]: https://zltech-hubmotor.en.made-in-china.com/product/yjumnkiUCNWh/China-5-5inch-24V-150W-400rpm-Brushless-Electric-DC-Agv-Wheel-Hub-Servo-Motor-with-Encoder.html
[m2]: https://aifitlab.com/products/zhongling-zllg55-asm150-v2-0-motor
[m3]: https://china.org.ru/product/62252270601
[d1]: https://www.alibaba.com/product-detail/ZLTECH-ZLAC8015D-24V-36V-48V-15A_1600450813009.html
[d2]: https://zltech-hubmotor.en.made-in-china.com/product/GFTAuCzSbKVf/China-Zltech-Zlac8015D-24V-36V-48V-15A-30A-500W-3-Phase-Canopen-RS485-AC-DC-Hub-Servo-Motor-Driver-for-Automatic-Delivery-Robot.html
[b1]: https://maqpart.com.br/botao-cogumelo-emergencia-gira-destrava-22mm-verm-1nf-lukma-04217
[b2]: https://www.lojaeletrica.com.br/bot-o-de-emergencia-22mm-c-trava-1nf-cogumelo-vm-p20akr-r-1b-margirius.html
[b3]: https://www.sartoriweb.com.br/botao-cogumelo-csw-beg-emergencia-c-trava-22mm-12882445-24494
[r1]: https://www.injepel.com.br/eletrica/rele-auxiliar-universal-24v-sem-suporte-5-terminais-40a-30a
[r2]: https://lojadaconexaoeletrica.com.br/products/rele-automotivo-dni-0211-24v-40a
[r3]: https://www.viapecas.com.br/rele-auxiliar-reversor-dni0216-24v-40-30a-5-terminais-com-suporte/p/1866
[e1]: https://www.braspower.com.br/bateria-de-litio-24v-10ah-unipower-uplfp2410
[e2]: https://produto.mercadolivre.com.br/MLB-5291951084-bateria-de-litio-24v-10ah-unipower-uplfp2410-_JM
[e3]: https://www.neosolar.com.br/loja/bateria-solar-litio-lfp-250wh-unipower-upflp24-4000-ciclos-25-6v.html
[c1]: https://www.ato.com/dc-dc-buck-converter-24v-to-13-8v
[c2]: https://www.madhornets.com/dc-dc-buck-step-down-module-24v-to-19v-5a-power-supply-converter-regulator/
[k1]: https://www.expertpower.us/es/products/24v-5a-charger-epc245
[k2]: https://www.aegisbattery.com/products/24v-5a-lifepo4-lifepo4
[l1]: https://www.aliexpress.us/item/3256809889069278.html
[l2]: https://sensorlidar.com/products/ldrobot-ld06-ld19-d300-of-laser-radar-lidar-scanner-360-scanning-d500-lidar-kit-support-ros1-and-ros2-for-indoor-and-outdoor
[l3]: https://www.sensorlidar.com/products/ldrobot-stl-06p-lidar-outdoor-light-resistance-60klx-5000hz-12m-360-scanning-support-ros1-and-ros2-replaces-ld06-lidar
[i1]: https://www.saravati.com.br/modulo-sensor-de-orientacao-absoluta-bno055-9-dof.html
[i2]: https://www.adafruit.com/product/2472
[i3]: https://produto.mercadolivre.com.br/MLB-3784035673-modulo-sensor-de-orientaco-bno055-9-dof-cjmcu055-_JM
[a1]: https://youyeetoo.com/products/astra-pro-plus
[a2]: https://www.mybotshop.de/Orbbec3D-Astra-Pro-Plus_1
[g1]: https://store.orbbec.com/products/gemini-336
[g2]: https://www.robotshop.com/products/orbbec-gemini-336-camera
[g3]: https://www.roboticscenter.ai/es/store/product/orbbec-gemini-336
[x1]: https://www.aztekcomputers.com/82635d435idk5p-realsense-d435i-depth-camera-intel/p
[x2]: https://www.roboticscenter.ai/de/store/product/intel-realsense-d435i
[x3]: https://aifitlab.com/products/intel-realsense-depth-camera-d435i
[o1]: https://www.robotshop.com/products/100mm-double-aluminum-omni-wheel-bearing-rollers
[o2]: https://ozrobotics.com/shop/double-aluminum-omni-wheel-bearing-rollers-100mm-14054/
[u1]: https://www.impactocnc.com/lm8uu
[u2]: https://www.autocorerobotica.com.br/rolamento-linear-8mm-lm8uu-impressora-3d-cnc
[u3]: https://www.marinostore.com/impressora-3d-cnc/rolamento-linear-lm8uu-8-mm
[h1]: https://www.smartprojectsbrasil.com.br/eixo-guia-linear-retificado-8x300mm-cnc-impressora-3d
[h2]: https://www.saravati.com.br/guia-eixo-linear-retificado-h7-8mm-x-300mm.html
[p1]: https://www.leroymerlin.com.br/perfil-estrutural-aluminio-20x20-v-slot-1000mm_1572396175
[p2]: https://www.amazon.com.br/Perfil-Estrutural-Alum%C3%ADnio-20x20-V-slot/dp/B0F5483T3Y

> Preços de loja mudam rápido e alguns itens estavam sem estoque na consulta
> (AIFitLab, Saravati). Conferir tudo na hora da compra.
>
> **Links testados em 2026-11-17, num navegador (Chromium), numa segunda revisão
> do PDF e à mão.** Todos os links foram testados. Trocados porque não abriam o
> produto: os 3 conversores (Fruugo fora de venda, Ampul fora do ar), o
> carregador da Ampul, o botão da Industrial Motores (página não encontrada), a
> Astra Pro Plus na loja da Orbbec (cai na página inicial), as omni da SuperDroid
> (indisponível) e da Hobbywater (cai na página inicial), a BNO055 GY do Mercado
> Livre (cai em página genérica) e o relé da Amazon (sem estoque). Conferidos à
> mão: a bateria e a CJMCU-055 no Mercado Livre e o motor no China.org.ru.
