# 🎛️ 02_control / Control & AITL Article Index

This directory organizes articles around  
**PID control, FSM, and AITL (Architecture for Integrated Technology Logic)**.

The focus is not control performance itself,  
but the **structure of control**, including:

- reliability-oriented design  
- safety boundaries  
- limits of applicability  
- and the role of human judgment

This series does not aim to make control stronger.  
It aims to **define where control holds, and where it must stop**.

---

## 📘 Fundamental Structure & Philosophy

This section defines the basic structure of AITL control
and the assumptions behind conventional control designs.

- [01 AITL Controller Overview](./01_aitl-controller.md)
- [02 Why FSM Control Often Fails](./02_fsm-control-no-effect.md)
- [03 PID Control Is Stronger Than Expected](./03_pid_is_stronger_than_expected.md)

---

## 🛡 Reliability Control & Design Limits

This section focuses on control failure that occurs
even when stability appears to be maintained.

- [04 Reliability Control Beyond Robust Control](./04_reliability-control-beyond-robust.md)
- [05 Why Reliability Control Fails at Timing](./05_reliability_control_timing_fail.md)
- [06 Reliability FSM in AITL](./06_aitl_reliability_fsm.md)

---

## 🔮 Future Design Directions & Control Classification

This section introduces control classification
to clarify where different control approaches apply.

- [07 B-Type Control and Future Direction](./07_btype_future_direction.md)

---

## ⚙ PID × FSM Integrated Design

This section covers control structures
that remain valid at the implementation level.

- [08 PID–FSM 10% Threshold Design](./08_pid_fsm_10pct_threshold_design.md)
- [09 Final AITL PID–FSM Design Based on Human Judgment](./09_aitl_pid_fsm_human_design_final.md)
- [10 Envelope Design and Recovery Strategy](./10_envelope_design-recovery.md)

---

## 🚧 A-Type / B-Type Control Constraints

This section explicitly defines
what control **cannot** do.

- [11 Limits of A-Type Control](./11_aitl_a_type_limit.md)
- [12 B-Type Control Guard Design](./12_aitl_b_type_guard.md)
- [13 FSM Reliability Guard](./13_fsm_reliability_guard.md)

---

## 🔒 Safety Boundaries & Packaging

This section defines boundaries
required to make control deployable as a system.

- [14 AITL Controller Reliability Boundary](./14_aitl_controller_reliability_boundary.md)
- [15 AITL Controller Safety Package (Initial Edition)](./15_aitl-controller-safety-package.md)
- [16 AITL Controller Safety Package (Integrated Edition)](./16_aitl-controller-safety-package.md)

---

## 🧾 Summary — Design Specifications

This section serves as a reference
for understanding the overall architecture.

- [17 AITL Control Architecture Specification](./17_aitl_control_architecture_spec.md)
- [18 AI Control Safety Design Checklist (Operational Use)](./18_ai_control_safety_checklist.md)
- [19 Applicability Limits of Adaptive Control (A-Type / B-Type)](./19_adaptive_control_applicability_limits.md)

---

## 🧭 Architectural Positioning

- **PID**: Inner real-time stabilization loop  
- **FSM**: Supervisory layer for mode and state transitions  
- **AITL (LLM)**: Redesign and reconfiguration layer  

> Control is not about making systems stronger,  
> but about **designing how they fail safely**.
