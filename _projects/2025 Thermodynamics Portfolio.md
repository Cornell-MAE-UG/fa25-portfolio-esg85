---
layout: project
title: Thermodynamics Portfolio - Sub-Zero Refrigerator Analysis
description: Vapor-Compression Refrigeration Cycle Analysis
technologies: [Thermodynamics, R-600a Refrigerant, Energy Analysis]
image: /assets/images/subzero-fridge.jpg
---

## Above-and-Beyond Cycle Analysis
**Device:** Sub-Zero CL4850SID/S (48-inch built-in side-by-side refrigerator/freezer, internal dispenser)  
**Course Text:** Moran & Shapiro, *Fundamentals of Engineering Thermodynamics*, Ch. 1–10

---

## 1. Personal Background & Motivation

This refrigerator is the refrigerator installed in my own home. In everyday use, I feel it keeps food fresh for longer than other refrigerators I have used. Because it is a real appliance I interact with daily, it is a good candidate for connecting the vapor-compression refrigeration theory from this course (control volumes, First Law, Second Law, and COP) to a real engineered product.

---

## 2. Device Overview and Real Operating Context

My home kitchen/room temperature is approximately **79°F (26.1°C)**. The unit is installed in tight cabinetry, which can reduce airflow across the condenser and increase the condensing temperature and compressor work. This report quantifies how that mechanism affects performance using a state-point cycle model and the device's published annual electricity use.

| Quantity | Value | How used in calculations |
|----------|-------|--------------------------|
| Annual energy use | **817 kWh/yr** | Converted to time-average electrical power input |
| Average electrical input | **93.3 W** | Used with COP to estimate average cooling rate |
| Recommended setpoints | **38°F fridge / 0°F freezer** | Cold-side reference temperatures for entropy/COP bounds |
| Electrical supply | **115 VAC, 60 Hz; 15 A circuit** | Shows maximum available electrical power margin |

*Source notes: Annual energy use and electrical info are from Sub-Zero product/spec pages and the EnergyGuide label; recommended setpoints are from the Sub-Zero Classic Use & Care Guide.*

![Sub-Zero CL4850SID/S refrigerator]({{ "/assets/images/subzero-front.jpg" | relative_url }}){: .inline-image-r style="width: 300px"}

---

## 3. Qualitative Description (How It Works)

Thermodynamically, the Sub-Zero refrigerator is a **vapor-compression refrigeration system**. It removes heat from the refrigerator/freezer compartments (low-temperature region) and rejects that heat to the kitchen air (high-temperature region) using electrical work supplied to a compressor. The refrigerant circulates in a closed loop through four main components:

1. **Evaporator** - Absorbs heat from food compartments
2. **Compressor** - Increases pressure and temperature of refrigerant vapor
3. **Condenser** - Rejects heat to kitchen air
4. **Expansion device (throttle)** - Reduces pressure for refrigerant return

### Vapor-Compression Cycle Components

```
[Evaporator] → [Compressor] → [Condenser] → [Expansion Valve] → [Evaporator]
   Q̇_L in         Ẇ_in           Q̇_H out        (throttle)
```

### Overall Control Volume Model

![Control volume diagram]({{ "/assets/images/cv-diagram.jpg" | relative_url }}){: .inline-image-l style="width: 350px"}

The system operates as a steady-cycle control volume with:
- **Cold reservoir**: Fridge/Freezer compartments (Q̇_L entering)
- **Hot reservoir**: Kitchen air at 79°F (Q̇_H leaving)
- **Work input**: Electrical power to compressor (Ẇ_in)

---

## 4. System Diagram & Governing Balances

I model the sealed refrigeration loop as a steady-cycle control volume. The working fluid mass circulates internally, so net mass flow across the outer boundary is approximately zero. Heat and work cross the boundary.

### Mass Balance (overall sealed loop):
```
(1) Σ ṁ_in − Σ ṁ_out = 0
```

### Energy Balance (steady-cycle First Law):
```
(2) Q̇_H = Q̇_L + Ẇ_in
```

### Entropy Balance (Second Law, two-reservoir form):
```
(3) Ṡ_gen = Q̇_H/T_H − Q̇_L/T_L ≥ 0
```

