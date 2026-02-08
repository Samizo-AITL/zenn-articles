---
layout: default
title: zenn-articles
---

# 【Semiconductor】🔺 05. Challenges of GAA and the Rise of CFET  
### — The Inevitability of Vertical Integration
topics: ["CFET", "GAA", "Next-Generation Semiconductors"]

---

## 🧭 Introduction

With the introduction of Gate-All-Around (GAA) structures,  
the problem of **electric-field control in MOSFETs has been largely solved**.

So what becomes the next limiting factor?

The answer is:

> **Not electric fields, but “placement” and “heat.”**

In this article, we examine:

- 🔹 The constraints that emerge after GAA  
- 🔹 Why scaling must move in the vertical (3D) direction  
- 🔹 The fundamental challenges inherent to CFET  

---

## ⚠️ Constraints That Appear After GAA

GAA structures deliver:

- Excellent resistance to SCE  
- Low-voltage operation  
- High switching efficiency  

At the same time, new limitations become apparent.

---

### 🧱 1. Footprint (Area) Limitations

- Nanosheets cannot be stacked laterally without bound  
- There are physical limits to sheet count and pitch  
- Standard-cell area becomes increasingly difficult to shrink  

This leads to a situation where:

> **Even with perfect electric-field control, there is no space left to place devices**

---

### 🔌 2. Interconnect and Power Congestion

As scaling progresses:

- Local interconnect density increases sharply  
- Power delivery issues such as IR drop become prominent  
- Crosstalk between signal and power lines worsens  

While GAA excels as a device,  
it is **structurally harsh from a routing and power perspective**.

---

### 🔥 3. Difficulty of Heat Dissipation

GAA channels suffer from:

- Reduced contact area with the substrate  
- Limited thermal escape paths  
- A tendency toward localized hot spots  

As performance increases:

> **Thermal effects become the dominant limiting factor**

---

## 🧩 The CFET Concept

One proposed solution to these constraints is  
**CFET (Complementary FET)**.

The core idea of CFET is straightforward:

- Stack NMOS and PMOS **vertically**  
- Halve lateral cell area  
- Increase integration density through 3D placement  

This is a structure aimed at:

> **Improving placement efficiency, not electric-field control**

---

## ⬆️ Why the Vertical Direction?

Lateral scaling has nearly reached its limits due to:

- Lithography constraints  
- Pitch limitations  
- Routing congestion  

In contrast, the vertical direction offers:

- A largely unused degree of freedom  
- Opportunities to shorten interconnects  
- Dramatic improvements in area efficiency  

CFET can therefore be described as:

> **A structure that fully exploits the remaining degrees of freedom**

---

## ⚡ Affinity with Backside Power Rail (BPR)

One reason CFET is becoming more realistic is  
the emergence of **Backside Power Rail (BPR)** technology.

- Power is delivered from the backside of the substrate  
- Front-side routing congestion is reduced  
- Power separation for vertically stacked devices becomes feasible  

CFET and BPR are designed as:

> **A paired solution enabling both 3D device stacking and power isolation**

---

## 🚧 Why CFET Is Not Easy

Despite its appeal, CFET is extremely challenging to realize.

---

### 🔥 1. Thermal Coupling Issues

- Heat interaction between upper and lower devices  
- Local temperature rise  
- Increased device-to-device variability  

> **Heat is the greatest enemy of 3D integration**

---

### 🧪 2. Process Temperature Constraints

- Upper devices must be fabricated after lower devices  
- High-temperature processes cannot be reused  
- Severe constraints on materials and process flows  

This directly impacts the foundations of manufacturing technology.

---

### 🔗 3. Inter-Device Interference

- Electrical coupling  
- Mechanical stress propagation  
- Correlated variability  

CFETs must be designed not as isolated devices, but as:

> **Integrated composites rather than individual transistors**

---

## 🔄 CFET Is the Next Necessity, but Not a Simple Answer

CFET is:

- Not a straightforward extension of GAA  
but  
- **An alternative solution to the problems GAA cannot solve**

It represents a shift in design axes:

- Electric fields → placement  
- Planar → three-dimensional  
- Device → system-level thinking  

---

## 📝 Summary

- ✅ GAA has largely completed electric-field control  
- ✅ The next constraints are area, interconnects, and heat  
- ✅ CFET optimizes placement efficiency via vertical stacking  
- ✅ Synergy with BPR is essential  
- ✅ The conditions for realization are extremely demanding  

CFET can be described as:

> **Not a structure where “if you can build it, you win,”  
> but one where the real question is whether it can be made to truly work**

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
