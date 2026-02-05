---
layout: default
title: SemiDevKit
---

# 【Semiconductor:08】🧰 SemiDevKit  
### — An Open Educational Kit Covering Device Physics → BSIM4 → SPICE → Physical Design End-to-End

---

This article introduces **SemiDevKit**,  
an open educational toolkit that enables **end-to-end learning**, from:

- semiconductor device physics  
- compact modeling (BSIM4)  
- SPICE simulation and reliability analysis  
- to VLSI physical design using OpenLane  

all within a single, coherent framework.

Official website and GitHub repository:

- **GitHub Pages (English documentation)**  
  [https://samizo-aitl.github.io/SemiDevKit/](https://samizo-aitl.github.io/SemiDevKit/)
- **GitHub Repository**  
  [https://github.com/Samizo-AITL/SemiDevKit](https://github.com/Samizo-AITL/SemiDevKit)

---

## 🧭 What Is SemiDevKit?

SemiDevKit is an **open-source educational toolkit**  
that covers the entire workflow listed below:

- Semiconductor device physics (1D Poisson / Drift–Diffusion)  
- Compact modeling (BSIM4)  
- SPICE analysis (DC / AC / scaling / reliability)  
- Reliability evaluation (NBTI / HCI)  
- OpenLane-based VLSI physical design flow (RTL → GDSII)

### 🎯 Target Audience

- Students who want a systematic understanding of semiconductor devices and VLSI  
- Researchers and engineers who want to experiment with device modeling, SPICE, and physical design in a lightweight environment  
- Educators building teaching materials independent of commercial TCAD/EDA tools  

---

## ✨ Key Features

### 🔬 1. Device Physics / TCAD Playground

Under the `tcad/` directory,  
SemiDevKit provides a **TCAD playground** centered on:

- 1D Poisson and Drift–Diffusion solvers  
- MOSFET Vg–Id and Vd–Id characteristics  
- Ferroelectric (FE) P–E modeling using the Landau–Khalatnikov equation  

Unlike commercial TCAD tools, which are often massive black boxes,  
these implementations are **Python-based and traceable directly from equations**.

---

### 📐 2. Compact Modeling (BSIM4 Suite)

The `bsim/` directory contains a comprehensive set of tools for BSIM4.

- Automatic generation of BSIM4 model cards  
- Physical parameter extraction, including:  
  - Oxide thickness (tox)  
  - Substrate doping (Na)  
  - Flat-band voltage (Vfb)  
  - Mobility (μ0)  
  - Channel length (L) and width (W)  

This structure explicitly bridges:

> **Device physics → compact models**

---

### ⚡ 3. SPICE Analysis (DC / AC / Reliability)

SPICE analysis scripts are also provided under `bsim/`.

- DC analysis (Vg–Id, Vd–Id)  
- AC analysis (Cgg–Vg, etc.)  
- Dimensional scaling analysis (L, W sweeps)  
- Reliability analysis (NBTI / HCI)  

Using Python + ngspice, the flow is fully automated:

> **Model generation → SPICE execution → visualization**

---

### 🧱 4. VLSI Physical Design (OpenLane-Lite)

The `openlane/` directory includes an **education-optimized OpenLane-Lite environment**.

- Lightweight flow based on OpenLane 2023  
- Docker / WSL2 compatible  
- Includes minimal example designs (e.g., `spm`)  
- Full RTL → GDSII execution  

This allows users to:

> **Experience a complete IC physical design flow without commercial tools**

---

## 🗂 Repository Structure (Overview)

```
SemiDevKit/
├── tcad/                       # Device physics (TCAD Playground)
│   ├── TCAD_PLAYGROUND
│   └── TCAD_PLAYGROUND_PZT
│
├── bsim/                       # Compact models + SPICE analysis
│   ├── Paramus
│   ├── BSIM4_ANALYZER_DC
│   ├── BSIM4_ANALYZER_CV
│   ├── BSIM4_ANALYZER_DIM
│   └── BSIM4_ANALYZER_RELIABILITY
│
├── openlane/                   # Physical design flow
│   ├── openlane-lite
│   └── openlane-superstable
│
└── docs/                       # Documentation (MathJax enabled)
```

---

## 🚀 Setup and Execution Examples

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/Samizo-AITL/SemiDevKit.git
cd SemiDevKit
```

---

### 2️⃣ Required Environment

- Python 3.10+  
- NumPy / SciPy / Matplotlib  
- ngspice  
- Docker (for OpenLane-Lite)  
- WSL2 recommended on Windows  

---

### 3️⃣ Example: SPICE DC Analysis

```bash
cd bsim/BSIM4_ANALYZER_DC/run
python run_vd.py
python run_vg.py
```

This workflow:

- Generates BSIM4 model cards  
- Runs SPICE simulations  
- Automatically plots Vd–Id and Vg–Id characteristics  

---

### 4️⃣ Example: Running OpenLane-Lite

```bash
cd openlane/openlane-lite
./docker/run_in_docker.sh
```

Execution steps:

1. Launch OpenLane 2023 container  
2. Load a small example design  
3. Run the RTL → GDSII flow  
4. Generate GDS output  

---

## 📘 Documentation (MathJax Enabled)

Theoretical notes under `docs/` are published on GitHub Pages.

Covered topics include:

- Device physics (Poisson / Drift–Diffusion)  
- Compact model theory (BSIM4)  
- SPICE analysis (DC / AC / reliability)  
- NBTI / HCI degradation models  
- RTL → GDS physical design flow  

Here, **code and theory are directly linked**.

---

## 📜 License

| Component | License | Description |
|---------|---------|-------------|
| Source code | MIT | Free use, modification, and redistribution |
| Text materials | CC BY / CC BY-SA | Attribution required |
| Figures | CC BY-NC | Non-commercial use only |
| External references | Original licenses | — |

---

## 📝 Summary

**SemiDevKit enables end-to-end learning**  
from semiconductor device physics to IC physical design  
without relying on commercial TCAD or EDA tools.

Its strongest points include:

- Python implementations traceable down to equations  
- Full BSIM4-based SPICE analysis  
- RTL → GDSII flow using OpenLane-Lite  

We recommend starting with:

- `bsim/BSIM4_ANALYZER_DC` for DC analysis  
- `openlane/openlane-lite` for the physical design flow  

- **GitHub Pages**  
  [https://samizo-aitl.github.io/SemiDevKit/](https://samizo-aitl.github.io/SemiDevKit/)
- **GitHub Repository**  
  [https://github.com/Samizo-AITL/SemiDevKit](https://github.com/Samizo-AITL/SemiDevKit)
