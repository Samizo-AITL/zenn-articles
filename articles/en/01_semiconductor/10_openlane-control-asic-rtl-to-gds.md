---
layout: default
title: OpenLane
---

# 【Semiconductor:10】🧩 What You Learn by Building a Control ASIC  
### — From RTL to GDS Using OpenLane
topics: ["OpenLane", "ASIC", "RTL", "Control Engineering", "SKY130"]

---

## 🧭 Introduction

This article is **not** a tutorial on how to use OpenLane.  
Nor is it merely a “tool verification log.”

It is a **record of a digital control ASIC design**,  
using a control system (PID) as the subject,  
that was actually completed end-to-end from **RTL to GDS**,  
together with a **verbalization of the design decisions** made along the way.

---

## ❓ Why ASIC Instead of an MCU?

MCUs are the common choice for implementing control systems.  
However, MCU-based control has inherent limitations:

- **Control-cycle jitter** caused by interrupts  
- **Loss of reproducibility** due to firmware updates  
- **Implicit state transitions** that are hard to observe  

In this project, these issues were avoided by  
**hardwiring the control logic itself**.

With an ASIC:

- The control cycle is **perfectly fixed**  
- State transitions are **explicitly defined as an FSM**  
- Latency is **provable at the cycle level**  

This is critically important for safety-critical  
and industrial control applications.

---

## 🏗 Adopted Architecture

The designed control ASIC consists of:

- A **PID controller** (fixed-point arithmetic)  
- **FSM-based supervisory control**  
- **PWM generation logic**  
- Single-clock, fully synchronous design  

The key is the hierarchy:

- Inner loop: PID (numerical computation, cycle guarantee)  
- Outer loop: FSM (INIT / RUN / FAULT)

This separation allows:

> *Clear role division between “control performance” and “safety”*

---

## 🔢 The Reality of Fixed-Point Design

Control theory is written in real numbers,  
but in an ASIC, everything is **finite bit-width**.

The critical issues are:

- Selection of Q-format  
- Bit growth in multiply–accumulate operations  
- Placement of saturation logic  

Many problems only become visible  
**after translating theory into actual RTL**.

In this project, the following rules were strictly enforced:

- Decide numerical ranges first  
- Always handle overflow explicitly  
- Never accept “it seems to work”  

---

## 🧰 What Using OpenLane Revealed

OpenLane is powerful—but it is not magic.

### 👍 Strengths

- Fully reproducible **RTL → GDS** flow  
- Integrated STA / DRC / LVS  
- Excellent for educational use  

At the same time, real constraints only become clear through practice.

---

## ⏱ How Gate-Level Simulation Was Handled

There are two types of gate-level simulation:

- **Functional (logic-only)**  
- **Timing-aware (with delays)**  

SKY130 standard cells heavily rely on  
UDP (User Defined Primitives),  
making full gate-level simulation difficult with Icarus Verilog.

In this project, responsibilities were clearly divided:

- RTL simulation → **functional verification**  
- STA → **timing guarantee**  
- Gate-level simulation → **investigation and reference only**

> Choosing *not* to run full gate-level timing simulation  
> can be a **correct design decision**.

---

## 📦 Deliverables

All results of this project are publicly available.

- 📘 **Design Documentation (GitHub Pages)**  
  [https://samizo-aitl.github.io/vi-control-asic-sky130/](https://samizo-aitl.github.io/vi-control-asic-sky130/)

- 💻 **RTL and OpenLane Flow (GitHub)**  
  [https://github.com/Samizo-AITL/vi-control-asic-sky130](https://github.com/Samizo-AITL/vi-control-asic-sky130)

The documentation includes, without omission:

- Control models  
- Fixed-point design decisions  
- RTL implementation  
- Verification results  
- GDS generation  

---

## 📝 Summary

OpenLane is an EDA tool,  
but fundamentally it felt like a **tool for sharpening design literacy**.

- What to do  
- What *not* to do  
- Why those decisions were made  

Only when these can be explained  
does an ASIC design truly feel “complete.”

If this article helps those interested in  
**the boundary between control engineering and hardware design**,  
it has achieved its purpose.