### Performance Metric:
```
(4) COP_R = Q̇_L / Ẇ_in
```

---

## 5. State-Point Cycle Model with Real Numbers

A full manufacturer thermodynamic test map is not publicly provided for this exact unit, so I build a realistic, citable state-point model using:
- (i) The unit's published annual electricity use
- (ii) The recommended compartment setpoints
- (iii) The common low-GWP domestic refrigerant **R-600a** (isobutane) used by many ENERGY STAR listed refrigerators
- (iv) Published R-600a thermodynamic property tables

### Chosen Representative Temperatures:

- **Evaporating saturation temperature**: T_e = **−26°C** (colder than the 0°F freezer air so heat can flow into the evaporator)
- **Condensing saturation temperature**: Because the unit is built into tight cabinetry, I use:
  - Baseline: T_c = **50°C** (tight cabinetry)
  - Better airflow: T_c = **45°C** (clean/optimal)
  - Restricted airflow: T_c = **55°C** (dust/blocked)

### R-600a Thermodynamic Properties

| Property | Value | Source/Notes |
|----------|-------|--------------|
| Specific heat, c_p | **1.692 kJ/(kg·K)** | R-600a vapor property datasheet |
| Specific heat ratio, k | **1.105** | R-600a vapor property datasheet |
| Isentropic efficiency, η_is | **0.70 (70%)** | Typical for small hermetic compressors |
| Molecular weight | **58.12 g/mol** | Isobutane (C₄H₁₀) |

### State Properties from R-600a Tables

| Quantity | Value | Meaning |
|----------|-------|---------|
| P_low @ −26°C | **0.559 bar** | Evaporator saturation pressure (State 1) |
| h₁ @ −26°C sat vapor | **519.67 kJ/kg** | Compressor inlet enthalpy (State 1) |
| s₁ @ −26°C sat vapor | **2.3057 kJ/(kg·K)** | Compressor inlet entropy (State 1) |
| h₃ @ 45°C sat liquid | **309.07 kJ/kg** | Condenser outlet enthalpy for clean case (State 3) |
| h₃ @ 50°C sat liquid | **322.16 kJ/kg** | Condenser outlet enthalpy for baseline (State 3) |
| h₃ @ 55°C sat liquid | **335.25 kJ/kg** | Condenser outlet enthalpy for restricted case (State 3) |

### Component Energy Relations

For steady-flow control volumes (neglecting Δke, Δpe):

```
(5) Compressor: Ẇ_in ≈ ṁ (h₂ − h₁)
(6) Condenser: Q̇_H ≈ ṁ (h₂ − h₃)
(7) Throttle: h₄ ≈ h₃ (isenthalpic throttling)
(8) Evaporator: Q̇_L ≈ ṁ (h₁ − h₄)
```

---

## 6. Step-by-Step Cycle Results (All Numbers)

Compressor modeling uses an ideal-gas approximation for vapor compression with constant c_p and k and an isentropic efficiency η_is = 0.70. For each condenser temperature case, I compute pressure ratio, isentropic outlet temperature, compressor specific work, refrigerating effect, COP, and then use the measured annual energy to estimate average Q̇_L and mass flow rate.

### CASE 1: Clean / Better Airflow (T_c = 45°C)

**Step 1: Identify state properties from R-600a tables**
- State 1 (evaporator outlet, saturated vapor at T_e = −26°C = 247.15 K):
  - P₁ = 0.559 bar
  - h₁ = 519.67 kJ/kg
  - s₁ = 2.3057 kJ/(kg·K)
- State 3 (condenser outlet, saturated liquid at T_c = 45°C = 318.15 K):
  - P₃ = 6.044 bar
  - h₃ = 309.07 kJ/kg

**Step 2: Calculate pressure ratio**
```
r_p = P_high / P_low = 6.044 bar / 0.559 bar = 10.81
```

**Step 3: Calculate isentropic compressor outlet temperature**
```
T_2s = T₁ × (P_high/P_low)^((k−1)/k)
T_2s = 247.15 K × (10.81)^(0.09502)
T_2s = 247.15 K × 1.2515 = 309.32 K
```

