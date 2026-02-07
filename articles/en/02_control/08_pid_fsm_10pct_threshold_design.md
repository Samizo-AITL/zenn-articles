---
layout: default
title: The Rationale Behind the “10% Rule” for Introducing FSM into PID Control
---

# 【Control】🧯 08. The Rationale Behind the “10% Rule” for Introducing FSM into PID Control
topics: ["control", "PID", "FSM", "reliability design", "industrial control"]

---

## Introduction

Designs that overlay an FSM (Finite State Machine) on top of PID control  
often *look* theoretically sound.

However, in real products and industrial systems,  
**there are many documented failure cases**.

This article explains:

- Why continuously active FSMs are dangerous  
- Why **10% deviation** is a rational trigger threshold  
- Why a **Reliability Guard (B-Type)** is indispensable  

—all from the perspective of **commercially viable control systems**.

---

## 🧱 Fundamental Policy (Get This Wrong and Everything Breaks)

Control layers must be strictly separated:

1. **PID: Primary control (always active)**  
2. **FSM: Exception handling (emergency only)**  
3. **Reliability Guard: Suppression of FSM overreach**

FSM is *not* “smart control.”  
FSM is **insurance**.

---

## ❌ Why FSM-First Designs Fail

When dealing with friction aging or long-term degradation:

- FSM switching continuously  
- State transitions triggered by small fluctuations  

such designs almost inevitably cause:

- Waveform discontinuities  
- Overcompensation  
- State-transition chatter  
- Customer complaints like:  
  > “Something feels… off.”

The end result is ironic:

> **The FSM damages the system more than the degradation itself.**

---

## ⏱ When *Should* FSM Activate?

The answer is simple:

> **Only when PID can be quantitatively proven  
> to no longer behave like the original PID.**

This requires **numerical triggers**, not intuition.

---

## 📉 Why “10%”?

### A Boundary That Emerged Naturally from the Degradation Model

In the friction-aging models used throughout this series:

- Continuous operation with PID alone  
- Approximately **5 years of equivalent degradation**  
- Produced about **10% deviation from the initial waveform**

Clear divergence appeared in at least one of:

- Amplitude  
- Phase (time delay Δt)  
- Control energy  

This **10% threshold** is:

- Not a rule of thumb  
- Not a convenient heuristic  

> **It is a boundary that emerged naturally from simulation results.**

---

## 📏 10% of *What*, Exactly?

FSM triggering is defined using an **OR condition**.

FSM activates if **any** of the following exceeds  
**10% relative to the initial PID response**:

- Amplitude deviation  
- Phase / timing deviation (Δt)  
- Control energy deviation  

### Why OR, Not AND?

Because AND conditions are **too slow in real systems**.

---

## ⚠ Reality Degrades Faster Than Models Predict

In actual equipment:

- Wear  
- Contamination  
- Temperature variation  
- Partial damage  

can compress what looks like  
“5 years of model degradation”  
into **a few months**.

Without OR conditions,  
**FSM intervention comes too late**.

---

## 🛑 The Role of B-Type (Reliability Guard)

FSM is not infallible.

FSM intervention can easily:

- Worsen control quality  
- Destabilize output  
- Cause excessive current or voltage  

This is **not rare**.

Therefore, B-Type introduces:

- Limits on FSM authority  
- Continuous monitoring of effort and efficiency  
- Rollback to PID dominance if reliability degrades  

In other words:

> **FSM itself must not be trusted blindly.**

---

## 🧾 The “10% Rule” from a Product Perspective

From a customer’s point of view:

- Years of stable PID behavior → no issue  
- Correction only after visible degradation → acceptable  
- Behavior changing from day one → distrust  

The **10% rule** is critical because it is:

- Explainable  
- Documentable in specifications  
- Defensible in customer support  

---

## Summary

- PID is the main actor  
- FSM is for emergencies  
- 10% is a model-derived, realistic threshold  
- FSM triggers use OR conditions  
- Reliability Guard constrains FSM behavior  

FSM is not intelligence.  
FSM is **insurance — the last line of defense**.

---

## Closing Remarks

If FSM is active from day zero,  
the PID design has likely failed.

If FSM activates **only after a 10% deviation**,  
that behavior is **correct for a commercial product**.
