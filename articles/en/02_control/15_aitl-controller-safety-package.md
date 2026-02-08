---
layout: default
title: zenn-articles
---

# 【Control】🛡️ 15. (Safety Design) What Is a Safety Envelope?
## Designing the Boundary AI Control Must Never Cross
topics: ["control engineering", "AI", "safety design", "FSM", "anomaly detection"]

---

## ⚠️ Introduction: The Most Dangerous Thing in AI Control Is “No Boundary”

In discussions about AI-based control, the most dangerous situation is this:

> *“No one has clearly defined how far the AI is allowed to go.”*

Poor performance is not the real risk.  
**The absence of a boundary is far more dangerous.**

This article explains **Safety Envelope**,  
the core concept of the **AI Control Safety Package**.

---

## 🧱 What Is a Safety Envelope?

In one sentence, a Safety Envelope is:

> **“The operational boundary that AI must never violate.”**

The critical point is this:

**A Safety Envelope is not decided by AI.**

---

### 📐 What a Safety Envelope Defines

- Permissible state space  
- Allowed input/output ranges  
- Allowed transition rates  
- Allowed time constraints (dwell time, response delay)

These are **designed and fixed by humans**,  
intentionally limiting the degrees of freedom of AI.

---

## 🚫 Why AI Must Not Define Its Own Boundary

AI systems—especially LLMs—have the following properties:

- They generate statistically plausible outputs  
- They do not recognize failure as failure  
- They reinterpret boundary conditions on their own  

In other words:

> **You must never let the entity that is being judged for safety  
> define what “safe” means.**

---

## 🧯 A Safety Envelope Is Not a Performance Limiter

This is a common misunderstanding.

A Safety Envelope is **not** designed to restrict performance.

Its real purpose is:

- Stop before entering a dangerous region  
- Switch modes before physical damage occurs  
- Keep the system in a recoverable state  

It is **design insurance**, not optimization.

---

## 🧩 Fundamental Components of a Safety Envelope

### 🟦 ① State Variable Selection

First, define what must be monitored:

- Physical variables (position, velocity, voltage, current)  
- Internal control states  
- Estimation errors  
- Variability or magnitude of AI outputs  

Not “observe everything,” but  
**“observe signs of failure.”**

---

### 🟧 ② Boundary Definition

Next, define allowable limits:

- Hard limits that must never be crossed  
- Soft limits that trigger warnings  
- Time-dependent constraints  

Here, **conservatism is a virtue**.

---

### 🟨 ③ Deterministic Violation Detection

Detect approach or violation of the boundary:

- Threshold monitoring  
- Gradient / rate-of-change monitoring  
- Abnormal state transition detection  

The key rule:

> **Detection must be deterministic, not AI-driven.**

---

### 🟥 ④ FSM-Based Supervisory Control

A Safety Envelope becomes effective only when paired with FSM.

Explicitly design states such as:

- Normal  
- Warning  
- Safe Mode  
- Shutdown  

These transitions are **designed, not inferred**.

---

## 🔗 Relationship to PID × FSM × LLM Architecture

### ⚙️ PID (Inner Layer)

- Operates only inside the Safety Envelope  
- Stability is guaranteed by PID design  

---

### 🧾 FSM (Supervisory Layer)

- Detects envelope violations  
- Forces mode transitions  

---

### 🧠 LLM (Outer Layer)

- Analyzes *why* a violation occurred  
- Proposes design improvements  

**LLMs do not define boundaries.  
They do not enforce them.  
They do not supervise them.**

---

## ❌ Common Mistakes

### 🚫 Learning the Safety Envelope with AI

- Boundaries drift  
- Reproducibility is lost  
- Accountability disappears  

---

### 🚫 Treating the Envelope as “Reference Only”

- Violations do not stop the system  
- No one owns responsibility  

A Safety Envelope **must have enforcement power**.

---

## 🧠 Summary

- The Safety Envelope is the lifeline of AI control  
- Boundaries are designed by humans  
- Detection and switching are deterministic  
- AI supports only from the outside  

AI control is not dangerous by itself.  
**Failing to design boundaries is.**

---

## 🔜 Next Article Preview

Next, we will cover:

> **“Recovery Control: How to Return Safely After Failure.”**

In AI control systems,  
the real difference appears **after something goes wrong**.

---

## 📚 References

- AI Control Safety Package  
  [https://samizo-aitl.github.io/ai-control-safety-package/](https://samizo-aitl.github.io/ai-control-safety-package/)

---

*End of Article*
