---
layout: default
title: zenn-articles
---

# 【MEMS】🧠 02. Visualizing Piezoelectric Hysteresis and Butterfly Displacement with *mems-ana*
topics: ["MEMS", "piezoelectric", "visualization", "Python", "simulation"]

---

## 📌 Introduction

In piezoelectric MEMS devices,  
it is critically important to develop an **intuitive understanding of  
“what actually moves when a voltage is applied.”**

Even when tracking equations and coefficients (such as $d_{33}$),  
it is common to lose a clear mental picture of the resulting behavior.

In this article, we use the lightweight analysis tool **mems-ana** to:

- Apply piezoelectric hysteresis inputs  
- Observe butterfly-type displacement–voltage (V–u) characteristics  
- Visualize the time evolution of spatial displacement distributions  

The goal is not numerical accuracy, but **to visually observe and internalize the behavior**.

> This article is the second installment in the *mems-ana* series.

---

## 🧪 Demo Overview

In this demonstration, we perform the following:

- **Input**  
  - A **P–$E_z$ hysteresis loop** driven by applied voltage $V$
- **Model**  
  - A $d_{33}$-dominant piezoelectric actuation model  
  - Thin-film rectangular diaphragm represented by a ROM
- **Output**  
  - Central displacement $u_z$  
  - Spatial displacement distribution $u_z(x,y)$  
  - Time evolution along the voltage cycle

The emphasis is on **behavioral understanding**, not precision fitting.

---

## 🎞 Demo Animation (Spatial Displacement)

At the link below, the spatial displacement  
$u_z(x,y)$ is displayed as a **real-time animation** along the voltage cycle.

**Interactive Demo (GitHub Pages)**  
[https://samizo-aitl.github.io/mems-ana/mems-ana_demo/](https://samizo-aitl.github.io/mems-ana/mems-ana_demo/)

- Displayed quantity: signed displacement distribution $u_z(x,y)$  
- Color scale: fixed across all frames  
- Voltage sweep: follows the hysteresis input

Because Zenn only supports static images,  
**please refer to the link above for the actual dynamic behavior**.

---

## 🔁 P–$E_z$ Hysteresis Input

In piezoelectric materials, polarization $P$ exhibits hysteresis  
with respect to the electric field $E_z$.

In this demo, we use:

- A hysteresis loop modeled after measured behavior  
- A $P(E_z)$ input converted from voltage drive  

The key points are:

- The input is explicitly nonlinear  
- The ROM-based structural model still responds smoothly  

This separation of **nonlinear input** and **interpretable structural response** is intentional.

---

## 🦋 Butterfly-Type Displacement–Voltage Characteristics

When a hysteresis input is applied,  
the central displacement $u_z$ exhibits a characteristic  
**butterfly-shaped curve**.

- Asymmetry between positive and negative voltage regions  
- History-dependent displacement response  

This behavior is **extremely common** in:

- Piezoelectric devices  
- MEMS actuators  

Before understanding it mathematically,  
it is valuable to **recognize the shape visually**.

---

## 🗺 Why Spatial Distributions Matter

By looking not only at scalar quantities (such as center displacement)  
but also at the **spatial distribution $u_z(x,y)$**, one can immediately see:

- Where deformation is concentrated  
- How mode shapes invert or evolve  
- Whether symmetry is preserved  

This is also excellent training for **interpreting FEM results** later.

---

## ⚙️ How to Run the Demo (Brief)

The demo can be executed using the code published in the following repository:

[https://github.com/Samizo-AITL/mems-ana](https://github.com/Samizo-AITL/mems-ana)

The basic workflow is:

1. Clone the repository  
2. Prepare a Python environment  
3. Run the scripts under `mems-ana_demo`

The setup is intentionally kept simple.

---

## 🚫 Scope and Limitations

This demo intentionally makes several simplifications:

- No strict reproduction of material nonlinearities  
- No higher-order vibration modes  
- No dynamic resonance analysis  

It is designed purely to answer the question:

> “When piezoelectric hysteresis is applied,  
>  what kind of *behavioral face* does a MEMS structure show?”

---

## 🧭 Position in the Series

- **01**: Design philosophy and overall architecture  
- **02**: Visualization demo (this article)  
- **03**: ROM mathematical structure and design policy  

The next article will dig deeper into  
**the equations and ROM structure that generate this behavior**.

---

## 📝 Closing Remarks

Viewing analysis results not as static numbers, but as  
**moving, evolving shapes**, dramatically changes:

- Speed of understanding  
- Design intuition  

The *mems-ana_demo* is designed as an **entry point for visualization**.

> First, observe.  
> Then, design.

That is where MEMS design truly begins.

---
