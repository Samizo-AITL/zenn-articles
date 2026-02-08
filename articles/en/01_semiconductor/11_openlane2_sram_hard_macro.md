---
layout: default
title: zenn-articles
---

# 【Semiconductor】🧠 11. Integrating an SRAM Hard Macro with OpenLane2 and Generating GDS  
topics: ["openlane2", "asic", "physicaldesign", "sram", "sky130"]

---

## 🧭 Introduction

This article presents a **physical design flow using OpenLane2 (v2)**  
that integrates an **SRAM hard macro** and successfully completes  
the process from **RTL to GDS**.

The critical point is that the goal of this article is **not** to design an SRAM.

Instead, the SRAM is treated purely as an **external hard macro**,  
with the objective of demonstrating a **realistic SoC physical integration methodology**.

---

## 🧱 Why We Do Not “Look Inside” the SRAM

In practical SoC design, SRAMs are typically:

- **Vendor-supplied hard macros**  
- Delivered with LEF / GDS / timing models only  
- Internally opaque and **not subject to modification or verification**

Accordingly, in this project the SRAM is handled with the following policy:

- Verilog is provided as **blackbox declarations only**  
- Placement and routing are based **solely on LEF**  
- GDS is used **only for final merging**  
- Internal DRC / LVS of the SRAM itself is out of scope  

This is not an evasion—it is **the correct and realistic design practice**.

---

## 🛠 Why OpenLane2 Was Chosen

OpenLane2 was selected over OpenLane (v1) for the following reasons:

- Configuration is **explicitly described using YAML / JSON**  
- Macro integration is **structurally clearer**  
- Each stage of the flow is **easier to track and reason about**

In particular, the expressiveness of **macro-aware floorplanning**  
is a major strength of OpenLane2.

---

## 🔄 SRAM Hard Macro Integration Flow

The steps taken in this project are as follows:

1. **Declare the SRAM as a blackbox in Verilog**  
2. **Reference external LEF / GDS files**  
3. **Fix macro placement using FIXED constraints**  
4. **Define floorplanning with halo and keepout regions**  
5. **Place and route standard cells**  
6. **Generate the final merged GDS**

The SRAM is not treated as a design variable,  
but rather as an **initial condition (constraint)**.

---

## 🗺 What Can Be Confirmed in the Final GDS

In the generated GDS, the following can be confirmed:

- The SRAM exists as a **large fixed macro**  
- Halo and keepout regions are properly respected  
- Standard cells are placed and routed around the SRAM  
- Internal SRAM transistors are not visible  

This is the **correct and expected outcome**.

The fact that the internal structure of the SRAM is not visible  
is itself proof that **hard macro integration was performed correctly**.

---

## ❓ Common Misconceptions

### Q. Is there value if the SRAM itself is not designed?

→ **Yes, absolutely.**

In real SoC design, the main difficulty lies not in:

- Logic design  
but in  
- **Macro placement, PDN, and routing constraints**

This project isolates and focuses on  
**the part of ASIC design that is closest to real-world practice**.

---

## 📦 Positioning of This Educational Material

All contents discussed in this article are organized in a  
**fully reproducible form** in the following repository:

- **GitHub Pages**  
  [https://samizo-aitl.github.io/openlane2-sram/](https://samizo-aitl.github.io/openlane2-sram/)

- **GitHub Repository**  
  [https://github.com/Samizo-AITL/openlane2-sram](https://github.com/Samizo-AITL/openlane2-sram)

Configuration files, structure, and design policies are included,  
making this material **directly reusable for educational purposes**.

---

## 📝 Summary

- SRAMs should be treated as **hard macros**  
- Not inspecting internal details is a **correct design decision**  
- OpenLane2 is **fully capable of macro integration**  
- Only when GDS is generated can the design be considered “done”  

If this article helps readers take a step toward  
**realistic ASIC design beyond standard-cell-only examples**,  
it has achieved its goal.
