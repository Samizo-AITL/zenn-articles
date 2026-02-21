---
layout: default
title: zenn-articles
---

# 【Semiconductor】⏱️ 25. Does OpenLane STA Lie?  
## The Real Reasons SDF, GLS, and Physical Reality Diverge

topics: ["OpenLane", "ASIC", "STA", "Timing", "EDA"]

---

## 🧭 Introduction: STA Passed — Yet It Still Doesn’t Work

If you use OpenLane long enough,  
you will inevitably encounter this situation:

- ✅ STA reports PASS  
- ✅ No Setup / Hold violations  
- ❌ Yet simulation or silicon does not work  

At this point, many people think:

> 🤔 **“Is STA lying?”**

Let us start with the conclusion.

> ❗ **STA does not lie.**  
> However, **it does not tell the whole truth either.**

Based on  
OpenLane Guide **Phase 3: Integration & Timing Truth**,  
this article explains:

- What STA actually guarantees  
- How much SDF / GLS can be trusted  
- The real cause of “STA passed but it doesn’t work”  

—by organizing the relationship between **logic, physics, and assumptions**.

🔗 OpenLane official repository  
[https://github.com/The-OpenROAD-Project/OpenLane](https://github.com/The-OpenROAD-Project/OpenLane)

🔗 Structured guide (source material)  
[https://samizo-aitl.github.io/openlane-guide/](https://samizo-aitl.github.io/openlane-guide/)

---

## 🧠 What STA Really Is: A Calculation Based on Assumptions

STA (Static Timing Analysis) is  
**an analysis performed with time frozen**.

It relies on the following assumptions:

- 📐 Cell delays match the models  
- 🧵 Interconnect delays match estimates  
- ⏱ Clocks arrive as expected  
- 🔁 Data transitions follow logic  

In other words, STA computes:

> 📊 **Worst-case timing in a world where all assumptions hold true**

---

## ⏱ The Physical Meaning of Setup and Hold

Setup and Hold are not equations.  
They are **physical phenomena**.

- Setup violation  
  → Data arrives too late  
- Hold violation  
  → Data arrives too early  

These are determined by:

- Wire length  
- Buffer stages  
- Clock skew  

> ⚠️ STA can only compute timing  
> **under the assumption that the physical world matches expectations**.

---

## 🔗 What Does SDF Actually Convey?

SDF (Standard Delay Format) provides:

- ⏱ Cell delays  
- 🧵 Interconnect delays  

as **timing annotations**.

However, note this carefully:

> ❗ **SDF only represents an “average” physical picture**

It does *not* include:

- IR drop  
- Crosstalk  
- Local temperature gradients  

---

## 🧪 What GLS Guarantees — and What It Does Not

Gate-Level Simulation (GLS) is widely misunderstood.

> 🤔 “If GLS passes, we’re safe, right?”

**No.**

GLS only guarantees:

- 🔁 Logical correctness of the netlist  
- ⏱ Delays are applied as described in the SDF  

> ❌ **It does not reproduce full silicon behavior.**

---

## ⚠️ The Truth Behind “STA Passed, but It Doesn’t Work”

In most cases, the root cause is one of the following:

1. 📉 Underestimated interconnect delay  
2. ⚡ Increased delay due to IR drop  
3. 🔊 Delay variation from crosstalk  
4. 🌡 Effects of temperature gradients  
5. 🔁 Local failures in the clock tree  

These are all:

> 📌 **Physical effects outside STA’s assumptions**

STA did not lie.  
**Reality violated the assumptions.**

---

## 🧱 The Limits of Timing Visibility in OpenLane

OpenLane is an open-source flow.

- Not all commercial EDA corrections are included  
- It is not designed for bleeding-edge nodes  
- Physical variation is simplified  

Therefore:

> 🧠 **OpenLane STA represents “educational and validation-level truth”**

It is *not* a final sign-off guarantee for mass production.

---

## 🧠 What Is Timing, Ultimately?

Here is the final conclusion:

> ⏱ **Timing is a collection of statistics and assumptions**

STA is powerful—but not omnipotent.

What designers must do is:

- Understand the assumptions  
- Question the physical reality  
- Inspect the layout  

---

## 📝 Summary

- ⏱ STA does not lie  
- ⚠️ It operates in a world of assumptions  
- 🔗 SDF / GLS are inherently limited  
- 🧱 Physical reality breaks assumptions  
- 👀 The layout is the final truth  

This is the conclusion of  
**Phase 3: Integration & Timing Truth**.

---

## ▶️ Next Article

Next is the **final article (Article 26)**.

- 💥 Common failure patterns  
- 🔀 How to use OpenLane1 vs OpenLane2  
- ♻️ Version pinning and reproducibility  
- 🧭 Why this guide is structured in this order  

We will summarize how to  
**use OpenLane without breaking it**.
