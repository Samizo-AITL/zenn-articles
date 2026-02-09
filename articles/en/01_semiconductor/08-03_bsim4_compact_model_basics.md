---
layout: default
title: zenn-articles
---

#【Semiconductor】 🧩 08-03. What Is BSIM4? — A Compact Model That Translates Physics into Circuits
topics: ["Semiconductor", "BSIM4", "MOSFET", "Compact Model", "SPICE"]

---

## 🧭 Introduction — What Comes After TCAD

In the previous article, we confirmed through **TCAD** that MOSFET operation is governed by:

- the **Poisson equation**
- the **Drift–Diffusion equations**

However, using TCAD directly for  
**circuit design and circuit simulation** is not practical.

- Computational cost is extremely high  
- Simulations do not scale with large numbers of transistors  

This is where **BSIM4** comes into play.

---

## 🧩 The Role of BSIM4 — What Kind of Model Is It?

**BSIM4** is a **compact model** for MOSFETs.

- **Inputs**: terminal voltages  
  $V_g$, $V_d$, $V_s$, $V_b$
- **Outputs**: terminal currents and capacitances  
  $I_d$, $C_{gs}$, $C_{gd}$, …

It is a mathematical model designed to compute these quantities  
**quickly and efficiently**.

In other words:

> **BSIM4 compresses the physical phenomena observed in TCAD  
> into a form that can be used immediately in circuit simulation.**

---

## 📦 Why Is It Called a “Compact Model”?

In TCAD, we directly solve:

- Spatial distributions (potential and carrier profiles)
- Partial differential equations

BSIM4, on the other hand, uses:

- Only terminal voltages
- Predefined model parameters

to calculate $I$–$V$ characteristics using  
**closed-form equations**.

That is:

> **Spatial information is discarded,  
> and behavior is summarized at the terminals.**

This philosophy defines a **compact model**.

---

## 🧠 Physics Embedded Inside BSIM4

BSIM4 is not just a collection of curve-fitting formulas.  
It internally captures many **real device physics effects**, such as:

- Threshold voltage variation ($V_{th}$)
- Short-channel effects
- Mobility degradation
- Velocity saturation
- Parasitic resistances and capacitances

These effects are represented by **hundreds of parameters**.

👉 The reason is not “complexity for its own sake,”  
👉 but because **real MOSFETs contain that much physics**.

---

## 😵 Why BSIM4 Looks “Difficult”

When you first see a BSIM4 `.model` card:

- There are too many parameters  
- Parameter names are not intuitive  
- Equations are long  

This reaction is completely normal.

But the key point is this:

> **You do not need to understand everything.**

---

## 🔍 The Right Way to Understand BSIM4

What matters when working with BSIM4 is understanding:

- Which physical effect each
