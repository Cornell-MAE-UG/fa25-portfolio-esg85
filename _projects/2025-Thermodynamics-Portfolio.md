---
layout: project
description: Vapor-Compression Refrigeration Cycle Analysis
technologies: [Thermodynamics, R-600a Refrigerant, Energy Analysis]
image: /assets/images/sub-zero-closed.png
---

<style>
/* Make sure layout doesn't constrain width */
main.container,
main.container-fluid{
  max-width: none !important;
  padding-left: 0 !important;
  padding-right: 0 !important;
  background: transparent !important;
}

/* Background */
body{
  background: linear-gradient(180deg, #0b1f33 0%, #102a43 45%, #081b2e 100%) !important;
}

/* Outer wrapper */
.pdf-shell{
  width: 100%;
  padding: 18px 18px 46px;
  display: flex;
  justify-content: center;
}

/* THIS is what makes it “screen-sized” */
.pdf-page{
  width: 98vw;                 /* nearly full screen */
  max-width: 1800px;           /* big monitors */
  background: #f8fafc;
  padding: 56px 72px;
  border-radius: 16px;
  box-shadow: 0 30px 90px rgba(0,0,0,0.45);
  border: 2px solid rgba(148,163,184,0.9);

  font-size: 19px;
  line-height: 1.65;
  color: #0b1220;
}

/* Headings */
.pdf-page h1{ font-size: 36px; color:#0b2a4a; }
.pdf-page h2{ font-size: 22px; color:#123a63; border-bottom:2px solid #cfe0f6; padding-bottom:8px; margin-top:26px; }
.pdf-page h3{ font-size: 19px; color:#1b4d85; margin-top:18px; }

.pdf-hr{
  border: none;
  border-top: 2px solid rgba(148,163,184,0.9);
  margin: 18px 0;
}

/* Tables (when markdown tables render) */
.pdf-page table{
  width: 100%;
  border-collapse: collapse;
  border: 2px solid rgba(148,163,184,0.9);
  margin: 14px 0;
  font-size: 16px;
}
.pdf-page th, .pdf-page td{
  border: 1.5px solid rgba(148,163,184,0.9);
  padding: 8px 10px;
  vertical-align: top;
}
.pdf-page th{
  background: #dbeafe;
  color: #0b2a4a;
  font-weight: 700;
}

/* Mobile */
@media (max-width: 900px){
  .pdf-page{
    width: 96vw;
    padding: 28px 16px;
    font-size: 17.5px;
  }
  .pdf-page h1{ font-size: 28px; }
}
/* Kill Bootstrap width constraints */
main.container,
main.container-fluid {
  max-width: none !important;
  padding-left: 0 !important;
  padding-right: 0 !important;
}

/* Outer shell */
.pdf-shell {
  width: 100%;
  padding: 24px 24px 56px;
  display: flex;
  justify-content: center;
}

/* TRUE wide page */
.pdf-page,
.wide-page {
  width: min(96vw, 2200px);   /* <-- wider than before */
  max-width: none;           /* <-- critical */
  background: #f8fafc;
  padding: 64px 96px;        /* wider text block */
  border-radius: 18px;

  font-size: 20px;
  line-height: 1.7;
  color: #0b1220;

  box-shadow: 0 35px 100px rgba(0,0,0,0.45);
  border: 2px solid rgba(148,163,184,0.85);
}

/* Mobile */
@media (max-width: 900px){
  .pdf-page {
    width: 98vw;
    padding: 28px 18px;
    font-size: 17.5px;
  }
}

</style>





<h1>Thermodynamics Portfolio: Sub Zero Refridgerator</h1>
<p class="pdf-subhead">
<b>Specific device:</b> Sub-Zero CL4850SID/S (48-inch built-in side-by-side refrigerator/freezer, internal dispenser)<br/>
</p>

<hr class="pdf-hr"/>

<h2>1. Personal Background &amp; Motivation</h2>
<p>
This refrigerator is the unit installed in my own home, making it a system I interact with daily when I am at home. Through regular use, I have found that it maintains food freshness longer than other refrigerators my family has previously used. Its familiarity and real-world operation make are the reason I chose it for connecting the vapor-compression refrigeration concepts from this course (control volumes, the First Law, the Second Law, and COP).
</p>

<hr class="pdf-hr"/>

<h2>2. Device Overview and Real Operating Context</h2>
<p>
My home kitchen/room temperature is approximately <b>79°F (26.1°C)</b>. The unit is installed in tight cabinetry, which can reduce airflow across the condenser and increase the condensing temperature and compressor work. This report quantifies how that mechanism affects performance using a refridgeration cycle model and the device's published annual electricity use.
</p>

<table>
  <thead>
    <tr>
      <th>Quantity</th>
      <th>Value</th>
      <th>How used in calculations</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Annual energy use</td>
      <td><b>817 kWh/yr</b></td>
      <td>Converted to time-average electrical power input</td>
    </tr>
    <tr>
      <td>Average electrical input</td>
      <td><b>93.3 W</b></td>
      <td>Used with COP to estimate average cooling rate</td>
    </tr>
    <tr>
      <td>Recommended setpoints</td>
      <td><b>38°F fridge / 0°F freezer</b></td>
      <td>Cold-side reference temperatures for entropy/COP bounds</td>
    </tr>
    <tr>
      <td>Electrical supply</td>
      <td><b>115 VAC, 60 Hz; 15 A circuit</b></td>
      <td>Shows maximum available electrical power margin</td>
    </tr>
  </tbody>
</table>

<p class="caption">
Source notes: Annual energy use and electrical info are from Sub-Zero product/spec pages and the EnergyGuide label; recommended setpoints are from the Sub-Zero Classic Use &amp; Care Guide.
</p>


<div class="row text-center">
  <div class="col-md-6">
    <div class="figure">
      <img src="{{ '/assets/images/sub-zero-closed.png' | relative_url }}"
           alt="Sub-Zero CL4850SID/S refrigerator closed"
           class="img-fluid">
      <div class="figcap">Figure. Sub-Zero CL4850SID/S refrigerator (closed).</div>
    </div>
  </div>

  <div class="col-md-6">
    <div class="figure">
      <img src="{{ '/assets/images/sub-zero-opened.jpg' | relative_url }}"
           alt="Sub-Zero CL4850SID/S refrigerator opened"
           class="img-fluid">
      <div class="figcap">Figure. Sub-Zero CL4850SID/S refrigerator (opened).</div>
    </div>
  </div>
</div>


<hr class="pdf-hr"/>

<h2>3. Qualitative Description (How It Works)</h2>
<p>
The Sub-Zero refrigerator is a <b>vapor-compression refrigeration system</b>. It removes heat from the refrigerator/freezer compartments (low-temperature region) and rejects that heat to the kitchen air (high-temperature region) using electrical work supplied to a compressor. The refrigerant circulates in a closed loop through four main components:
</p>
<ul>
  <li><b>Evaporator</b> – Absorbs heat from food compartments</li>
  <li><b>Compressor</b> – Increases pressure and temperature of refrigerant vapor</li>
  <li><b>Condenser</b> – Rejects heat to kitchen air</li>
  <li><b>Expansion device (throttle)</b> – Reduces pressure for refrigerant return</li>
</ul>

<div class="eqblock">
  <div class="eqline"><b>Vapor-compression loop:</b> [Evaporator] → [Compressor] → [Condenser] → [Expansion Valve] → [Evaporator]</div>
  <div class="eqline">Heat absorbed: Q̇<sub>L</sub> in (from compartments) &nbsp;&nbsp;|&nbsp;&nbsp; Work input: Ẇ<sub>in</sub> (electric) &nbsp;&nbsp;|&nbsp;&nbsp; Heat rejected: Q̇<sub>H</sub> out (to kitchen)</div>
</div>

<hr class="pdf-hr"/>
<div class="figure text-center">
  <img src="{{ '/assets/images/vapor-diagram.jpg' | relative_url }}"
       alt="Descriptive alt text"
       class="img-fluid">
  <div class="figcap">Diagram of Vapor-compression loop</div>
</div>

<h2>4. System Diagram &amp; Governing Balances</h2>
<p>
I model the sealed refrigeration loop as a steady-state control volume. The working fluid mass circulates internally, so net mass flow across the outer boundary is approximately zero. Heat and work cross the boundary.
</p>

<div class="eqblock">
  <div class="eqline"><b>Mass balance (overall sealed loop):</b> (1) &nbsp; Σṁ<sub>in</sub> − Σṁ<sub>out</sub> = 0</div>
</div>
<div class="eqblock">
  <div class="eqline"><b>Energy balance (steady-state First Law):</b> (2) &nbsp; Q̇<sub>H</sub> = Q̇<sub>L</sub> + Ẇ<sub>in</sub></div>
</div>
<div class="eqblock">
  <div class="eqline"><b>Entropy balance (Second Law, two-reservoir form):</b> (3) &nbsp; Ṡ<sub>gen</sub> = Q̇<sub>H</sub>/T<sub>H</sub> − Q̇<sub>L</sub>/T<sub>L</sub> ≥ 0</div>
</div>
<div class="eqblock">
  <div class="eqline"><b>Performance metric:</b> (4) &nbsp; COP<sub>R</sub> = Q̇<sub>L</sub> / Ẇ<sub>in</sub></div>
</div>

<hr class="pdf-hr"/>

<div class="row text-center">
  <div class="col-md-6">
    <div class="figure">
      <img src="{{ '/assets/images/ts-diagram.jpg' | relative_url }}"
           alt="TS Diagram"
           class="img-fluid">
      <div class="figcap">Figure. Sub-Zero CL4850SID/S refrigerator (closed).</div>
    </div>
  </div>

  <div class="col-md-6">
    <div class="figure">
      <img src="{{ '/assets/images/pv-diagram.jpg' | relative_url }}"
           alt="PV Diagram"
           class="img-fluid">
      <div class="figcap">Figure. Sub-Zero CL4850SID/S refrigerator (opened).</div>
    </div>
  </div>
</div>

<h2>5. State-Point Cycle Model with Real Numbers</h2>
<p>
A full manufacturer thermodynamic setup is not publicly provided for this exact unit, so I build a model using:
</p>
<ul>
  <li>(i) The unit's published annual electricity use</li>
  <li>(ii) The recommended compartment setpoints</li>
  <li>(iii) The common low-GWP domestic refrigerant <b>R-600a</b> (isobutane) used by many ENERGY STAR listed refrigerators</li>
  <li>(iv) R-600a thermodynamic property tables</li>
</ul>

<h3>Chosen Representative Temperatures</h3>
<ul>
  <li><b>Evaporating saturation temperature:</b> T<sub>e</sub> = <b>−26°C</b></li>
  <li><b>Condensing saturation temperature:</b>
    <ul>
      <li>Clean / better airflow: T<sub>c</sub> = <b>45°C</b></li>
      <li>Baseline tight cabinetry: T<sub>c</sub> = <b>50°C</b></li>
      <li>Restricted airflow: T<sub>c</sub> = <b>55°C</b></li>
    </ul>
  </li>
</ul>

<h3>R-600a Thermodynamic Properties</h3>
<table>
  <thead>
    <tr><th>Property</th><th>Value</th><th>Source/Notes</th></tr>
  </thead>
  <tbody>
    <tr><td>Specific heat, c<sub>p</sub></td><td><b>1.692 kJ/(kg·K)</b></td><td>R-600a vapor property datasheet</td></tr>
    <tr><td>Specific heat ratio, k</td><td><b>1.105</b></td><td>R-600a vapor property datasheet</td></tr>
    <tr><td>Isentropic efficiency, η<sub>is</sub></td><td><b>0.70 (70%)</b></td><td>Typical for small hermetic compressors</td></tr>
    <tr><td>Molecular weight</td><td><b>58.12 g/mol</b></td><td>Isobutane (C₄H₁₀)</td></tr>
  </tbody>
</table>

<h3>State Properties from R-600a Tables</h3>
<table>
  <thead>
    <tr><th>Quantity</th><th>Value</th><th>Meaning</th></tr>
  </thead>
  <tbody>
    <tr><td>P<sub>low</sub> @ −26°C</td><td><b>0.559 bar</b></td><td>Evaporator saturation pressure (State 1)</td></tr>
    <tr><td>h₁ @ −26°C sat vapor</td><td><b>519.67 kJ/kg</b></td><td>Compressor inlet enthalpy (State 1)</td></tr>
    <tr><td>s₁ @ −26°C sat vapor</td><td><b>2.3057 kJ/(kg·K)</b></td><td>Compressor inlet entropy (State 1)</td></tr>
    <tr><td>h₃ @ 45°C sat liquid</td><td><b>309.07 kJ/kg</b></td><td>Condenser outlet enthalpy (clean case)</td></tr>
    <tr><td>h₃ @ 50°C sat liquid</td><td><b>322.16 kJ/kg</b></td><td>Condenser outlet enthalpy (baseline)</td></tr>
    <tr><td>h₃ @ 55°C sat liquid</td><td><b>335.25 kJ/kg</b></td><td>Condenser outlet enthalpy (restricted case)</td></tr>
  </tbody>
</table>

<h3>Component Energy Relations</h3>
<div class="eqblock">
  <div class="eqline">(5) Compressor: Ẇ<sub>in</sub> ≈ ṁ (h₂ − h₁)</div>
  <div class="eqline">(6) Condenser: Q̇<sub>H</sub> ≈ ṁ (h₂ − h₃)</div>
  <div class="eqline">(7) Throttle: h₄ ≈ h₃ (isenthalpic throttling)</div>
  <div class="eqline">(8) Evaporator: Q̇<sub>L</sub> ≈ ṁ (h₁ − h₄)</div>
</div>

<hr class="pdf-hr"/>

<h2>6. Step-by-Step Cycle Results (All Numbers)</h2>
<p>
Compressor modeling uses an ideal-gas approximation for vapor compression with constant c<sub>p</sub> and k and an isentropic efficiency η<sub>is</sub> = 0.70.
For each condenser temperature case, I compute pressure ratio, isentropic outlet temperature, compressor specific work, refrigerating effect, COP, and then use the measured annual energy to estimate average Q̇<sub>L</sub> and mass flow rate.
</p>

<h3>CASE 1: Clean / Better Airflow (T<sub>c</sub> = 45°C)</h3>

<div class="eqblock">
  <div class="eqline"><b>Step 1:</b> State 1 at T<sub>e</sub> = −26°C (247.15 K): P₁ = 0.559 bar, h₁ = 519.67 kJ/kg, s₁ = 2.3057 kJ/(kg·K)</div>
  <div class="eqline"><b>Step 1:</b> State 3 at T<sub>c</sub> = 45°C (318.15 K): P₃ = 6.044 bar, h₃ = 309.07 kJ/kg</div>
  <div class="eqline"><b>Step 2:</b> r<sub>p</sub> = 6.044/0.559 = 10.81</div>
  <div class="eqline"><b>Step 3:</b> T₂s = 247.15 × (10.81)<sup>0.09502</sup> = 309.32 K</div>
  <div class="eqline"><b>Step 4:</b> Δh<sub>is</sub> = 1.692(309.32 − 247.15) = 105.15 kJ/kg</div>
  <div class="eqline"><b>Step 5:</b> w<sub>in</sub> = 105.15/0.70 = 150.21 kJ/kg; h₂ = 519.67 + 150.21 = 669.88 kJ/kg</div>
  <div class="eqline"><b>Step 6:</b> h₄ = h₃ = 309.07 kJ/kg</div>
  <div class="eqline"><b>Step 7:</b> q<sub>L</sub> = 519.67 − 309.07 = 210.60 kJ/kg</div>
  <div class="eqline"><b>Step 8:</b> COP<sub>R</sub> = 210.60/150.21 = 1.40</div>
  <div class="eqline"><b>Key results used in summary:</b> Q̇<sub>L</sub> = 130.7 W, Q̇<sub>H</sub> = 223.9 W, ṁ = 0.620 g/s, Ṡ<sub>gen</sub> = 0.2365 W/K</div>
</div>

<h3>CASE 2: Baseline Tight Cabinetry (T<sub>c</sub> = 50°C)</h3>

<div class="eqblock">
  <div class="eqline"><b>Step 2:</b> r<sub>p</sub> = 6.887/0.559 = 12.32</div>
  <div class="eqline"><b>Step 3:</b> (k−1)/k = 0.09502; T₂s = 247.15 × (12.32)<sup>0.09502</sup> = 313.76 K</div>
  <div class="eqline"><b>Step 4:</b> Δh<sub>is</sub> = 1.692(313.76 − 247.15) = 112.70 kJ/kg</div>
  <div class="eqline"><b>Step 5:</b> w<sub>in</sub> = 112.70/0.70 = 161.00 kJ/kg; h₂ = 519.67 + 161.00 = 680.67 kJ/kg</div>
  <div class="eqline"><b>Step 6:</b> h₄ = h₃ = 322.16 kJ/kg</div>
  <div class="eqline"><b>Step 7:</b> q<sub>L</sub> = 519.67 − 322.16 = 197.51 kJ/kg</div>
  <div class="eqline"><b>Step 8:</b> COP<sub>R</sub> = 197.51/161.00 = 1.227 ≈ 1.23</div>
  <div class="eqline"><b>Step 9:</b> Ẇ = 817,000 Wh / 8766 hr = 93.19 W</div>
  <div class="eqline"><b>Step 10:</b> Q̇<sub>L</sub> = 1.227 × 93.19 = 114.37 W</div>
  <div class="eqline"><b>Step 11:</b> ṁ = 114.37 / 197,510 = 0.000579 kg/s = 0.579 g/s</div>
  <div class="eqline"><b>Step 12:</b> Q̇<sub>H</sub> = 114.37 + 93.19 = 207.56 W ≈ 207.6 W</div>
  <div class="eqline"><b>Step 13:</b> Ṡ<sub>gen</sub> = 207.56/299.26 − 114.37/255.37 = 0.2460 W/K ≥ 0 ✓</div>
  <div class="eqline"><b>Step 14:</b> COP<sub>Carnot</sub> = 255.37/(299.26−255.37) = 5.82; η<sub>II</sub> = 1.227/5.82 = 0.211 = 21.1%</div>
</div>

<h3>CASE 3: Restricted Airflow (T<sub>c</sub> = 55°C)</h3>

<div class="eqblock">
  <div class="eqline"><b>Step 2:</b> r<sub>p</sub> = 7.730/0.559 = 13.83</div>
  <div class="eqline"><b>Step 3:</b> T₂s = 247.15 × (13.83)<sup>0.09502</sup> = 317.24 K</div>
  <div class="eqline"><b>Step 4–5:</b> Δh<sub>is</sub> = 118.56; w<sub>in</sub> = 169.37 kJ/kg</div>
  <div class="eqline"><b>Step 6–8:</b> h₄ = 335.25; q<sub>L</sub> = 184.42 kJ/kg; COP = 1.09</div>
  <div class="eqline"><b>Same power (93.2 W):</b> Q̇<sub>L</sub> = 101.5 W; ṁ = 0.550 g/s; Q̇<sub>H</sub> = 194.7 W</div>
  <div class="eqline"><b>Entropy:</b> Ṡ<sub>gen</sub> = 194.7/299.26 − 101.5/255.37 = 0.2532 W/K ≥ 0 ✓</div>
</div>

<h3>Summary Table of All Results</h3>
<table>
  <thead>
    <tr>
      <th>Case</th>
      <th>T<sub>c</sub> (°C)</th>
      <th>P<sub>high</sub> (bar)</th>
      <th>P ratio</th>
      <th>w<sub>in</sub> (kJ/kg)</th>
      <th>q<sub>L</sub> (kJ/kg)</th>
      <th>COP<sub>R</sub></th>
      <th>Q̇<sub>L</sub> (W)</th>
      <th>Q̇<sub>H</sub> (W)</th>
      <th>ṁ (g/s)</th>
      <th>Ṡ<sub>gen</sub> (W/K)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Clean / better airflow</td>
      <td>45</td><td>6.044</td><td>10.81</td><td>150.21</td><td>210.60</td><td>1.40</td><td>130.7</td><td>223.9</td><td>0.620</td><td>0.2365</td>
    </tr>
    <tr>
      <td>Baseline (tight cabinetry)</td>
      <td>50</td><td>6.887</td><td>12.32</td><td>161.00</td><td>197.51</td><td>1.23</td><td>114.4</td><td>207.6</td><td>0.579</td><td>0.2460</td>
    </tr>
    <tr>
      <td>Restricted airflow (dust/blocked)</td>
      <td>55</td><td>7.730</td><td>13.83</td><td>169.37</td><td>184.42</td><td>1.09</td><td>101.5</td><td>194.7</td><td>0.550</td><td>0.2532</td>
    </tr>
  </tbody>
</table>

<hr class="pdf-hr"/>

<h2>7. Design/Operating Change Analysis: Condenser Heat Rejection in Tight Cabinetry</h2>
<p>
Because the unit is built into tight cabinetry, the condenser may run hotter due to reduced airflow. This increases condenser saturation pressure, increases compressor pressure ratio, increases compressor specific work w<sub>in</sub>, and reduces COP. 
</p>

<h3>Annual energy impact estimate (keeping the same cooling load)</h3>
<table>
  <thead>
    <tr>
      <th>Scenario</th>
      <th>Assumed condenser condition</th>
      <th>COP<sub>R</sub></th>
      <th>Avg Ẇ needed for same Q̇<sub>L</sub> (W)</th>
      <th>Annual energy (kWh/yr)</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Cleaner / better airflow</td><td>T<sub>c</sub> ≈ 45°C</td><td>1.39</td><td>82.4</td><td>722</td></tr>
    <tr><td>Baseline (your installation)</td><td>T<sub>c</sub> ≈ 50°C</td><td>1.23</td><td>93.3</td><td>817</td></tr>
    <tr><td>Restricted airflow</td><td>T<sub>c</sub> ≈ 55°C</td><td>1.09</td><td>105.1</td><td>920</td></tr>
  </tbody>
</table>

<p class="caption">
Interpretation: moving from a “cleaner/better airflow” condenser condition (45°C) to a “restricted airflow” condition (55°C) can increase annual energy from about 722 to 920 kWh/yr for the same average cooling requirement. This follows from Ẇ<sub>in</sub> = Q̇<sub>L</sub>/COP<sub>R</sub>.
</p>

<hr class="pdf-hr"/>

<h2>8. Extra: Heat Leak Model (UA) and Ambient Temperature Sensitivity</h2>
<p>
To connect the cycle results to a building-physics style model, I estimate an equivalent overall heat leak coefficient UA by putting all heat gains (through insulation, gasket leakage, door openings, internal lights/fans, and warm food loads) into a one linear relation:
</p>
<div class="eqblock">
  <div class="eqline">Q̇<sub>L</sub> ≈ UA · (T<sub>ambient</sub> − T<sub>cold,eq</sub>)</div>
</div>

<h3>Detailed UA Calculation</h3>
<div class="eqblock">
  <div class="eqline">T<sub>ambient</sub> = 79°F = 26.11°C = 299.26 K</div>
  <div class="eqline">T<sub>freezer</sub> = 0°F = −17.78°C = 255.37 K</div>
  <div class="eqline">ΔT = 299.26 − 255.37 = 43.89 K</div>
  <div class="eqline">UA = Q̇<sub>L</sub>/ΔT = 114.4 W / 43.89 K = 2.606 W/K ≈ 2.61 W/K</div>
</div>

<h3>Ambient Temperature Sensitivity (70°F vs 79°F)</h3>
<div class="eqblock">
  <div class="eqline"><b>At 70°F (294.26 K):</b> ΔT = 38.89 K → Q̇<sub>L</sub> ≈ 2.61×38.89 = 101.5 W</div>
  <div class="eqline">COP<sub>Carnot,70F</sub> = 6.57; COP<sub>actual,70F</sub> ≈ 1.39 → Ẇ ≈ 73.0 W → Annual ≈ 640 kWh/yr</div>
  <div class="eqline"><b>At 79°F (299.26 K):</b> Annual ≈ 817 kWh/yr</div>
</div>

<hr class="pdf-hr"/>

<hr class="pdf-hr"/>

<h2>10. Conclusion</h2>
<p>
  This project demonstrates how vapor-compression refrigeration theory can be applied to a real household appliance using a combination of thermodynamic cycle modeling, manufacturer data, and measured energy consumption. By modeling the Sub-Zero CL4850SID/S refrigerator as a steady-state control volume system and using R-600a refrigerant properties, the analysis connects abstract concepts such as the First and Second Laws, compressor work, and coefficient of performance (COP) to an appliance used daily.

  The results show that real-world performance is strongly influenced by operating conditions and installation constraints, particularly ambient temperature and condenser airflow. While ideal cycle assumptions provide useful insight, incorporating measured annual energy use and realistic boundary conditions yields a more accurate picture of actual system behavior. Overall, this analysis illustrates how thermodynamics serves as a practical engineering tool for evaluating energy efficiency, design tradeoffs, and everyday system performance.
</p>

<h2>11. Sources</h2>
<ul>
  <li>
    <strong>Sub-Zero (CL4850SID/S):</strong>
    Official product page and trade/spec resources (specifications, capacity, electrical supply, annual energy).
  </li>

  <li>
    <strong>Sub-Zero Classic Series Use & Care Guide:</strong>
    Recommended temperature setpoints (38°F refrigerator, 0°F freezer).
  </li>

  <li>
    <strong>EnergyGuide (CL4850SID/S family):</strong>
    Annual energy use value (817 kWh/yr).
  </li>

  <li>
    <strong>ENERGY STAR listing (CL4850S/S family):</strong>
    Efficiency and refrigerant context (used for low-GWP discussion).
  </li>

  <li>
    <strong>R-600a properties:</strong>
    Saturation tables and property datasheets (e.g., <em>c<sub>p</sub></em>, <em>k</em>) for cycle calculations.
  </li>
</ul>