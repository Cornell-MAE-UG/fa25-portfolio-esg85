---
layout: project
title: Statics Case Study – Nutcracker Force & Usability Analysis
description: Free body diagram analysis, torque balance, and actuator sizing for a nutcracker mechanism
technologies: [Statics, Free Body Diagrams, Torque Analysis]
image: /assets/images/diagram-2020.png
math: true
---
<div class="toc-box">
  <h2>Table of Contents</h2>
  <ul>
    <li><a href="#question-1">Question 1: Overall Nutcracker Design</a></li>
    <li><a href="#question-2">Question 2: Flexible Nutcracker Handle Beam Design</a></li>
  </ul>
</div>

## Problem Statement

**Given:**  
Design a nutcracker with specified geometry and applied forces.

**Find:**  
1. Whether the nutcracker is usable by a human  
2. Required handle force  
3. Required actuator stroke (if motorized)

**Plan:**  
- Draw Free Body Diagram (FBD)  
- Assume reasonable dimensions  
- Apply static equilibrium (∑M = 0, ∑F = 0)  
- Evaluate human usability  
- Calculate actuator stroke requirement  

---

## Free Body Diagram
<img src="{{ '/assets/images/diagram-2020.png' | relative_url }}"
           class="img-fluid">
<!-- ![Nutcracker Sketch 1]({{ "/assets/images/diagram-2020.png" }}) -->

The nutcracker consists of two symmetric handles connected by a pivot.

Assumptions:
- Required crushing force at nut: ~3600 N  
- Distance from pivot to handle end: L  
- Distance from pivot to nut contact: d  
- Applied handle force: F_H  

---

## Static Equilibrium Analysis

Taking moments about the pivot:

$$
\sum M_{pivot} = 0
$$

$$
F_H L = F_N d
$$

From design assumptions:

- Required nut force:  

$$
F_N = 3600 \, N
$$

- Applied handle force:  

$$
F_H = 600 \, N
$$

Solving:

$$
600L = 3600d
$$

$$
L = 6d
$$

### Interpretation

The handle must be **6× longer** than the distance to the nut contact point to generate sufficient crushing force.

This creates a large mechanical advantage requirement.

---

## Usability Evaluation

600 N ≈ 135 lbf

This is **very high for sustained human grip force**.

Conclusion:

- The design is not ergonomically practical.
- A longer handle improves leverage.
- Mechanical or motorized assistance is recommended.

---

## Actuator Design Consideration

<img src="{{ '/assets/images/workthrough-2020.jpg' | relative_url }}"
           class="img-fluid">