**Step 4: Calculate isentropic enthalpy change**
```
Δh_is = c_p × (T_2s − T₁)
Δh_is = 1.692 kJ/(kg·K) × (309.32 K − 247.15 K)
Δh_is = 1.692 × 62.17 = 105.15 kJ/kg
```

**Step 5: Calculate actual compressor work**
```
w_in = Δh_is / η_is = 105.15 kJ/kg / 0.70 = 150.21 kJ/kg
h₂ = h₁ + w_in = 519.67 + 150.21 = 669.88 kJ/kg
```

**Step 6: Throttle process (isenthalpic)**
```
h₄ = h₃ = 309.07 kJ/kg
```

**Step 7: Calculate refrigerating effect**
```
q_L = h₁ − h₄ = 519.67 − 309.07 = 210.60 kJ/kg
```

**Step 8: Calculate coefficient of performance**
```
COP_R = q_L / w_in = 210.60 / 150.21 = 1.40
```

**Step 9: Calculate actual power and cooling rate**
```
Annual energy = 817 kWh/yr (from EnergyGuide)
Hours per year = 365.25 × 24 = 8766 hr/yr
Ẇ_avg = 817,000 Wh / 8766 hr = 93.2 W

For better airflow at COP=1.40:
Assuming same baseline cooling: Q̇_L = 114.6 W
Ẇ_clean = Q̇_L / COP_clean = 114.6 W / 1.40 = 81.7 W
```

**Step 10: Calculate mass flow rate**
```
If system runs at full capability: Q̇_L = 1.40 × 93.2 = 130.7 W
ṁ = Q̇_L / q_L = 130.7 W / 210.60 kJ/kg = 0.620 g/s
```

**Step 11: Calculate heat rejection rate**
```
Q̇_H = Q̇_L + Ẇ_in = 130.7 W + 93.2 W = 223.9 W
```

**Step 12: Calculate entropy generation rate**
```
T_L = 0°F = −17.78°C = 255.37 K
T_H = 79°F = 26.11°C = 299.26 K
Ṡ_gen = Q̇_H/T_H − Q̇_L/T_L
Ṡ_gen = 223.9/299.26 − 130.7/255.37 = 0.7483 − 0.5118 = 0.2365 W/K ≥ 0 ✓
```

---

### CASE 2: Baseline Tight Cabinetry (T_c = 50°C) — DETAILED

![Condenser with restricted airflow]({{ "/assets/images/condenser-tight.jpg" | relative_url }}){: .inline-image-r style="width: 250px"}

**Step 1: Identify state properties from R-600a tables**
- State 1 (evaporator outlet, saturated vapor at T_e = −26°C = 247.15 K):
  - P₁ = 0.559 bar
  - h₁ = 519.67 kJ/kg
  - s₁ = 2.3057 kJ/(kg·K)
  - T₁ = 247.15 K
- State 3 (condenser outlet, saturated liquid at T_c = 50°C = 323.15 K):
  - P₃ = 6.887 bar (interpolated)
  - h₃ = 322.16 kJ/kg (interpolated)

**Step 2: Calculate pressure ratio**
```
r_p = P_high / P_low = 6.887 bar / 0.559 bar = 12.32
```

**Step 3: Calculate isentropic compressor outlet temperature**
```
Exponent: (k−1)/k = (1.105−1)/1.105 = 0.09502
T_2s = T₁ × (P_high/P_low)^((k−1)/k)
T_2s = 247.15 K × (12.32)^0.09502
ln(12.32) = 2.5111, so 12.32^0.09502 = e^(0.2386) = 1.2694
T_2s = 247.15 K × 1.2694 = 313.76 K = 40.61°C
```

**Step 4: Calculate isentropic enthalpy change**
```
Δh_is = c_p × (T_2s − T₁)
Δh_is = 1.692 kJ/(kg·K) × (313.76 K − 247.15 K)
Δh_is = 1.692 kJ/(kg·K) × 66.61 K = 112.70 kJ/kg
```

