---
title: "【Semiconductor】Visualizing MOSFET L/W Scaling and Short-Channel Effects with SPICE"
emoji: "📏"
type: "tech"
topics: ["Semiconductor", "MOSFET", "Scaling", "Short-Channel Effects", "BSIM4"]
published: true
---

## 🚀 Introduction

MOSFETs are often described as devices where

> **“smaller means faster.”**

However, in real silicon, shrinking a device also reveals another face:

- ⚠️ Reduced controllability  
- ⚠️ Increased leakage current  
- ⚠️ Enhanced parameter variability  

In this article, using **BSIM4 models and SPICE simulations**, we perform  
**L/W dimensional scaling analysis** to understand:

- Why device characteristics change when dimensions shrink
- Where textbook intuition breaks down in real devices

All observations are based on **actual simulation results**.

---

## 📐 What Is Dimensional Scaling?

MOSFET dimensional scaling examines the impact of changing:

- Channel length: $L$
- Device width: $W$

For an ideal long-channel MOSFET, one might expect:

- $I_d \propto W$
- $I_d \propto 1/L$

However, **real devices deviate significantly from this ideal behavior**.

The root cause of this deviation is known as  
👉 **Short-Channel Effects (SCE)**.

---

## 🧰 Analysis Environment (SemiDevKit)

This article uses the following DIM analysis module:

- **BSIM4_ANALYZER_DIM**  
  https://samizo-aitl.github.io/SemiDevKit/bsim/bsim4_analyzer_dim/

### Key Features
- Python + ngspice
- BSIM4 (130 nm educational model)
- Fully automated flow:
  - L/W-dependent model generation
  - Netlist creation
  - SPICE execution
  - CSV / PNG output

👉 Enables **hands-free comparison of dimensional dependence**.

---

## 🔬 Channel Length ($L$) Scaling

### How to Run

```bash
cd bsim/bsim4_analyzer_dim/run
python run_vg_dim.py
python run_vd_dim.py
```

This analysis varies the channel length $L$ step by step and compares:

- Vg–Id (transfer characteristics)
- Vd–Id (output characteristics)

---

### ⚠️ What Happens When $L$ Becomes Shorter?

From the simulation results, we observe:

- 📉 Threshold voltage roll-off
- 📉 Reduced output resistance
- ⚡ DIBL (Drain-Induced Barrier Lowering)
- ⚠️ Degraded current saturation

These phenomena collectively define  
👉 **Short-Channel Effects (SCE)**.

---

### ■ Vg–Id (L Sweep, NMOS)

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_dim/nmos_vgid.png" width="80%">

👉 Shorter $L$ lowers $V_{th}$ and increases leakage  
👉 $g_m$ enhancement and loss of gate control occur simultaneously

---

### ■ Vd–Id (L Sweep, NMOS)

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_dim/nmos_vdid.png" width="80%">

👉 Weaker saturation and stronger $V_d$ dependence  
👉 A classic signature of DIBL

---

## 📏 Device Width ($W$) Scaling

### How to Run

```bash
cd bsim/bsim4_analyzer_dim/run
python run_vg_dim.py
python run_vd_dim.py
```

(Only the fixed-width condition is changed.)

---

### 🤔 Intuition vs. Reality in $W$ Scaling

Intuitively, one might expect:

- Increasing $W$ → proportional increase in current

In practice, however, the following effects become significant:

- Parasitic resistance ($R_{dsw}$)
- Parasitic capacitance ($C_{gg}$)
- Narrow-width effects

👉 **Increasing width does not solve everything**  
👉 This is a critical consideration in standard-cell design

---

## 🧠 The Role of BSIM4

BSIM4 explicitly includes:

- Threshold voltage roll-off
- DIBL
- Mobility degradation
- Narrow-width effects

as **dimension-dependent parameters**.

As a result, SPICE simulations alone can reveal:

> **“What breaks when the device is scaled.”**

This makes BSIM4 an effective bridge between device physics and circuit design.

---

## 🔗 Relationship with TCAD

In TCAD simulations, short-channel scaling shows:

- Distorted electrostatic potential
- Drain electric field penetrating into the channel

BSIM4 DIM analysis:
- Compresses these spatial effects
- Into observable **I–V characteristics**

👉 BSIM4 acts as a **bridge between TCAD and circuit-level design**.

---

## 💡 The True Value of DIM Analysis

DIM analysis is particularly valuable for:

- SRAM β-ratio design
- Standard-cell drive-strength tuning
- Performance vs. leakage trade-off studies

👉 It reveals **how far scaling can be pushed before functionality degrades**.

---

## 📝 Summary

- 📏 L/W scaling strongly alters MOSFET characteristics  
- ⚠️ Shorter $L$ introduces short-channel effects  
- 📐 Increasing $W$ is not a simple linear solution  
- 🧠 BSIM4 + SPICE enable realistic device behavior analysis  

To understand MOSFETs as **real devices rather than equations**,  
DIM analysis is an indispensable tool.

---

## Next Article 👉

**08: What Is NBTI? — How MOSFETs Degrade Over Time**
