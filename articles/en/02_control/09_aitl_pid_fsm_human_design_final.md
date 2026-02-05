---
layout: default
title: Design Guidelines for Reliability Control Completed by PID × FSM × Human Design
---

# 【Control:09】Design Guidelines for Reliability Control Completed by PID × FSM × Human Design
topics: ["PID", "FSM", "control engineering", "reliability design", "system design"]

---

# Design Guidelines for Reliability Control Completed by PID × FSM × Human Design  
— Final Consolidation of AITL B-Type Control

---

## 🧭 1. The Destination of This Series

Throughout this series, we have examined PID control, FSMs, reliability control,  
and long-term degradation to clarify one central question:

**What should be automated, and what must remain a human decision?**

The conclusion is surprisingly simple:

> **PID performs control,  
> FSM performs judgment,  
> gains are decided by humans.**

With this, reliability control is complete.

---

## ⚙️ 2. Why PID Remains the Primary Controller

PID control is classical and not academically novel.  
Yet in real-world systems, it remains unmatched due to:

- High stability  
- Simple implementation  
- Debuggability  
- Explainability  

The most critical factor is **explainability**.

In real products, any control behavior that cannot be explained  
will not be accepted.

PID remains the optimal solution in this regard.

---

## 🚦 3. FSM Is Not “Control” — It Is Judgment

FSMs are often misunderstood as:

- Switching optimal controllers per state  
- Acting as an intelligent controller  

However, as demonstrated in this series,  
**systems become fragile when FSMs actively control behavior.**

The correct role of an FSM is strictly limited:

> **To judge whether the system is still in a normal state  
> or has deviated from its expected behavior.**

An FSM must not:

- Compute gains  
- Optimize performance  
- Learn dynamically  

It is a **supervisory judgment layer only**.

---

## 📐 4. Thresholds Are a Design Philosophy, Not Just Numbers

The “10%” threshold appears repeatedly in this series.  
But the number itself is not the essence.

What truly matters is:

- Having a **reference baseline (initial response)**  
- Making decisions based on **deviation**, not absolutes  
- Switching behavior once a boundary is crossed  

The threshold could be:

- 5%  
- 10%  
- 20%  

That value is a **design parameter**,  
chosen by engineers based on system, application, and safety requirements.

> This design does not advocate “10% control.”  
> It advocates **explicitly designing thresholds**.

---

## ⛔ 5. Gains Must Not Be Computed On-Site

When degradation progresses, it may seem elegant to  
“compute optimal gains on the fly.”

In real systems, this is dangerous:

- No reproducibility  
- No explainability  
- No quality assurance  

Therefore, B-Type control enforces a strict rule:

> **Gains are designed, verified, and approved offline.  
> They are never computed during operation.**

The FSM only decides  
**whether to apply a pre-approved gain set or not**.

---

## 🤖 6. The Proper Role of LLMs

Large Language Models are powerful,  
but they do not need to be embedded into control loops.

In this design, LLMs are limited to:

- Assisting gain design  
- Organizing degradation scenarios  
- Verbalizing design rationale  

Final decisions are always made by **human engineers**.

> **LLMs are advisors, not decision-makers.**

This boundary is what makes the design usable in practice.

---

## 📚 7. Accepting the Gap Between Academia and the Field

This design is not academically cutting-edge.

- No strict optimality proofs  
- Thresholds are experience-based  
- Human judgment is explicitly involved  

Yet this is precisely why it works in the field:

- It is explainable  
- It is robust  
- It supports long-term operation  

This is not a weakness.

> **Designs strong in papers and designs strong in the field  
> are not the same.**

This series deliberately chose the latter.

---

## 🧩 8. Why This Is “Complete”

Beyond this point:

- Smarter FSMs lead to fragility  
- More automation blurs responsibility  
- More theory increases distance from the field  

So we stop here.

> **PID controls,  
> FSM judges,  
> humans design.**

With this three-layer structure,  
reliability control is fully realized.

---

## 📣 9. A Final Message to the Reader

This article does not claim to present the only correct answer.  
However, it can confidently state this:

> **This is a design endpoint that can be used to the end in real systems.**

Nothing more needs to be added.  
Nothing needs to be removed.

Design is also the act of  
**deciding where to stop**.

This is that stopping point.

---

*End of Final Article*
