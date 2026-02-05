---
layout: default
title: What Reliability Control Needed Was Not “Going Faster,” but Knowing When to Stop
---

# 【Control:06】🛑 What Reliability Control Needed Was Not “Going Faster,” but Knowing When to Stop
topics: ["control engineering", "PID control", "reliability", "FSM", "simulation"]

---

## Introduction (Continuation from the Previous Article)

In the previous article, we demonstrated that:

> **Under friction aging, control strategies that preserve only timing (Δt) inevitably fail.**

Through a comparison between:

- Conventional **PID control**
- **AITL control (FSM-based retuning)**

we reached a clear conclusion:

- AITL can detect delay and compensate for it  
- But at the cost of **losing amplitude (controllability)**  
- This was not a bug, but an **inevitable design consequence**

In this article, we go one step further and ask:

> **What was actually missing for “Reliability Control”?**

---

## ❌ The Problem Was Not “Retuning”

First, to avoid misunderstanding:

The AITL implementation in this study did succeed in:

- Detecting degradation  
- Performing retuning  
- Improving response in some aspects  

Yet it **still failed as reliability control**.

The reason turned out to be very simple.

---

## 🧠 What Was Missing Was the Ability to “Stop”

The FSM logic in AITL was essentially:

- Detect degradation  
- Strengthen gains  
- Bias the response toward faster timing  

However, one critical question was never asked:

> **Did this retuning actually improve reliability?**

That judgment was completely absent.

---

## 📊 What Was Actually Happening (Numerical View)

Let us revisit the results under friction aging equivalent to 1000 days.

```
Controller | Δt mean [s] | |Δt| [s] | Amp ratio
----------------------------------------------
PID_only  |   -0.4730   |  0.4730 |  0.902
AITL      |   -1.3807   |  1.3807 |  0.888
```

- AITL attempted to cancel delay  
- But **|Δt| actually worsened**  
- The amplitude ratio **fell below the safe threshold (0.9)**  

In other words:

> **A well-intended retuning action was actively degrading reliability.**

---

## 🧩 The Concept of a Reliability FSM

This led to the introduction of a new idea:

> **An FSM that judges whether retuning is allowed at all.**

The principle is extremely simple.

---

## 🔁 Three States Are Sufficient

The FSM only needs three states:

- **OK**: within acceptable range  
- **LAG**: excessive delay  
- **LEAD**: excessive advance  

The key insight is:

> **LEAD (too fast) must also be treated as degradation.**

---

## ⚠️ “Too Fast” Is Also an Abnormal Condition

From a traditional control engineer’s intuition:

- Delay → bad  
- Faster response → good  

But from a reliability perspective, this is incorrect.

An overly advanced response:

- Increases saturation risk  
- Reduces effective amplitude  
- Erodes future degradation tolerance  

Thus:

> **LEAD is a form of hidden reliability degradation.**

---

## 🛡 Guard Conditions as a Design Decision

The following guard condition was added to the FSM:

- **Amplitude ratio A/A₀ < 0.9**  
  → Gain strengthening **forbidden**

The resulting behavior was:

```
AITL | State = LEAD
     | Amp ratio = 0.888
     | Action = BLOCK
```

This enabled the system to decide:

> **“Any further adjustment will break reliability.”**

---

## 💡 The Most Important Insight

The core lesson from this study is:

> **Reliability control is not about continuously improving performance,  
> but about stopping before things get worse.**

---

## ❓ Did AITL Fail?

No.

The AITL implementation (A-Type):

- Successfully demonstrated adaptive control  
- But did not yet reach reliability control  

This is not a failure, but a clear design milestone:

> **It clarified where adaptive control ends and reliability control begins.**

---

## ▶ What Comes Next

At this point, the following have become clear:

- Optimizing Δt alone is dangerous  
- Amplitude and saturation must be included  
- Retuning requires **rejection and rollback mechanisms**

The next step is therefore:

> **Designing a new AITL (B-Type)  
> with Reliability as the explicit objective function**

---

## Summary

- Preserving timing alone does not constitute reliability control  
- Adaptive control and reliability control are fundamentally different  
- Reliability control requires the ability to **stop**  
- FSMs are not only for “acting intelligently,”  
  but also for **deciding not to act**

---

## 🔗 References

- **Reproducible Code and Environment**  
  [https://github.com/Samizo-AITL/aitl-controller-a-type](https://github.com/Samizo-AITL/aitl-controller-a-type)

- **Detailed Analysis (GitHub Pages)**  
  [https://samizo-aitl.github.io/aitl-controller-a-type/docs/reliability/](https://samizo-aitl.github.io/aitl-controller-a-type/docs/reliability/)

---

👉 Next Preview  
**“PID vs AITL Through Reliability Cost — Why ‘Ordinary PID’ Still Wins”**
