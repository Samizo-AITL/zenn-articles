---
layout: default
title: Planar MOSFET and Short Channel Effects
---

# 【Semiconductor】🔬 01. Planar MOSFET and SCE  
### — The Real Reason Scaling Hit a Wall
topics: ["Semiconductor", "MOSFET", "SCE", "Device Physics"]

---

## 🧭 Introduction

For many decades, MOSFET performance improvements were achieved simply by **shrinking dimensions**.  
However, beyond a certain technology node, **Short Channel Effects (SCE)** became dominant, and  
classical scaling could no longer be sustained.

In this article, we examine from a **device-physics perspective**:

- ❓ Why SCE was unavoidable in planar MOSFETs  
- ⚠️ Why this limitation is not a fabrication limit but an **electric-field control limit**  
- 🔁 Why a structural transition (FinFET and beyond) was inevitable  

---

## ⚡ The Physical Essence of Short Channel Effects

Typical manifestations of SCE include:

- Threshold voltage (Vth) roll-off  
- DIBL (Drain-Induced Barrier Lowering)  
- Degradation of subthreshold characteristics  

The key point is that these are not independent phenomena.  
They all share a common physical origin:

> **“Electrodes other than the gate begin to dominate the channel potential.”**

---

## 📐 The Problem Is Not Dimensions, but Electric Fields

Even if the gate length is reduced, once the gate can no longer sufficiently control  
the channel potential, the planar MOSFET reaches a **structural limit**.

Specifically:

- Source/drain depletion regions intrude toward the center of the channel  
- Drain voltage directly modulates the source-side potential barrier  
- Thinning the gate oxide still means **control only from the top**  

This is not a matter of lithography or process precision.

> **“From how many directions, and how strongly, can the electric field envelop the channel?”**

This is fundamentally a **structural problem**, not a manufacturing one.

---

## 🚫 Why the Planar Structure Could Not Solve This

In a planar MOSFET, the gate controls the channel from **only one side (the top)**.

As a result:

- As channel length shrinks  
- The influence of the drain electric field increases  
- The relative strength of gate control decreases  

This leads to a **reversal of dominance**.

No amount of the following can fundamentally resolve the issue:

- Thinner gate oxides  
- High-k dielectric materials  
- Increased channel doping  

Because the problem lies in the **insufficient directionality of gate electric-field control itself**.

---

## 📉 “SCE Countermeasures” = Breakdown of Scaling Laws

Classical scaling theory (Dennard scaling) assumed:

- Constant electric field  
- Simultaneous scaling of dimensions and voltage  

Once SCE becomes significant:

- Electric fields can no longer be kept constant  
- Supply voltage cannot be reduced  
- Leakage current increases exponentially  

Thus:

> **The emergence of SCE signifies the breakdown of scaling theory itself.**

---

## 🔁 Structural Transition Was Not Evolution, but Necessity

The only viable solution was:

> **To change the device structure so that the gate controls the channel from multiple directions.**

This led to:

- FinFET (three-sided gate control)  
- Gate-All-Around (GAA)  
- Nanosheet / nanowire devices  

These were:

- 🚀 Not merely new technologies for higher performance  
but  
- 🧱 **Inevitable solutions after planar MOSFETs reached a physical dead end**

---

## 📝 Summary

- ✅ SCE is a **structure-induced collapse of electric-field control** due to scaling  
- ✅ The core issue is not dimensions, but **gate dominance over the channel**  
- ✅ Planar MOSFETs reached an unavoidable structural limit  
- ✅ FinFET and beyond were not optional—they were **physically inevitable**

---

## 📚 References and Related Links

### 📘 Edusemi-v4x | Advanced Node Technologies (FinFET, GAA, CFET)

- **GitHub Pages (Public Educational Material, English/Japanese)**  
  [https://samizo-aitl.github.io/Edusemi-v4x/f_chapter1_finfet_gaa/](https://samizo-aitl.github.io/Edusemi-v4x/f_chapter1_finfet_gaa/)

- **GitHub (Source Management, Markdown Manuscripts)**  
  [https://github.com/Samizo-AITL/Edusemi-v4x/tree/main/f_chapter1_finfet_gaa](https://github.com/Samizo-AITL/Edusemi-v4x/tree/main/f_chapter1_finfet_gaa)

### 🧩 Related Chapter

- Planar MOSFET → FinFET → GAA → CFET  
  This article corresponds to **Chapter 1 (Special Edition)**,  
  explaining the historical transition of **electric-field control structures**.
