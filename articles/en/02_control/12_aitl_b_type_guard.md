---
layout: default
title: Reliability Design — Adaptive Control Is Usable Only When It Can Be Stopped
---

# 🛑 【Control:12】Reliability Design  
## Adaptive Control Is Usable Only When It Can Be Stopped — B-Type AITL
topics: ["control", "reliability", "FSM", "adaptive control"]

---

## ❗ The Biggest Misconception About Adaptive Control

There is a persistent misconception about adaptive control.

> **“If adaptation works, it should keep running.”**

The results of A-Type clearly deny this assumption.

- Adaptation **can** work  
- But **continuing it breaks reliability**

This leads to what is truly required:

> **A design that can decide to stop.**

---

## 🧱 What Is B-Type?

B-Type does not aim for performance improvement.

> **B-Type = an architecture where adaptation is permission-based**

Adaptation is not always ON.

It must be:

- Evaluated  
- Authorized  
- And stopped if conditions are violated  

---

## 👀 What Is Monitored Is Not Performance

B-Type does *not* monitor performance metrics.

Instead, it monitors:

- **Δt / Δt₀** (time reliability)
- **Kp / Kp₀** (compensation magnitude)
- Saturation and loss of authority

> **Not “Did it get faster?”  
> but “Is it starting to break?”**

---

## 🔐 Permission Logic (Minimal Specification)

Adaptation is permitted only when *all* of the following are satisfied:

```
Δt / Δt₀ ≤ threshold
Kp / Kp₀ ≤ threshold
```

If *any* condition is violated:

- Adaptation is stopped
- The system falls back to fixed PID

---

## 🧯 Fixed PID Is Not a Failure

This point is critical.

> **Fixed PID is not a failure.  
> It is the reliability floor.**

In B-Type design,  
“adaptation not allowed”  
is a **correct and expected outcome**.

---

## 🔁 Relationship to A-Type

| | A-Type | B-Type |
|---|---|---|
| Purpose | Demonstrate adaptation | Protect reliability |
| Adaptation | Always active | Conditional |
| Decision basis | Performance | Reliability |

> **A-Type is for experimentation.  
> B-Type is for operation.**

---

## 🔜 The Next Question

> **“Isn’t that decision a black box?”**

In the next article, we explain how  
**FSM-based Reliability Guards** provide  
**explicit and explainable reasons for stopping adaptation**.

---

*End of Article*
