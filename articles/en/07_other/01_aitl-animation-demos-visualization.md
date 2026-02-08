---
layout: default
title: zenn-articles
---

# 【Video】🎞️ 01. Understanding the Three-Layer Control Architecture Through Animation Demos
topics: ["aitl", "control-theory", "visualization", "css", "svg", "canvas"]

---

*This article is intended for engineers interested in **conceptual visualization** for control systems, architectures, and education.*

---

## 🧠 Introduction — Why Do We “Animate”?

In control theory and architectural design, we often face the following problems:

- Equations are correct, but intuition does not develop  
- Diagrams are understandable, but motion is missing  
- Implementations are traceable, but the global picture is easily lost  

In this article, we use the **Animation Demos** published at  
[https://samizo-aitl.github.io/aitl-animation-demos/](https://samizo-aitl.github.io/aitl-animation-demos/)  
as a reference to explain a design approach that enables understanding through **animation**:

- Control structure  
- State transitions  
- Physical behavior  

---

## 🏗️ Overview of AITL (Three-Layer Control Architecture)

AITL is based on the following three-layer structure:

```
LLM (Redesign / Strategy Layer)
 └ FSM (State Supervision / Mode Transition)
    └ PID (Real-Time Control Loop)
```

### 📌 Roles of Each Layer

- **PID**  
  Real-time control. Ensures stability and tracking performance, including voltage–current (V–I) response.
- **FSM**  
  Manages states, modes, and abnormal transitions.
- **LLM**  
  Performs PID re-identification and FSM rule redesign during performance degradation or failure.

Animation Demos act as **training wheels** to visually share this layered structure and role separation.

---

## 🧩 Structure of the Animation Demos

### 🎨 ① CSS Animation Demos

- Orbit / Fade-in / Pulse  
- Layer stack representation  

**Purpose**
- Periodicity of control loops  
- Layered hierarchy  
- Relative influence and weighting  

---

### 🧭 ② SVG + JavaScript Demos

- AITL control flow  
- FSM state transitions  
- Inkjet ejection models  

**Purpose**
- Explicit representation of states and transitions  
- Visualization of causality  
- Expression of control authority transfer  

---

### 🧪 ③ Canvas Demos

- Particle motion  
- Simplified physical simulations  

**Purpose**
- Intuitive understanding of continuous dynamics  
- Behavioral insight prior to equations  

---

### ⚡ ④ Semiconductor and Physical Animations

- Potential distribution in pn junctions  
- Surface potential of MOS / NMOS devices  

**Purpose**
- Connecting V–I characteristics with physical phenomena  
- Understanding the control target itself  

---

## 🧩 Implementation Example ①: CSS Pulse Animation

```css
.pulse {
  animation: pulseAnim 1.5s infinite ease-in-out;
}

@keyframes pulseAnim {
  0%, 100% {
    transform: scale(1);
    opacity: 1;
  }
  50% {
    transform: scale(1.2);
    opacity: 0.6;
  }
}
```

### 🎯 Control-Theoretic Interpretation

- **Period**: control loop cycle  
- **Amplitude**: gain variation  
- **Opacity**: influence or weighting  

PID response can be understood as **oscillation**, not equations.

---

## 🧩 Implementation Example ②: FSM Visualization with SVG

```js
const svg = document.querySelector("svg");

function addNode(x, y) {
  const c = document.createElementNS(
    "http://www.w3.org/2000/svg",
    "circle"
  );
  c.setAttribute("cx", x);
  c.setAttribute("cy", y);
  c.setAttribute("r", 18);
  svg.appendChild(c);
}
```

### 🔁 Correspondence with FSM

- Nodes: states  
- Edges: transition conditions  
- Animation: movement of control authority  

A static FSM diagram becomes a **dynamic model**.

---

## 🧠 Why Animation Is Effective

- Equations: precise but slow to understand  
- Diagrams: understandable but static  
- Animations: slightly ambiguous but fast to grasp  

In early design, education, and discussion phases, the following are critical:

- Rapid understanding  
- Shared mental models  
- Reduced cognitive load  

Animation Demos function as **intellectual warm-up tools** before equations, SPICE, or FEM.

---

## 🧬 Mapping Between AITL and Animation

| Layer | Represented in Animation |
|------|--------------------------|
| PID  | Oscillation, tracking, convergence |
| FSM  | State transitions, mode switching |
| LLM  | Reconfiguration, branching decisions |

Animations are not decoration.  
They are **the lightest-weight models for sharing design thinking**.

---

## 🧾 Summary

- Animation Demos serve as training wheels for understanding AITL  
- CSS / SVG / Canvas are powerful tools for design education  
- Making things “move” reveals structure  
- They bridge intuition to equations, code, and physics  

👉 Demo collection  
[https://samizo-aitl.github.io/aitl-animation-demos/](https://samizo-aitl.github.io/aitl-animation-demos/)

---

## 🚀 Next Steps

- Independent explanations of PID / FSM / LLM layers  
- Deep dives into individual demos  
- Educational and design template standardization  

These will be released sequentially.

---

> Animation is not decoration.  
> It is the lightest model for sharing design thinking.
