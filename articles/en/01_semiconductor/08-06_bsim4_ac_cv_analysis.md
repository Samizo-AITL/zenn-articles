---
layout: default
title: zenn-articles
---

# 【Semiconductor】 📐 08-06. BSIM4 AC/CV Analysis — How to Read Parasitic Capacitance and Frequency Response Correctly"
topics: ["Semiconductor", "BSIM4", "SPICE", "AC Analysis", "CV Analysis"]

---

## 🚀 Introduction

In the previous article, we focused on **DC analysis (V–I characteristics)**.  
However, MOSFETs are **not devices used only under DC conditions**.

- ⚡ High-speed digital circuits  
- 🎛 Analog circuits  
- 📡 Frequency response and bandwidth design  

For all of these applications,  
👉 **understanding parasitic capacitance and frequency behavior is essential**.

In this article, using the **BSIM4 model**, we systematically explain:

- 📊 **AC analysis (frequency response)**  
- 🧪 **CV analysis (capacitance characteristics)**  

with a clear focus on **what can be trusted and what requires caution**.

---

## 🧭 Difference Between AC Analysis and CV Analysis

### 🔹 What is AC Analysis?
- Superimposes a **small-signal AC excitation** around a DC operating point
- Sweeps frequency to evaluate circuit response

What you can observe:
- Small-signal gain
- Phase response
- Bandwidth
- Transconductance $g_m$
- Output resistance $r_o$

👉 AC analysis tells us **how fast a circuit can respond**.

---

### 🔹 What is CV Analysis?
- Evaluates **intrinsic capacitance components** inside a MOSFET
- Observes how capacitance changes with bias conditions

Typical capacitances:
- Gate capacitance $C_{gg}$
- (Reference) $C_{gs}$, $C_{gd}$, $C_{gb}$

👉 CV characteristics directly affect **delay, switching speed, and high-frequency behavior**.

---

## 🧰 Analysis Environment (SemiDevKit)

This article uses the following tool:

- **BSIM4 C–V Extraction Tool (ngspice)**  
  [https://samizo-aitl.github.io/SemiDevKit/bsim/bsim4_analyzer_cv/](https://samizo-aitl.github.io/SemiDevKit/bsim/bsim4_analyzer_cv/)

### Prerequisites
- BSIM4 model cards (educational / analytical)
- ngspice 41 (64-bit)
- Python 3.9+
- matplotlib

---

## ⚠️ How to Think About CV Analysis (Important)

In BSIM4, capacitances are defined based on **terminal charges**.

### Physically Meaningful Capacitance

```math
C_{gg} = \frac{dQ_g}{dV_g}
```

- The derivative of total gate charge
- Uniquely defined by MOS electrostatics

---

### Pitfall: Partitioned Capacitances

BSIM4 can also output:
- $C_{gs}$
- $C_{gd}$
- $C_{gb}$

However, these are:
- Strongly dependent on the **charge-partitioning algorithm**
- Not guaranteed to satisfy:

```math
C_{gs} + C_{gd} + C_{gb} \neq C_{gg}
```

👉 Therefore, they are **not always suitable as physical CV characteristics**.

For this reason, this tool intentionally adopts:

> ✅ **Extraction of $C_{gg}$ only**  
> ❌ $C_{gs}$ / $C_{gd}$ / $C_{gb}$ are excluded

This ensures **physical interpretability and numerical stability**.

---

## 🧪 Running CV Analysis

```bash
python run_cv.py
```

This automatically generates and executes:

- NMOS / PMOS
- Temperature corners: LT / RT / HT

for a total of **six simulation conditions**.

---

## 🧩 NMOS / PMOS Terminal Conditions

### 🔹 NMOS
- S = D = B = 0 V
- Gate sweep: 0 → VDD

### 🔹 PMOS (Important)
- S = D = B = VDD
- Gate sweep: VDD → 0 V

👉 Matches **real device ON/OFF behavior**  
👉 Ensures physically correct PMOS biasing

---

## 📈 CV Analysis Results

### ■ NMOS C–V (130 nm, RT)

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_cv/nmos_cv.png" width="80%">

- Accumulation → depletion → inversion
- U-shaped $C_{gg}$–$V_g$ characteristic

---

### ■ PMOS C–V (130 nm, RT)

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_cv/pmos_cv.png" width="80%">

- Sweep from VDD → 0 V
- Consistent with real PMOS operation

---

## 📡 AC Analysis: Frequency Response

```bash
python run_ac.py
```

In AC analysis:
- A small AC signal is applied
- Frequency is swept around a DC operating point

This reveals:
- Gain
- Phase
- Bandwidth

👉 **If DC analysis is incorrect, AC analysis becomes meaningless**  
👉 Always follow the order: **DC → AC → CV**

---

## 🧠 Where Do Parasitic Capacitances Come From?

MOSFET parasitic capacitances originate from:
- Gate oxide
- Channel formation
- Gate overlap regions
- Depletion regions

These are exactly the **potential and carrier distributions observed in TCAD**.

👉 BSIM4 simply **compresses this physics into a compact model**.

---

## 🔗 Relationship with DC Analysis

A critical principle:

> **AC and CV analyses are completely dependent on the DC operating point**

- Incorrect DC → meaningless AC/CV
- Correct DC → meaningful small-signal analysis

👉 Always start from **DC correctness**.

---

## 📝 Summary

- 📊 AC analysis evaluates frequency response
- 🧪 CV analysis evaluates parasitic capacitance
- ⚠️ In BSIM4, **only $C_{gg}$ has clear physical meaning**
- 🧠 Correct DC analysis is the foundation of everything

To use BSIM4 as a **trustworthy model**,  
you must clearly understand **what to look at — and what not to trust**.

---

## Next Article 👉

**07: MOSFET L/W Scaling and Short-Channel Effects**
