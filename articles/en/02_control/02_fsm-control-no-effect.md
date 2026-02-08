---
layout: default
title: zenn-articles
---

# 【Control】⚠ 02. A Case Where FSM-Based Control Did Not Work
topics: ["control", "FSM", "PID"]

---

## Introduction

We examined a control configuration in which  
**FSM (Finite State Machine)–based supervisory control**  
was added on top of a discrete-time PID control system.

To state the conclusion upfront:

> **Under the tested conditions, no clear benefit from FSM control was observed.**

This article documents that result and provides brief analysis.

---

## 🔧 What Was Done

The evaluated configuration was as follows:

- Continuous-time plant  
- Discrete-time PID control (with ZOH assumption)  
- Introduction of sampling-period jitter  
- Consideration of disturbances occurring **between samples (intersample)**  
- Placement of an FSM as a supervisory layer to switch control modes  

The FSM monitored the following indicators:

- Growth of control error  
- Oscillatory tendencies  
- Variations in control input magnitude  

---

## 🎯 Expected Behavior

Initially, we expected the following:

- FSM intervention when sampling conditions deteriorated  
- Mode switching during performance degradation  
- Overall improvement compared to PID-only control  

---

## 📉 Actual Results

The observed results were:

- In many cases, **the FSM was not triggered at all**  
- Even when the FSM was triggered, no clear performance improvement was observed  
- In most conditions, behavior was similar to PID-only control  

At least under the tested setup:

> **We could not claim that “adding an FSM improved control performance.”**

---

## 🤔 Discussion

### Intersample Disturbances Are Outside the FSM’s Scope

Disturbances occurring between samples  
are phenomena that alter system states in **continuous time**.

Since an FSM can only make decisions at sampling instants, it cannot:

- Directly suppress such disturbances  
- Respond immediately at the moment they occur  

This is not a design mistake, but a **structural limitation of FSM-based control**.

---

### FSM Silence Is Not Necessarily a Failure

An FSM is not a device that must always react to every situation.

If:

- Control assumptions have not yet collapsed  
- The lower-layer PID can still handle the disturbance  

then it is natural for the FSM to remain inactive.

From this perspective, the result can also be interpreted as:

> **The FSM correctly avoided unnecessary intervention.**

---

## 🧾 Summary

- FSM-based control was tested, but no clear benefit was observed under the given conditions  
- Intersample disturbances are not problems that FSMs can directly address  
- FSMs are not devices for improving control performance, but mechanisms for operational judgment  
- When applied outside their proper scope, FSMs may appear to “not work”  

FSMs and supervisory control are not universal solutions.  
**Identifying their effective scope is itself part of the design process.**

---

## 📝 Closing Remarks

Although this is a “case where it did not work,”  
the result is still valuable for future design decisions.

For those considering similar architectures,  
this may serve as a reminder **not to overestimate what FSM-based supervision can achieve**.
