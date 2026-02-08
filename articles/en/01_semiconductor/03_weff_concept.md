---
layout: default
title: zenn-articles
---

# 【Semiconductor】📐 03. Understanding Weff  
### — Width W Becomes a Structural Parameter
topics: ["Weff", "FinFET", "Circuit Design", "Device Modeling"]

---

## 🧭 Introduction

The transition from planar MOSFETs to FinFETs was not merely  
a change in device structure.

It fundamentally altered:

> **How circuit designers interpret and use “width W”**

In this article, we organize:

- 🔹 The meaning of W in the planar era  
- 🔹 The essence of Weff in FinFETs  
- 🔹 Why circuit design and layout became inseparable  

---

## 📏 Width W in the Planar Era

In planar MOSFETs,  
the channel width W was a **pure layout dimension**.

- W could be increased continuously in the lateral direction  
- L was fixed by the process; W was chosen by the designer  
- Current capability was roughly expressed as  
  **I ∝ (W / L)**  

In other words, circuit designers could:

> **Freely tune W/L as an electrical parameter**

In this era,  
layout was merely the *result* of circuit design,  
and current–voltage (I–V) characteristics were largely captured by equations.

---

## 🧱 Weff in FinFETs

With FinFETs, this assumption collapses.

This is because the channel is no longer a planar surface,  
but a **three-dimensional fin structure**.

As a result, the effective channel width  
is no longer an arbitrarily stretchable quantity, but:

> **A value determined by geometry (Weff)**

Conceptually:

```
Weff ≒ 2 × Hfin + Wfin
```

- The two sidewalls carry most of the current  
- The top surface (Wfin) is secondary  
- Hfin and Wfin are process-defined  

Thus:

> **Current capability (I–V behavior) directly depends on geometry itself**

---

## 🔢 The Meaning of “Increasing W” Has Changed

In the planar era, “doubling W” meant:

- Doubling the lateral layout width  
- Approximately doubling the current  

This was a **continuous operation**.

In FinFETs, however:

- The number of fins increases: 1 → 2 → 3  
- Weff increases **discretely**  
- Fine-grained adjustment is nearly impossible  

This signifies that:

> **Circuit design has entered a world of quantized width**

---

## 🧩 Design Implications of Weff

The introduction of Weff brings fundamental changes.

### 🔹 1. Direct Coupling of Circuit Design and Layout

- Transistor dimensions are finalized in layout  
- I–V characteristics cannot be determined from schematics alone  
- PCells and explicit fin-count specification become mandatory  

---

### 🔹 2. The End of “W/L-Based Design”

- L remains important  
- But W is no longer a continuous variable  
- Design freedom is constrained by structure  

This can be interpreted as:

> **Circuit design stepping into the domain of device design**

---

### 🔹 3. Changing Role of Compact Models

In the FinFET era:

- BSIM-CMG  
- BSIM-IMG  

and other **multi-gate-aware models** become essential.

These models do not merely fit I–V curves; they embed:

- Weff  
- Fin count  
- Geometric structure  

as **physical parameters**.

The compact model becomes  
a *translator* between circuit intent and device structure.

---

## ⚖ Weff Is Not a Loss of Design Freedom

At first glance, Weff may appear to:

- Restrict design freedom  
- Make circuit design less flexible  

In reality, it simply enforces:

> **Design only within the regime where electric-field control is valid**

This is a physically correct constraint  
and is inseparable from the success of FinFETs.

---

## 📝 Summary

- ✅ In the planar era, W was a continuous layout parameter  
- ✅ In FinFETs, **W → Weff (a structural quantity)**  
- ✅ Current capability depends directly on geometry  
- ✅ Circuit design, layout, and models are inseparable  
- ✅ Weff is not a limitation, but a **physics-aligned design axis**  

The concept of Weff quietly tells us that:

> **In deeply scaled technologies,  
> circuit design can no longer ignore structure**

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
why structural transitions became inevitable.  
Reading it together with the subsequent FinFET, GAA, and CFET articles is recommended.*
