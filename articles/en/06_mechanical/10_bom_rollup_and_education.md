---
layout: default
title: zenn-articles
---

# 【Mechanical Design】📈 10. Becoming Resilient to Design Changes with Roll-up Management
topics: ["BOM", "Design Changes", "Quality", "Manufacturing", "PLM"]

---

## 🎯 1. Purpose of This Article

This article organizes the concept of **Roll-up management**,  
which aggregates and evaluates information attached to a BOM from

**Parts → Sub-Assemblies → Product**

from the perspective of BOM operation.

It explains how Roll-up management supports:

- Identifying the impact range of design changes  
- Clarifying the basis for decision-making  

The content is based on the BOM attribute management and evaluation model described in the following educational material:

- 📘 Reference material:  
  [https://samizo-aitl.github.io/EduMecha/08_production_process/06_bom_generation/](https://samizo-aitl.github.io/EduMecha/08_production_process/06_bom_generation/)

---

## 🧾 2. Why Attribute Management Is Necessary

Some information may not be visible at the design stage,  
but becomes essential in downstream processes.

- 🌱 Environmental compliance (RoHS / REACH)  
- 💰 Cost  
- 🌍 Export control (classification, HS code)  

If this information is collected only after the fact,  
confirmation work becomes case-by-case and reproducibility is lost.

---

## 🔗 3. Managing Attributes at the Part Level

The premise of Roll-up management is clear.

- Attributes are managed at the **minimum unit (part)**  
- Decisions are made at the **product level**  

Therefore, the BOM manages the following information for each part:

- 📄 Referenced drawings  
- 🧪 Environmental attributes  
- 💰 Cost information  
- 🌍 Export-related information  

---

## 📈 4. Basic Structure of Roll-up Management

In Roll-up management, information is aggregated in the following order:

- Part level  
- Sub-assembly level  
- Product BOM level  

Through this aggregation, the product can be evaluated **simultaneously** in terms of:

- Environmental compliance  
- Cost  
- Export eligibility  

---

## ⚡ 5. Behavior During Design Changes

When a design change occurs,

- Update the part information  
- Re-evaluate the BOM  

This alone makes it possible to identify:

- Which assemblies are affected  
- Whether the impact propagates to the entire product  

This mechanism is  
**not for speeding up design changes**,  
but **for preventing incorrect decisions**.

---

## 🎓 6. Effects on Education and Standardization

Roll-up management is also well suited for:

- New engineer training  
- Design standardization  
- Audit 대응 (audit readiness)  

Because decision criteria are  
**explicitly defined in the BOM and its attributes**,  
the need for explanation based on personal experience is reduced.

---

## ✅ 7. Summary

This article organized:

- 📈 The concept of Roll-up management  
- 🔗 Methods for aggregating part attributes  
- ⚡ Evaluation procedures during design changes  

Roll-up management extends the BOM  
from a simple parts list to an **evaluation infrastructure**.

As a result,  
design changes, mass production ramp-up, and audit 대응  
can all be handled using the same information structure.
