---
layout: default
title: FSM Design — Making Adaptive Control Explainable
---

# 【Control】🛡️ 13. FSM Design  
## Making Adaptive Control Explainable — What a Reliability Guard Really Is
topics: ["FSM", "control design", "reliability", "adaptive control"]

---

## ❌ “The AI Just Stopped It” Is the Worst Answer

There is one phrase that adaptive control must never produce.

> **“Why did it stop?”  
> “...the AI decided.”**

That answer is unacceptable in real systems.

If the reason cannot be explained,  
the control system cannot be trusted.

---

## 🧭 The Role of the FSM Reliability Guard

The FSM Reliability Guard is a **decision-only layer**.

It does *not*:

- Optimize  
- Learn  
- Compute control values  

It only does this:

> **Observe → Compare → Permit / Block**

Nothing more.

---

## 📏 What the FSM Actually Monitors

Typical monitored metrics include:

- $R_{\Delta t} = \Delta t / \Delta t_0$
- $R_{K_P} = K_P / K_{P0}$

These metrics are chosen because they are:

- Dimensionless  
- Ratio-based  
- Directly explainable from logs  

---

## 🔎 FSM Decisions Are Deterministic

FSM guard logic is explicitly defined.

```
if R_Δt > threshold:
    ADAPT_BLOCKED
```

Therefore, the system can always say:

> **“At this time, this value exceeded the threshold,  
> so adaptation was stopped.”**

This is not interpretation.  
It is execution of a rule.

---

## 🧯 Stopping Is the Correct Outcome

This is the core principle of the FSM Guard.

> **Stopping = not broken**

Only a control system that can stop adaptation  
can be used over long operational periods.

---

## 🔗 A-Type → B-Type → Robust Control

- **A-Type**: measure the limits  
- **B-Type**: protect the limits  
- **Robust Control**: operate within the limits  

The FSM Reliability Guard  
is the **bridge between all three**.

---

## ✅ Summary

- Adaptive control is not universal  
- Therefore, a stopping design is required  
- The stopping decision must be explainable via FSM  

> **Adaptive control becomes engineering  
> only when it can explain itself.**

---

*End of Article*