**Step 5: Calculate actual compressor work with efficiency**
```
η_is = 0.70 (isentropic efficiency)
w_in = Δh_actual = Δh_is / η_is = 112.70 / 0.70 = 161.00 kJ/kg

Actual outlet enthalpy:
h₂ = h₁ + w_in = 519.67 + 161.00 = 680.67 kJ/kg

Actual outlet temperature (approximate):
T₂ = T₁ + Δh_actual/c_p = 247.15 + 161.00/1.692 = 342.31 K = 69.16°C
```

**Step 6: Throttle process (isenthalpic expansion)**

The throttling valve (capillary tube or expansion device) is an adiabatic process with no work. By First Law: h₄ = h₃
```
h₄ = h₃ = 322.16 kJ/kg
```
State 4 is a two-phase mixture at evaporator pressure (0.559 bar, −26°C)

**Step 7: Calculate refrigerating effect (evaporator heat absorption)**
```
q_L = h₁ − h₄ = 519.67 − 322.16 = 197.51 kJ/kg
```
This is the heat absorbed per kg of refrigerant circulated.

**Step 8: Calculate cycle coefficient of performance**
```
COP_R = q_L / w_in = 197.51 / 161.00 = 1.227 ≈ 1.23
```

**Step 9: Convert annual energy to average power**
```
Annual consumption from EnergyGuide label: 817 kWh/yr
Convert to Watt-hours: 817 kWh = 817,000 Wh
Hours in one year: 365.25 days/yr × 24 hr/day = 8766 hr/yr

Average electrical power input:
Ẇ_avg = 817,000 Wh / 8766 hr = 93.19 W ≈ 93.2 W
```

**Step 10: Calculate average cooling rate**
```
Using First Law relationship:
Q̇_L = COP_R × Ẇ_in = 1.227 × 93.19 W = 114.37 W ≈ 114.4 W
```
This represents the time-averaged heat removal from both compartments.

**Step 11: Calculate refrigerant mass flow rate**
```
From evaporator energy balance: Q̇_L = ṁ × q_L
Therefore: ṁ = Q̇_L / q_L
ṁ = 114.37 W / 197.51 kJ/kg = 114.37 J/s / 197,510 J/kg
ṁ = 0.000579 kg/s = 0.579 g/s
```
This is the time-averaged refrigerant circulation rate.

**Step 12: Calculate heat rejection rate to kitchen**
```
From First Law energy balance on entire system:
Q̇_H = Q̇_L + Ẇ_in = 114.37 + 93.19 = 207.56 W ≈ 207.6 W

Alternative verification using refrigerant properties:
Q̇_H = ṁ × (h₂ − h₃) = 0.000579 kg/s × (680.67 − 322.16) kJ/kg
Q̇_H = 0.000579 × 358.51 = 207.58 W ✓ (matches)
```

**Step 13: Verify Second Law (entropy generation must be positive)**
```
Temperature conversions:
• Cold reservoir: T_L = 0°F = −17.78°C = 255.37 K
• Hot reservoir: T_H = 79°F = 26.11°C = 299.26 K

Entropy generation rate (Second Law):
Ṡ_gen = Q̇_H/T_H − Q̇_L/T_L
Ṡ_gen = 207.56 W / 299.26 K − 114.37 W / 255.37 K
Ṡ_gen = 0.6938 W/K − 0.4478 W/K = 0.2460 W/K ≥ 0 ✓
```
The positive value confirms the Second Law is satisfied (irreversible process).

**Step 14: Compare to Carnot COP (theoretical maximum)**
```
COP_Carnot = T_L / (T_H − T_L)
COP_Carnot = 255.37 K / (299.26 K − 255.37 K) = 255.37 / 43.89 = 5.82

Second-law efficiency: η_II = COP_actual / COP_Carnot
η_II = 1.227 / 5.82 = 0.211 = 21.1%
```
This shows the system operates at 21% of ideal Carnot efficiency.

---

### CASE 3: Restricted Airflow (T_c = 55°C)

**Step 1: Identify state properties**
- State 1 (unchanged): P₁ = 0.559 bar, h₁ = 519.67 kJ/kg, T₁ = 247.15 K
- State 3: P₃ = 7.730 bar, h₃ = 335.25 kJ/kg at T_c = 55°C

