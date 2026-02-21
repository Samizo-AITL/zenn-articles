---
layout: default
title: zenn-articles
---

# 【Semiconductor】🧱 23. OpenLane Is 90% About the Environment  
## WSL2, Docker, and PDK Pitfalls You Must Avoid

topics: ["OpenLane", "ASIC", "EDA", "Docker", "WSL"]

---

## 🧭 Introduction: Why Does OpenLane “Not Work”?

OpenLane is an **open-source ASIC design flow** that enables a full pipeline  
from **RTL to GDSII**.

🔗 Official repository:  
[https://github.com/The-OpenROAD-Project/OpenLane](https://github.com/The-OpenROAD-Project/OpenLane)

Despite this, users frequently report the following issues:

- ❌ Installation fails  
- ❌ The flow stops halfway  
- ❌ It worked yesterday, but is broken today  
- ❌ The tutorial was followed exactly, yet synthesis fails  

Let us start with the conclusion.

> ⚠️ **90% of OpenLane problems are caused by the environment.**

Before blaming RTL or constraints,  
**the environment itself is often already broken**.

This article is based on  
**Phase 1: Environment Survival** of the OpenLane Guide, and explains—  
with reasons, not procedures—

- 🧱 Why the order must never be skipped  
- 🔀 Why OpenLane1 and OpenLane2 must be separated  
- 📦 Why the PDK must be fixed  

📘 The original structured guide is available here:  
[https://samizo-aitl.github.io/openlane-guide/](https://samizo-aitl.github.io/openlane-guide/)

---

## 🧩 OpenLane Is Not a “Tool” — It Is an Environment

This mindset is essential.

OpenLane is **not a single tool**.

It is a tightly coupled environment consisting of:

- 🧠 Yosys (logic synthesis)  
- 🏗 OpenROAD (placement & routing)  
- 🧪 Magic / Netgen (DRC / LVS)  
- ⏱ STA / Tcl / Python / Make  

All of these are integrated **inside Docker containers**.

Therefore:

> 💥 When OpenLane breaks,  
> it means **something in WSL × Docker × Host OS × PDK is broken**.

---

## 🐳 WSL2 + Docker Desktop Is Not a Compromise

Common misconceptions include:

- 🤔 “Wouldn’t native Linux be faster?”  
- 🤔 “Is Docker really necessary?”  

These are **the first traps beginners fall into**.

### Why WSL2 + Docker?

There are three reasons:

1. 🧼 **To eliminate host OS differences**  
2. 🧨 **To contain dependency chaos**  
3. ♻️ **To operate under the assumption that environments are disposable**

OpenLane environments are **not meant to be grown long-term**.

> 🔁 **Reproducible containers that can be recreated at any time**

WSL2 + Docker Desktop fits this philosophy perfectly.

---

## 🔀 Mixing OpenLane1 and OpenLane2 Will Break Everything

This is the **most common and most destructive failure point**.

### Fundamentally Different Design Philosophies

| Item | OpenLane1 | OpenLane2 |
|---|---|---|
| 🎯 Purpose | Stable operation | Experimentation |
| 🧭 Flow | Makefile-based | Python-based |
| 📦 PDK | Fixed | Variable |
| ♻️ Reproducibility | High | Low |

**They are not designed to coexist.**

If they share the same WSL, Docker setup, or PDK path,  
🚨 **failure is guaranteed**.

> “After testing OpenLane2, OpenLane1 stopped working.”

This is not a bug.  
It is **the expected outcome**.

---

## 📦 Using the “Latest” PDK Is the Worst Choice

Beginners often say:

> ✨ “I want to use the latest PDK.”

This is a **fatal mistake**.

### A PDK Is a Massive Set of Assumptions

A PDK is not just data.

It defines:

- ⚡ SPICE models  
- 📐 LEF / DEF  
- ⏱ Timing models  
- 🧪 DRC rules  

Changing the PDK means:

> 🔄 **All design assumptions change.**

### The Only Correct Rule

- 📌 Fix the PDK  
- 🔗 Fix it together with the OpenLane version  
- 🧪 Test updates only in separate environments  

Without this discipline,  
**reproducibility is impossible**, especially for CI or education.

---

## ⚖️ Broken Environments vs. Stable Environments

### 💣 Characteristics of Broken Environments

- OpenLane1 and 2 mixed together  
- PDK updated mid-project  
- Docker images treated as persistent assets  
- No environment export  

### 🛡 Characteristics of Stable Environments

- Clear separation by purpose  
- Fixed PDK  
- Disposable Docker containers  
- Export / Import as standard practice  

---

## 💾 WSL Export / Import Is Not a Backup

WSL Export / Import is **not disaster recovery**.

> 🔑 **It is a required operational mechanism.**

- 📤 Export when the environment works  
- 🧪 Export before experiments  
- 📥 Import immediately when broken  

Ignoring this guarantees eventual failure.

---

## 🧱 Why the Order Must Never Be Skipped

The OpenLane Guide strictly enforces order for a reason.

> ❗ **If the environment is broken,  
> physical design and timing analysis are meaningless.**

---

## 📝 Summary

- 🧠 OpenLane is 90% environment  
- 🐳 WSL2 + Docker is mandatory  
- 🔀 OpenLane1 and OpenLane2 must be separated  
- 📦 PDK must be fixed  
- 💾 Export / Import is part of normal operation  

This is the conclusion of  
**Phase 1: Environment Survival**.

---

## ▶️ Next Article

Next is **Phase 2: Physical Design Reality**.

- 🏗 Why automated flows fail  
- ⏱ Why timing suddenly collapses  
- 👀 What you must inspect in the GUI  

**OpenLane is not magic.**  
We will expose the physical reality behind the automation.
