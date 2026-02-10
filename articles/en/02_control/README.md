# 🎛️ 02_control / Control & AITL Article Index

This directory systematically organizes articles on  
**PID control, FSM, and AITL (Architecture for Integrated Technology Logic)**,  
covering control theory, reliability-oriented design, safety boundaries,  
and human-centered design philosophy.

---

## 📘 Fundamental Structure & Philosophy

- [01 AITL Controller Overview](./01_aitl-controller.md)
- [02 Why FSM Control Often Fails](./02_fsm-control-no-effect.md)
- [03 PID Control Is Stronger Than Expected](./03_pid_is_stronger_than_expected.md)

---

## 🛡 Reliability Control & Design Limits

- [04 Reliability Control Beyond Robust Control](./04_reliability-control-beyond-robust.md)
- [05 Why Reliability Control Fails at Timing](./05_reliability_control_timing_fail.md)
- [06 Reliability FSM in AITL](./06_aitl_reliability_fsm.md)

---

## 🔮 Future Design Directions & Control Classification

- [07 B-Type Control and Future Direction](./07_btype_future_direction.md)

---

## ⚙ PID × FSM Integrated Design

- [08 PID–FSM 10% Threshold Design](./08_pid_fsm_10pct_threshold_design.md)
- [09 Final AITL PID–FSM Design Based on Human Judgment](./09_aitl_pid_fsm_human_design_final.md)
- [10 Envelope Design and Recovery Strategy](./10_envelope_design-recovery.md)

---

## 🚧 A-Type / B-Type Control Constraints

- [11 Limits of A-Type Control](./11_aitl_a_type_limit.md)
- [12 B-Type Control Guard Design](./12_aitl_b_type_guard.md)
- [13 FSM Reliability Guard](./13_fsm_reliability_guard.md)

---

## 🔒 Safety Boundaries & Packaging

- [14 AITL Controller Reliability Boundary](./14_aitl_controller_reliability_boundary.md)
- [15 AITL Controller Safety Package (Initial Edition)](./15_aitl-controller-safety-package.md)
- [16 AITL Controller Safety Package (Integrated Edition)](./16_aitl-controller-safety-package.md)

---

## 🧭 Architectural Positioning

- **PID**: Inner real-time stabilization loop  
- **FSM**: Supervisory layer for modes and state transitions  
- **AITL (LLM)**: Redesign and reconfiguration layer for anomalies and degradation  

> Control is not about making systems stronger,  
> but about **designing how they fail safely**.
