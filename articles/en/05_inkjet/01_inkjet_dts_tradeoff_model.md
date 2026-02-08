---
layout: default
title: zenn-articles
---

# 【Inkjet】🖨️ 01. Inkjet DTS: Design Trade-offs Between Drop Density, Throughput, and Spread
topics: ["inkjet", "design", "trade-off", "modeling", "DTS"]

---

## 📌 Introduction

Inkjet technology has evolved under conflicting requirements such as  
**higher resolution, higher speed, and stable print quality**.

In practice, engineers frequently face questions like:

- Why does print quality degrade when speed increases?  
- Why do higher dot densities cause bleeding and non-uniformity?  
- Where exactly is the *design limit*?  

This article introduces the **Inkjet DTS (Density–Throughput–Spread) model**,  
which organizes these questions **not as empirical know-how**,  
but as a **design-oriented trade-off model**.

This model is intended:

👉 not to explain inkjet physics itself, but  
👉 to provide a **minimal framework to support design decisions**.

---

## 🧩 What Is Inkjet DTS?

**Inkjet DTS** abstracts inkjet printing using three variables:

| Symbol | Meaning | Design Interpretation |
|---|---|---|
| D | Drop Density | Dot density (resolution, gradation) |
| T | Throughput | Throughput (speed, productivity) |
| S | Spread | Dot spread (bleeding, image degradation) |

These three variables are **not independent**.  
They are inherently linked by **unavoidable trade-offs**.

> Increasing D tends to worsen S  
> Increasing T tends to increase S  
> Suppressing S constrains achievable D and T  

Inkjet DTS visualizes this **inevitable relationship as a structure**,  
rather than treating it as scattered empirical rules.

---

## 🧠 Why Modeling Is Necessary

Inkjet development routinely involves decisions such as:

- Reducing nozzle pitch  
- Increasing carriage or transport speed  
- Modifying ink viscosity or surface tension  
- Adjusting drying or fixation conditions  

In many cases, these decisions rely heavily on:

- Local optimization  
- Generation-specific constraints  
- Tacit knowledge of experienced engineers  

Inkjet DTS aims to:

- **Create a shared design language**
- **Elevate discussion from intuition to structure**
- **Provide a comparison axis for next-generation technologies**

---

## 📐 Fundamental DTS Relationship (Conceptual Model)

Inkjet DTS assumes the following conceptual relationships:

- Dot spread S increases as a function of  
  drop density D and throughput T
- Design is the problem of  
  **maximizing D and T while keeping S within an acceptable range**

This is not a strict physical or mathematical model,  
but a **coarse-grained abstraction usable for design decisions**.

This intentional simplification allows:

- Technology-independent discussion  
- Applicability across different head architectures  
- Consistent reasoning across generations  

---

## 📊 Visualization and Design Insight

By visualizing the D–T–S space, Inkjet DTS reveals:

- Regions that are physically unsafe  
- Regions where control or compensation is feasible  
- Regions dominated by material limitations  

In other words:

> **Design limits appear not as a single line, but as a surface.**

This provides structural answers to questions like:  
“Why does this condition fail?”

---

## 🧭 Positioning of Inkjet DTS

Inkjet DTS is:

- Not a replacement for CFD or detailed physical simulations  
- Not a rejection of experiments or measurements  

Instead, it serves as a **design framework** for:

- Pre-experimental condition setting  
- Early-stage technology comparison  
- Design reviews, education, and discussions  

---

## 🔗 Implementation and Demo Page

The Inkjet DTS concept is published with  
**visualizations, demos, and implementation examples** at the following site:

👉 **Inkjet DTS Demo Page**  
[https://samizo-aitl.github.io/inkjet-dts/](https://samizo-aitl.github.io/inkjet-dts/)

For design philosophy, visualization examples, and model structure,  
please refer to the above page.

---

## 📝 Summary

- Inkjet DTS is an **abstract design model for inkjet systems**
- It structures the D–T–S trade-off explicitly
- It elevates empirical knowledge into a **design language**
- It is applicable across technologies and generations

For those who want to treat inkjet technology  
not merely as a phenomenon, but as a **design problem**,  
this model is intended to serve as a stable thinking framework.

---
