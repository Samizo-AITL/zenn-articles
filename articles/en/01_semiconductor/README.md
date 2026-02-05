# 🧩 01_Semiconductor | Article Index

---

## 📘 Device Physics & Structures (up to Post-CFET)

This section organizes MOS device structures from the viewpoint of  
**short-channel effects, electrostatic control, and scaling constraints**.  
The focus is on **why structural changes became necessary**, not on generational comparisons.

- [01. Planar SCE Problem — Short-Channel Effects in Planar MOSFETs](./01_planar_sce_problem.md)
- [02. FinFET Structure — FinFET Architecture and Electrical Characteristics](./02_finfet_structure.md)
- [03. Weff Concept — Effective Channel Width (Weff)](./03_weff_concept.md)
- [04. GAA Structure — Gate-All-Around (GAA) Devices](./04_gaa_structure.md)
- [05. CFET Challenge — Technical Challenges of CFET](./05_cfet_challenge.md)
- [06. Post-CFET — The Essence of the Post-CFET Era (Beyond Devices)](./06_post_cfet.md)

---

## 🛠 Design Methodology & Abstraction

This section addresses **how physical constraints are handled across design layers**.  
It clarifies the roles and assumptions of device-, circuit-, and system-level abstraction.

- [07. SystemDK — A Design World Where SystemDK Is a Prerequisite](./07_systemdk.md)

---

## 🛠 Design, Modeling & EDA

This section covers **models, parameters, and assumptions used in semiconductor design**.  
It explicitly distinguishes **what models represent and what they do not**.

- [08. SemiDevKit — A Development Kit for Semiconductor Design](./08_semidevkit.md)

---

## 🔁 OpenLane / RTL → GDS Flow

This section describes a **practical RTL-to-GDS flow using open-source EDA tools**.  
Automated steps and steps requiring explicit design decisions are treated separately.

- [09. OpenLane Minimal Flow — Pre-Declared Minimal RTL → GDS Flow](./09_openlane_minimal_rtl_predeclared_flow.md)
- [10. OpenLane Control ASIC — RTL-to-GDS Design of a Control ASIC](./10_openlane-control-asic-rtl-to-gds.md)
- [11. OpenLane2 SRAM Hard Macro — Integrating SRAM Hard Macros with OpenLane2](./11_openlane2_sram_hard_macro.md)
- [12. OpenLane1 Setup — OpenLane v1 Environment Setup](./12_openlane1_setup.md)
- [13. OpenLane2 Setup — OpenLane v2 Environment Setup](./13_openlane2_setup.md)
- [14. OpenLane PDK — PDK Structure and Compatibility with OpenLane](./14_openlane_pdk.md)

---

## 🧱 Legacy Technology | Failure and Engineering Decisions

This section records **actual product cases** from the late 1990s to early 2000s, focusing on:

- Observed failure phenomena  
- Corresponding physical mechanisms  
- Limits of yield recovery  
- Decisions to continue or terminate development  

The purpose is **documentation**, not reuse in current manufacturing.

- [15. What Is Legacy Technology? — Failures from the Era Ruled by Physics](./15_legacy_intro.md)
- [16. Pause Refresh Anomalies in 0.25 µm DRAM — Observed Phenomena](./16_legacy_dram_1.md)
- [17. Physical Origin of Pause Refresh Failures in 0.25 µm DRAM](./17_legacy_dram_2.md)
- [18. What Was PSRAM Intended to Achieve? — The Premise of Reusing DRAM](./18_legacy_psram_1.md)
- [19. What Happened to PSRAM, and Why Did It End? — Pause × Disturb](./19_legacy_psram_2.md)

---

## 🧭 How to Read This Series

- **📘 Device physics and design assumptions**  
  → 01 → 06 → 07  

- **🛠 EDA and implementation flow**  
  → 12 → 09 → 10 → 11 → 13 → 14  

- **🧱 Product failures and decisions**  
  → 15 → 16 → 17 → 18 → 19  

---

## 🎯 Scope of This Series

- Semiconductor device physics  
- Design methodology and abstraction  
- EDA flows  
- Product-level failures and decisions (Legacy)

The following are out of scope:

- Detailed conditions of current mass-production processes  
- Reproducible manufacturing recipes  
- Company-specific confidential information  

---

## 🔚 Closing

This index serves as an **entry point for cross-referencing semiconductor technology**  
from multiple perspectives: physics, design methodology, tools, and real products.
