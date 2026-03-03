---
layout: project
title: Statics Case Study – Nutcracker Force & Usability Analysis
description: Free body diagram analysis, torque balance, and actuator sizing for a nutcracker mechanism
technologies: [Statics, Free Body Diagrams, Torque Analysis]
image: /assets/images/nutcracker-sketch.png
---

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

![Nutcracker Sketch 1](/assets/images/diagram-2020.png)

The nutcracker consists of two symmetric handles connected by a pivot.

Assumptions:
- Required crushing force at nut: ~3600 N  
- Distance from pivot to handle end: L  
- Distance from pivot to nut contact: d  
- Applied handle force: F_H  

---

## Static Equilibrium Analysis

Taking moments about the pivot:

\[
\sum M_{pivot} = 0
\]

\[
F_H L = F_N d
\]

From design assumptions:

- Required nut force:  
  \[
  F_N = 3600 \, N
  \]

- Applied handle force:  
  \[
  F_H = 600 \, N
  \]

Solving:

\[
600L = 3600d
\]

\[
L = 6d
\]

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

![Nutcracker Sketch 2](/assets/images/workthrough-2020.png)

If using a linear actuator:

Required crushing force:
\[
F_N ≈ 3600 N
\]

Handle force equivalent:
\[
F_H ≈ 600 N
\]

Compression requirement at nut:
\[
\Delta x_{nut} ≈ 0.25 \text{ in}
\]

Since:

\[
L = 6d
\]

Stroke requirement scales proportionally:

\[
Stroke ≈ 0.25 \times 6 = 1.5 \text{ in}
\]

### Recommended Specification

- Force rating ≥ 150 lbf (≈ 600 N)  
- Stroke length ≈ 2 inches  
- Linear actuator configuration  

---

## Engineering Takeaways

- Mechanical advantage trades distance for force.
- Human-centered design must consider ergonomic force limits.
- Even simple consumer tools require equilibrium analysis.
- Design improvements include:
  - Increasing handle length
  - Adding gearing
  - Adding motorized actuation

---

## Reflection

This project demonstrates:

- Free body diagram modeling
- Moment balance
- Mechanical advantage analysis
- Translating theory into real-world usability
- Preliminary actuator sizing

This is a practical application of static equilibrium principles to consumer product design.