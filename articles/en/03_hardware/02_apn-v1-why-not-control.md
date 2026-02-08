---
layout: default
title: zenn-articles
---

# 【Hardware】 🧱 02. aitl-physical-reference v1  
### — Why We *Still* Do Not Control

---

## 📌 Introduction

**aitl-physical-reference v1** is a board that deliberately stays at the point where  
it *looks* like it could be controlled — **but is not, yet**.

This is not because it is incomplete.  
It is a **design decision**.

Before introducing control,  
there is still physical reality that must be fixed.  
Version 1 exists to make that boundary explicit.

---

## 🔄 What Changed from v0 to v1

In v0, the following were fixed in the smallest possible form:

- Voltage is something to be measured  
- Current is something constrained by resistance  
- Physical boundaries are defined by the PCB outline  

v1 takes exactly one step further.

- Logical signals can now be **exported externally**  
- Observation points are **more explicitly defined**  
- But **behavior is still not defined**

It exposes a state that *feels* controllable,  
while **intentionally leaving it undefined**.

That tension is the point of v1.

---

## ❓ Why We Still Do Not Add Control

PID, FSM, AI-based control —  
all of them deal with **how outputs should change**.

But before that, the following must be fixed:

- What exactly is being measured  
- Whether the voltage and current are reproducible  
- Whether physical constraints (copper, layout) are respected  

Control is a **choice**.  
Physics is a **precondition**.

v1 chooses **not to add control**,  
so that this precondition cannot be ignored.

---

## 1️⃣ Schematic (v1): Logic Is Exposed, Behavior Is Not Written

![Schematic v1](https://samizo-aitl.github.io/aitl-physical-reference/docs/img/04_apn_sch_v1.png)

Logical signals are, for the first time, explicitly routed outside.

However:

- No state transitions are defined  
- No feedback loop exists  
- No time response is specified  

It allows the *illusion* of control,  
but control itself does not yet exist.

---

## 2️⃣ PCB Layout (v1): Copper Quietly Restricts Freedom

![PCB v1](https://samizo-aitl.github.io/aitl-physical-reference/docs/img/05_apn_pcb_v1.png)

Even as logic increases,  
current still flows **only on this copper**.

- Trace length  
- Return paths  
- Component placement  
- Board outline  

None of these can be bypassed by control logic.

**The degrees of freedom of control are silently constrained by physics.**  
This layout exists to make that visible.

---

## 3️⃣ 3D View (v1): The Object Exists, Control Does Not

![3D v1](https://samizo-aitl.github.io/aitl-physical-reference/docs/img/06_apn_3d_v1.png)

It has height.  
It has touchable components.  
It has measurable points.

And yet, this board  
**still does nothing**.

Here, we deliberately stop the misconception that  
“implemented” means “controllable.”

---

## 🧭 The True Nature of v1: A Boundary Definition Reference

**aitl-physical-reference v1** is:

- Not an MCU evaluation board  
- Not a control demo board  

It is a **reference that fixes the boundary between logic and physics**.

- Test Points define the *observation boundary*  
- Resistors define *physical constraints*  
- The PCB outline defines *the edge of the world*  

This is the board that draws the line  
**before control is allowed to step in**.

---

## 🧩 Position Within AITL

In AITL (Architecture for Integrated Technology Logic),  
the layers are explicitly separated:

- Physical layer  
- Logical layer  
- Adaptive layer  

v1 belongs entirely to the lowest layer.  
It is the **reference point of the Physical layer**.

Only after this layer is fixed  
do higher-level control and reasoning gain meaning.

---

## ⏭️ What Comes Next

In v2, **behavior** will be introduced for the first time.

- But still not AI  
- Still not optimization  

What comes first is:

> **Control that humans can fully explain**

---

## 🧾 Summary

Control was not added because  
there was still *physics left to fix*.

**aitl-physical-reference v1** is  
a design that deliberately pauses  
in order to move forward correctly.

Before control,  
physics must exist as it truly is.

v1 is the reference that marks that boundary.

---

## 🔗 Links

- GitHub Pages  
  [https://samizo-aitl.github.io/aitl-physical-reference/](https://samizo-aitl.github.io/aitl-physical-reference/)

- GitHub Repository  
  [https://github.com/Samizo-AITL/aitl-physical-reference](https://github.com/Samizo-AITL/aitl-physical-reference)

---
