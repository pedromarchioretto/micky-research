# Análise comparativa de robôs

## 1. Caracterização Técnica da Base M.I.C.K.Y.

A base M.I.C.K.Y. utiliza uma estrutura de perfis de alumínio industrial 40x40mm e um sistema de tração baseado em rodas Mecanum e utilizando 4 motores de passo Nema para locomoção.

- **Custo Total (BOM):** R$ 5.222,63 (aprox. $950 USD)
- **Payload Operacional:** 32,55 kg
- **Atuadores (Ativos):** 4x motores de passo Nema 23 com torque de 30 kgf.cm cada
- **Rodas:** Conjunto Mecanum MEC-100 (100 mm de diâmetro). Capacidade nominal de 15 kg por roda
- **Estrutura:** Chassis modular em Perfil Alumínio 40x40mm (Canal 8)

### 1.1 Cálculos de Torque e Força Dinâmica

A performance da base sob carga é determinada pelo torque efetivo nos eixos e o raio da roda:

- **Torque Total Bruto ($T_{total}$):**

    **$T_{total}$ = 4 × 30 kgf.cm = 120 kgf.cm ≈ 11,77 Nm**


- **Força Tangencial Total ($F_t$):** Para rodas de raio $r = 5 cm$:

    **($F_t$) = 120 kgf.cm / 5 cm = 24 kgf**


Com uma força de tração de 24 kgf para um payload de 32,55 kg (somado à massa própria de ~25 kg), a base opera com uma **Razão de Tração/Peso Total de ~0,41**, o que garante estabilidade em manobras de strafe lateral sem perda de passos em acelerações moderadas.

---

## 2. Tabela Comparativa: Bases Omnidirecionais

Abaixo, a compilação dos dados técnicos das bases solicitadas, incluindo modelos de baixo custo e plataformas de referência industrial.

| Modelo (Etiqueta) | Payload (kg) | Custo (USD) | Tipo de Tração | Eficiência ($/kg) |
|------------------|-------------|------------|----------------|------------------|
| M.I.C.K.Y. | 32,55 | ~$950 | Mecanum (4 eixos) | $29,18 |
| Wheeltec R550 | 15,00 | $532 | Mecanum (4 eixos) | $35,46 |
| myAGV 2023 Pi | 5,00 | $949 | Mecanum (Planetário) | $189,80 |
| Mecabot Pro | 22,00 | $6.918 | Mecanum (c/ Suspensão) | $314,45 |
| SuperDroid IG52 | 90,00 | $3.750 | Mecanum (Corrente) | $41,66 |
| AGV Pro | 50,00 | ~$6.000* | Mecanum/Omni | $120,00 |
| TIAGo OMNI Base | 100,00 | ~$15.000* | Mecanum (Industrial) | $150,00 |
| TidyBot++ | 90,00 | ~$10.000* | Powered Casters | $111,11 |


---

## 3. Análise da Relação Custo vs. Payload

O gráfico de dispersão (representado pelos eixos abaixo) permite identificar a eficiência de projeto. Bases situadas no quadrante inferior direito representam a maior entrega de carga por dólar investido.

> ![Grafico](grafico_cost_vs_payload.png)

### 3.1 Discussão do Posicionamento do M.I.C.K.Y.

A análise do gráfico revela que o M.I.C.K.Y. ocupa um nicho de **Anomalia de Eficiência**.

- **M.I.C.K.Y. vs. myAGV 2023 Pi:**  
Ambos custam aproximadamente o mesmo ($950). No entanto, o M.I.C.K.Y. entrega **6,5 vezes mais payload** (32,55 kg vs 5 kg).  
Enquanto o myAGV foca em um design compacto com chassis de plástico injeção e motores de pequeno porte, o M.I.C.K.Y. utiliza perfis estruturais 40x40mm que permitem suportar braços robóticos e baterias de alta densidade sem deflexão do chassis.

- **M.I.C.K.Y. vs. Mecabot Pro:**  
O Mecabot Pro custa sete vezes mais, porém seu payload é **32% inferior (22 kg)**.  
A justificativa técnica é que o Mecabot Pro prioriza sensores integrados (Orbbec/LiDAR M10P) e um sistema de suspensão independente.  
O M.I.C.K.Y. prova que é possível obter maior capacidade de tração mecânica através de componentes COTS (Commercial Off-The-Shelf) industriais por uma fração do preço.

### 3.2 O Desafio Industrial: TIAGo OMNI Base e SuperDroid

Estas bases representam os limites superiores de carga.

- **TIAGo OMNI Base:**  
É o benchmark de design para robótica de serviço. Com rodas de 207 mm e motores industriais, ele carrega 100 kg.  
O M.I.C.K.Y. consegue atingir **32% dessa carga útil custando menos de 7% do valor**, tornando-o uma alternativa viável para laboratórios com orçamento restrito.

- **SuperDroid IG52:**  
Atinge payloads de 90 kg através de uma redução por corrente (10:15).  
Embora eficiente em carga, o sistema de corrente exige lubrificação e ajuste de tensão, enquanto o acoplamento direto do M.I.C.K.Y. reduz a manutenção mecânica.

---

## 4. Análise de Materiais e Manutenibilidade

- **Chassis (Alumínio 40x40mm vs. Placa 3mm):**  
O uso de perfis 40x40mm na M.I.C.K.Y. oferece um momento de inércia de seção muito superior às chapas de 3mm do Wheeltec R550 ou ao chassis de ABS do myAGV.  
Isso permite suportar o payload de 32,55 kg de forma estática sem risco de empenamento a longo prazo.

- **Modularidade:**  
A utilização de porcas martelo nos trilhos dos perfis permite reposicionar sensores como o BNO055 e o Hub USB 3.0 TP-Link para equilibrar o centro de massa conforme a carga aumenta.  
Bases de metal cortado a laser (Mecabot/SuperDroid) não possuem essa flexibilidade sem modificações estruturais.

- **Redundância de Motores:**  
A aquisição de 6 motores Nema 23 fornece uma reserva técnica.  
Caso seja necessário aumentar o payload para >50 kg, a ativação dos outros 2 eixos elevaria o torque total para **180 kgf.cm**, colocando a base em um patamar de força superior ao AGV Pro.
