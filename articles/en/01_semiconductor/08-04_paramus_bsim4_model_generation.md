---
layout: default
title: zenn-articles
---

# 【Semiconductor】 ⚙️ 08-04. Learning BSIM4 Model Generation with Paramus — Graduating from the Black-Box `.model`
topics: ["Semiconductor", "BSIM4", "SPICE", "Model Generation", "MOSFET"]

---

## 🧭 Introduction — Why `.model` Files Become Black Boxes

BSIM4 is a very powerful **MOSFET compact model**,  
but in practice and education it is often treated as:

- “Model cards are *given*”
- “The internals are *not to be touched*”

As a result:

- Parameter changes cannot be logically explained  
- Simulation results must simply be *taken on faith*  

This is exactly the assumption that **Paramus** is designed to break.

In this article, we take the perspective of:

> **Generating a BSIM4 model yourself from physical parameters**

with the goal of understanding the *meaning* behind a `.model` file.

---

## 🤔 Why Learn Model Generation?

The `.model` used in SPICE analysis  
is not just a configuration file.

It contains a condensed summary of **device physics**, such as:

- Oxide thickness $t_{ox}$
- Substrate doping $N_A$
- Carrier mobility $\mu$
- Threshold voltage $V_{th}$

Once you understand model generation, you can:

> **Explain in your own words  
> why device characteristics change when a parameter is modified**

---

## ⚙️ The Role of Paramus — Standing Between Physics and Circuits

Within SemiDevKit, the role of Paramus can be summarized as:

```
TCAD (Device Physics)
   ↓
Paramus (Physics → Model Translation)
   ↓
BSIM4 (SPICE-Usable Form)
```

👉 **Paramus acts as a “translator.”**

- Lighter than TCAD  
- Closer to physics than BSIM4  

It occupies this **intermediate layer**.

---

## 📥 Inputs and 📤 Outputs Matter

### 📥 Inputs (Physical Parameters)
- Oxide thickness $t_{ox}$
- Substrate doping $N_A$
- Carrier mobility $\mu$
- Estimated threshold voltage

### 📤 Outputs (BSIM4 Model)
- BSIM4 `.model` file
- Directly usable in SPICE

The key point is to generate the model while consciously tracking:

> **Physical quantities → BSIM4 parameters**

---

## 🧠 Basic Philosophy of Model Generation

Paramus operates with the following **simple workflow**:

1. Accept physical parameters  
2. Determine **initial values** for BSIM4 parameters  
3. Embed them into a template  

The emphasis here is on:

> **Meaningful initial values rather than aggressive optimization**

👉 Not “does it fit?”  
👉 but **“why is this value reasonable?”**

---

## 🧩 What It Means to Graduate from the Black Box

By using Paramus, you can track at the model level:

- What happens when $t_{ox}$ is changed  
- How $V_{th}$ shifts with increased doping  
- How mobility affects $I_d$  

This intuition is essential for connecting:

- **TCAD**
- **SPICE**

and understanding how they relate.

---

## 🧪 Execution Environment in SemiDevKit

Paramus is included in the **BSIM section of SemiDevKit**.

🔗 Paramus Page  
[https://samizo-aitl.github.io/SemiDevKit/bsim/Paramus/](https://samizo-aitl.github.io/SemiDevKit/bsim/Paramus/)

The generated `.model` files can be directly used for:

- DC analysis
- AC / CV analysis
- Reliability analysis (NBTI / HCI)

---

## ▶ What Comes Next — Using the Generated Model

Once the model is generated, the next phase is **using it**.

- Sweep gate voltage $V_g$  
- Sweep drain voltage $V_d$  
- Read the resulting $V$–$I$ characteristics  

👉 **A model is not finished when it is created.**  
👉 **It gains meaning only when it is used.**

---

## 📝 Summary

- Paramus is an educational tool for **BSIM4 model generation**  
- It reveals the mapping between physical and model parameters  
- Once you can question a `.model`, your understanding of SPICE deepens dramatically  

---

## ▶ Next Article

👉 **05: Reading MOSFET DC Characteristics with BSIM4**  
— Understanding model behavior through $V$–$I$ analysis

---

⚙️ *From here, the series proceeds through  
“Model Generation → DC Analysis → AC/CV → Reliability.”*
