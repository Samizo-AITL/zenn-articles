


---
title: "[Semiconductor] 01. SemiDevKit Overview — Connecting TCAD, SPICE, and Reliability in One Flow"
emoji: "🧩"
type: "tech"
topics: ["Semiconductor", "TCAD", "BSIM4", "SPICE", "Reliability"]
published: true
---

## 🧭 Positioning of This Article (Series Hub)

**SemiDevKit** is an educational toolkit designed to connect the following semiconductor domains,  
which are often learned **in isolation**, into a **single continuous flow**:

- 🧪 **Device Physics (TCAD)**
- 🧩 **Compact Modeling (BSIM4)**
- 🔌 **Circuit Simulation (SPICE)**
- ⏳ **Reliability (NBTI / HCI)**

This article serves as the **entry point (hub / table of contents)** for the entire series.

🔗 SemiDevKit Top Page  
[https://samizo-aitl.github.io/SemiDevKit/](https://samizo-aitl.github.io/SemiDevKit/)

---

## 🤔 Why an End-to-End Flow Is Necessary

Semiconductor learning tends to become **fragmented**:

- You understand the equations, but they never connect to **V–I**
- `.model` files turn into **black boxes**
- SPICE is reduced to just **looking at results**
- Reliability stops at “it degrades” without deeper insight

SemiDevKit intentionally **breaks this fragmentation** and is designed around the idea that:

> **Physics → Model → Circuit (V–I) → Degradation**

should be understood as **one continuous line**, not separate topics.

---

## 🧱 Overall Flow of SemiDevKit

```
TCAD (Poisson / Drift–Diffusion)
   ↓
BSIM4 (Compact Model)
   ↓
SPICE (DC / AC / CV)
   ↓
Reliability (NBTI / HCI)
```

### 🔑 Key Points
- Each layer can be studied **independently**
- But understanding earlier layers directly **strengthens** later ones
- **V–I (Voltage–Current)** characteristics act as the common language

---

## 📘 What You Learn at Each Layer

### ① 🧪 TCAD (Device Physics)
- Poisson equation (electrostatic potential)
- Drift–Diffusion (carrier transport)
- Why MOSFET **V–I characteristics** emerge

🔗 TCAD Pages  
[https://samizo-aitl.github.io/SemiDevKit/tcad/](https://samizo-aitl.github.io/SemiDevKit/tcad/)

---

### ② 🧩 BSIM4 (Compact Modeling)
- Compressing physics into a **circuit-usable form**
- Physical meaning of BSIM4 parameters
- Visualizing what a `.model` **actually represents**

🔗 BSIM Pages  
[https://samizo-aitl.github.io/SemiDevKit/bsim/](https://samizo-aitl.github.io/SemiDevKit/bsim/)

---

### ③ 🔌 SPICE (Simulation)
- **DC analysis**: $V_g$–$I_d$, $V_d$–$I_d$
- **AC / CV analysis**: parasitic capacitance, frequency response
- **Geometry dependence**: L/W and short-channel effects

👉 Experience how **model parameters appear in V–I**

---

### ④ ⏳ Reliability
- **NBTI**: negative bias × temperature × time → $V_t$ shift
- **HCI**: oxide damage due to high-field carriers

👉 Adding the **time axis** brings designs closer to reality

---

## 📚 Series Index

- **01**: SemiDevKit Overview (this article)
- **02**: TCAD (Poisson / Drift–Diffusion)
- **03**: BSIM4 Theory (Physics → Model)
- **04**: Paramus (BSIM4 Model Generation)
- **05**: DC Analysis (V–I: $V_g$–$I_d$, $V_d$–$I_d$)
- **06**: AC / CV Analysis (Parasitic Capacitance, Frequency)
- **07**: Device Scaling (L/W and Short-Channel Effects)
- **08**: NBTI (Time-Dependent Degradation)
- **09**: HCI (High-Field Degradation)

---

## 🎯 Intended Audience

- Students who want a **systematic understanding** of semiconductors
- Engineers who want to use **BSIM4 / SPICE with real meaning**
- Learners who want to experience the **full design flow without commercial TCAD / EDA tools**

---

## ▶ Next Article

Next, we start from the very upstream layer.

👉 **02: Understanding the Essence of MOSFETs with TCAD**  
(Poisson / Drift–Diffusion)
