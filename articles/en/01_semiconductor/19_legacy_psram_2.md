---
layout: default
title: Legacy psram2
---

# 【Semiconductor】19. What Happened to PSRAM, and Why Did It End?  
## — The Reality of Pause × Disturb
topics: ["Semiconductor", "PSRAM", "DRAM", "Reliability", "Yield"]

---

## 🧭 Introduction

In the previous article, we organized how PSRAM was built upon the following  
**structure and assumptions**:

- Using DRAM cells  
- Employing internal refresh control  
- Presenting itself as SRAM-like to the outside  

In this article, we record  
**what actually happened under those assumptions**,  
and **what decisions were ultimately made**.

---

## ⚠️ Failures That Surfaced in PSRAM

The failures that became problematic in PSRAM  
can be broadly classified into two types:

- **Pause Refresh Fail**
- **Disturb Refresh Fail**

Both were already known phenomena in DRAM,  
but in PSRAM the decisive difference was that  
**they appeared simultaneously depending on usage conditions**.

---

## ⏸ Pause Refresh Fail (PSRAM)

In PSRAM, the following conditions tended to overlap:

- Long standby periods  
- Intermittent internal refresh  
- Operation in high-temperature environments  

As a result,

> **Leakage that did not surface in DRAM  
> appeared directly as retention failure**

This was not:

- A new physical phenomenon  
- A new defect  

It was fundamentally the same as  
the **Pause Refresh anomaly already observed in 0.25 µm DRAM**.

---

## ⚡ Disturb Refresh Fail (PSRAM)

The other problem was **Disturb**.

In PSRAM, the following **usage patterns** occurred routinely:

- Access concentrated on specific addresses  
- Other regions remaining idle for long periods  

As a consequence, the following coexisted on the same chip:

- Frequently toggled word lines  
- Cells left untouched for extended durations  

---

## 🧬 Cross-Sectional Structure Where Disturb Occurs (Reference)

Here, we present  
the **physical device cross-section**  
necessary to understand Disturb in PSRAM.

<p align="center">
  <img
    src="https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/figs/disturb.png"
    width="55%">
</p>

<p align="center">
  <em>
    Figure 1: Conceptual cross-section of leakage and electric-field concentration  
    during Disturb events in PSRAM (using DRAM cells)
  </em>
</p>

What this figure illustrates are  
**well-known physical effects**, such as:

- Electric-field concentration during word-line switching  
- Increased I<sub>off</sub> due to short-channel effects in cell MOS transistors  
- Amplified leakage at diffusion edges and isolation boundaries of adjacent cells  

Disturb operates not as:

> **a one-time destructive event**,  

but as:

> **a phenomenon that accumulates minute degradation over time**.

---

## 🔗 Coupling of Pause × Disturb

The critical point is that  
**Pause and Disturb were not fatal when acting alone**.

- Pause by itself  
- Disturb by itself  

were both contained within guaranteed conditions.

The problem arose when:

> **the two became coupled along the time axis**

In that case:

- Disturb gradually eroded cell state  
- Pause provided no opportunity for recovery  
- High temperature exponentially accelerated leakage  

Through this chain,  
failures increased **at a boundary** rather than gradually.

---

## 🌡 Temperature as a Boundary Condition

The failure behavior of PSRAM  
**changed character abruptly when a temperature boundary was crossed**.

- Up to ~85 °C: failures were almost nonexistent  
- At 90 °C (guaranteed point): conditionally acceptable  
- Above 95 °C: failures increased sharply  

Failures did not:

- Increase slowly  
- Degrade progressively  

Instead, they:

> **appeared the moment a certain condition was exceeded**

This was a **boundary phenomenon**.

---

## 🛠 What Yield Recovery Could and Could Not Achieve

Mass production could not be halted.

Therefore,  
**short-term feasible countermeasures** were implemented.

### Implemented Measures

- Reduction of process-induced damage  
- Suppression of junction leakage  
- Optimization of back-bias conditions  
- Redefinition of test conditions  

As a result:

- Initial yield: ~30%  
- Post-recovery yield: **on the order of 70–80%**

---

## 🧱 Limits That Still Remained

However, the following did not change:

- Extremely thin high-temperature margin  
- Persistent dependence on usage patterns  
- Further degradation with continued scaling  

These were not due to:

- Insufficient improvement  
- Implementation mistakes  

They were **structural limitations**.

---

## 🧭 The Decision That Was Made

The final decision was unambiguous.

> **Even if a technology can be made to work,  
> it should not be continued if it cannot scale long-term**

- PSRAM became manufacturable  
- But it could not be carried into future generations  
- Return on investment could not be justified  

As a result:

> **Withdrawal from the PSRAM roadmap**

was chosen.

---

## 🧾 Summary (Failures and Decision)

PSRAM was:

- Not a failed technology  
- But not a sustainable one either  

The limits were created by  
**the coupling of well-known physics—  
Pause × Disturb × temperature—  
through the way the memory was used**.

This was not:

- A design failure  
- An implementation error  

It was a record of:

> **assumptions exceeding the range that could be tolerated**

---

## 🔗 Primary Sources (References)

- Legacy Technology Archive  
  [https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/](https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/)

- PSRAM (2001) Cases  
  [https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/psram_2001/](https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/psram_2001/)

- Pause / Disturb in PSRAM  
  [https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/psram_2001/pause_disturb_psram/](https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/psram_2001/pause_disturb_psram/)

- Yield Recovery  
  [https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/psram_2001/yield_recovery/](https://samizo-aitl.github.io/Edusemi-Plus/archive/legacy/psram_2001/yield_recovery/)

---

### ✅ Series Complete

- 0 Introduction  
- 1 DRAM Part 1 (Phenomenology)  
- 2 DRAM Part 2 (Physics)  
- 3 PSRAM Part 1 (Structure)  
- 4 PSRAM Part 2 (Failures and Decision)

**All five articles are now complete.**