**Step 2: Pressure ratio**
```
r_p = 7.730 / 0.559 = 13.83
```

**Step 3: Isentropic outlet temperature**
```
T_2s = 247.15 K × (13.83)^0.09502
ln(13.83) = 2.6271, so 13.83^0.09502 = e^0.2497 = 1.2835
T_2s = 247.15 × 1.2835 = 317.24 K
```

**Step 4: Isentropic work**
```
Δh_is = 1.692 × (317.24 − 247.15) = 1.692 × 70.09 = 118.56 kJ/kg
```

**Step 5: Actual compressor work**
```
w_in = 118.56 / 0.70 = 169.37 kJ/kg
h₂ = 519.67 + 169.37 = 689.04 kJ/kg
T₂ = 247.15 + 169.37/1.692 = 347.25 K = 74.10°C
```

**Step 6-8: Throttle and refrigerating effect**
```
h₄ = h₃ = 335.25 kJ/kg
q_L = 519.67 − 335.25 = 184.42 kJ/kg
COP_R = 184.42 / 169.37 = 1.09
```

**Step 9: Energy calculations**
```
If same cooling load maintained (114.4 W):
Ẇ_needed = Q̇_L / COP = 114.4 / 1.09 = 105.05 W
Annual energy = 105.05 W × 8766 hr = 920,880 Wh = 921 kWh/yr

If same power (93.2 W):
Q̇_L = 1.09 × 93.2 = 101.5 W
ṁ = 101.5 / 184.42 = 0.550 g/s
Q̇_H = 101.5 + 93.2 = 194.7 W
```

**Step 10: Entropy generation**
```
Ṡ_gen = 194.7/299.26 − 101.5/255.37 = 0.6506 − 0.3974 = 0.2532 W/K ≥ 0 ✓
```

---

### Summary Table of All Results

| Case | T_c (°C) | P_high (bar) | P ratio | w_in (kJ/kg) | q_L (kJ/kg) | COP_R | Q̇_L (W) | Q̇_H (W) | ṁ (g/s) | Ṡ_gen (W/K) |
|------|----------|--------------|---------|--------------|-------------|-------|---------|---------|---------|-------------|
| Clean / better airflow | 45 | 6.044 | 10.81 | 150.21 | 210.60 | 1.40 | 130.7 | 223.9 | 0.620 | 0.2365 |
| **Baseline (tight cabinetry)** | **50** | **6.887** | **12.32** | **161.00** | **197.51** | **1.23** | **114.4** | **207.6** | **0.579** | **0.2460** |
| Restricted airflow | 55 | 7.730 | 13.83 | 169.37 | 184.42 | 1.09 | 101.5 | 194.7 | 0.550 | 0.2532 |

---

## 7. Design/Operating Change Analysis: Condenser Heat Rejection

Because the unit is built into tight cabinetry, the condenser may run hotter due to reduced airflow. This increases condenser saturation pressure, increases compressor pressure ratio, increases compressor specific work w_in, and reduces COP.

### Annual Energy Impact Estimate

Keeping the same cooling load across scenarios:

| Scenario | Assumed condenser condition | COP_R | Avg Ẇ needed for same Q̇_L (W) | Annual energy (kWh/yr) |
|----------|----------------------------|-------|-------------------------------|------------------------|
| Cleaner / better airflow | T_c ≈ 45°C | 1.40 | 81.7 | 722 |
| **Baseline (your installation)** | **T_c ≈ 50°C** | **1.23** | **93.2** | **817** |
| Restricted airflow | T_c ≈ 55°C | 1.09 | 105.1 | 921 |

**Interpretation:** Moving from a 'cleaner/better airflow' condenser condition (45°C) to a 'restricted airflow' condition (55°C) can increase annual energy from about **722 to 921 kWh/yr** for the same average cooling requirement. This directly follows from Ẇ_in = Q̇_L/COP_R.

**Energy cost impact:** At $0.15/kWh electricity rate:
- Best case (45°C): 722 kWh × $0.15 = **$108.30/yr**
- Baseline (50°C): 817 kWh × $0.15 = **$122.55/yr**
- Worst case (55°C): 921 kWh × $0.15 = **$138.15/yr**
- **Total range: $29.85/yr difference** between best and worst airflow

