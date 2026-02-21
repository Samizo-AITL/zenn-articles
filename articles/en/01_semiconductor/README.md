# 🔬 01_Semiconductor | Article Index

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

## 🛠 Design, Modeling, and EDA

In this section,  
we organize the **models, parameters, and EDA assumptions** used in semiconductor design.  
The **scope represented by each model** and the **scope not represented** are clearly defined.

- [08. SemiDevKit DevKit Concept for Semiconductor Design](./08_semidevkit.md)
  - [08-01. SemiDevKit Overview](./08-01_semidevkit_overview.md)
  - [08-02. TCAD (Poisson / Drift–Diffusion)](./08-02_tcad_poisson_drift_diffusion.md)
  - [08-03. Fundamentals of the BSIM4 Compact Model](./08-03_bsim4_compact_model_basics.md)
  - [08-04. BSIM4 Model Generation Using Paramus](./08-04_paramus_bsim4_model_generation.md)
  - [08-05. BSIM4 DC Analysis (V–I)](./08-05_bsim4_dc_vi_analysis.md)
  - [08-06. BSIM4 AC / CV Analysis](./08-06_bsim4_ac_cv_analysis.md)
  - [08-07. MOSFET Scaling and Short-Channel Effects](./08-07_mosfet_scaling_short_channel.md)
  - [08-08. Fundamentals of NBTI Reliability](./08-08_nbti_reliability_basics.md)
  - [08-09. Fundamentals of HCI Reliability](./08-09_hci_reliability_basics.md)

---

## 🔁 OpenLane / RTL → GDS Flow

- [00. OpenLane Overview / Beginner-friendly · One Article to See the Whole Picture](./00_openlane_overview.md)

This section describes a **practical RTL-to-GDS flow using open-source EDA tools**.  
Automated steps and steps requiring explicit design decisions are treated separately.

- [09. OpenLane Minimal Flow — Pre-Declared Minimal RTL → GDS Flow](./09_openlane_minimal_rtl_predeclared_flow.md)
- [10. OpenLane Control ASIC — RTL-to-GDS Design of a Control ASIC](./10_openlane-control-asic-rtl-to-gds.md)
- [11. OpenLane2 SRAM Hard Macro — Integrating SRAM Hard Macros with OpenLane2](./11_openlane2_sram_hard_macro.md)
- [12. OpenLane1 Setup — OpenLane v1 Environment Setup](./12_openlane1_setup.md)
- [13. OpenLane2 Setup — OpenLane v2 Environment Setup](./13_openlane2_setup.md)
- [14. OpenLane PDK — PDK Structure and Compatibility with OpenLane](./14_openlane_pdk.md)

### 🧠 OpenLane: Design Philosophy, Reality, and Operations (Phase 1–3 + Appendix)

This section focuses on the **conceptual foundation required to use the above flow without breaking it**.  
It organizes the causal relationship between **Environment → Physical Design → Timing → Operations**.

- [23. OpenLane Is 90% About the Environment / Environment Survival](./23_openlane_environment_survival.md)
- [24. Automation Is Not Magic / Physical Design Reality](./24_openlane_physical_design_reality.md)
- [25. Does STA Lie? / Integration & Timing Truth](./25_openlane_timing_truth.md)
- [26. How to Use OpenLane Without Breaking It / Operational Rules & Appendix](./26_openlane_operational_rules.md)

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

## 🧪 Test, Quality, and Failure Analysis

This section covers mass-production quality control, including  
**process monitoring, product screening, and root-cause investigation**.  
The entire quality loop is organized along the flow: ETEST → WAT → FA.

- [20. What Is ETEST? — An Evaluation Process for Quantitative Monitoring of Process Variations](./20_etest_process_monitoring.md)
- [21. Why Is Wafer Testing the “Last Line of Defense”? — A Screening Process for Defective Dies](./21_wafer_test_quality_gate.md)
- [22. What Does Failure Analysis (FA) Decide? — Determining Corrective Targets](./22_failure_analysis_root_cause.md)

---

## 🔎 How to Read This Series

- **📘 Device physics and design assumptions**  
  → 01 → 06 → 07 → 08  
  (From the physical background of Planar / FinFET / GAA / CFET  
  to design assumptions established by SystemDK and SemiDevKit)

- **🛠 EDA and implementation flow**  
  → 08-01 → 08-03 → 08-05 → 00 → 12 → 09 → 10 → 11 → 13 → 14  
  (Following the RTL-to-GDS flow based on modeling and V–I assumptions)

- **🧱 Product failures and engineering decisions**  
  → 15 → 16 → 17 → 18 → 19  
  (Fact-based records of observed failures and decision-making in legacy technologies)

- **🧪 Quality control and decision flow in mass production**  
  → 20 → 21 → 22  
  (Process monitoring with ETEST, screening by wafer testing,  
  and root-cause determination and corrective decisions through FA)

- **🧠 If You Want to Use OpenLane Without Breaking It (Design Philosophy, Reality, and Operations)**  
  → 23 → 24 → 25 → 26  
  (Environment setup → Limits of physical design → Timing truth → Operations and reproducibility)

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
