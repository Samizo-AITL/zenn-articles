---
layout: default
title: zenn-articles
---

# 【Semiconductor】 🧠 08-02. Understanding the Essence of MOSFETs with TCAD — Poisson Equation and Drift–Diffusion
topics: ["Semiconductor", "TCAD", "MOSFET", "Poisson Equation", "Drift-Diffusion"]

---

## 🧭 Introduction — Where Do V–I Characteristics Come From?

The **V–I characteristics** of a MOSFET are not something that suddenly appear  
inside a circuit simulator.

Their true origin lies in the physical phenomena occurring **inside the device**:

- **Electrostatics (potential distribution)**
- **Carrier transport**

In this article, from a **TCAD (Technology Computer-Aided Design)** perspective, we focus on:

- 🧮 the **Poisson equation** (which determines potential)
- 🚗 the **Drift–Diffusion equations** (which determine current)

to explain  
👉 **why MOSFET $V$–$I$ characteristics take the shape they do**.

---

## 🔍 What Is TCAD?

TCAD is a simulation methodology that **directly solves physical phenomena**  
inside semiconductor devices using numerical methods.

What you provide includes:

- Device structure
- Doping profiles
- Material parameters
- Bias conditions

And as a result, you can simultaneously and continuously observe:

- Electrostatic potential
- Electric field
- Carrier density
- Current density

> 📌 If circuit simulation is a world of “observing results,”  
> **TCAD is the world of observing the moment those results are born.**

---

## 🧮 Poisson Equation — The Origin of Everything

The Poisson equation is the foundation of semiconductor physics, linking:

> **Charge distribution → Potential distribution**

In MOS structures:

- Gate voltage
- Oxide thickness $t_{ox}$
- Substrate doping $N_A$

control **surface potential**, which in turn governs channel formation.

In short:

> **Whether a channel forms or not is determined first by electrostatics.**

---

## 🧱 What Happens in a MOS Structure (Role of Poisson)

As the gate voltage increases, the following sequence occurs in a MOS structure:

1. Gate voltage is applied  
2. Surface potential changes through the oxide  
3. Carriers accumulate at the surface  
4. A channel is formed  

All of this is **governed by the Poisson equation**.

👉 **“Potential creates the channel.”**

---

## 🚗 Drift–Diffusion Equations — What Determines Current

A channel alone does not produce current.  
Current is determined by the **Drift–Diffusion equations**:

- **Drift**: carrier motion driven by electric fields  
- **Diffusion**: carrier motion driven by concentration gradients  

These equations naturally explain:

- Why $I_d$ increases when $V_d$ increases  
- Why a linear region appears at low voltages  

👉 **“Transport equations create $I_d$.”**

---

## 📈 V–I Characteristics Are a Stack of Physics

With TCAD, the following quantities are observed simultaneously:

- Potential distribution
- Carrier density distribution
- Current density distribution

As a **direct consequence** of these physical quantities stacking together:

- $V_g$–$I_d$ characteristics  
- $V_d$–$I_d$ characteristics  

**emerge naturally**.

---

## 🧪 SemiDevKit: An Educational 1D TCAD Playground

SemiDevKit provides a **lightweight 1D TCAD environment**  
specifically designed for educational use.

- Poisson + Drift–Diffusion
- Implemented in Python
- One-to-one correspondence between equations, code, and plots

🔗 TCAD Top Page  
[https://samizo-aitl.github.io/SemiDevKit/tcad/](https://samizo-aitl.github.io/SemiDevKit/tcad/)

---

## 📊 Example ①: MOSCAP C–V Characteristics (Result of Poisson)

How does the **C–V characteristic** of a MOS capacitor change  
when oxide thickness $t_{ox}$ is varied?

![MOSCAP C–V](https://samizo-aitl.github.io/SemiDevKit/assets/tcad_playground/moscap_cv_tox.png)

👉 **Differences in potential distribution appear as capacitance.**

---

## 📊 Example ②: nMOS $V_g$–$I_d$ Characteristics

$n$MOS $V_g$–$I_d$ characteristics with varying oxide thickness.

![nMOS Vg–Id](https://samizo-aitl.github.io/SemiDevKit/assets/tcad_playground/nmos_vgid_tox.png)

- Thinner $t_{ox}$ → lower $V_{th}$  
- Higher $I_d$ at the same $V_g$  

👉 **Poisson → Drift–Diffusion → $I_d$**

---

## 📊 Example ③: nMOS $V_d$–$I_d$ Characteristics

![nMOS Vd–Id](https://samizo-aitl.github.io/SemiDevKit/assets/tcad_playground/nmos_vdid_tox.png)

- Low $V_d$: linear region  
- High $V_d$: saturation region  

👉 **Transport equations naturally create operating regions.**

---

## 🔗 TCAD Is Not the Final Goal

TCAD is extremely powerful, but it has limitations:

- High computational cost  
- Too heavy for circuit-level design  

This is where **BSIM4** comes in.

> **Compressing the physics observed in TCAD  
> into a form immediately usable in circuits**

That is the role of **compact models**.

---

## 📝 Summary

- MOSFET $V$–$I$ characteristics result from Poisson and Drift–Diffusion equations  
- Electrostatics create the channel; transport equations determine current  
- TCAD reveals the moment when equations become reality  

---

## ▶ Next Article

👉 **03: What Is BSIM4? — A Compact Model That Translates Physics into Circuits**

---

🧩 *The SemiDevKit series continues from  
“TCAD → BSIM → SPICE → Reliability.”*
