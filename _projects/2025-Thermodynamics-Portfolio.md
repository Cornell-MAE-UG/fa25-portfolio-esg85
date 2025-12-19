---
layout: project
title: Thermodynamics Portfolio - Sub-Zero Refrigerator Analysis
description: Vapor-Compression Refrigeration Cycle Analysis (state-point model + airflow/ambient sensitivity)
technologies: [Thermodynamics, R-600a Refrigerant, Energy Analysis]
image: /assets/images/subzero-fridge.jpg

# These populate the nicer project sidebar (from the updated project.html)
device: Sub-Zero CL4850SID/S (48-inch built-in side-by-side refrigerator/freezer, internal dispenser)
course: Moran & Shapiro, Fundamentals of Engineering Thermodynamics (Ch. 1–10)
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

<div class="table-wrap">

| Quantity | Value | How used in calculations |
|---|---:|---|
| Annual energy use | **817 kWh/yr** | Converted to time-average electrical power input |
| Average electrical input | **93.3 W** | Used with COP to estimate average cooling rate |
| Recommended setpoints | **38°F fridge / 0°F freezer** | Cold-side reference temperatures for entropy/COP bounds |
| Electrical supply | **115 VAC, 60 Hz; 15 A circuit** | Shows maximum available electrical power margin |

</div>

*Source notes: Annual energy use and electrical info are from Sub-Zero product/spec pages and the EnergyGuide label; recommended setpoints are from the Sub-Zero Classic Use & Care Guide.*

![Sub-Zero CL4850SID/S refrigerator]({{ "/assets/images/subzero-front.jpg" | relative_url }}){: .inline-image-r style="width: 320px"}
*Figure 1. Sub-Zero CL4850SID/S (front view).*

<div class="clearfix"></div>

---

## 3. Qualitative Description (How It Works)

Thermodynamically, the Sub-Zero refrigerator is a **vapor-compression refrigeration system**. It removes heat from the refrigerator/freezer compartments (low-temperature region) and rejects that heat to the kitchen air (high-temperature region) using electrical work supplied to a compressor. The refrigerant circulates in a closed loop through four main components:

1. **Evaporator** — Absorbs heat from food compartments  
2. **Compressor** — Increases pressure and temperature of refrigerant vapor  
3. **Condenser** — Rejects heat to kitchen air  
4. **Expansion device (throttle)** — Reduces pressure for refrigerant return  

### Vapor-Compression Cycle Components

```text
[Evaporator] → [Compressor] → [Condenser] → [Expansion Valve] → [Evaporator]
   Q̇_L in         Ẇ_in           Q̇_H out        (throttle)
