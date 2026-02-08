---
layout: default
title: zenn-articles
---

# 【Semiconductor】🟢 04. GAA Structure  
### — The Completed Form of Electric-Field Control
topics: ["GAA", "Nanosheet", "MOSFET"]

---

## 🧭 Introduction

Planar MOSFETs reached a dead end due to SCE,  
and FinFETs restored electric-field control through **geometry**.

So what does the next step,  
**Gate-All-Around (GAA)**, truly represent?

In this article, GAA is positioned as:

> **Not an extension of scaling technology,  
> but the “completed solution” to electric-field control as a design problem**

---

## 🧩 Positioning of GAA

GAA is often described as  
“the next-generation structure after FinFET.”

However, from a physical standpoint, GAA is:

- Not an improved FinFET  
but  
- **A structure that operates at a higher design level**

If FinFET is a structure that *increased* gate enclosure,  
then GAA is:

> **A structure designed from the outset with 100% enclosure as a premise**

---

## 🧱 Structural Characteristics

The basic structure of GAA is as follows:

- Channel: nanowire / nanosheet  
- Gate: fully surrounds the channel  
- Source and drain: connected vertically  

This configuration results in:

- Channel potential constrained on all sides  
- Extremely limited paths for drain electric-field intrusion  
- Subthreshold characteristics approaching ideal behavior  

---

## 🔒 Why GAA Is Close to a “Final Form”

The essence of SCE has consistently been:

> **Electrodes other than the gate  
> dominating the channel potential**

In GAA structures:

- The gate is adjacent to the channel in all directions  
- There is virtually no escape path for the electric field  
- The potential distribution is almost entirely defined by gate boundary conditions  

In principle, this means:

> **There is very little room left to further strengthen gate control**

In this sense, GAA represents:

> **A structure extremely close to the theoretical limit  
> of electric-field control**

---

## 📐 Extension of Weff in GAA

In FinFETs, Weff was determined by:

- Fin height  
- Fin width  
- Number of fins  

In GAA, Weff becomes even more explicitly defined by:

- **Sheet width**  
- **Number of stacked sheets**

Conceptually:

```
Weff ≒ Sheet width × Number of sheets
```

The critical point here is that:

> **Weff has become purely an accumulated structural quantity**

---

## 🛠 Where Did Design Freedom Move?

In the GAA era:

- Gate length  
- Gate oxide  
- Electric-field control  

are already close to being “fully optimized.”

As a result, design freedom has shifted almost entirely to:

- Sheet width  
- Sheet thickness  
- Number of stacked sheets  
- Sheet-to-sheet spacing  

These are **three-dimensional structural parameters**.

This signifies that:

> **Electrical characteristic design has fully transitioned  
> into structural design**

---

## 🎯 The Design Philosophy Reached by GAA

GAA is not:

- A means to achieve further scaling  
but rather  
- **The definitive solution to making electric-field control fully valid**

In this structure, discussions such as:

- “How to suppress SCE”  
- “How to further reduce voltage”  

are no longer the central theme.

Instead, the focus shifts to the **next set of physical constraints**:

- Quantum effects  
- Thermal transport  
- Manufacturing variability  
- Mechanical stability  

---

## 📝 Summary

- ✅ GAA is not an extension of FinFET, but a structure at a different level  
- ✅ Full gate enclosure brings electric-field control close to its theoretical limit  
- ✅ Weff has become a completely structure-dependent parameter  
- ✅ The design battlefield has shifted from electric fields to **3D geometry**  

GAA can be described as:

> **The structure in which MOSFETs  
> have fully answered the challenge of electric-field control**

---

## 📚 References and Related Links

### 📘 Edusemi-v4x | Advanced Node Technologies (FinFET, GAA, CFET)

- **GitHub Pages (Public Educational Material, Japanese)**  
  [https://samizo-aitl.github.io/Edusemi-v4x/f_chapter1_finfet_gaa/](https://samizo-aitl.github.io/Edusemi-v4x/f_chapter1_finfet_gaa/)

- **GitHub (Source Management, Markdown Manuscripts)**  
  [https://github.com/Samizo-AITL/Edusemi-v4x/tree/main/f_chapter1_finfet_gaa](https://github.com/Samizo-AITL/Edusemi-v4x/tree/main/f_chapter1_finfet_gaa)

### 📖 Related Chapter

- Planar MOSFET → FinFET → GAA → CFET  
  This article corresponds to **Special Chapter 1**,  
  which systematically explains the **evolution of electric-field control structures**.

---

*This article is positioned as an introduction that starts from  
the physical limits of planar MOSFETs (SCE) and explains  
why structural transitions were inevitable.  
It is recommended to read it together with the subsequent FinFET, GAA, and CFET articles.*
