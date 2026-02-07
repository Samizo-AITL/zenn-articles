---
layout: default
title: OpenLane PDK
---

# 【Semiconductor】🧩 14. What Makes a PDK Compatible with OpenLane?  
### — Why SKY130 Works Smoothly and GF180 Becomes Difficult
topics: ["openlane", "asic", "pdk", "sky130", "gf180"]

---

## 🧭 Introduction

When working with OpenLane, you inevitably encounter the following questions:

- Why does **SKY130** flow relatively smoothly?
- Why is **GF180 Open PDK** often harder to use in the same way?
- Is this a configuration problem—or a PDK issue?

In this article, we frame the answer as a **difference in design assumptions**.

To state the conclusion upfront:

> **GF180 is not “bad.”**  
> **Rather, the design world implicitly assumed by OpenLane  
> differs from the design world GF180 is optimized for.**

---

## 🧱 What Kind of Flow Is OpenLane? (Assumptions)

OpenLane is a **digital-only, fully automated flow** that integrates:

- RTL → logic synthesis  
- Automatic place & route (P&R)  
- Automatic STA / DRC / LVS  
- GDS generation  

into a **single, end-to-end pipeline**.

The key point is:

> OpenLane is **not a framework that generalizes all PDKs**

Instead, the flow implicitly assumes  
a certain **PDK structure and design philosophy**.

---

## 📋 PDK Conditions OpenLane Effectively Requires

PDKs that work “smoothly” with OpenLane tend to share common traits.

### 1. OpenPDK-Compatible Structure
- Well-organized `libs.ref` / `libs.tech`  
- Existing OpenLane configuration files (e.g., `config.tcl`)  
- Standard-cell–centric view hierarchy  

### 2. Digital Standard-Cell Assumptions
- Synthesis → P&R → STA flows consistently  
- No primary dependence on high-voltage or special-purpose cells  

### 3. Designed for Automation
- Minimal human intervention required  
- Flow assumes and absorbs certain “PDK behaviors”  

These are **implicit assumptions**, not formally specified requirements.

---

## ✅ Why SKY130 Works Well with OpenLane

The SKY130 PDK provides:

- OpenPDK-compatible structure  
- A strong focus on digital standard cells  
- Extensive use in education and PoC contexts  

In other words:

> **The design world assumed by OpenLane  
> aligns closely with the design world SKY130 was built for**

As a result, even with imperfect tuning,  
the flow often completes successfully.

---

## 🧠 Design Assumptions of GF180 Open PDK

GF180MCU Open PDK is optimized with a different philosophy.

### Characteristics of GF180
- High-voltage support (5V / 10V class)  
- Mixed-signal and analog use cases  
- Product-oriented, real-chip design focus  
- High design freedom  

From a PDK standpoint, this is **entirely healthy and correct**.

However:

> **It is not primarily designed for  
> fully automated, digital-only, one-click flows**

---

## ⚠ Why GF180 Becomes Difficult with OpenLane

This is not a binary “works / does not work” issue.

- Basic PDK setup and tests may succeed  
- But achieving an **RTL → GDS automatic flow  
  with the same ease as SKY130 is often difficult**

The reasons include:

- Partial mismatch with OpenLane’s assumed PDK structure  
- High-voltage and special cells conflicting with automation  
- Design decisions that the flow cannot automatically resolve  

In short, this is:

> **Not a configuration failure,  
> but a mismatch in design assumptions**

---

## ❗ On the Statement “GF180 Cannot Be Used with OpenLane”

This article frames the issue as follows:

- ❌ “GF180 cannot be used with OpenLane at all”  
- ⭕ “GF180 has a narrower applicability  
> for OpenLane-style fully automated digital flows”

This distinction matters.

GF180 excels in **a different design domain**,  
and this neither diminishes GF180 nor OpenLane.

---

## 🎯 Use Cases Where GF180 Excels

GF180 is well suited for:

- High-voltage drivers  
- Mixed-signal circuits  
- Custom-driven design flows  
- Product-oriented designs with strong human control  

👉 **Designer-driven design world**

---

## ⚙ Use Cases Where OpenLane Excels

OpenLane is strongest in:

- Education  
- Proof-of-concept designs  
- Digital-only implementations  
- Validation of automated flows  

👉 **Flow-driven design world**

There is no superiority here—  
**only different roles**.

---

## 🧭 The Correct Decision Axis for Designers

The most important judgment is:

- Do not force a PDK to fit a tool  
- Do not force a tool onto a PDK  
- **First check whether the design assumptions align**

> Choosing a PDK means choosing  
> **not just a process, but a design philosophy**

---

## 📝 Summary

- OpenLane is a digital automation flow  
- Compatible PDKs share implicit assumptions  
- SKY130 aligns well with those assumptions  
- GF180 is optimized for a different design world  
- “Difficulty” reflects boundary conditions, not failure  

With this understanding, designers can:

- Avoid overestimating OpenLane  
- Avoid misunderstanding PDKs  
- Make sound architectural decisions  

---

## 🧩 Closing

At this point, we have safely established three pillars:

1. OpenLane1: make it run once  
2. OpenLane2: manage the environment  
3. OpenLane × PDK: understand the assumptions  

This is not a tool tutorial,  
but a discussion about **where designers stand**.

When assumptions align,  
tools will always work in your favor.
