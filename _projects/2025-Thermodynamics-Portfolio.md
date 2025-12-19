---
layout: project
title: "Thermodynamics Portfolio — Sub-Zero Refrigerator Cycle Analysis"
description: "Above-and-beyond vapor-compression refrigeration cycle analysis (real numbers, state points, COP, Second Law)."
technologies: [Thermodynamics, Vapor-Compression, R-600a, First Law, Second Law, COP]
image: /assets/images/subzero-fridge.jpg
permalink: /projects/2025-Thermodynamics-Portfolio/
---

<!-- =========================================================
  Elegant self-contained styling (safe for GitHub Pages)
========================================================== -->
<style>
/* ... keep your existing :root and other styles ... */

/* ---------- Elegant equation formatting (NOT code-looking) ---------- */
.eq{
  font-family: var(--sans);
  background: rgba(255,255,255,0.05);
  border: 1px solid var(--stroke);
  border-radius: 14px;
  padding: 14px 14px;
  margin: 12px 0;
  box-shadow: 0 10px 26px rgba(0,0,0,0.18);
}

.eq .eq-title{
  font-size: 0.85rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--muted2);
  margin-bottom: 10px;
}

.eq .line{
  display: flex;
  gap: 12px;
  align-items: baseline;
  padding: 6px 0;
  border-top: 1px dashed rgba(255,255,255,0.10);
}
.eq .line:first-of-type{ border-top: none; }

.eq .lhs{
  min-width: 120px;
  font-weight: 700;
  color: rgba(255,255,255,0.88);
}

.eq .rhs{
  flex: 1;
  color: rgba(255,255,255,0.84);
}

.eq .rhs em{
  font-style: normal;
  color: var(--accent);
  font-weight: 700;
}

.eq .rhs .subtle{
  color: var(--muted2);
  font-weight: 500;
}

.eq .rhs .final{
  color: var(--accent2);
  font-weight: 800;
}

@media (max-width: 700px){
  .eq .line{ flex-direction: column; gap: 6px; }
  .eq .lhs{ min-width: auto; }
}
/* ---------- Pretty wide tables that scroll nicely ---------- */
.table-wrap{
  overflow-x: auto;
  border-radius: 16px;
  border: 1px solid var(--stroke);
  background: rgba(0,0,0,0.14);
  box-shadow: 0 10px 26px rgba(0,0,0,0.18);
  margin: 12px 0 6px 0;
}

.table-wrap table{
  min-width: 1100px; /* forces scroll instead of ugly wrapping */
  border: none;
  margin: 0;
}

.table-wrap th{
  position: sticky;
  top: 0;
  background: rgba(255,255,255,0.09);
  backdrop-filter: blur(6px);
  z-index: 1;
}

.table-wrap td, .table-wrap th{
  padding: 10px 12px;
  white-space: nowrap; /* prevents broken wrapping */
}

.table-wrap td:first-child, .table-wrap th:first-child{
  white-space: normal; /* allow the Case name to wrap */
  min-width: 240px;
}

.section h2{
  padding-bottom: 10px;
  border-bottom: 1px solid rgba(255,255,255,0.10);
}
</style>


