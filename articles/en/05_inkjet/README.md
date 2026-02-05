# 05_inkjet / Inkjet Physics & Drive Articles Index

This directory treats **inkjet systems** as the intersection of  
MEMS, physics, circuits, and timing causality, and clarifies the  
**design limits that are already determined before control is even considered**.

---

## 📘 Trade-offs & Design Space

- [01 Inkjet DTS Trade-off Model](./01_inkjet_dts_tradeoff_model.md)

> Ejection performance is determined by the trade-off among  
> **D (Drop) × T (Timing) × S (Stability)**.

---

## ⏱ Timing and Causality

- [02 Visualization of Inkjet Timing Causality](./02_inkjet-timing-causality-visualization.md)

> Even when it appears that waveforms are being “controlled,”  
> **causality has already been fixed on the physical side**.

---

## ⚡ Driver Circuits and Physical Coupling (GF180)

- [03 GF180 Inkjet Driver Design (Fundamentals)](./03_gf180-inkjet-driver.md)
- [04 GF180 Inkjet Driver Design (Advanced)](./04_gf180-inkjet-driver.md)
- [05 GF180 Inkjet Driver Design (Integrated)](./05_gf180-inkjet-driver.md)

> A driver circuit is  
> **not a controller, but a part of the physical phenomenon itself**.

---

## 🧭 Positioning of This Directory

- **05_inkjet**:
  - The intersection of MEMS, fluidics, electricity, and time
  - An ultra-fast physical domain where FSMs and LLMs cannot intervene
- A concrete implementation example of **04_mems**
- An empirical demonstration of why **02_control** must not intervene

> **Inkjet is not a control target,  
> but the causal structure itself.**

---

## 🔗 Related Directories

- [04_mems / MEMS Analysis & Analog Physics](../04_mems/)
- [03_hardware / Hardware & Physical Control](../03_hardware/)
- [02_control / Control & AITL](../02_control/)

---

