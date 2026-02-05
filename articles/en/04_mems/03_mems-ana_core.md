---
layout: default
title: Mathematical Structure and Design Policy of mems-ana_core Built with ROM
---

# 🧠 【MEMS:03】Mathematical Structure and Design Policy of *mems-ana_core* Built with ROM
topics: ["MEMS", "ROM", "modeling", "mathematics", "Python"]

---

## 📌 Introduction

In the previous article (MEMS:02),  
we visually explored the **behavior of a MEMS structure under piezoelectric hysteresis input**  
through a visualization demo.

In this article, we focus on what lies beneath that behavior:  
the **mathematical structure and design policy of *mems-ana_core***.

The purpose of this article is **not**:

- A line-by-line explanation of implementation code  
- A strictly accurate reproduction of physical phenomena  

Instead, the goal is to clarify—explicitly and from a designer’s perspective—

> Why this mathematical structure was chosen  
> What is intentionally included in the model, and what is intentionally excluded  

> This article is the third installment in the *mems-ana* series.

---

## 🧩 Positioning of *mems-ana_core*

**mems-ana_core** corresponds to:

- The computational core of *mems-ana*  
- A concrete implementation of a **Reduced Order Model (ROM)**  

Its defining characteristics are:

1. **Dominant modes are explicitly assumed**
2. **A clear correspondence between physical quantities and equations**
3. **Calibration parameters with limited and explicit meaning**

Rather than prioritizing raw speed,  
the design prioritizes **structural readability and interpretability**.

---

## 🧱 Modeling Assumptions

The intended targets are typical:

- Thin-film MEMS structures  
- Rectangular diaphragms  
- Small-deformation, quasi-static responses  

Accordingly, the following are **outside the model scope**:

- Geometric nonlinearity  
- Large deformation  
- Local plasticity  

If these assumptions do not hold,  
*mems-ana_core* should **not** be used.

---

## 📐 Basic Form of the Reduced Order Model (ROM)

The displacement field $u(x,y,t)$ is expressed as  
a product of spatial modes $\phi_n(x,y)$  
and time-dependent coefficients $q_n(t)$:

$$
u(x,y,t) = \sum_{n=1}^{N} q_n(t)\,\phi_n(x,y)
$$

The key design choices here are:

- Intentionally keeping $N$ **small**
- Selecting only **physically meaningful modes**

In *mems-ana_core*, mode selection is guided by:

- Symmetry  
- Dominant deformation behavior  
- Boundary conditions  

The result is a model with the **minimum number of modes required to capture behavior**.

---

## ⚙️ Structure of the Governing Equations

The general ROM-based equation of motion takes the form:

$$
M \ddot{\mathbf{q}} + C \dot{\mathbf{q}} + K \mathbf{q}
= \mathbf{f}(t)
$$

where:

- $\mathbf{q}$: vector of modal coordinates  
- $M$: mass matrix  
- $C$: damping matrix  
- $K$: stiffness matrix  

Because *mems-ana_core* primarily targets:

- Quasi-static behavior  
- Low-frequency response  

the inertial and damping terms  
($\ddot{\mathbf{q}}$, $\dot{\mathbf{q}}$)  
are often simplified or omitted.

---

## ⚡ Treatment of Piezoelectric Actuation

Piezoelectric actuation is introduced as  
an **external force term $\mathbf{f}(t)$**.

The critical modeling decision is that:

- The piezoelectric constant $d_{33}$ is treated as an  
  **effective proportional coefficient**
- The exact electric field distribution is not solved  

This yields a simplified, design-oriented causal chain:

- Voltage → polarization → equivalent force  

which preserves **interpretability and controllability**.

---

## 🔁 Positioning of Hysteresis Input

The **P–$E_z$ hysteresis** used in MEMS:02 is:

- **Not** a detailed internal material model  

Instead, it represents:

- A **representative nonlinear input waveform**

Thus, *mems-ana_core*:

- Does not solve hysteresis as an internal state  
- Treats it as a **history-dependent external input**

This choice:

- Prevents excessive mathematical complexity  
- Maintains ROM transparency and clarity  

---

## 🎯 Calibration Philosophy

Calibration in *mems-ana_core* can reference:

- FEM results  
- Experimental measurements  

but the philosophy remains consistent:

> Fit numerical values **without destroying parameter meaning**

In practice, calibration is limited to parameters such as:

- Global stiffness scaling  
- Effective piezoelectric coupling coefficient  
- Damping coefficient  

Arbitrary parameter fitting is explicitly avoided.

---

## 🔗 Relationship with FEM (Revisited)

*mems-ana_core* is **not** a replacement for FEM.

The intended division of roles is:

- **FEM**  
  - Local stress analysis  
  - Complex geometries  
  - Higher-order modes  

- **mems-ana_core**  
  - Global behavior  
  - Sensitivity and trends  
  - Design reasoning  

FEM results are used as  
**reference points to reason about “why” behavior occurs**.

---

## 🗂 GitHub Repository

The implementation of *mems-ana_core* discussed here  
is available in the following GitHub repository:

[https://github.com/Samizo-AITL/mems-ana](https://github.com/Samizo-AITL/mems-ana)

Please refer to the repository for  
the correspondence between equations and code.

---

## 🧭 Series Summary

- **01**: Design philosophy and overall structure  
- **02**: Visualization demo (observing behavior)  
- **03**: ROM mathematical structure and design policy (this article)

Together, these three articles present:

- Thought process  
- Observed behavior  
- Mathematical foundation  

as a **single, coherent narrative**.

---

## 📝 Closing Remarks

*mems-ana_core* is designed not as:

> A model that produces exact answers  

but as:

> A model that helps designers think  

Rather than minimizing equations,  
the priority is **not to minimize meaning**.

ROMs are approximations—  
but **good approximations accelerate design thinking**.

If this article helps clarify  
how and why models are constructed in MEMS design,  
it has achieved its purpose.

---
