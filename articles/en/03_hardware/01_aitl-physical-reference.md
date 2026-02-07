---
layout: default
title: aitl-physical-reference Fix the Physics Before Control
---

# [Hardware] 🧱 01. aitl-physical-reference  
### — Fixing Physics Before Control

---

## 📌 Introduction

**aitl-physical-reference** is a  
**minimal physical reference PCB** designed to anchor abstract control logic  
to **real voltage, real current, and real copper traces**.

This is not a “control board.”  
It is a **reference point that defines how physics exists before control begins**.

---

## 🎯 Why This Exists

Control theory, AI, FSMs, and PID controllers often assume the following—implicitly:

- Voltage is ideally generated  
- Current flows as required  
- Outputs can be treated as logical values  

In reality:

- Voltage is **unknown unless measured**  
- Current is **constrained by resistance**  
- Boundaries are defined by **copper traces and PCB outlines**

This board exists to **fix that overlooked but fundamental layer**  
in the smallest possible form.

---

## 🧩 Components (Intentionally Minimal)

This board contains only the following elements:

- **LED**: Visualization of output state  
- **Resistor**: Physical constraint on current  
- **Switch**: Discrete physical event input  
- **Test Points**: Locations to measure voltage and current  
- **PCB Outline (Edge.Cuts)**: The physical boundary  

There is no “function.”  
There is only **meaning**.

---

## 🔁 Logic → Physics → Copper

### 1️⃣ Schematic (Logic → Physics)

![Schematic](https://samizo-aitl.github.io/aitl-physical-reference/docs/img/01_apr_sch_v0.png)

*A minimal schematic that anchors abstract logic to measurable voltage and current.*

---

### 2️⃣ PCB Layout (Explicit Physical Constraints)

![PCB Layout](https://samizo-aitl.github.io/aitl-physical-reference/docs/img/02_apr_pcb_v0.png)

*The “physical truth” defined by copper traces, component placement, and board outline.*

---

### 3️⃣ 3D View (Existence as an Object)

![3D View](https://samizo-aitl.github.io/aitl-physical-reference/docs/img/03_apr_3d_v0.png)

*An object with height you can touch, connectors you can plug in, and points you can probe.*

---

## 🚫 What This Is Not

To avoid misunderstanding, this must be stated clearly.

- Not an MCU evaluation board  
- Not a feature-rich demo board  
- Not a performance-optimized design  
- Not tied to a specific control architecture  

This is a **reference**.  
Nothing more. Nothing less.

---

## 🛠️ How to Use It

This board can be used in the following contexts:

- As a **physical starting point** for control education  
- To verify assumptions before FSM / PID / AI control  
- To share physical intuition with logic-focused designers  
- As the **baseline physical layer** of AITL  
  (Architecture for Integrated Technology Logic)

It is the board you start with when you say:

> “Let’s begin from reality.”

---

## 🧾 Summary

Control can only stand on top of physics.

**aitl-physical-reference** fixes that **lowest layer**  
as a schematic, as copper, and as a physical object.

> Before control, there must be physics.

This board exists to make that fact unavoidable—  
a **minimal, uncompromising reference**.

---

## 🔗 Links

- GitHub Pages  
  [https://samizo-aitl.github.io/aitl-physical-reference/](https://samizo-aitl.github.io/aitl-physical-reference/)

- GitHub Repository  
  [https://github.com/Samizo-AITL/aitl-physical-reference](https://github.com/Samizo-AITL/aitl-physical-reference)

---
