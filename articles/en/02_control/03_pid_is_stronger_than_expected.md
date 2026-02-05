---
layout: default
title: PID Control Is More Complete Than You Think
---

# 【Control:03】🧠 PID Control Is More Complete Than You Think
topics: ["control engineering", "PID", "AI", "LLM", "robotics"]

---

## Introduction

As AI and LLM-based control attract increasing attention,  
many people—including myself—tend to think:

- “Traditional control theory may be approaching its limits.”  
- “AI could enable much smarter control.”  

With that expectation, I designed and implemented an  
**AITL (Adaptive / Intelligent Triple-Layer) control architecture**,  
combining **PID × FSM × LLM**, and evaluated it against a standalone PID controller  
using Python-based simulations.

The conclusion, stated plainly, was this:

> **Modern control theory—especially PID control—is far more complete and robust  
> than commonly assumed, and even with AITL, it is difficult to demonstrate  
> a clear advantage over a well-designed PID controller.**

This article documents that evaluation process  
and the sober conclusions drawn from it.

---

## 🔍 Why I Tried to Build AITL

The idea behind AITL is straightforward:

- **PID**: real-time control (inner loop)  
- **FSM**: state supervision and mode switching (middle loop)  
- **LLM**: redesign, re-identification, and decision support (outer loop)  

The underlying expectations were:

- “PID is fast but rigid.”  
- “FSM detects abnormal conditions.”  
- “LLM redesigns the controller instead of a human.”  

In particular, I expected benefits in systems with:

- Large disturbances  
- Long-term operation with changing characteristics  

---

## 🎯 Baseline: Implementing PID Properly

A critical point in this evaluation was **not to trivialize PID control**.

The baseline PID controller was implemented with:

- Full **P / I / D terms enabled**  
- Explicit disturbance inputs  
- Evaluation including divergence and saturation conditions  
- No artificial handicaps (e.g., setting I = 0)  

Under these conditions, a properly tuned PID controller showed:

- Robust disturbance rejection  
- Fast response  
- Clearly explainable behavior  
- Easy debugging and maintenance  

In short, **a well-designed PID controller is extremely strong**.

---

## 🧩 Adding AITL (PID × FSM × LLM)

Next, FSM and LLM layers were added:

- FSM: detects increased disturbances or degraded response  
- LLM: generates redesign strategies for PID gains  
- Re-identified PID is re-applied  

Structurally, this is sound.  
It simply **separates what humans already do**.

However, in practice, several issues emerged:

- Redesign introduces time delays  
- Design intent becomes opaque (black-box behavior)  
- Performance differences compared to PID alone  
  are not clearly visible in response plots  

---

## 📉 Results: No Clear Advantage

To be completely honest:

> **Under these conditions, no clear win over standalone PID was observed.**

From both performance and operational perspectives:

- Stability: PID alone was sufficient  
- Responsiveness: PID was faster  
- Explainability: PID was overwhelmingly superior  
- Maintainability: PID was far more practical  

---

## 🧠 Why PID Is So Strong

The reasons are straightforward:

- The theory is mature  
- Decades of field experience are embedded  
- Robustness is a first-class design goal  
- Behavior is mathematically explainable  

**A properly designed PID controller is already close to optimal**  
—that was the strongest takeaway from this study.

---

## 🌱 Where AITL Might Still Make Sense

This does not mean AITL is meaningless.

AITL may be valuable in contexts such as:

- Unmanned or remote systems  
- Long-term autonomous operation (space, deep sea, etc.)  
- Environments where frequent human redesign is impossible  
- Layers *outside* direct control performance (decision and reconfiguration)  

In other words:

> **AITL is not a technology to directly improve control performance,  
> but a framework for structuring design and decision-making.**

---

## 🧾 Conclusion

AI- and LLM-based control is appealing.  
But once implemented and compared honestly:

> **Modern control theory is already very strong.**

This is not a failure.  
It is the result of **testing reality against expectation**.

AITL should not be positioned as a replacement for PID,  
but rather as a **conceptual scaffold** to revisit  
when truly necessary.

---

## 📝 Closing Remarks

“AI will dramatically improve everything”  
—reality is not that simple.

But:

> **Trying it, and drawing a clear boundary,  
> is itself a meaningful engineering outcome.**

I hope this serves as a useful reference  
for others facing similar questions.
