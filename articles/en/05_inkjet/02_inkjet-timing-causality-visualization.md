---
layout: default
title: zenn-articles
---

# 【Inkjet】🖨️ 02. inkjet-timing: Visualizing Temporal Causality in Piezoelectric Inkjet Systems
topics: ["inkjet", "control engineering", "physical modeling", "visualization", "aitl"]

---

## 📌 Introduction

At first glance, a piezoelectric inkjet system may appear simple:  
*apply a waveform and a droplet is ejected.*

In reality, however, it is a system in which multiple physical domains—

- Electrical (V–I)
- Mechanical (displacement)
- Fluidic (pressure and flow)

—are **causally connected on a shared microsecond-scale time axis**.

This article introduces **inkjet-timing**,  
a visualization project designed to make this temporal causality intuitive.

---

## 🧩 What Is inkjet-timing?

**inkjet-timing** is an educational / PoC project that visualizes:

> “How electrical, mechanical, and fluid phenomena are causally connected  
> along the same time axis in piezoelectric inkjet ejection.”

The focus is not numerical accuracy or CFD-level reproduction, but:

- Temporal order
- Delay
- Phase relationships
- Flow of causality

---

## 📊 What Is Visualized

A single shared time axis is used, with signals stacked vertically:

- Drive voltage **V(t)**
- Current response **I(t)**
- Piezoelectric displacement **Δx(t)**
- Channel pressure **P(t)**
- Ink flow rate **Q(t)** (outflow / inflow)

Each waveform belongs to a different physical domain,  
yet **all are linked by temporal causality**.

What matters is not the absolute value, but:

> **Which phenomenon rises first, and in what order.**

---

## 🧠 Why This Is Not PID Control

Inkjet droplet ejection is characterized by:

- Fully open-loop operation
- Feed-forward driving
- Completion within a few microseconds

There is no time to run feedback control  
during droplet formation.

Stability is instead *physically embedded* through:

- Drive waveform design
- Mechanical damping
- Acoustic and fluidic structures

This places inkjet actuation in a **different category**  
from PID-based feedback control.

---

## 🧭 Design Intent

This visualization is designed under the following assumptions:

- Not CFD (qualitative, not quantitative)
- Causal structure prioritized over parameter precision
- Representation of a normally operating overdamped system

The goal is not numerical prediction, but:

> “Why does this phenomenon occur at *this* timing?”

—enabling rapid acquisition of **physical intuition**.

---

## 📐 How to Read the Visualization

- Horizontal axis: time (microsecond scale)
- Vertical axis: physical domains (top to bottom: electrical → mechanical → fluid)
- A single time cursor penetrates all domains
- Each domain’s marker represents the instantaneous state

It can be understood as:

> **An oscilloscope extended across physical domains**

rather than signals alone.

---

## 🔗 Live Demo (GitHub Pages)

An interactive browser-based demo is publicly available:

👉 [https://samizo-aitl.github.io/inkjet-timing/index.html](https://samizo-aitl.github.io/inkjet-timing/index.html)

- No installation required
- Fully browser-based
- Adjustable gains and timing
- Intended for education, explanation, and design reviews

---

## 🧩 Positioning Within AITL

In AITL (Architecture-Integrated Thinking Loop):

- PID: real-time feedback control
- FSM: state transition management
- Physical design: embedded stability

inkjet-timing represents a class of systems where:

- Behavior is determined by structure and timing
- Stability is inherent in physical design
- Causal relationships must be viewed holistically

Inkjet waveform design can thus be framed as:

> **A feed-forward control problem under strict physical constraints**

---

## 📜 License

### Code

Source code including HTML, JavaScript, and CSS  
is released under the **MIT License**.

### Conceptual Model and Explanations

Physical interpretation, causal structure, and design philosophy  
are provided for **educational and research purposes**.

When reusing the conceptual model or methodology,  
appropriate attribution is requested.

---

## 📝 Closing Remarks

This project is intentionally simplified.

It is **not**:

- A replacement for detailed simulation
- A production optimization tool

However, with respect to a single point—

> **“Seeing time and causality correctly”**

—it significantly advances understanding of inkjet system design.

---

**GitHub Repository**  
[https://github.com/Samizo-AITL/inkjet-timing](https://github.com/Samizo-AITL/inkjet-timing)

---
