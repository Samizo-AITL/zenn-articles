# 03_hardware / Hardware & Physical Control Articles Index

In this directory,  
**AITL (Architecture for Integrated Technology Logic)** is re-examined  
from the **physical and hardware layer**, with a clear focus on:

- **Why control is not yet possible**
- **Where control must not be applied**

This section exists to explicitly define the **non-controllable domain**  
that must be fixed *before* PID, FSM, or AI can safely operate.

---

## 📘 Physical References & Baseline Definitions

- [01 AITL Physical Reference](./01_aitl-physical-reference.md)

> Before designing control,  
> define **what “physical reality” is** and  
> **what serves as the reference point**.

---

## 🚫 Clarifying Why Control Is Not Yet Possible

- [02 Why APN v1 Is Not Control](./02_apn-v1-why-not-control.md)

> Distinguish between  
> **things that look like control**  
> and **what real control actually is**.

---

## 🧱 Hardware Architecture

- [03 Hardware Architecture v2 (Physical Layer)](./03_hardware_architecture_v2_physical_loop.md)

> Before software,  
> **physical placement, wiring, and responsibility separation**  
> already determine control feasibility and limits.

---

## ⚙ Physical Control and AITL

- [04 AITL Physical Control v3](./04_aitl_physical_control_v3.md)

> Define the **conditions, limits, and safety boundaries**  
> under which AITL can exist at the physical layer.

---

## 🧭 Positioning of This Directory

- **03_hardware**  
  - Deals with **physics, structure, and layout before control**
  - Explicitly defines the domains that  
    **PID / FSM / LLM must never touch**

- Paired with **02_control**  
  - 02 = Logical and control architecture  
  - 03 = Physical and embodied architecture  

> **The moment you try to control what cannot be controlled,  
> the system begins to fail.**

---

## 🔗 Related Directories

- [01_semiconductor / Semiconductor Fundamentals](../01_semiconductor/)
- [02_control / Control & AITL](../02_control/)

