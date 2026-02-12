---
layout: default
title: zenn-articles
---

# 【Mechanical Design】📦 08. Organizing the Workflow from Design to Mass Production Ordering with BOM
topics: ["BOM", "Mechanical Design", "Manufacturing", "Design Process", "PLM"]

---

## 🎯 1. Purpose of This Article

This article organizes a typical workflow in manufacturing:

**Design → Engineering → Procurement → Mass Production Ordering**

and clarifies the role played by the **BOM (Bill of Materials)** within this process.

The content is based on the generalized model described in the following educational material:

- 📘 Reference material:  
  [https://samizo-aitl.github.io/EduMecha/08_production_process/](https://samizo-aitl.github.io/EduMecha/08_production_process/)

---

## 🔄 2. Typical Workflow from Design to Mass Production Ordering

In many manufacturing environments, the workflow proceeds as follows:

- ✏️ Design drawing review  
- 🛠 Engineering drawing development  
- 📤 Distribution to related departments  
- 📋 BOM linkage  
- 🏭 Procurement and mass production ordering  

This flow itself is not unusual.  
The key point is whether **the information generated at each step is correctly handed over to the next step**.

---

## 🧩 3. Information Generated at Each Stage

### ✏️ 3.1 Design Drawing Review
- Design intent  
- Requirements and specifications  
- Functional and performance conditions  

### 🛠 3.2 Engineering Drawing Development
- Manufacturing conditions  
- Materials  
- Tolerances  
- Inspection criteria  

### 📤 3.3 Distribution to Related Departments
- Engineering notices  
- Evaluation results  
- Preconditions for manufacturing and procurement  

Although this information may be valid within each individual stage,  
**it becomes difficult to reuse if the relationships between stages are lost**.

---

## 📋 4. Role of the BOM

The BOM is management information that links the following elements:

- 🧱 Part structure (parent-child relationships and quantities)  
- 📐 Drawings and specifications  
- 🧪 Technical conditions  
- 🚚 Procurement conditions  

The BOM functions as a **connection point that transforms design information into a form usable for procurement and production**.

---

## ⚠️ 5. Problems When the BOM Is Weak

When the BOM is treated as a simple parts list, the following issues tend to occur:

- ❌ The impact range of design changes cannot be identified  
- ❌ Procurement decisions become case-by-case  
- ❌ Mismatches in conditions appear in downstream processes  

These are not individual mistakes, but  
**structural problems in information management**.

---

## 🧠 6. Information Aggregated in the BOM

At a minimum, the BOM aggregates the following information:

- 🔗 Parent-child structure and quantities  
- 📄 Referenced drawings  
- 🧪 Technical conditions  
- 🚚 Procurement conditions  

When this information is managed consistently,  
the effort required to confirm changes during design revisions or mass production ramp-up can be minimized.

---

## ✅ 7. Summary

This article organized:

- 🔄 A typical workflow from design to mass production ordering  
- 📋 The role played by the BOM within that workflow  

A BOM is not merely a parts list.  
It is a **management unit that connects design information to mass production operations**.

In the next article, we will organize  
the **🧩 part numbering system and operational rules** required to operate the BOM in a stable manner.
