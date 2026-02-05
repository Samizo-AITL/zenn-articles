---
layout: default
title: Why “Timing-Only Control” Fails Under Friction Aging
---

# 【Control:05】⏱️ Why “Timing-Only Control” Fails Under Friction Aging
topics: ["control engineering", "PID control", "reliability", "simulation"]

---

## Introduction

A control system is not acceptable simply because it “moves.”  
**In long-term operation, what breaks first is often *when* it moves—its timing.**

In this article, we compare:

- Conventional **PID control**
- **AITL control (FSM-based gain retuning)**

on a plant subjected to friction aging equivalent to **1000 days**, and show a case where:

> **A control strategy that appears successful actually collapses as a reliability control.**

---

## 🎯 Objective of the Experiment

The objective is **not accuracy improvement**.

> **Can response timing (Δt) be preserved under long-term degradation?**

This question is evaluated explicitly from a **Reliability** perspective.

---

## 🧪 Experimental Conditions (Key Points)

### Degradation Model
- Increase in Coulomb friction and static friction  
- Degradation level: **equivalent to 1000 days**

### Controllers Compared
- **Initial**: PID designed at day = 0  
- **PID_only**: fixed gains applied after degradation  
- **AITL**: FSM-based gain retuning (naive implementation)

---

## 📉 Results: Timing Degradation (Δt)

The comparison result is shown below.

![Timing degradation under friction aging](https://samizo-aitl.github.io/aitl-controller-a-type/data/pid_vs_aitl_friction_aging.png)

- **PID_only**
  - Response amplitude is preserved  
  - However, peak timing gradually drifts, accumulating Δt  

- **AITL**
  - Peak timing remains close to the initial response  
  - Δt is suppressed  

At first glance, AITL appears to be a “success.”

---

## ⚠️ But What Actually Happened

Closer inspection of the AITL response reveals:

- Reduced amplitude  
- Sluggish motion  
- Emergence of flat (inactive) regions  

In other words:

> **Timing was preserved at the cost of controllability.**

---

## ❓ Why Did This Happen?

The reason is straightforward.

- AITL optimized **only Δt (timing)** as its objective  
- Amplitude, saturation, and control effort were not evaluated  

As a result:

> **Timing-oriented retuning alone can collapse motion authority.**

This is not a bug—it is an **inevitable design failure**.

---

## 🧠 What Reliability Control Really Means

This result makes one thing clear:

**Reliability Control ≠ optimization of a single metric**

At minimum, the following must be considered jointly:

- Δt (timing)  
- Amplitude (controllability)  
- Saturation ratio (health margin)  
- Stability of retuning behavior  

Reliability Control is therefore a **constrained multi-objective design problem**.

---

## 🧩 Design Lessons Learned

- Preserving Δt alone does not constitute reliability control  
- Gain retuning is not mere tuning—it is a **design action**  
- FSMs must detect not only degradation, but also **overcorrection**

---

## That’s All for This Article

In this article, we clarified:

- Where naive AITL control **breaks down**
- What perspectives are essential for Reliability Control  

Next, we will move on to:

> **Designing a Reliability FSM with amplitude and saturation constraints**

---

## 🔗 References

- **GitHub (Code and Reproducible Environment)**  
  [https://github.com/Samizo-AITL/aitl-controller-a-type](https://github.com/Samizo-AITL/aitl-controller-a-type)

- **Detailed Analysis (GitHub Pages)**  
  [https://samizo-aitl.github.io/aitl-controller-a-type/docs/reliability/demo_friction_aging_analysis.html](https://samizo-aitl.github.io/aitl-controller-a-type/docs/reliability/demo_friction_aging_analysis.html)
