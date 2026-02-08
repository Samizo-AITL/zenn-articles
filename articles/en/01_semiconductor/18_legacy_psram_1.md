---
layout: default
title: zenn-articles
---

# 【Semiconductor】18. What Was PSRAM Intended to Achieve?  
## — The Premise of Reusing DRAM
topics: ["Semiconductor", "PSRAM", "DRAM", "Memory", "Architecture"]

---

## 🧭 Introduction — Why Did PSRAM Become an Option?

Around the year 2000,  
a memory called **PSRAM (Pseudo-SRAM)** was introduced to the market.

Its external interface looked like SRAM,  
while DRAM cells were used internally.

In this article, we organize:

- **What PSRAM was intended to solve**
- **The structural assumptions** on which it was built

Discussions of failures and limitations are deferred to the **next article**.

---

## 📱 Background of PSRAM — Constraints of Mobile Systems

In the late 1990s,  
systems for mobile devices faced the following requirements simultaneously:

- A memory with **simple external control**
- **Extremely low standby power consumption**
- Cost kept **at the level of DRAM**

However, the available options at the time were polarized.

| Type | Characteristics |
|---|---|
| SRAM | High speed, simple control, high cost |
| DRAM | High density, low cost, complex control |

PSRAM was conceived to fill  
the **gap** between usability and cost.

---

## 🎯 The Core Concept of PSRAM

The central idea of PSRAM was extremely simple.

> **Keep the inside as DRAM,  
> but make it look like SRAM from the outside**

Rather than abandoning DRAM and creating a new type of cell,  
the premise was to **maximize reuse of existing DRAM technology**.

---

## 🏗 Key Points of the Internal Structure

### ① Using the DRAM Cell Array as Is

- The storage element is a **standard DRAM cell**
- High density and low cost are exactly those of DRAM

There is no special physical design  
unique to PSRAM at the cell level.

---

### ② Internal Refresh Control

The defining feature of PSRAM is that it:

- **Automatically executes refresh internally**
- Eliminates the need for external refresh control

As a result,  
it can be accessed externally **with the same ease as SRAM**.

---

### ③ An Access-Priority Control Policy

The internal control policy was:

- **Access takes priority** when requests are present
- **Batch refresh** is performed during idle periods

This choice was reasonable for mobile applications because it:

- Avoids access latency  
- Reduces average power consumption  

---

## 🧩 Assumed Usage Conditions

PSRAM was designed as a  
**memory dedicated to mobile applications**.

The assumed usage conditions were:

- Long standby periods  
- Intermittent access  
- High-temperature environments (up to ~90 °C)  
- Strict low-power requirements  

These differed clearly  
from the conventional usage patterns of DRAM.

---

## ⚖️ The Decisive Difference Between DRAM and PSRAM

The critical point here is the following:

> **PSRAM uses DRAM cells as-is,  
> but it is not used in the same way as DRAM**

- DRAM  
  - Is always refreshed at fixed intervals  
- PSRAM  
  - Refresh intervals **depend on usage patterns**

This difference would later take on major significance.

---

## ✅ A “Rational Design” for Its Time

The structure of PSRAM was:

- Not technically radical  
- Compatible with existing DRAM processes  
- Directly aligned with market requirements  

In this sense,  
it was **an extremely rational design for its time**.

At this stage, words such as:

- Failure  
- Limitation  
- Withdrawal  

had not yet become reality.

---

## 🧾 Summary (Structure)

PSRAM was a memory with a  
**clear and consistent objective**:

- Reuse DRAM technology  
- Provide the usability of SRAM  

- Not a special cell  
- Not based on special physics  
- Only the **usage model** was different  

The problem was that  
**this usage model quietly violated  
the physical assumptions of DRAM**.

---

## 🔗 Primary Sources (References)

- Legacy Technology Archive  
  [https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/](https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/)

- PSRAM (2001) Cases  
  [https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/psram_2001/](https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/psram_2001/)

- PSRAM Architecture  
  [https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/psram_2001/psram_architecture/](https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/psram_2001/psram_architecture/)

---

### ⏭ Next

In the next article,  
we will cover **the failures that actually surfaced in PSRAM**.

Why Pause and Disturb  
became problematic **in combination**.

No evaluation, no hindsight—  
**only the facts**.