<!-- ![Nutcracker Sketch 2]({{ /assets/images/workthrough-2020.png" }}) -->

If using a linear actuator:

Required crushing force:

$$
F_N \approx 3600 \, N
$$

Handle force equivalent:

$$
F_H \approx 600 \, N
$$

Compression requirement at nut:

$$
\Delta x_{nut} \approx 0.25 \text{ in}
$$

Since:

$$
L = 6d
$$

Stroke requirement scales proportionally:

$$
Stroke \approx 0.25 \times 6 = 1.5 \text{ in}
$$

### Recommended Specification

- Force rating ≥ 150 lbf (≈ 600 N)  
- Stroke length ≈ 2 inches  
- Linear actuator configuration  

## Final Design Recommendation

Based on analysis, the current manual configuration is not ergonomically feasible.

Recommended improvements:
- Increase handle length to increase mechanical advantage
- Add compound linkage
- Implement geared mechanism
- Use linear actuator for assisted operation

This project reinforced how static equilibrium analysis directly informs product usability and human-centered design.

<hr class="pdf-hr"/>

<style>
.toc-box{
  background: #f1f5f9;
  border: 1.5px solid #cbd5e1;
  border-left: 6px solid #2563eb;
  padding: 16px 20px;
  border-radius: 12px;
  margin: 18px 0 24px;
}

.toc-box h2{
  border-bottom: none !important;
  margin-top: 0 !important;
  padding-bottom: 0 !important;
  font-size: 22px;
  color: #0b2a4a;
}

.toc-box ul{
  margin: 8px 0 0 20px;
}

.toc-box a{
  color: #1d4ed8;
  font-weight: 700;
  text-decoration: none;
}

.toc-box a:hover{
  text-decoration: underline;
}
</style>


<style>
.beam-box{
  background: #eef6ff;
  border: 1.5px solid #bfdbfe;
  border-left: 6px solid #3b82f6;
  padding: 14px 18px;
  border-radius: 12px;
  margin: 14px 0;
  overflow-x: auto;
}

.beam-result{
  background: #ecfdf5;
  border: 1.5px solid #a7f3d0;
  border-left: 6px solid #10b981;
  padding: 14px 18px;
  border-radius: 12px;
  margin: 16px 0;
}

.beam-warning{
  background: #fff7ed;
  border: 1.5px solid #fed7aa;
  border-left: 6px solid #f97316;
  padding: 14px 18px;
  border-radius: 12px;
  margin: 16px 0;
}

.beam-eq{
  margin: 6px 0;
  font-family: Georgia, "Times New Roman", serif;
  font-size: 18px;
}

.beam-svg{
  width: 100%;
  max-width: 1000px;
  height: auto;
}

.beam-figure{
  background: white;
  border: 1.5px solid #cbd5e1;
  border-radius: 14px;
  padding: 18px;
  margin: 18px 0;
  text-align: center;
}

.beam-caption{
  font-size: 15px;
  color:#475569;
  margin-top: 10px;
}
</style>

<h2>12. Additional Beam Analysis: Flexible Nutcracker Handles</h2>

<p>
In the original design, the nutcracker handles were assumed to be rigid. For this additional analysis, I updated the model by treating each handle as an elastic beam. This means the handle can bend under the combined transverse loading from the actuator and from the nut.
</p>

<p>
The goal of this section is to find the location of maximum elastic deflection and select a mass-efficient beam design that keeps the vertical deflection below <b>2% of the handle length</b>.
</p>

<table>
  <thead>
    <tr>
      <th>Variable</th>
      <th>Value</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>L</td>
      <td><b>0.1524 m</b></td>
      <td>Total handle length</td>
    </tr>
    <tr>
      <td>a</td>
      <td><b>0.0254 m</b></td>
      <td>Distance from fixed end to nut force</td>
    </tr>
    <tr>
      <td>F<sub>A</sub></td>
      <td><b>600 N</b></td>
      <td>Transverse actuator force</td>
    </tr>
    <tr>
      <td>F<sub>N</sub></td>
      <td><b>3600 N</b></td>
      <td>Transverse nut reaction force</td>
    </tr>
    <tr>
      <td>δ<sub>allow</sub></td>
      <td><b>0.02L = 0.003048 m = 3.05 mm</b></td>
      <td>Maximum allowed elastic deflection</td>
    </tr>
  </tbody>
</table>

<h3>12.1 Assumptions</h3>

<ul>
  <li>The handle is modeled as a <b>cantilever beam</b> fixed at the pivot end.</li>
  <li>Only transverse force components are considered.</li>
  <li>The actuator force acts at the free end of the handle.</li>
  <li>The nut force acts at distance <b>a</b> from the fixed end.</li>
  <li>The material behaves linearly elastically.</li>
  <li>Euler-Bernoulli beam theory and superposition are used.</li>
  <li>The beam has constant bending stiffness <b>EI</b>.</li>
</ul>

<div class="beam-warning">
  <b>Sign convention:</b> The actuator force and nut reaction force are treated as acting in opposite transverse directions, so their deflection effects subtract from each other.
</div>

<h3>12.2 Deflection Equations</h3>

<p>
Using beam deflection superposition, the total deflection is written in two regions because the nut force is applied at an intermediate point along the handle.
</p>

<p><b>For 0 ≤ x ≤ a:</b></p>

<div class="beam-box">
  <div class="beam-eq">
    y(x) = 1/(6EI) [ F<sub>A</sub>x²(3L − x) − F<sub>N</sub>x²(3a − x) ]
  </div>
</div>

<p><b>For a ≤ x ≤ L:</b></p>

<div class="beam-box">
  <div class="beam-eq">
    y(x) = 1/(6EI) [ F<sub>A</sub>x²(3L − x) − F<sub>N</sub>a²(3x − a) ]
  </div>
</div>

<p>
Since the deflection increases toward the free end for this loading case, the maximum vertical elastic deflection occurs at:
</p>

<div class="beam-result">
  <b>Maximum deflection location:</b> x = L = 0.1524 m, at the actuator end of the handle.
</div>

<h3>12.3 Maximum Deflection Requirement</h3>

<p>
At the free end, x = L, the maximum deflection is:
</p>

<div class="beam-box">
  <div class="beam-eq">
    δ<sub>max</sub> = F<sub>A</sub>L³/(3EI) − F<sub>N</sub>a²(3L − a)/(6EI)
  </div>
</div>

<p>
Substituting the values:
</p>

<div class="beam-box">
  <div class="beam-eq">
    δ<sub>max</sub> = [600(0.1524)³/3 − 3600(0.0254)²(3(0.1524) − 0.0254)/6] / EI
  </div>
  <div class="beam-eq">
    δ<sub>max</sub> = 0.5408 / EI
  </div>
</div>

<p>
The allowable deflection is:
</p>

<div class="beam-box">
  <div class="beam-eq">
    δ<sub>allow</sub> = 0.02L = 0.02(0.1524) = 0.003048 m
  </div>
</div>

<p>
Therefore, the required bending stiffness is:
</p>

<div class="beam-box">
  <div class="beam-eq">
    0.5408 / EI ≤ 0.003048
  </div>
  <div class="beam-eq">
    EI ≥ 177.4 N·m²
  </div>
</div>

<div class="beam-result">
  <b>Required bending stiffness:</b> EI ≥ 177.4 N·m².
</div>

<h3>12.4 Beam Design Selection</h3>

<p>
To make the handle mass-efficient, I chose a hollow rectangular beam. This shape is efficient in bending because it places material far from the neutral axis while removing material near the center, where it contributes less to bending stiffness.
</p>

<table>
  <thead>
    <tr>
      <th>Design Choice</th>
      <th>Selected Value</th>
      <th>Reason</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Material</td>
      <td><b>Carbon fiber reinforced polymer</b></td>
      <td>High stiffness-to-weight ratio</td>
    </tr>
    <tr>
      <td>Young's modulus</td>
      <td><b>E ≈ 135 GPa</b></td>
      <td>Provides high elastic stiffness</td>
    </tr>
    <tr>
      <td>Cross-section</td>
      <td><b>Hollow rectangular tube</b></td>
      <td>Mass-efficient bending shape</td>
    </tr>
    <tr>
      <td>Outer height</td>
      <td><b>20 mm</b></td>
      <td>Large bending depth increases I</td>
    </tr>
    <tr>
      <td>Outer width</td>
      <td><b>10 mm</b></td>
      <td>Compact handle width</td>
    </tr>
    <tr>
      <td>Wall thickness</td>
      <td><b>0.5 mm</b></td>
      <td>Reduces mass while maintaining stiffness</td>
    </tr>
  </tbody>
</table>

<h3>12.5 Second Moment of Area</h3>

<p>
For a hollow rectangular cross-section:
</p>

<div class="beam-box">
  <div class="beam-eq">
    I = [bh³ − (b − 2t)(h − 2t)³] / 12
  </div>
</div>

<p>
Using b = 10 mm, h = 20 mm, and t = 0.5 mm:
</p>

<div class="beam-box">
  <div class="beam-eq">
    I = [10(20)³ − 9(19)³] / 12
  </div>
  <div class="beam-eq">
    I = 1522 mm⁴ = 1.522 × 10⁻⁹ m⁴
  </div>
</div>

<p>
Then:
</p>

<div class="beam-box">
  <div class="beam-eq">
    EI = (135 × 10⁹)(1.522 × 10⁻⁹)
  </div>
  <div class="beam-eq">
    EI = 205.5 N·m²
  </div>
</div>

<div class="beam-result">
  <b>Stiffness check:</b> 205.5 N·m² &gt; 177.4 N·m², so the design satisfies the stiffness requirement.
</div>

<h3>12.6 Final Deflection Check</h3>

<div class="beam-box">
  <div class="beam-eq">
    δ<sub>max</sub> = 0.5408 / 205.5
  </div>
  <div class="beam-eq">
    δ<sub>max</sub> = 0.00263 m = 2.63 mm
  </div>
</div>

<div class="beam-result">
  <b>Final result:</b> δ<sub>max</sub> = 2.63 mm &lt; 3.05 mm, so the vertical elastic deflection is below 2% of the handle length.
</div>

<h3>12.7 Final Design Drawing</h3>
<div class="beam-figure">
<img src="{{ '/assets/images/new_nutcracker.jpg' | relative_url }}"
           class="img-fluid">
  <defs>
    <marker id="beamArrow" markerWidth="10" markerHeight="10" refX="5" refY="5" orient="auto-start-reverse">
      <path d="M 0 0 L 10 5 L 0 10 z" fill="#0f172a"/>
    </marker>

    <linearGradient id="beamHandleGrad" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="#334155"/>
      <stop offset="50%" stop-color="#64748b"/>
      <stop offset="100%" stop-color="#1e293b"/>
    </linearGradient>
  </defs>

  <text x="500" y="38" text-anchor="middle" font-size="28" font-weight="700" fill="#0b2a4a">
    Flexible Nutcracker Handle Beam Design
  </text>

  <circle cx="170" cy="260" r="46" fill="#cbd5e1" stroke="#0f172a" stroke-width="4"/>
  <circle cx="170" cy="260" r="18" fill="#f8fafc" stroke="#0f172a" stroke-width="3"/>
  <text x="170" y="335" text-anchor="middle" font-size="18" fill="#334155">Fixed pivot</text>

  <path d="M 205 235 C 365 200, 600 200, 860 225 C 890 230, 890 270, 860 275 C 600 300, 365 300, 205 285 Z"
        fill="url(#beamHandleGrad)" stroke="#0f172a" stroke-width="4"/>

  <ellipse cx="300" cy="260" rx="70" ry="38" fill="#facc15" stroke="#92400e" stroke-width="4"/>
  <path d="M250 260 L275 235 L325 235 L350 260 L325 285 L275 285 Z"
        fill="#fff7ed" stroke="#92400e" stroke-width="3"/>
  <text x="300" y="335" text-anchor="middle" font-size="18" fill="#334155">Nut contact</text>

  <line x1="300" y1="155" x2="300" y2="220" stroke="#0f172a" stroke-width="4" marker-end="url(#beamArrow)"/>
  <text x="320" y="150" font-size="20" font-weight="700" fill="#0f172a">
    F<tspan baseline-shift="sub" font-size="14">N</tspan> = 3600 N
  </text>

  <line x1="835" y1="330" x2="835" y2="275" stroke="#0f172a" stroke-width="4" marker-end="url(#beamArrow)"/>
  <text x="855" y="340" font-size="20" font-weight="700" fill="#0f172a">
    F<tspan baseline-shift="sub" font-size="14">A</tspan> = 600 N
  </text>

  <line x1="170" y1="420" x2="835" y2="420" stroke="#334155" stroke-width="3" marker-start="url(#beamArrow)" marker-end="url(#beamArrow)"/>
  <text x="502" y="455" text-anchor="middle" font-size="20" font-weight="700" fill="#334155">
    L = 0.1524 m
  </text>

  <line x1="170" y1="385" x2="300" y2="385" stroke="#334155" stroke-width="3" marker-start="url(#beamArrow)" marker-end="url(#beamArrow)"/>
  <text x="235" y="375" text-anchor="middle" font-size="18" fill="#334155">
    a = 0.0254 m
  </text>

  <rect x="680" y="195" width="150" height="70" rx="12" fill="#f8fafc" stroke="#0f172a" stroke-width="3"/>
  <rect x="698" y="211" width="114" height="38" rx="6" fill="#cbd5e1" stroke="#0f172a" stroke-width="2"/>
  <text x="755" y="182" text-anchor="middle" font-size="18" font-weight="700" fill="#0b2a4a">
    Cross-section
  </text>
  <text x="755" y="292" text-anchor="middle" font-size="16" fill="#334155">
    20 mm × 10 mm × 0.5 mm wall
  </text>

  <rect x="410" y="90" width="360" height="64" rx="12" fill="#ecfdf5" stroke="#10b981" stroke-width="3"/>
  <text x="590" y="118" text-anchor="middle" font-size="18" font-weight="700" fill="#065f46">
    Carbon Fiber Reinforced Polymer
  </text>
  <text x="590" y="143" text-anchor="middle" font-size="16" fill="#065f46">
    E ≈ 135 GPa, EI = 205.5 N·m²
  </text>
</svg>

<div class="beam-caption">
Final design: carbon fiber reinforced polymer hollow rectangular handle, 20 mm tall × 10 mm wide × 0.5 mm wall thickness.
</div>
</div>

<p>
Overall, this additional analysis shows that the flexible handle design satisfies the deflection requirement. The selected hollow carbon fiber handle is mass-efficient because it provides enough bending stiffness while removing unnecessary material near the neutral axis.
</p>