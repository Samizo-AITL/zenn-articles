---
layout: default
title: OpenLane1
---

# 【Semiconductor:12】🧰 OpenLane1  
### — Building a Reproducible RTL→GDS Environment with WSL2 + Docker
topics: ["openlane", "asic", "eda", "docker", "wsl2"]

---

## 🧭 Introduction

OpenLane is an **open-source ASIC design flow**  
that enables an end-to-end process from **RTL to GDSII**.

However, the first and most common hurdle is always  
**environment setup**.

- Many tools are involved  
- OS dependencies exist  
- It is unclear what exactly counts as “success”  

This article deliberately narrows the objective:

> **Before trying to “understand” OpenLane,  
> first make it run all the way to the end once.**

To achieve that, we focus on **OpenLane1 (Docker-based)**  
and explain how to set up a **reproducible environment**.

---

## 🧱 What Is OpenLane1? (Assumptions of This Article)

There are currently two major OpenLane lineages:

- **OpenLane1**: the traditional Docker-based flow  
- OpenLane2: the newer Python-based flow (Nix recommended)  

This article covers **OpenLane1 only**.

Key characteristics of OpenLane1:

- Environment is fixed and isolated via Docker  
- Widely used in education and PoC contexts  
- Well suited for experiencing the entire flow end-to-end  

👉 **Chosen to prioritize understanding the design flow, not the environment itself.**

---

## 🖥 Assumed Environment (Fixed)

To ensure reproducibility, the following setup is assumed:

- Windows 11  
- WSL2  
- Ubuntu 22.04 (inside WSL)  
- Docker Desktop (with WSL integration enabled)  

macOS or native Linux setups also work,  
but are **out of scope for this article**.

---

## 🛠 Prerequisites (Essentials Only)

### WSL2

- Enable WSL2  
- Install Ubuntu 22.04  

Follow Microsoft’s official documentation for detailed steps.

---

### Docker Desktop

- Install Docker Desktop  
- Enable **Settings → Resources → WSL integration**  
- Check Ubuntu 22.04 as the target distribution  

If this is disabled, **OpenLane will not run**.

---

## 📦 Obtaining and Building OpenLane1

All operations are performed inside Ubuntu on WSL2.

```bash
cd ~
git clone https://github.com/The-OpenROAD-Project/OpenLane.git
cd OpenLane
make
```

- Docker images will be built  
- The first build requires time and disk space  

---

## ✅ Verification (Most Important Step)

Always run **`make test`**.

```bash
make test
```

### What `make test` Means

This checks whether:

- Synthesis  
- Place & route  
- Verification tools  

can all **launch and execute successfully**.

> If this step fails,  
> **OpenLane cannot be used in that environment.**

Do not proceed—fix the environment first.

---

## 🎯 First Success Experience (GDS Generation)

Once the test passes, run a sample design.

```bash
make mount
```

Inside the container:

```bash
cd designs/spm
flow.tcl -interactive
```

Run the flow to completion and confirm that  
a **GDS file is generated** under the `runs/` directory.

Note: sample designs and exact steps may vary  
depending on the OpenLane version.  
Always consult the official README as well.

---

## ⚠ Common Pitfalls (Typical Cases)

### Docker / WSL2 Issues

- Docker Desktop not running  
- WSL integration disabled  
- Insufficient memory allocated to WSL2  

---

### File Location

- Running from a Windows-mounted directory  
  → **Place the project inside the WSL filesystem**  

---

### GUI-Related Issues

- DISPLAY errors  
  → Avoid GUI usage in the initial setup  

---

## 🧠 Why Start with OpenLane1?

OpenLane1 excels because:

- You do not need deep environment knowledge  
- You can experience the **entire design flow once**  

> OpenLane1 is not just an EDA tool—  
> it is **educational infrastructure for completing a full design loop**.

---

## 🚀 Next Steps

- Run your own RTL  
- Adjust constraints (clock, floorplan)  
- Consider the alternative lineage: OpenLane2  

In the next article, we will address:

> **Why OpenLane2 exists as a separate lineage at all**

from a design-philosophy perspective.

---

## 📝 Summary

- OpenLane1 is the shortest path to “making it run”  
- Passing `make test` is the minimum requirement  
- If GDS is generated, it is a success  
- Deep optimization and extensions come later  

First, run the loop once.
