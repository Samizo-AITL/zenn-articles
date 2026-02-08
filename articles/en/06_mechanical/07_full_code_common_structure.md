---
layout: default
title: zenn-articles
---

# 【Mechanical Design】🧠 07. What Is Full Code Design? — A Common Structure Shared by FreeCAD, LaTeX, and Klayout
topics: ["design philosophy", "CAD", "FreeCAD", "LaTeX", "Klayout", "Git"]

---

## 🏁 Introduction (Final Chapter)

In this series, starting from mechanical design,  
we have explored the idea of **reconstructing design with “code as the subject.”**

We have covered:

- The limitations of GUI CAD  
- Using FreeCAD in a code-driven manner  
- A realistic division of roles between GUI and code  
- Design where diffs gain meaning through Git  
- FreeCAD as a geometric engine  

In this final article, we take one step back and abstract the discussion to answer a single question:

> **What was Full Code Design, in the end?**

---

## 🔑 The Essence of Full Code Design

Let us start with the conclusion.

> **Full Code Design is a design approach in which the primary source of truth is not the artifact, but its generator.**

Here, “generator” refers to:

- Code that generates CAD models  
- LaTeX that generates PDFs  
- Scripts that generate layouts  
- RTL that describes circuits  

GUI files, PDFs, STEP files, and GDS are not rejected.  
However, they are **not treated as the core of the design**.

---

## 📄 The Limitations of Artifact-Centered Design

In many design environments, implicitly:

- Drawings  
- CAD files  
- PDFs  

are treated as the “authoritative” source.

In such a structure:

- Why a dimension exists  
- What changes affect what  
- What design decisions were made  

**do not remain as history**.

Design changes become “work,”  
and diffs **lose their meaning**.

---

## 🧩 A Common Structure in Full Code Design

Although the fields differ, the structure is the same.

```text
[ Generator (Code) ]
        ↓
[ Artifact (for viewing / manufacturing) ]
```

Examples include:

- FreeCAD  
  - Python / parameters  
  - → STEP / drawings  

- LaTeX  
  - .tex  
  - → PDF  

- Klayout  
  - .ly / .py  
  - → GDS  

- RTL  
  - .v / .sv  
  - → netlists / layout  

**All design changes return to the generator.**  
This is the common structure of Full Code Design.

---

## 🧮 Why Diffs Gain Meaning

When the generator is code:

- Dimension changes  
- Condition changes  
- Rule changes  

all become **textual diffs**.

Those diffs can include:

- What was changed  
- Where it was changed  
- Why it was changed (comments)  

As a result,  
**design reviews become possible**.

---

## 🖥 Are GUIs Unnecessary?

No, they are not.

It is important to emphasize that Full Code Design:

- Does not reject GUIs  
- Is not automation absolutism  

GUIs are extremely effective for:

- Visualization  
- Verification  
- Exploration  

What matters is that  
**GUI operations do not become the primary source of design information**.

---

## ⚖️ How Far Should Design Be Coded?

Not everything needs to be coded.

- Fine shape adjustments  
- Aesthetic considerations  
- One-off experiments  

If everything is coded, design can actually break down.

The key is this:

> **Only leave in code the decisions you want to be able to explain later.**

---

## ✅ A Practical Test for Full Code Design

In real work, these questions are sufficient:

- Do modifications return to the generator, not the artifact?  
- Can artifacts be deleted and regenerated?  
- Can you understand changes by reading the diff?  

If the answer is YES,  
the design qualifies as Full Code Design.

---

## 🎯 Closing Remarks

What this series has discussed is not a new technology.

It is simply a matter of  
**aligning, as a structure, the discomfort many designers have long felt.**

Design moves from:

- Work  
- Individual craftsmanship  
- One-off artifacts  

to **long-term, reusable assets**.

If this series has helped clarify one way of organizing that transition,  
it has fulfilled its purpose.

---

**Full Code Mechanical Design / End**

---
