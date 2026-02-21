---
layout: default
title: zenn-articles
---

# 【Semiconductor】🧠 00. OpenLane Overview | Beginner-friendly · One Article to See the Whole Picture
topics: ["OpenLane", "EDA", "VLSI", "Semiconductor", "SKY130"]

---

This article is written for **people who are touching OpenLane for the first time**.

👉 **What kind of tool OpenLane actually is**  
👉 **What you should expect / should NOT expect from it**  
👉 **What you should understand next after this article**

All of these are organized so that **you can grasp the whole picture in a single read**.

⚠️ This article does **not** explain commands or step-by-step procedures.  
⚠️ The top priority here is to **understand the overall structure correctly**.

---

## 🧩 1. What is OpenLane?

**OpenLane is an open-source physical design flow that runs from RTL (Verilog) to GDS in one go.**

### 📥 Inputs
- Verilog RTL
- Constraints such as clock and I/O information

### 📤 Outputs
- GDS (final layout data)

### 🎯 Target
- Digital ASIC designs  
- Mainly **SKY130 PDK**

👉 You can think of OpenLane as  
**“a fixed flow that executes synthesis, placement, routing, and DRC/LVS end-to-end.”**

---

## 🚧 2. Why OpenLane Exists

Traditional ASIC design environments have long suffered from:

- 💸 Extremely expensive commercial EDA tools  
- 🧵 Complex tool integration and configuration  
- 📚 Very high learning costs  

OpenLane was created to address these issues by:

- Combining open-source EDA tools  
- Fixing the overall flow in advance  
- Allowing designers to **experience the full RTL → GDS process**

---

## 🧰 3. What’s Inside OpenLane (Tool Composition)

OpenLane itself is **not** a single EDA tool.  
It is a **flow manager** that runs multiple EDA tools in a predefined order.

| Stage | Tool | Role |
|---|---|---|
| Logic synthesis | Yosys | RTL → gates |
| Placement | RePlAce | Standard-cell placement |
| CTS | TritonCTS | Clock tree generation |
| Routing | TritonRoute | Signal routing |
| Verification | Magic / Netgen | DRC / LVS |

👉 OpenLane does **not** design circuits by itself.  
👉 It acts as a **controller that drives tools in the correct sequence**.

---

## 🔁 4. Basic Flow (Fixed Order)

The processing order in OpenLane is **always fixed**:

1. Load RTL  
2. Logic synthesis  
3. Floorplanning  
4. Standard-cell placement  
5. Clock Tree Synthesis (CTS)  
6. Signal routing  
7. DRC / LVS  
8. GDS generation  

⚠️ **This order never changes.**

---

## 🤯 5. Common Misunderstandings with OpenLane

The following misunderstandings arise **naturally from OpenLane’s characteristics**.

### ❌ “It’s automatic, so everything will pass”
👉 **No.**  
If the RTL is problematic, synthesis or routing will fail normally.

### ❌ “Tuning parameters will fix everything”
👉 **If the design itself is broken, tuning will not save it.**

### ❌ “It can replace commercial EDA tools”
👉 **Its main purpose is learning, experimentation, and understanding.**

OpenLane is  
🪞 **a tool that exposes the reality of physical design.**

---

## 🪜 6. Recommended Learning Order

The recommended way to proceed is:

1. 🧠 **Understand the big picture with this article**  
2. ▶️ Run a minimal RTL and generate GDS  
3. 📄 Read the logs  
4. 💥 Understand why failures occur  
5. 🔧 Adjust parameters only when necessary  

👉 **Do not aim for optimization from the beginning.**

---

## ✅ 7. What OpenLane Can / Cannot Do

### ✅ Can do
- Provide an end-to-end RTL → GDS experience  
- Help you understand the full physical design flow  
- Enable failure analysis through logs  

### ❌ Cannot do
- Design high-performance production ASICs  
- Match commercial EDA-level optimization  
- Fully automate physical design without human judgment  

---

## 🗺 8. Position of This Article (00)

This article is:

- Not a step-by-step guide  
- Not an experiment log  

👉 It serves as **the map for the entire OpenLane article series**.

Subsequent articles will cover:

- Minimal flows  
- Practical design examples  
- Failure cases and operational lessons  

---

## 📘 9. What to Read Next

- **09. Running OpenLane with a Minimal RTL (No Tuning)**  
  - Observe what happens with default settings

---

## 🏁 Summary

- OpenLane is a learning-oriented RTL → GDS physical design flow  
- It is automatic, but not omnipotent  
- **Understanding the overall structure comes first**

If you get lost, **come back to this article (00).**
