---
layout: default
title: AITL-controller
---

# 【Control】🧩 01. AITL-controller  
### — An Integrated Three-Layer Control Architecture: PID × FSM × LLM

---

This article introduces **AITL-controller**,  
a lightweight framework that integrates a **three-layer control architecture**:

- **PID** (real-time control)  
- **FSM** (state supervision)  
- **LLM** (intelligent control and redesign)

The framework is designed for **education and research use**,  
making advanced control architectures accessible and reproducible.

- Official site:  
  [https://samizo-aitl.github.io/aitl-controller-a-type/](https://samizo-aitl.github.io/aitl-controller-a-type/)

- GitHub repository:  
  [https://github.com/Samizo-AITL/aitl-controller-a-type](https://github.com/Samizo-AITL/aitl-controller-a-type)

---

## 🧠 What Is AITL-controller?

AITL-controller is a framework that **unifies classical control, formal control, and intelligent control**  
into a single, coherent architecture suitable for learning and experimentation.

The three layers are clearly separated by responsibility:

- PID: numerical stability and real-time performance  
- FSM: explicit system states and transitions  
- LLM: diagnosis, adaptation, and redesign  

This separation is intentional and fundamental.

---

## 🧱 Three-Layer Architecture (PID × FSM × LLM)

### 1️⃣ Inner Loop: PID (Real-Time Control)

- The innermost layer directly controls the plant or robot  
- Examples: angle stabilization, velocity control, posture regulation  
- Responsible for **stability** and **dynamic response**

PID runs at high frequency and handles  
**millisecond-level real-time behavior**,  
exactly as in classical control systems.

---

### 2️⃣ Middle Loop: FSM (Finite State Machine)

- The supervisory layer managing **system modes and state transitions**  
- Examples:  
  - Idle → Running → Fault  
  - Lift → Hold → Place  

FSM determines:

- Which PID controller is active  
- Which parameters are enabled  
- When transitions should occur  

It acts as an explicit and inspectable **control supervisor**.

---

### 3️⃣ Outer Loop: LLM (Intelligent Control)

- Detection of faults, anomalies, and performance degradation  
- Responsible for **reasoning, diagnosis, and redesign**

Typical roles include:

- Automatic re-identification of PID parameters  
- Proposing modifications to state-transition rules  
- Inferring abnormal trends from operation logs  

This layer leverages LLM strengths such as:

- Adaptation to out-of-model behavior  
- Natural-language explanation and design rationale generation  

---

## ❓ Why a Three-Layer Architecture?

Traditional control systems can be built using PID and FSM alone,  
but they suffer from inherent limitations:

- Poor adaptability to environmental changes  
- Manual fault analysis by human experts  
- High skill requirements for parameter tuning  

AITL-controller assigns these responsibilities to the LLM layer,  
with the goal of enabling:

> **Self-improving control systems**

at the education and research level.

---

## 📦 Repository Structure (Overview)

```
aitl-controller/
├── core/
│   ├── pid/             # PID modules (stability & performance)
│   ├── fsm/             # FSM modules (state transitions)
│   └── llm/             # LLM modules (redesign & reasoning)
│
├── demo/
│   ├── inverted_pendulum/   # Inverted pendulum demo
│   ├── quadrotor/           # Quadrotor control example
│   └── simple_robot/        # Small-scale robot systems
│
├── docs/
│   ├── architecture/        # Three-layer architecture explanation
│   ├── math/                # PID & FSM mathematics
│   ├── llm/                 # Design guidelines for LLM control
│   └── examples/            # Tutorials
│
└── assets/                  # Figures and workflow materials
```

The framework core resides in **core/**,  
while **demo/** provides immediately runnable examples.

---

## 🔄 Typical Control Loop Structure

AITL-controller assumes the following control loop:

```
Sensor → PID → Actuator → Plant
        ↑        ↓
        FSM ← LLM (Outer loop)
```

### Role Summary
- PID: real-time error correction  
- FSM: orchestration of PID controllers and modes  
- LLM: analysis and redesign of PID and FSM structures  

---

## 🧪 Example: Inverted Pendulum Demo

In the inverted pendulum example, the three layers cooperate as follows:

1. **PID**: stabilizes the pendulum angle  
2. **FSM**: manages states such as  
   - Stabilize  
   - Recover  
   - Fault  
3. **LLM**:  
   - Analyzes the cause of failures  
   - Suggests improved PID gains  
   - Proposes refinements to state-transition logic  

The LLM **never directly drives actuators**.  
Its role is strictly to **improve the control structure itself**.

---

## 🧩 The Role of LLM Control (Design Policy)

In AITL-controller, the LLM layer is assigned three explicit tasks:

### 1. Monitoring
- Detect anomalies and performance degradation from logs

### 2. Diagnosis
- Identify root causes in an explainable manner

### 3. Redesign
- Improve PID gains  
- Modify state-transition tables  
- Refine supervisory rules  

All improvements are expressed through  
**natural language, code generation, or structured design proposals**.

---

## ⚙ Setup

```bash
git clone https://github.com/Samizo-AITL/aitl-controller.git
cd aitl-controller
pip install -r requirements.txt
```

Full documentation is available on the  
official GitHub Pages site.

---

## 🎓 Educational and Research Applications

AITL-controller is suitable for:

- Learning classical control (PID, FSM)  
- Research on AI/LLM integration into control systems  
- Advanced robotics control education  
- Validation of autonomous redesign algorithms  
- Explainable AI (XAI) for fault handling  

In education, it naturally supports the progression:

> **Understanding PID/FSM fundamentals**  
> → **Improving them using LLMs**

---

## 📝 Summary

AITL-controller integrates three distinct layers:

- **PID**: real-time control  
- **FSM**: explicit state supervision  
- **LLM**: intelligent redesign and reasoning  

Built on classical control principles, it aims to become  
an **educational and research platform for next-generation control systems**  
in the age of AI.

---

- Official site:  
  [https://samizo-aitl.github.io/aitl-controller-a-type/](https://samizo-aitl.github.io/aitl-controller-a-type/)

- GitHub repository:  
  [https://github.com/Samizo-AITL/aitl-controller-a-type](https://github.com/Samizo-AITL/aitl-controller-a-type)
