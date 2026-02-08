---
layout: default
title: zenn-articles
---

# 【MEMS】🧠 01. Design Philosophy and Overall Architecture of *mems-ana*  
### A Lightweight ROM-Based Analysis Tool for MEMS

topics: ["MEMS", "analysis", "ROM", "Python", "simulation"]

---

## 📌 Introduction

In MEMS (Micro Electro Mechanical Systems) design,  
**analysis is indispensable** because structure, materials, and actuation methods are tightly coupled.

At the same time, rigorous FEM-based analysis often comes with drawbacks:

- Time-consuming model construction  
- Heavy parameter studies  
- Excessive complexity for early-stage design exploration  

This article introduces the lightweight MEMS analysis tool **mems-ana**, developed with these challenges in mind, and provides a **high-level overview** of:

- The design philosophy behind it  
- What it is intended to do  
- What it deliberately chooses *not* to do  

---

## 🧩 What Is mems-ana?

**mems-ana** is a **lightweight MEMS analysis tool based on Reduced Order Models (ROMs)**.

Its primary goals are:

- To **complement**, not replace, FEM  
- To support **sensitivity analysis and behavioral understanding** in early design stages  
- To serve as a tool for education, PoC development, and design thinking training  

Rather than pursuing maximum accuracy, mems-ana prioritizes:

> **Lightweight computation, speed, and structural interpretability**

---

## 🧮 Why ROM?

Many MEMS structures share common characteristics:

- Thin-film structures  
- Simple geometries (rectangular, circular)  
- A small number of dominant modes  

In such cases, displacement $u(x,y,t)$ can be expressed as:

$$
u(x,y,t) = \sum_{n} q_n(t)\,\phi_n(x,y)
$$

That is, the essential behavior can be captured by a **limited set of modes**.

mems-ana is built on this assumption:

- The number of modes is intentionally restricted  
- The system is reduced to **physically meaningful degrees of freedom**  

This enables a balance between computational efficiency and interpretability.

---

## 🔀 Division of Roles with FEM

mems-ana does not reject FEM.  
Instead, it emphasizes **clear separation of roles**.

| Aspect | mems-ana | FEM |
|---|---|---|
| Early-stage design | ◎ | △ |
| Sensitivity / trend analysis | ◎ | ○ |
| Higher-order modes | △ | ◎ |
| Local stress evaluation | × | ◎ |
| Computational cost | Light | Heavy |

mems-ana is a tool for answering:

> “Why does this structure behave this way?”

— **quickly and structurally**.

---

## ⚙️ What mems-ana Can Do (Overview)

mems-ana supports analyses such as:

- Natural frequencies and mode shapes (simplified)
- Voltage–displacement (V–u) characteristics
- Static and quasi-static response under piezoelectric actuation
- Visualization of spatial displacement distributions
- Time-domain response and animation

All of these are implemented with:

- Python-based code  
- Explicit modeling assumptions  
- A structure where equations and implementation remain traceable  

---

## 🚫 Deliberate Limitations (Important)

mems-ana includes **intentional constraints**:

- No nonlinear large-deformation analysis  
- No evaluation of local stress concentration  
- No attempt to reproduce all real-device phenomena  

Instead, it focuses on:

- Making assumptions explicit  
- Limiting the meaning of calibration parameters  
- Clearly defining the **valid operating range**  

> Deciding *what not to do* is a critical part of tool design.

---

## 🧩 Relation to Education, PoC, and AITL

mems-ana is not intended as a standalone solver.  
It is designed to be used in contexts such as:

- Educational tools (physics and design thinking)
- PoC evaluation of design ideas
- AITL (Architecture for Integrated Technology Logic), as a means of structuring design knowledge

In particular, mems-ana emphasizes:

- Human-interpretable models  
- Consistency from equations → implementation → visualization  

These are **prerequisites for intelligence and automation**, not optional extras.

---

## 🔗 GitHub Repository

The source code and demos for **mems-ana** introduced in this article are available at:

[https://github.com/Samizo-AITL/mems-ana](https://github.com/Samizo-AITL/mems-ana)

---

## 📚 About This Series

This article is the first installment in the **mems-ana series**.

- **01**: Design philosophy and overview (this article)  
- **02**: Visualization demos (piezo hysteresis and butterfly displacement)  
- **03**: Mathematical structure of `mems-ana_core` and ROM design  

The next article will focus on  
**“how it actually behaves”** through concrete visualization examples.

---

## 📝 Closing Remarks

mems-ana is designed not as:

> “a tool to produce the correct answer,”  

but as:

> **“a tool to think with.”**

If this article helps convey that lightweight analysis can be a valid and powerful option for early-stage design exploration and hypothesis testing, it has served its purpose.

---
