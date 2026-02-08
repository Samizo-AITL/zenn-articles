---
layout: default
title: zenn-articles
---

# 【Semiconductor】🧪 09. OpenLane superstable  
### — Verifying “Minimal RTL → GDS” with Pre-Declared Conditions
topics: ["OpenLane", "SKY130", "EDA", "Semiconductor", "VLSI"]

---

## 🧭 Introduction

When working with OpenLane, the following questions naturally arise:

- “Does this flow really complete with *ordinary RTL*?”
- “Does it require extensive tuning to work?”
- “Are reported success cases adjusted *after* seeing the results?”

When reading articles about EDA flows,  
it is not uncommon to find cases where **conditions are tweaked after success is observed**.

In this experiment, we therefore asked a stricter question:

> **If we pre-declare a minimal, self-written RTL design and fixed constraints,  
> can OpenLane superstable truly complete the flow from RTL to GDS without modification?**

---

## 🧩 What Was Done (Key Points)

The experiment was intentionally simple.

- Prepare a **self-written minimal RTL (a counter)**  
- **Fix all constraints before execution**  
- Run OpenLane **superstable without any modification**  
- Judge success **only by whether a GDS is generated**  

Performance evaluation and optimization were  
**explicitly excluded from the scope of this verification**.

---

## 📌 What “Pre-Declaration” Means

The key concept here is **pre-declaration**.

This is not an official OpenLane term, but refers to:

> **Deciding the RTL, constraints, and success criteria  
> before seeing any results**

### 📝 Pre-Declared Items

- RTL contents (no post-editing)  
- Constraints such as clock period and utilization (no post-tuning)  
- Success criterion: **“A GDS is generated” — nothing more**

This explicitly avoids:

- Relaxing constraints if the run fails  
- Presenting only hand-tuned configurations as “success stories”  

---

## 🧱 Design Contents (Minimal RTL)

The design is **truly minimal**.

| Item | Description |
|---|---|
| Function | Free-running counter |
| FSM | None |
| Clock | Single clock |
| Reset | None (simulation-only initialization) |
| Macros | Not used |

RTL file:  
`rtl/spm_min_counter.v`

---

## ⏱ Pre-Fixed Constraints

| Item | Value |
|---|---|
| Clock period | 10 ns (100 MHz) |
| Core utilization | 30% |
| Aspect ratio | 1.0 |

Configuration file:  
`openlane/config.tcl`

---

## 🧪 RTL Simulation (Testbench)

```
spm_min_counter/
├─ README.md
├─ rtl/
├─ sim/
│  ├─ tb_spm_min_counter.v
│  ├─ run.sh
│  └─ wave/
├─ openlane/
├─ runs/
├─ results/
└─ run_log/
```

### Testbench Policy

- RTL not modified  
- No reset added  
- Simulation-only initialization only  

---

## 📈 GTKWave Waveform

<p align="center">
  <img
    src="https://raw.githubusercontent.com/Samizo-AITL/SemiDevKit/main/openlane/openlane-superstable/spm_min_counter/results/gtkwave.png"
    style="width:80%;"
  >
</p>

---

## 🧩 OpenLane Execution Results

- RTL → GDS completed  
- DRC / LVS passed  

---

## 🗺 KLayout Layout View

<p align="center">
  <img
    src="https://raw.githubusercontent.com/Samizo-AITL/SemiDevKit/main/openlane/openlane-superstable/spm_min_counter/results/1_overview.png"
    style="width:80%;"
  >
</p>

---

## 📝 Summary

This verification confirms that **OpenLane superstable**:

- Can complete **RTL → GDS**  
- With a **minimal RTL design**  
- Under **pre-declared, fixed conditions**  
- **Without post-hoc tuning or modification**

---

## 🔗 Reference Links

- **GitHub Pages**  
  [https://samizo-aitl.github.io/SemiDevKit/openlane/openlane-superstable/spm_min_counter](https://samizo-aitl.github.io/SemiDevKit/openlane/openlane-superstable/spm_min_counter)

- **GitHub Repository**  
  [https://github.com/Samizo-AITL/SemiDevKit/tree/main/openlane/openlane-superstable/spm_min_counter](https://github.com/Samizo-AITL/SemiDevKit/tree/main/openlane/openlane-superstable/spm_min_counter)
