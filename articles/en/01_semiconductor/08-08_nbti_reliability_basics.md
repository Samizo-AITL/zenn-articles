---
title: "【Semiconductor】What Is NBTI? — How MOSFETs Degrade Over Time"
emoji: "⏱️"
type: "tech"
topics: ["Semiconductor", "NBTI", "Reliability", "MOSFET", "BSIM4"]
published: true
---

## ⏱️ Introduction

In the previous articles, we have examined **initial MOSFET characteristics** through:

- 🧪 **TCAD** for physical understanding  
- 📐 **BSIM4** for compact modeling  
- 🔌 **SPICE** for electrical characterization  

However, in real silicon devices, there is an unavoidable reality:

> **A device that works well today may not behave the same way five years later.**

One of the most representative causes of this behavior is  
👉 **NBTI (Negative Bias Temperature Instability)**.

NBTI is a fundamental reliability issue that explains how  
**MOSFETs gradually degrade over time**.

---

## 🔥 What Is NBTI?

NBTI mainly affects **pMOSFETs** when the following conditions coexist:

- Negative gate bias
- Elevated temperature
- Long operating time

It is therefore classified as a  
**time-dependent reliability degradation mechanism**.

Its most distinctive feature is:

> **The threshold voltage $V_t$ shifts as a function of time.**

---

## 🧠 What Is Happening Physically?

Under NBTI stress conditions, near the gate-oxide / silicon interface:

- Interface states are generated
- Trap states become activated and permanently charged

As a result:

- Even with the same applied $V_g$
- The same channel charge density cannot be formed

👉 **The MOSFET becomes harder to turn on**

This manifests as **reduced on-current and increased delay**.

---

## 📉 Impact on V–I Characteristics

NBTI effects appear directly in **DC characteristics**.

Typical observations include:
- A **rightward shift** of the $V_g$–$I_d$ curve
- Degradation of subthreshold behavior
- Reduced $I_d$ at the same $V_g$

All of these are consequences of:

> **Threshold voltage shift ($\Delta V_{th}$)**

---

## 📐 How BSIM4 Treats NBTI

In BSIM4, NBTI is represented as:

- Degradation modeled through **parameter variation**
- Time-dependent $V_t$ shift
- Comparison of characteristics before and after degradation

A critical limitation must be noted:

> **BSIM4 alone does not directly solve time evolution**

For this reason, SemiDevKit adopts a hybrid approach:

- 🧪 **SPICE**: Accurate measurement at $t = 0$  
- 🧮 **Python**: Time-dependent degradation modeling for $t > 0$

---

## 🧰 NBTI Analysis with SemiDevKit

The following module is used:

- **BSIM4 Analyzer Reliability**  
  https://samizo-aitl.github.io/SemiDevKit/bsim/bsim4_analyzer_reliability/

This framework provides fully automated:

- Initial VG–ID extraction
- Threshold voltage extraction using gmmax and constant-current methods
- Application of time-dependent degradation models
- Reconstruction of degraded device characteristics

---

## 🔬 NBTI Analysis Flow

```
t = 0
 ├─ VG–ID sweep
 │     ├→ Vtg0 (gmmax method)
 │     └→ Vtc0 (constant-current method)
 ├─ DC extraction
 │     └→ Idlin0 / Idsat0

t > 0
 ├─ Apply ΔVth(t) model
 ├─ Apply ΔId(t) model
 ├─ Reconstruct Vtg1 / Vtc1 / Idlin1 / Idsat1

→ Export CSV results
→ Generate degradation plots
→ Overlay VG–ID curves
```

---

## 🚀 Execution Example

```bash
cd bsim/bsim4_analyzer_reliability/run
python run_nbti_pmos.py
```

---

## 📊 Example Results

### ■ PMOS NBTI: Vg–Id Degradation (Linear Scale)

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_reliability/pmos_nbti_vgid.png" width="80%">

👉 Clear rightward shift of the Vg–Id curve  
👉 Reduced drain current at the same gate voltage

---

### ■ PMOS NBTI: ΔVtg vs. Stress Time

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_reliability/nbit_dvtg.png" width="80%">

👉 Degradation follows a **power-law time dependence**  
👉 Early-stage degradation is dominant

---

## ⚠️ Why NBTI Matters

NBTI leads to:

- Reduced operating frequency
- Loss of timing margin
- Long-term reliability failure

It is especially critical for:
- Low-voltage operation
- SRAM and low-$V_{dd}$ logic
- Long-lifetime products (automotive, industrial)

👉 **NBTI is a hard constraint, not an optional consideration.**

---

## 🔗 TCAD / BSIM / SPICE Relationship

NBTI fits naturally into the same conceptual chain:

- **TCAD**: Physical processes at the interface  
- **BSIM4**: Parameterized degradation models  
- **SPICE**: Circuit-level impact assessment  

👉 **Reliability is also a “physics → model → circuit” problem.**

---

## 📝 Summary

- ⏱️ NBTI is a time-dependent reliability degradation mechanism  
- 🟦 It primarily affects pMOSFETs  
- 📉 It appears as a threshold voltage shift  
- 🧪 BSIM4 + SPICE + Python enable clear visualization  

MOSFETs are no longer evaluated by:

> **“Does it work?”**

but by:

> **“How long does it keep working?”**

---

## Next Article 👉

**09: What Is HCI? — Why High Electric Fields Destroy MOSFETs**
