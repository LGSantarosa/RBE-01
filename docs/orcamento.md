# Orçamento do RBE-01

**Data:** 2026-11-10 · estimativa a partir de preços públicos ·
apresentação: https://claude.ai/artifact/XmZhHhXqM3zNK3EUs9yJVv (slides 12–16)

- Dólar: **R$ 5,51** (Cepea). Importado ≈ **2× o preço em dólar** (II 60% com
  dedução de US$ 30 + ICMS 17–20% por dentro). Abaixo de US$ 50 em plataforma
  certificada, só ICMS (~1,25×). Regra de 2026 a confirmar na Receita.
- **NUC (Gigantec) já temos:** custo 0 (assumido pros 5 robôs, a confirmar).
- R$ em negrito = preço no Brasil. Números entre colchetes = fontes no fim.

## Resumo

| Por robô | R$ (faixa) | Onde pesa |
|---|---|---|
| Tração: 2 motores + driver (importado) | 3.900 – 5.050 | câmbio e imposto |
| Energia: baterias, DC-DC, elétrica, estação | 2.900 – 4.300 | baterias |
| Sensores: LiDAR, câmera, IMU (NUC já temos) | 1.700 – 5.900 | **câmera** |
| Mecânica: omnis, módulos, chassi | 2.200 – 3.700 | solda e corte |
| **Total por robô** | **11.000 – 19.000** | |
| **5 robôs + 1 kit de tração reserva** | **58.000 – 100.000** | |

## Tração e energia

| Item | Qtd | Preço encontrado | R$ por robô | Fontes |
|---|---|---|---|---|
| Motor ZLTECH ZLLG55 5,5" | 2 | US$ 99–104 (fábrica, 1–49 pç); US$ 110–164 revenda | 3.900 – 5.050 (com driver, frete e imposto) | 5, 6, 7 |
| Driver ZLAC8015D | 1 | US$ 115 (Alibaba, 1–49 pç); US$ 145–158 outros | no item acima | 8, 9 |
| Bateria LiFePO4 24 V 10 Ah (Unipower UPLFP2410) | 2 | **R$ 970 – 1.188** no Brasil | 1.950 – 2.400 | 10, 11 |
| Conversor DC-DC 19 V (NUC) | 1 | € 10 (buck-boost 5 A) a € 33 (19 V 5 A fixo) | 100 – 300 | 21, 22 |
| Elétrica: botão, relé, chaves, fusíveis, cabos | — | Botão **R$ 33** (Metaltex) a R$ 198; relé 24 V 40 A € 3–11 | 300 – 600 | 23, 24 |
| Estação: 2 carregadores 29,2 V + contatos | 1 | Carregador 29,2 V 5 A US$ 13–29 | 550 – 1.000 | 28, 29 |

> **Conferir:** a corrente do BMS da Unipower. A tração precisa de ≥ 30 A contínuo (008).

## Computação e sensores

| Item | Qtd | Preço encontrado | R$ por robô | Fontes |
|---|---|---|---|---|
| NUC (Gigantec) | 1 | **Já temos**. Pra comparar: mini PC N100 novo R$ 1.300 – 3.506 | **0** | 12, 13 |
| LiDAR LD06-LD ou STL-06P (sucessor do LD06) | 1 | US$ 28–31 (AliExpress); US$ 99 (STL-06P) | 200 – 900 | 14, 15 |
| Câmera: Orbbec Astra Pro Plus | 1 | US$ 150 (loja Orbbec) | ~1.450 | 16 |
| Câmera: Orbbec Gemini 336 | (ou) | US$ 390–420 | ~4.250 – 4.650 | 17 |
| Câmera: Intel RealSense D435i | (ou) | US$ 399 – 550 (linha em fim de vida) | ~4.400 – 6.000 | 18 |
| IMU BNO055 + adaptador USB | 1 | **R$ 51 – 95** (ML, da China); **R$ 237 – 300** (lojas BR) | 75 – 340 | 19, 20 |

> **A câmera decide:** a Astra Pro Plus economiza ~R$ 3 mil por robô, ~R$ 15 mil nos 5. Falta ver se o alcance mínimo dela enxerga o pé perto do robô (014).

## Mecânica

| Item | Qtd | Preço encontrado | R$ por robô | Fontes |
|---|---|---|---|---|
| Roda omni Ø100 alumínio, dupla, com rolamento | 2 | US$ 62–80 (Nexus, carga de 30 kg) | 1.000 – 1.300 | 25 |
| Módulo da omni: 4 buchas LM8UU, hastes Ø8, molas, anéis, chapa | 2 | LM8UU € 1,50 – US$ 4 cada; resto sem preço | 200 – 400 | 26 |
| Perfis 20×20 e mastro | — | € 3,30 – 8,90 o metro (Europa) | no chassi | 27 |
| Chassi: bandeja soldada, corte de chapa, placa, painéis, peças 3D, batentes, para-lamas | — | Sem preço público: pedir orçamento com o DXF | 1.000 – 2.000 | — |


## Em aberto

- Conferir se o BMS da Unipower dá ≥ 30 A contínuo (008).
- A omni de 30 kg fica abaixo dos ≥ 40 kg pedidos (010).
- LD06 parece descontinuado: LD06-LD ou STL-06P; conferir driver ROS 2.
- Câmera: Astra Pro Plus economiza ~R$ 3 mil/robô; conferir alcance mínimo (014).
- Tensão de entrada do NUC Gigantec define o DC-DC (003).
- O NUC Gigantec cobre os 5 robôs?
- Kit ZLTECH pode passar de US$ 3.000 por remessa (muda o regime).
- Solda e corte: pedir orçamento com o DXF.