---

## 8. Heat Leak Model (UA) and Ambient Temperature Sensitivity

To connect the cycle results to a building-physics style model, I estimate an equivalent overall heat leak coefficient UA by lumping all heat gains (through insulation, gasket leakage, door openings, internal lights/fans, and warm food loads) into a single linear relation:

```
Q̇_L ≈ UA · (T_ambient − T_cold,eq)
```

### Detailed UA Calculation

**Temperature difference (baseline case):**
```
T_ambient = 79°F = 26.11°C = 299.26 K
T_freezer = 0°F = −17.78°C = 255.37 K
ΔT = 299.26 K − 255.37 K = 43.89 K
```

**Baseline case UA:**
```
UA = Q̇_L / ΔT = 114.4 W / 43.89 K = 2.606 W/K ≈ 2.61 W/K
```

**Physical interpretation:** This UA value represents the combined thermal conductance of:
- Insulation (polyurethane foam, typical R-value ~30 ft²·°F·hr/Btu)
- Door gaskets (rubber seals with some air leakage)
- Thermal bridges (hinges, shelving supports)
- Internal heat sources (lighting: ~3-5 W, fans: ~5-8 W)
- Usage patterns (door openings: ~20-30 times/day for typical family)

**Estimating insulation contribution alone:**
```
For a side-by-side 48" unit, approximate total surface area:
A_total ≈ 2(H×W + H×D + W×D) where H≈1.8m, W≈1.2m, D≈0.75m
A_total ≈ 2(1.8×1.2 + 1.8×0.75 + 1.2×0.75) = 2(4.41) ≈ 8.8 m²

If insulation thickness t = 75 mm with polyurethane k = 0.024 W/(m·K):
UA_insulation = (k × A) / t = (0.024 × 8.8) / 0.075 = 2.81 W/K
```

This is close to measured UA = 2.61 W/K, suggesting insulation dominates the heat leak.

### Ambient Temperature Sensitivity Analysis

**Compare performance at 70°F (21.1°C) vs 79°F (26.1°C):**

**At T_H = 70°F = 294.26 K:**
```
ΔT = 294.26 − 255.37 = 38.89 K
Q̇_L,70F = UA × ΔT = 2.61 × 38.89 = 101.5 W
COP_Carnot,70F = 255.37 / 38.89 = 6.57
COP_actual,70F ≈ 1.23 × (6.57/5.82) = 1.39
Ẇ_70F = 101.5 / 1.39 = 73.0 W
Annual energy at 70°F: 73.0 W × 8766 hr = 640 kWh/yr
```

**At T_H = 79°F = 299.26 K (baseline):**
```
ΔT = 43.89 K
Q̇_L,79F = 2.61 × 43.89 = 114.4 W
COP_Carnot,79F = 255.37 / 43.89 = 5.82
COP_actual,79F = 1.23 (measured)
Ẇ_79F = 114.4 / 1.23 = 93.2 W
Annual energy at 79°F: 93.2 W × 8766 hr = 817 kWh/yr ✓ (matches EnergyGuide)
```

**Impact summary:**
- Percentage increase in power: (93.2 − 73.0) / 73.0 × 100% = **+27.7%**
- Annual energy increase: 817 − 640 = **177 kWh/yr** additional
- At $0.15/kWh electricity cost: 177 kWh × $0.15 = **$26.55/yr** extra operating cost

### Impact of Condenser Temperature on System Performance

**Mechanism:** Higher ambient → higher condenser temperature → higher pressure ratio → more compressor work → lower COP

**Quantified relationship (from cycle analysis):**

Change from T_c = 45°C to T_c = 55°C (10°C span):
- Pressure ratio increases: 10.81 → 13.83 **(+28.0%)**
- Compressor work increases: 150.2 → 169.4 kJ/kg **(+12.8%)**
- Refrigerating effect decreases: 210.6 → 184.4 kJ/kg **(−12.4%)**
- COP decreases: 1.40 → 1.09 **(−22.1%)**
- For same cooling load, power increases: 81.7 → 105.1 W **(+28.5%)**
- Annual energy increases: