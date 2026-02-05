---
layout: default
title: zenn-articles
---

# 🧩 01_Semiconductor | Article Index

---

## 📘 Device Physics & Structures (up to Post-CFET)

- [01. Planar SCE Problem — Short-Channel Effects in Planar MOSFETs](./01_planar_sce_problem.md)
- [02. FinFET Structure — FinFET Architecture and Electrical Characteristics](./02_finfet_structure.md)
- [03. Weff Concept — Effective Channel Width (Weff)](./03_weff_concept.md)
- [04. GAA Structure — Gate-All-Around (GAA) Devices](./04_gaa_structure.md)
- [05. CFET Challenge — Technical Challenges of CFET](./05_cfet_challenge.md)
- [06. Post-CFET — The Essence of the Post-CFET Era (Beyond Devices)](./06_post_cfet.md)

---

## 🛠 Design Methodology & Abstraction

- [07. SystemDK — A Design World Where SystemDK Is a Prerequisite](./07_systemdk.md)

---

## 🛠 Design, Modeling & EDA

- [08. SemiDevKit — A Development Kit for Semiconductor Design](./08_semidevkit.md)

---

## 🔁 OpenLane / RTL → GDS Flow

- [09. OpenLane Minimal Flow — Pre-Declared Minimal RTL → GDS Flow](./09_openlane_minimal_rtl_predeclared_flow.md)
- [10. OpenLane Control ASIC — RTL-to-GDS Design of a Control ASIC](./10_openlane-control-asic-rtl-to-gds.md)
- [11. OpenLane2 SRAM Hard Macro — Integrating SRAM Hard Macros with OpenLane2](./11_openlane2_sram_hard_macro.md)
- [12. OpenLane1 Setup — OpenLane v1 Environment Setup](./12_openlane1_setup.md)
- [13. OpenLane2 Setup — OpenLane v2 Environment Setup](./13_openlane2_setup.md)
- [14. OpenLane PDK — PDK Structure and Compatibility with OpenLane](./14_openlane_pdk.md)

---

## 🧱 Legacy Technology | Failure, Physics, and Engineering Decisions

> **Records from an era when semiconductor products were  
> directly ruled by device physics, process limitations,  
> and non-negotiable reliability constraints.**

- [15. What Is Legacy Technology? — Failures from the Era Ruled by Physics](./15_legacy_intro.md)
- [16. Pause Refresh Anomalies in 0.25 µm DRAM — Observed Phenomena](./16_legacy_dram1.md)
- [17. Physical Origin of Pause Refresh Failures in 0.25 µm DRAM](./17_legacy_dram2.md)
- [18. What Was PSRAM Intended to Achieve? — The Premise of Reusing DRAM](./18_legacy_psram1.md)
- [19. What Happened to PSRAM, and Why Did It End? — Pause × Disturb](./19_legacy_psram2.md)

This section is **not a historical supplement**.  
It documents **how real products failed, how engineers responded,  
and how final business decisions were made**  
when physics could not be abstracted away.

---

## 🧭 How to Read This Series

- **Physics-first understanding**  
  → 01 → 06 → 07 → 15 → 17  

- **Hands-on ASIC / OpenLane practice**  
  → 12 → 09 → 10 → 11 → 13 → 14  

- **Design philosophy & decision-making**  
  → 06 → 07 → 14 → 18 → 19  

---

## 🎯 Core Questions Addressed

- Why were structural transitions inevitable?  
- Why are EDA tools never universal?  
- Why do some technically valid solutions fail as products?  
- Why must modern design be approached at the system level?  

> **Not “Can we build it?”  
> but “Can it survive physics, usage, and time?”**

---

## 🔚 Closing

`01_Semiconductor` is the **entry point for understanding semiconductor technology  
as an integrated system of physics, design, tools, usage, and decisions**.

Legacy Technology exists here to remind us:

> **Physics never disappears —  
> it only waits until abstraction fails.**
