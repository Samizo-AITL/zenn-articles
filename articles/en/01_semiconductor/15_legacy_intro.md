---
layout: default
title: zenn-articles
---

# 【Semiconductor】15. What Is Legacy Technology  
## — A Record of Failures from the Era When Semiconductors Were Ruled by Physics
topics: ["Semiconductor", "Technology History", "DRAM", "Reliability"]

---

# 🧭 What Is Legacy Technology?

**Legacy Technology** is not  
an archive created to nostalgically look back on old semiconductor technologies.

It is a structured record of  
**real failures and recoveries** that occurred in an era  
when semiconductor devices were **directly and unavoidably governed by physical constraints**.

This was before problems could be  
“hidden” by software, firmware,  
or system-level compensation.

Moments when process integration, cell structure, and device physics  
**directly determined yield, reliability, and business decisions**  
are preserved here.

📌 **The complete archive covered by this article** is available at:  
[https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/](https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/)

---

## 🕰 Historical Background  
### — The Era When DRAM Was “Pure Physics”

Until the mid-1990s, Japan stood at the forefront of DRAM technology worldwide.

Multiple domestic manufacturers simultaneously achieved:

- 🔬 World-class **DRAM development**
- 🏭 World-class **DRAM mass production**

The core axes of competition were not limited to density or cost,  
but focused on:

- 🧱 Cell stability  
- ⏳ Data retention  
- 🛡 Long-term reliability  

At that time, DRAM cell design was treated fundamentally  
as an **analog, physics-driven problem**.

---

## 🏗 Design Culture and Assumptions of the Time

The design culture of that era was built on clear assumptions:

- 🧮 Cell capacitance must be **secured structurally**
- ⚠️ Time-dependent failures are **abnormal events**
- 🌍 The market uses devices in  
  **unpredictable and often aggressive ways**

While this culture produced extremely robust memory devices,  
it relied heavily on one critical premise:

> ❗ **Physical margins must never be violated**

As long as this premise held,  
reliability was something that could be **guaranteed by design**.

---

## ⚠️ The Turning Point  
### (Late 1990s to Early 2000s)

As scaling entered the **0.25 µm generation and beyond**,  
this premise began to collapse.

### 🔄 What Changed

| Item | Reality |
|---|---|
| 🧮 Cell capacitance | Structural margins collapsed |
| 💧 Leakage / Disturb | Became the norm, not exceptions |
| ⏳ Retention | Became the dominant constraint |
| 💰 Market pressure | Speed and cost prioritized over physical certainty |

At the same time, DRAM prices entered a long-term decline,  
forcing decisions to **push products into mass production  
before failure mechanisms were fully understood**.

Failures such as Pause, Disturb, and Retention loss  
were no longer hypotheses.

They became **real problems** that surfaced:

- 🧪 In actual products  
- 🖥 In real systems  
- 👤 Through real user behavior  

---

## 🔍 Why Read Legacy Technology Now?

The technologies discussed here are  
already **more than 20 years old**.

However,  
**the structure of failure has not aged.**

The same causal structures repeatedly appear  
in modern semiconductor systems:

- 🧩 Device limits are masked by system-level solutions  
- 🧑‍💻 Reliability risks are delegated to software  
- 📊 Physical uncertainty is absorbed into business decisions  

What has changed is only the  
**scale, vocabulary, and abstraction layers**.

---

## 🎯 Scope of This Archive

This archive focuses on the  
**intersection of physics, manufacturing, and decision-making**.

- 🧪 Semiconductor process integration (1990s–early 2000s)
- 💾 DRAM and Pseudo-SRAM
- ⚡ Physical failures such as leakage, Disturb, and Retention
- 📉 Yield recovery under severe constraints
- 🧭 Engineering decisions under business pressure

The following are **intentionally excluded**:

- 🚫 Know-how applicable to current fabs
- 🔒 Confidential process conditions
- 🧬 Reproducible manufacturing recipes

---

## 🧭 How to Read This Archive

Each case is organized in the following order:

1. 🏗 **Process / Structure**  
2. 🔎 **Observed failure modes**  
3. 🧠 **Physical root causes**  
4. 🧪 **Manifestation in tests / binning**  
5. 🔧 **Yield recovery or strategic decisions**

This is not a retrospective explanatory order.  
It reflects **the actual sequence in which problems appeared and were resolved in the field**.

---

## 🧱 Positioning

There is only one reason this archive exists.

> 🧱 **Physics does not disappear as technology advances.**

It merely becomes easier to ignore.

This archive records the moments  
when **physics could no longer be ignored**.

---

## 🔗 Related Links (Primary Sources)

- 📚 Legacy Technology Archive  
  [https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/](https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/)

- 📘 0.25 µm DRAM Case List  
  [https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/dram_025um/](https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/dram_025um/)

- 📙 PSRAM (2001) Case List  
  [https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/psram_2001/](https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/psram_2001/)

---

### ⏭ Next

From the next article onward,  
we will enter the **actual anomalies observed in 0.25 µm generation DRAM**.

First, we will address only  
**what was happening**.

The causes and interpretations will follow later.
