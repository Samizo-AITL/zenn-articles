---
layout: default
title: Adaptive Control Can Work, but Cannot Be Guaranteed — The Limit of A-Type
---

# 🧪 【Control:11】Adaptive Control Can Work, but Cannot Be Guaranteed  
## — The Reached Limit of A-Type
topics: ["control", "adaptive control", "PID", "FSM", "reliability"]

---

## 🧭 Introduction

Adaptive control is attractive.

- It tracks a degrading plant  
- It reduces manual tuning  
- It responds to environmental changes  

However, in real design practice, one question always arises:

> **“Can this really be used continuously and safely?”**

In this article, through quantitative evaluation using  
**AITL (PID × FSM × LLM) A-Type**, we clarify:

- What adaptive control **can do**
- And what it **cannot do** (its limits)

---

## 🧩 What Is AITL A-Type? (Minimal Definition)

AITL A-Type is a three-layer control architecture:

```
Inner Loop : PID (real-time control)
Middle Loop: FSM (mode switching)
Outer Loop : LLM (gain adjustment — Kp only in A-Type)
```

A-Type is *not* designed to win performance comparisons.

> **Its purpose is to measure  
> how far adaptive control behavior can actually hold.**

That is the role of A-Type.

---

## 🧱 Evaluation Conditions: Plant Aging (Equivalent to 1000 Days)

- Target: V–I current control system (RL model)
- Aging: Resistance increase (equivalent to friction aging)
- Aging level: Up to **1000 days equivalent**
- Disturbance: Step disturbance + noise

Controllers compared:

- Fixed PID
- PID × FSM
- **AITL (A-Type)**

---

## 📉 Waveforms Alone Are Not Enough

First, the waveform comparison.

![V–I current control demo](https://samizo-aitl.github.io/aitl-controller-a-type/data/12_vi_current_control_sales_demo.png)

Frankly, this figure alone does not reveal a clear winner.

- AITL appears to track the reference
- Fixed PID does not collapse either  

**That is exactly why another evaluation axis is required.**

---

## ⏱ Evaluation Metric: Δt (Recovery Time)

Let the disturbance occur at time $t_0$,  
and let $t_s$ be the time when the error returns within the tolerance band.

$$
\Delta t = t_s - t_0
$$

Δt directly reflects:

- Response speed
- Timing consistency
- Operational reliability

---

## 📊 Results: Adaptation Does Not Guarantee Δt

![Aging sweep metrics](https://samizo-aitl.github.io/aitl-controller-a-type/data/13_aging_sweep_delta_t.png)

### Observations

- As aging progresses, **Δt degrades for all controllers**
- AITL performs better in **moderate aging**
- Under severe aging, **Δt increases even with AITL**

The conclusion is clear:

> **Adaptive control does not guarantee  
> time-based reliability.**

---

## 🧠 This Is Not a Failure

What matters is that:

- The limit became **visible**
- The limit was **measurable**
- The limit can be **designed around**

> **An adaptive controller with a measurable limit  
> is far more usable than one with an unknown limit.**

---

## 🔭 The Next Question

> **“Then when should adaptation be stopped?”**

To answer that question,  
we introduce **B-Type (reliability-prioritized AITL)**.

The next article focuses on  
**the design of stopping itself**.

---

*End of Article*