## Fontes (consultadas em 2026-11-10)

1. Cepea: dólar comercial — <https://www.cepea.org.br/br/serie-de-preco/dolar.aspx>
2. Econet: Portaria MF 1.342/2026 — <https://blog.econeteditora.com.br/remessa-conforme-o-que-muda-com-a-portaria-mf-1-342-2026/>
3. Forbes: compras internacionais — <https://forbes.com.br/forbes-money/2026/09/taxa-das-blusinhas-veja-como-ficam-as-compras-internacionais/>
4. ICMS nas compras internacionais — <https://amdjus.com.br/icms-sobre-compras-internacionais-permanece-mesmo-sem-taxa-das-blusinhas/>
5. ZLTECH: motor 5,5" (fábrica) — <https://zltech-hubmotor.en.made-in-china.com/product/yjumnkiUCNWh/China-5-5inch-24V-150W-400rpm-Brushless-Electric-DC-Agv-Wheel-Hub-Servo-Motor-with-Encoder.html>
6. ZLLG55ASM150 no AliExpress — <https://imall.com/product/5.5-inch-built-in-encoder-robot-hub-servo-motor-ZLLG55ASM150/Home-Improvement-Electrical-Equipment-Supplies/aliexpress.com/32993257531/144-11934341/en>
7. AIFitLab: motores ZLTECH — <https://aifitlab.com/collections/zhongling-technology-motor>
8. ZLAC8015D no Alibaba — <https://www.alibaba.com/product-detail/ZLTECH-ZLAC8015D-24V-36V-48V-15A_1600450813009.html>
9. ZLAC8015D no Made-in-China — <https://zltech-hubmotor.en.made-in-china.com/product/GFTAuCzSbKVf/China-Zltech-Zlac8015D-24V-36V-48V-15A-30A-500W-3-Phase-Canopen-RS485-AC-DC-Hub-Servo-Motor-Driver-for-Automatic-Delivery-Robot.html>
10. Braspower: Unipower UPLFP2410 — <https://www.braspower.com.br/bateria-de-litio-24v-10ah-unipower-uplfp2410>
11. Mercado Livre: bateria 24 V 10 Ah — <https://lista.mercadolivre.com.br/bateria-litio-24v-10ah>
12. Mercado Livre: mini PC N100 — <https://lista.mercadolivre.com.br/mini-pc-intel-n100>
13. Amazon BR: mini PC N100 — <https://www.amazon.com.br/mini-pc-n100/s?k=mini+pc+n100>
14. AliExpress: LD06-LD — <https://www.aliexpress.us/item/3256809889069278.html>
15. Sensorlidar: STL-06P — <https://www.sensorlidar.com/products/ldrobot-stl-06p-lidar-outdoor-light-resistance-60klx-5000hz-12m-360-scanning-support-ros1-and-ros2-replaces-ld06-lidar>
16. Loja Orbbec: Astra Pro Plus — <https://store.orbbec.com/products/astra-pro-plus>
17. Openelab: Orbbec Gemini 336 — <https://openelab.io/a/s/products/orbbec-gemini-336-stereo-vision-camera-with-infrared-imaging>
18. Guia RealSense D435i (2026) — <https://www.roboticscenter.ai/guides/robot-vision/realsense-guide>
19. Mercado Livre: BNO055 — <https://lista.mercadolivre.com.br/sensor-bno055-9-dof>
20. HPE Robótica: BNO055 — <https://www.hperobotica.com.br/arduino/sensores-e-modulos/modulo-sensor-de-orientacao-absoluta-bno055-9-dof-cjmcu055>
21. RobotShop: buck-boost 5 A — <https://eu.robotshop.com/products/dc-dc-buck-boost-converter-module-5a>
22. Fruugo: conversor 19 V 5 A — <https://www.fruugo.pt/modulo-conversor-dc-dc-buckboost-de-936v-para-19v-5a-com-ampla-faixa-de-entrada-e-saida-de-19v-5a/p-449714284-946792468>
23. Magalu: botão cogumelo com trava — <https://www.magazineluiza.com.br/busca/interruptor+trava>
24. RS: relé TE 24 V 40 A — <https://it.rs-online.com/web/p/rele-per-automotive/6900795>
25. RobotShop: omni Ø100 alumínio — <https://eu.robotshop.com/products/100mm-double-aluminum-omni-wheel-bearing-rollers>
26. Botnroll: LM8UU — <https://www.botnroll.com/pt/parafusos/1879-rolamento-de-esferas-para-guias-lineares-8mm-lm8uu-.html>
27. Systeal: perfil V-slot 20×20 — <https://www.systeal.com/en/profiles-20-series/1668-v-slot-aluminium-profile-20x20-6mm-slot.html>
28. Amazon: carregador 29,2 V 5 A — <https://www.amazon.com/Charger-LiFePO4-Battery-29-2V5A-3P-Plug/dp/B07PV6SJSP>
29. Bioenno: carregador 29,2 V — <https://www.bioennopower.com/products/29-2v-10a-ac-to-dc-charger-5a-for-24v-lifepo4-batteries-bpc-2410c>
