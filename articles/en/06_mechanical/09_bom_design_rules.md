---
layout: default
title: zenn-articles
---

# 【Mechanical Design】🧩 09. Practical BOM Operation Rules Using a 6-Digit Code + Suffix
topics: ["BOM", "Part Numbering", "Mechanical Design", "Manufacturing", "PLM"]

---

## 🎯 1. Purpose of This Article

This article organizes the **part numbering system and operational rules** that are essential for stable BOM operation.

In particular, it clarifies, from a practical viewpoint:

- Why part number design is critical  
- How to properly distinguish between a 6-digit code and a suffix  

The content is based on the BOM generation and operation rules described in the following educational material:

- 📘 Reference material:  
  [https://samizo-aitl.github.io/EduMecha/08_production_process/06_bom_generation/](https://samizo-aitl.github.io/EduMecha/08_production_process/06_bom_generation/)

---

## 🧱 2. A Part Number Is Not Just an Identifier

A part number is not merely a management ID.

It is a **design rule** that fixes:

- Design decisions  
- Boundaries of change  
- Units of management responsibility  

If this is ambiguous, a BOM cannot be operated reliably over the long term.

---

## 🔢 3. Basic Structure of the 6-Digit Code + Suffix

The basic structure of the part number discussed in this article is as follows:

- 6-digit code: represents parts that are functionally identical  
- Suffix: represents minor changes or differences in manufacturing conditions  

This separation makes it possible to clearly distinguish between:

- Functional changes  
- Conditional or manufacturing changes  

---

## ⚖️ 4. Criteria for Functional vs. Minor Changes

The basic operational rule in practice is simple.

### ✅ When to Issue a New 6-Digit Code
- Function or performance changes  
- Intended use or role changes  

### 🔁 When to Manage with a Suffix
- Minor dimensional adjustments  
- Surface treatment changes  
- Manufacturing conditions or production site differences  

Not crossing this boundary is the most important point for keeping the BOM stable.

---

## 🧪 5. Special Handling of Material Codes (Leading Digit = 6)

Materials are directly related to:

- 🌱 Environmental regulations  
- 🔥 Hazardous material control  
- 🌍 Export control  

Therefore, material codes are managed under the assumption that they are **always accompanied by attribute information** such as SDS, regulatory data, and export-related information.

---

## 🧠 6. Effects of Proper Part Number Design

When the part numbering system is well organized, the following benefits are obtained:

- 🔍 The impact range of design changes becomes clear  
- 🔄 Decisions on BOM revisions can be made more quickly  
- 📋 Coordination with procurement, quality, and export control becomes easier  

This is not a tool issue, but a **rule design issue**.

---

## ✅ 7. Summary

This article organized:

- 🧩 The concept of part numbering systems  
- 🔢 How to distinguish between 6-digit codes and suffixes  
- 🧪 The special nature of material codes  

The success or failure of BOM operation is **largely determined by part number design**.

In the next article, we will move on to  
how to **add and evaluate attribute information in the BOM**,  
specifically focusing on **📈 Roll-up management**.