<div class="thermo-wrap">

  <div class="hero">
    <h1>Thermodynamics Portfolio: Above-and-Beyond Vapor-Compression Cycle Analysis</h1>
    <p class="sub">
      <b>Device:</b> Sub-Zero CL4850SID/S (48" built-in side-by-side refrigerator/freezer, internal dispenser).<br/>
      <b>Course text:</b> Moran &amp; Shapiro, <i>Fundamentals of Engineering Thermodynamics</i>, Ch. 1–10.
    </p>

    <div class="meta-grid">
      <div class="pill"><div class="k">Ambient</div><div class="v">79°F (26.1°C), built into tight cabinetry</div></div>
      <div class="pill"><div class="k">Annual energy</div><div class="v">817 kWh/yr</div></div>
      <div class="pill"><div class="k">Avg electrical input</div><div class="v">≈ 93.2 W</div></div>
      <div class="pill"><div class="k">Setpoints</div><div class="v">38°F fridge / 0°F freezer</div></div>
    </div>

    <p class="foot">
      All numeric assumptions, state-point values, and results on this page are transcribed from (and consistent with) the submitted report :contentReference[oaicite:1]{index=1}.
    </p>
  </div>

  <div class="toc">
    <strong>Contents</strong>
    <div>
      <a href="#motivation">1. Personal Background & Motivation</a> ·
      <a href="#context">2. Device Overview & Operating Context</a> ·
      <a href="#qual">3. Qualitative Description</a> ·
      <a href="#balances">4. Governing Balances</a> ·
      <a href="#model">5. State-Point Model</a> ·
      <a href="#results">6. Full Cycle Calculations</a> ·
      <a href="#designchange">7. Design/Operating Change Analysis</a> ·
      <a href="#ua">8. Heat-Leak (UA) + Ambient Sensitivity</a> ·
      <a href="#measurements">9. Optional Measurements</a> ·
      <a href="#sources">10. Sources</a>
    </div>
  </div>

  <!-- ========================================================= -->
  <div id="motivation" class="section">
    <h2>1. Personal Background & Motivation</h2>
    <p class="muted">
      This refrigerator is installed in my own home. In everyday use, I feel it keeps food fresh for longer than other refrigerators I have used.
      Because it is a real appliance I interact with daily, it is a strong candidate for connecting vapor-compression refrigeration theory
      (control volumes, First Law, Second Law, COP) to a real engineered product. :contentReference[oaicite:2]{index=2}
    </p>
  </div>

  <!-- ========================================================= -->
  <div id="context" class="section">
    <h2>2. Device Overview & Real Operating Context</h2>

    <div class="callout">
      <b>Key idea:</b> Tight cabinetry can reduce airflow across the condenser → higher condensing temperature → higher compressor work → lower COP.
      This page quantifies that mechanism using a state-point model plus published annual electricity use. :contentReference[oaicite:3]{index=3}
    </div>

    <table>
      <thead>
        <tr><th>Quantity</th><th>Value</th><th>How used in calculations</th></tr>
      </thead>
      <tbody>
        <tr><td>Annual energy use</td><td>817 kWh/yr</td><td>Converted to time-average electrical power input</td></tr>
        <tr><td>Average electrical input</td><td>≈ 93.3 W</td><td>Used with COP to estimate average cooling rate</td></tr>
        <tr><td>Recommended setpoints</td><td>38°F fridge / 0°F freezer</td><td>Cold-side reference temperatures for entropy/COP bounds</td></tr>
        <tr><td>Electrical supply</td><td>115 VAC, 60 Hz; 15 A circuit</td><td>Shows available electrical power margin</td></tr>
      </tbody>
    </table>

    <p class="foot muted">
      Source notes (as stated in the report): annual energy + electrical info from Sub-Zero product/spec pages and EnergyGuide; setpoints from the Sub-Zero Classic Use & Care Guide. :contentReference[oaicite:4]{index=4}
    </p>
  </div>

  <!-- ========================================================= -->
  <div id="qual" class="section">
    <h2>3. Qualitative Description (How It Works)</h2>

    <p class="muted">
      Thermodynamically, this Sub-Zero refrigerator operates as a vapor-compression refrigeration system: it removes heat from the refrigerator/freezer
      compartments (low-temperature region) and rejects that heat to the kitchen air (high-temperature region) using electrical work supplied to a compressor.
      The refrigerant circulates in a closed loop through four main components: <b>evaporator → compressor → condenser → expansion device (throttle)</b>. :contentReference[oaicite:5]{index=5}
    </p>

    <div class="grid2">
      <div class="eq">
  <div class="eq-title">Case 2 — Baseline Tight Cabinetry (Tc = 50°C)</div>

  <div class="line">
    <div class="lhs">Given</div>
    <div class="rhs">
      State 1: P₁ = 0.559 bar, h₁ = 519.67 kJ/kg, T₁ = 247.15 K
      <span class="subtle"> (sat vapor at Te = −26°C)</span>
      <br/>
      State 3: P₃ = 6.887 bar, h₃ = 322.16 kJ/kg <span class="subtle">(interp. at Tc = 50°C)</span>
    </div>
  </div>

  <div class="line">
    <div class="lhs">Pressure ratio</div>
    <div class="rhs">
      rₚ = P_high / P_low = 6.887 / 0.559 = <span class="final">12.32</span>
    </div>
  </div>

  <div class="line">
    <div class="lhs">Exponent</div>
    <div class="rhs">
      (k−1)/k = (1.105−1)/1.105 = <em>0.09502</em>
    </div>
  </div>

  <div class="line">
    <div class="lhs">Isentropic T₂s</div>
    <div class="rhs">
      T₂s = T₁·(rₚ)^((k−1)/k) = 247.15·(12.32)^0.09502 = <span class="final">313.76 K</span>
      <span class="subtle">(≈ 40.61°C)</span>
    </div>
  </div>

  <div class="line">
    <div class="lhs">Δh_is</div>
    <div class="rhs">
      Δh_is = cₚ·(T₂s − T₁) = 1.692·(313.76 − 247.15) = <span class="final">112.70 kJ/kg</span>
    </div>
  </div>

  <div class="line">
    <div class="lhs">w_in, h₂</div>
    <div class="rhs">
      w_in = Δh_is/η_is = 112.70/0.70 = <span class="final">161.00 kJ/kg</span><br/>
      h₂ = h₁ + w_in = 519.67 + 161.00 = <span class="final">680.67 kJ/kg</span>
    </div>
  </div>

  <div class="line">
    <div class="lhs">Throttle</div>
    <div class="rhs">
      h₄ = h₃ = <span class="final">322.16 kJ/kg</span>
    </div>
  </div>

  <div class="line">
    <div class="lhs">q_L</div>
    <div class="rhs">
      q_L = h₁ − h₄ = 519.67 − 322.16 = <span class="final">197.51 kJ/kg</span>
    </div>
  </div>

  <div class="line">
    <div class="lhs">COP</div>
    <div class="rhs">
      COP_R = q_L / w_in = 197.51 / 161.00 = <span class="final">1.227 ≈ 1.23</span>
    </div>
  </div>

  <div class="line">
    <div class="lhs">Power</div>
    <div class="rhs">
      Ẇ_avg = 817,000 Wh / 8766 hr = <span class="final">93.19 W</span>
    </div>
  </div>

  <div class="line">
    <div class="lhs">Cooling rate</div>
    <div class="rhs">
      Q̇_L = COP·Ẇ = 1.227·93.19 = <span class="final">114.37 W</span>
    </div>
  </div>

  <div class="line">
    <div class="lhs">ṁ</div>
    <div class="rhs">
      ṁ = Q̇_L / q_L = 114.37 / 197,510 = <span class="final">0.000579 kg/s = 0.579 g/s</span>
    </div>
  </div>

  <div class="line">
    <div class="lhs">Heat out</div>
    <div class="rhs">
      Q̇_H = Q̇_L + Ẇ = 114.37 + 93.19 = <span class="final">207.56 W</span>
    </div>
  </div>

  <div class="line">
    <div class="lhs">Second Law</div>
    <div class="rhs">
      T_L = 255.37 K, T_H = 299.26 K<br/>
      Ṡ_gen = Q̇_H/T_H − Q̇_L/T_L = 207.56/299.26 − 114.37/255.37
      = <span class="final">0.2460 W/K ≥ 0</span> ✓
    </div>
  </div>

  <div class="line">
    <div class="lhs">Carnot bound</div>
    <div class="rhs">
      COP_Carnot = T_L/(T_H−T_L) = 255.37/(299.26−255.37) = <span class="final">5.82</span><br/>
      η_II = COP_actual/COP_Carnot = 1.227/5.82 = <span class="final">0.211 ≈ 21.1%</span>
    </div>
  </div>
</div>

Overall control-volume view (sealed loop):<br/>
Cold spaces (Fridge + Freezer): heat in Q̇L<br/>
Kitchen air (79°F): heat out Q̇H<br/>
Compressor: work in Ẇin
      </div>
    </div>
  </div>

  <!-- ========================================================= -->
  <div id="balances" class="section">
    <h2>4. System Diagram & Governing Balances (Moran Ch. 4–5)</h2>

    <p class="muted">
      The sealed refrigeration loop is modeled as a steady-cycle control volume. Working-fluid mass circulates internally, so net mass flow across the
      outer boundary is approximately zero. Heat and work cross the boundary. :contentReference[oaicite:6]{index=6}
    </p>

    <div class="eq">
(1) Mass balance (overall sealed loop):  Σṁ_in − Σṁ_out = 0
    </div>

    <div class="eq">
(2) Energy balance (steady-cycle First Law):  Q̇_H = Q̇_L + Ẇ_in
    </div>

    <div class="eq">
(3) Entropy balance (Second Law, two-reservoir form):  Ṡ_gen = Q̇_H/T_H − Q̇_L/T_L  ≥  0
    </div>

    <div class="eq">
(4) Performance metric (Moran Ch. 10):  COP_R = Q̇_L / Ẇ_in
    </div>
  </div>

  <!-- ========================================================= -->
  <div id="model" class="section">
    <h2>5. State-Point Cycle Model with Real Numbers</h2>

    <p class="muted">
      A full manufacturer thermodynamic test map for this exact unit is not public, so this model uses:
      (i) published annual electricity use, (ii) recommended compartment setpoints, (iii) a common low-GWP domestic refrigerant assumption (R-600a),
      and (iv) published R-600a property tables. The goal is to compute key cycle quantities
      (q<sub>L</sub>, w<sub>in</sub>, COP, ṁ, Q̇<sub>L</sub>, Q̇<sub>H</sub>) at representative operating temperatures and quantify sensitivity to condenser conditions. :contentReference[oaicite:7]{index=7}
    </p>

    <h3>Chosen representative temperatures</h3>
    <ul class="muted">
      <li><b>Evaporating saturation temperature:</b> T<sub>e</sub> = −26°C (colder than 0°F freezer air so heat can flow into the evaporator). :contentReference[oaicite:8]{index=8}</li>
      <li><b>Condensing saturation temperature cases:</b> baseline T<sub>c</sub> = 50°C; compare cleaner/better-airflow at 45°C and restricted-airflow at 55°C. :contentReference[oaicite:9]{index=9}</li>
    </ul>

    <h3>State-property values used</h3>
    <table>
      <thead>
        <tr><th>Quantity</th><th>Value</th><th>Meaning</th></tr>
      </thead>
      <tbody>
        <tr><td>P<sub>low</sub> @ −26°C</td><td>0.559 bar</td><td>Evaporator saturation pressure (State 1)</td></tr>
        <tr><td>h<sub>1</sub> @ −26°C sat vapor</td><td>519.67 kJ/kg</td><td>Compressor inlet enthalpy (State 1)</td></tr>
        <tr><td>s<sub>1</sub> @ −26°C sat vapor</td><td>2.3057 kJ/(kg·K)</td><td>Compressor inlet entropy (State 1)</td></tr>
        <tr><td>h<sub>3</sub> @ 45°C sat liquid</td><td>309.07 kJ/kg</td><td>Condenser outlet enthalpy, clean case (State 3)</td></tr>
        <tr><td>h<sub>3</sub> @ 50°C sat liquid (interp.)</td><td>322.16 kJ/kg</td><td>Condenser outlet enthalpy, baseline tight cabinetry (State 3)</td></tr>
        <tr><td>h<sub>3</sub> @ 55°C sat liquid</td><td>335.25 kJ/kg</td><td>Condenser outlet enthalpy, restricted airflow (State 3)</td></tr>
      </tbody>
    </table>
    <p class="foot muted">Values listed exactly as used in the report. :contentReference[oaicite:10]{index=10}</p>

    <h3>Component energy relations (steady-flow CV, neglect Δke, Δpe)</h3>
    <div class="eq">
(5) Compressor: Ẇ_in ≈ ṁ (h₂ − h₁)<br/>
(6) Condenser: Q̇_H ≈ ṁ (h₂ − h₃)<br/>
(7) Throttle: h₄ ≈ h₃ (isenthalpic throttling)<br/>
(8) Evaporator: Q̇_L ≈ ṁ (h₁ − h₄)
    </div>
  </div>

  <!-- ========================================================= -->
  <div id="results" class="section">
    <h2>6. Step-by-Step Cycle Results (All Numbers)</h2>

    <div class="callout">
      <b>Compressor model:</b> ideal-gas approximation with constant c<sub>p</sub>, k and isentropic efficiency η<sub>is</sub> = 0.70. :contentReference[oaicite:11]{index=11}
    </div>

    <table>
      <thead>
        <tr><th>Property</th><th>Value</th><th>Notes</th></tr>
      </thead>
      <tbody>
        <tr><td>c<sub>p</sub> (R-600a vapor)</td><td>1.692 kJ/(kg·K)</td><td>Used for Δh ≈ c<sub>p</sub>ΔT</td></tr>
        <tr><td>k (R-600a vapor)</td><td>1.105</td><td>Used for T₂s relation</td></tr>
        <tr><td>η<sub>is</sub></td><td>0.70</td><td>Typical small hermetic compressor</td></tr>
        <tr><td>Molecular weight</td><td>58.12 g/mol</td><td>Isobutane (C₄H₁₀)</td></tr>
      </tbody>
    </table>
    <p class="foot muted">Property values as stated in the report. :contentReference[oaicite:12]{index=12}</p>

    <!-- ========== CASE 1 ========== -->
    <details>
      <summary>CASE 1 — Clean / Better Airflow (T<sub>c</sub> = 45°C): full calculation steps</summary>

      <div class="eq">
State 1 (T_e = −26°C = 247.15 K): P₁ = 0.559 bar, h₁ = 519.67 kJ/kg, s₁ = 2.3057 kJ/(kg·K)<br/>
State 3 (T_c = 45°C = 318.15 K): P₃ = 6.044 bar, h₃ = 309.07 kJ/kg
      </div>

      <div class="eq">
Step 2: Pressure ratio: r_p = P_high / P_low = 6.044 / 0.559 = 10.81
      </div>

      <div class="eq">
Step 3: Isentropic outlet temperature:<br/>
T₂s = T₁ (P_high/P_low)^{(k−1)/k} = 247.15 × (10.81)^{0.09502} = 309.32 K
      </div>

      <div class="eq">
Step 4: Isentropic enthalpy change:<br/>
Δh_is = c_p (T₂s − T₁) = 1.692(309.32 − 247.15) = 105.15 kJ/kg
      </div>

      <div class="eq">
Step 5: Actual compressor work (η_is = 0.70):<br/>
w_in = Δh_is/η_is = 105.15/0.70 = 150.21 kJ/kg<br/>
h₂ = h₁ + w_in = 519.67 + 150.21 = 669.88 kJ/kg
      </div>

      <div class="eq">
Step 6: Throttle (isenthalpic): h₄ = h₃ = 309.07 kJ/kg
      </div>

      <div class="eq">
Step 7: Refrigerating effect: q_L = h₁ − h₄ = 519.67 − 309.07 = 210.60 kJ/kg
      </div>

      <div class="eq">
Step 8: COP: COP_R = q_L / w_in = 210.60 / 150.21 = 1.402 ≈ 1.40
      </div>

      <div class="eq">
Step 9–12 (power, ṁ, Q̇H, Ṡ_gen): uses annual energy conversion and two-reservoir entropy balance (see report).<br/>
Key computed example shown in report: ṁ ≈ 0.620 g/s, Q̇H ≈ 223.9 W, Ṡ_gen ≈ 0.2365 W/K
      </div>

      <p class="foot muted">Case 1 steps and numbers are copied from the report. :contentReference[oaicite:13]{index=13}</p>
    </details>

    <!-- ========== CASE 2 ========== -->
    <details open>
      <summary>CASE 2 — Baseline Tight Cabinetry (T<sub>c</sub> = 50°C): full detailed steps</summary>

      <div class="eq">
State 1 (T_e = −26°C = 247.15 K): P₁ = 0.559 bar, h₁ = 519.67 kJ/kg, s₁ = 2.3057 kJ/(kg·K), T₁ = 247.15 K<br/>
State 3 (T_c = 50°C = 323.15 K): P₃ = 6.887 bar (interp.), h₃ = 322.16 kJ/kg (interp.)
      </div>

      <div class="eq">
Step 2: Pressure ratio: r_p = 6.887 / 0.559 = 12.32
      </div>

      <div class="eq">
Step 3: Exponent: (k−1)/k = (1.105−1)/1.105 = 0.09502<br/>
T₂s = 247.15 × (12.32)^{0.09502} = 313.76 K (≈ 40.61°C)
      </div>

      <div class="eq">
Step 4: Δh_is = c_p (T₂s − T₁) = 1.692(313.76 − 247.15) = 112.70 kJ/kg
      </div>

      <div class="eq">
Step 5: Actual compressor work: w_in = Δh_is/η_is = 112.70/0.70 = 161.00 kJ/kg<br/>
h₂ = h₁ + w_in = 519.67 + 161.00 = 680.67 kJ/kg<br/>
Approx. T₂ = T₁ + (Δh_actual/c_p) = 247.15 + 161.00/1.692 = 342.31 K (≈ 69.16°C)
      </div>

      <div class="eq">
Step 6: Throttle (adiabatic, no work): h₄ = h₃ = 322.16 kJ/kg
      </div>

      <div class="eq">
Step 7: Refrigerating effect: q_L = h₁ − h₄ = 519.67 − 322.16 = 197.51 kJ/kg
      </div>

      <div class="eq">
Step 8: COP: COP_R = q_L / w_in = 197.51 / 161.00 = 1.227 ≈ 1.23
      </div>

      <div class="eq">
Step 9: Annual energy → average power:<br/>
817 kWh/yr = 817,000 Wh/yr; 8766 hr/yr → Ẇ_avg = 817,000/8766 = 93.19 W
      </div>

      <div class="eq">
Step 10: Average cooling rate: Q̇_L = COP × Ẇ = 1.227 × 93.19 = 114.37 W
      </div>

      <div class="eq">
Step 11: Mass flow rate: ṁ = Q̇_L / q_L = 114.37 / 197,510 = 0.000579 kg/s = 0.579 g/s
      </div>

      <div class="eq">
Step 12: Heat rejection: Q̇_H = Q̇_L + Ẇ = 114.37 + 93.19 = 207.56 W<br/>
Check: Q̇_H = ṁ(h₂ − h₃) = 0.000579(680.67−322.16)kJ/kg = 207.58 W ✓
      </div>

      <div class="eq">
Step 13: Reservoir temperatures:<br/>
T_L = 0°F = 255.37 K;  T_H = 79°F = 299.26 K<br/>
Ṡ_gen = Q̇_H/T_H − Q̇_L/T_L = 207.56/299.26 − 114.37/255.37 = 0.2460 W/K ≥ 0 ✓
      </div>

      <div class="eq">
Step 14: Carnot COP and second-law efficiency:<br/>
COP_Carnot = T_L/(T_H − T_L) = 255.37/(299.26−255.37) = 5.82<br/>
η_II = COP_actual/COP_Carnot = 1.227/5.82 = 0.211 ≈ 21.1%
      </div>

      <p class="foot muted">Case 2 steps and numbers are copied from the report. :contentReference[oaicite:14]{index=14}</p>
    </details>

    <!-- ========== CASE 3 ========== -->
    <details>
      <summary>CASE 3 — Restricted Airflow (T<sub>c</sub> = 55°C): full detailed steps</summary>

      <div class="eq">
State 1 (unchanged): P₁ = 0.559 bar, h₁ = 519.67 kJ/kg, T₁ = 247.15 K<br/>
State 3: P₃ = 7.730 bar, h₃ = 335.25 kJ/kg at T_c = 55°C = 328.15 K
      </div>

      <div class="eq">
Pressure ratio: r_p = 7.730/0.559 = 13.83
      </div>

      <div class="eq">
T₂s = 247.15 × (13.83)^{0.09502} = 317.24 K
      </div>

      <div class="eq">
Δh_is = 1.692(317.24 − 247.15) = 118.56 kJ/kg<br/>
w_in = 118.56/0.70 = 169.37 kJ/kg<br/>
h₂ = 519.67 + 169.37 = 689.04 kJ/kg<br/>
T₂ ≈ 247.15 + 169.37/1.692 = 347.25 K (≈ 74.10°C)
      </div>

      <div class="eq">
Throttle: h₄ = h₃ = 335.25 kJ/kg<br/>
q_L = h₁ − h₄ = 519.67 − 335.25 = 184.42 kJ/kg<br/>
COP = 184.42/169.37 = 1.089 ≈ 1.09
      </div>

      <div class="eq">
If same cooling load (114.4 W): Ẇ_needed = 114.4/1.089 = 105.05 W → Annual ≈ 921 kWh/yr<br/>
If same power (93.2 W): Q̇_L = 1.089 × 93.2 = 101.5 W; ṁ ≈ 0.550 g/s; Q̇_H ≈ 194.7 W<br/>
Ṡ_gen = 194.7/299.26 − 101.5/255.37 = 0.2532 W/K ≥ 0 ✓
      </div>

      <p class="foot muted">Case 3 steps and numbers are copied from the report. :contentReference[oaicite:15]{index=15}</p>
    </details>

<h3>Summary table (all cases)</h3>

<div class="table-wrap">
  <table>
    <thead>
      <tr>
        <th>Case</th><th>Tc (°C)</th><th>P_high (bar)</th><th>P ratio</th>
        <th>w_in (kJ/kg)</th><th>q_L (kJ/kg)</th><th>COP_R</th>
        <th>Q̇_L (W)</th><th>Q̇_H (W)</th><th>ṁ (g/s)</th><th>Ṡ_gen (W/K)</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Clean / better airflow</td><td>45</td><td>6.044</td><td>10.81</td>
        <td>150.21</td><td>210.60</td><td>1.40</td>
        <td>130.7</td><td>223.9</td><td>0.620</td><td>0.2365</td>
      </tr>
      <tr>
        <td><strong>Baseline (tight cabinetry)</strong></td><td><strong>50</strong></td><td><strong>6.887</strong></td><td><strong>12.32</strong></td>
        <td><strong>161.00</strong></td><td><strong>197.51</strong></td><td><strong>1.23</strong></td>
        <td><strong>114.4</strong></td><td><strong>207.6</strong></td><td><strong>0.579</strong></td><td><strong>0.2460</strong></td>
      </tr>
      <tr>
        <td>Restricted airflow (dust/blocked)</td><td>55</td><td>7.730</td><td>13.83</td>
        <td>169.37</td><td>184.42</td><td>1.09</td>
        <td>101.5</td><td>194.7</td><td>0.550</td><td>0.2532</td>
      </tr>
    </tbody>
  </table>
</div>

    <p class="foot muted">Table values match the report. :contentReference[oaicite:16]{index=16}</p>

  </div>

  <!-- ========================================================= -->
  <div id="designchange" class="section">
    <h2>7. Design/Operating Change Analysis: Condenser Heat Rejection in Tight Cabinetry</h2>

    <p class="muted">
      Tight cabinetry can increase condenser temperature due to reduced airflow. That increases condenser saturation pressure, increases compressor pressure ratio,
      increases compressor specific work, and reduces COP. The results above quantify this trend. :contentReference[oaicite:17]{index=17}
    </p>

    <h3>Annual energy impact estimate (same cooling load)</h3>
    <table>
      <thead>
        <tr><th>Scenario</th><th>Assumed condenser condition</th><th>COP_R</th><th>Avg Ẇ needed (W)</th><th>Annual energy (kWh/yr)</th></tr>
      </thead>
      <tbody>
        <tr><td>Cleaner / better airflow</td><td>Tc ≈ 45°C</td><td>1.39</td><td>82.4</td><td>722</td></tr>
        <tr><td>Baseline (your installation)</td><td>Tc ≈ 50°C</td><td>1.23</td><td>93.3</td><td>817</td></tr>
        <tr><td>Restricted airflow</td><td>Tc ≈ 55°C</td><td>1.09</td><td>105.1</td><td>920</td></tr>
      </tbody>
    </table>

    <p class="muted">
      Interpretation: moving from “cleaner/better airflow” (45°C) to “restricted airflow” (55°C) increases annual energy from about 722 to 920 kWh/yr for the same
      average cooling requirement, since Ẇ = Q̇_L / COP_R. :contentReference[oaicite:18]{index=18}
    </p>
  </div>

  <!-- ========================================================= -->
  <div id="ua" class="section">
    <h2>8. Extra: Heat-Leak Model (UA) and Ambient Temperature Sensitivity</h2>

    <p class="muted">
      To connect the cycle results to a building-physics style model, the report estimates an equivalent overall heat leak coefficient
      UA by lumping heat gains into a linear relation: Q̇_L ≈ UA (T_ambient − T_cold,eq). :contentReference[oaicite:19]{index=19}
    </p>

    <div class="eq">
Baseline ΔT: T_ambient = 79°F = 299.26 K; T_freezer = 0°F = 255.37 K → ΔT = 43.89 K<br/>
UA = Q̇_L / ΔT = 114.4 W / 43.89 K = 2.606 W/K ≈ 2.61 W/K
    </div>

    <details>
      <summary>What does UA physically represent here?</summary>
      <ul class="muted">
        <li>Combined conductance of insulation, gasket leakage, thermal bridges, internal fans/lights, and usage patterns. :contentReference[oaicite:20]{index=20}</li>
        <li>Insulation-only back-of-envelope: area ≈ 8.8 m²; polyurethane k ≈ 0.024 W/(m·K); thickness 0.075 m → UA ≈ 2.81 W/K (close to 2.61 W/K). :contentReference[oaicite:21]{index=21}</li>
      </ul>
    </details>

    <h3>Ambient temperature sensitivity (70°F vs 79°F)</h3>
    <div class="eq">
At 70°F: ΔT = 38.89 K → Q̇_L ≈ 2.61×38.89 = 101.5 W<br/>
COP_Carnot,70F = 6.57; COP_actual,70F ≈ 1.39 → Ẇ ≈ 73.0 W → Annual ≈ 640 kWh/yr<br/><br/>
At 79°F (baseline): Q̇_L ≈ 114.4 W; COP_Carnot = 5.82; COP_actual = 1.23 → Ẇ ≈ 93.2 W → Annual ≈ 817 kWh/yr
    </div>

    <p class="muted">
      Impact summary in the report: power increases by ≈ 27.7% (73.0 → 93.2 W), annual energy increases by ≈ 177 kWh/yr (640 → 817),
      costing about $26.55/yr at $0.15/kWh. :contentReference[oaicite:22]{index=22}
    </p>

    <h3>Combined condenser + ambient effect (quantified)</h3>
    <ul class="muted">
      <li>From Tc = 45°C to 55°C: pressure ratio +28.0%, compressor work +12.8%, refrigerating effect −12.4%, COP −22.1%. :contentReference[oaicite:23]{index=23}</li>
      <li>For same cooling load: power +28.5% and annual energy 722 → 921 kWh (+27.6%). :contentReference[oaicite:24]{index=24}</li>
      <li>Moving from ideal (70°F + clean condenser) to challenging (79°F + restricted condenser) can raise annual energy by ~280 kWh/yr (640 → 920), about a 44% operating-cost increase (per report conclusion). :contentReference[oaicite:25]{index=25}</li>
    </ul>
  </div>

  <!-- ========================================================= -->
  <div id="measurements" class="section">
    <h2>9. Optional Measurements to Personalize Further</h2>

    <p class="muted">
      To make the analysis even more device-specific, the report recommends: (i) photo of rating plate (refrigerant charge in grams),
      (ii) measured condenser-air temperature behind the grille, (iii) short power log (plug-in meter for compressor cycling),
      and (iv) door-opening frequency. :contentReference[oaicite:26]{index=26}
    </p>
  </div>

  <!-- ========================================================= -->
  <div id="sources" class="section">
    <h2>10. Sources (as listed in the report)</h2>

    <p class="muted">
      Sub-Zero manufacturer sources (model specs, capacity, annual kWh, electrical supply), Sub-Zero Classic Series Use &amp; Care Guide (recommended setpoints),
      EnergyGuide label (817 kWh/yr), ENERGY STAR listing context, and published R-600a saturation tables / R-600a datasheet for c_p and k. :contentReference[oaicite:27]{index=27}
    </p>

    <div class="tag">Moran &amp; Shapiro Ch. 1–10</div>
    <div class="tag">EnergyGuide 817 kWh/yr</div>
    <div class="tag">R-600a property tables</div>
    <div class="tag">First Law + Second Law</div>
  </div>

</div>
