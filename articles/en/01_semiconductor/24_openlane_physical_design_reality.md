---
layout: default
title: zenn-articles
---

# 【Semiconductor】🏗️ 24. OpenLane Automation Is Not Magic  
## The Reality of Placement, Routing, and Clocks

topics: ["OpenLane", "ASIC", "PhysicalDesign", "OpenROAD", "EDA"]

---

## 🧭 Introduction: “One Command to GDS” Is an Illusion

Anyone who starts using OpenLane  
eventually thinks this at least once:

> ▶️ “If I run `make run`, GDS will just come out automatically, right?”

This is **half true—and half completely wrong**.

OpenLane *can* automatically run  
**RTL → GDSII**.

However, this is only possible for  
**designs that are physically feasible**.

This article is based on  
OpenLane Guide **Phase 2: Physical Design Reality**, and explains:

- Why automated flows fail  
- Why timing suddenly collapses  
- What you must inspect in the GUI  

—all from the perspective of **physical design reality**.

🔗 OpenLane official repository  
[https://github.com/The-OpenROAD-Project/OpenLane](https://github.com/The-OpenROAD-Project/OpenLane)

🔗 Structured guide (source material)  
[https://samizo-aitl.github.io/openlane-guide/](https://samizo-aitl.github.io/openlane-guide/)

---

## 🧩 What OpenLane Really Is: OpenROAD-Based Physical Design

The physical design part of OpenLane  
is built around **OpenROAD**.

- 🧱 Placement  
- 🌳 CTS (Clock Tree Synthesis)  
- 🧵 Routing  
- ⏱ STA (Static Timing Analysis)  

These are **not independent stages**.

> 🔗 **They form a single, tightly coupled physical problem.**

---

## 🧱 Placement: Where Almost Everything Is Decided

Placement determines  
**nearly 90% of what happens later**.

- Standard cell density  
- White space around macros  
- Routing congestion  

If you push too hard here:

- Routing fails  
- CTS cannot build a clock tree  
- STA suddenly loses all slack  

This leads to **cascading failures**.

> ⚠️ A design broken at placement  
> is almost never recoverable later.

---

## 🌳 CTS: A Clock Is Not Just a Signal

Many beginners misunderstand CTS.

> ⏱ “A clock is just another signal, right?”

**Absolutely not.**

A clock is a **privileged net**:

- It must reach every sequential element  
- Skew control is critical  
- Its delay *defines* design constraints  

When CTS breaks:

- Setup and Hold collapse simultaneously  
- Buffer counts explode  
- Power consumption skyrockets  

---

## 🧵 Routing: Not the “Final Step”

Many people think routing is simply  
the final step after placement and CTS.

> 🧵 “Routing comes last, right?”

This is another misconception.

In reality:

- Routing congestion is mostly decided during placement  
- Clock routing directions are fixed during CTS  

Routing merely **makes the consequences visible**.

> ❗ If massive DRC errors appear during routing,  
> the real problem occurred much earlier.

---

## ⚖️ The Three-Way Tradeoff: Area, Routing, and Clock

Most failed OpenLane designs fall into this trap:

- 📐 Minimize area  
- 🧵 Avoid routing congestion  
- ⏱ Increase clock frequency  

These **cannot all be satisfied at once**.

Improving one inevitably sacrifices another.

OpenLane is **not a magical tool**  
that resolves this contradiction automatically.

---

## 👀 Inspect Failure in the GUI

If you use OpenLane,  
**you must inspect the GUI (OpenROAD / Magic)**.

Key things to check:

- ❌ Abnormally dense standard cell regions  
- ❌ Excessive clock buffers  
- ❌ Localized routing congestion (red-hot regions)  

> 👁 **If it looks wrong, it will not work.**

In many cases,  
the layout view is more honest than STA logs.

---

## 🧠 The Philosophy and Limits of OpenROAD

OpenROAD is powerful—but not omnipotent.

- It cannot fully understand human intent  
- Unrealistic constraints fail as-is  
- It does not make design decisions for you  

OpenLane is:

> 🤖 **Not a tool that thinks instead of the designer**

This must be clearly understood.

---

## 🧱 Why Automated Flows Suddenly Break

The reason is simple:

> ⚠️ **A physically impossible design  
> cannot be made possible by automation**

If the environment (Phase 1) is correct  
and the flow still fails,

**the cause is almost always physical design.**

---

## 📝 Summary

- 🏗 Placement is the starting point of everything  
- 🌳 Clocks are privileged nets  
- 🧵 Routing visualizes earlier decisions  
- ⚖️ Tradeoffs are unavoidable  
- 👀 Designs not checked in the GUI are dangerous  

This is the conclusion of  
**Phase 2: Physical Design Reality**.

---

## ▶️ Next Article

Next is **Phase 3: Integration & Timing Truth**.

- ⏱ Can STA really be trusted?  
- 🔗 What do SDF and GLS actually guarantee?  
- ❓ Why does “STA pass but silicon fail”?  

**Does timing lie?**  
We will answer this question directly.
