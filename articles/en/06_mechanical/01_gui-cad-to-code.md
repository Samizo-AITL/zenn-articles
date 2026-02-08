---
layout: default
title: zenn-articles
---

# 【Mechanical Design】🛠️ 01. Escaping GUI CAD: Thinking of Mechanical Design as Code
topics: ["mechanical design", "cad", "python", "design philosophy"]

---

## 📌 Introduction

Most mechanical design today is done using GUI-based CAD tools.  
Have you ever thought:

> “If I were asked to recreate this design again, it would be a pain”?

When you try to treat a design as a **reusable asset**,  
purely GUI-driven workflows quickly reach their limits.

In this article, we introduce an alternative approach:  
**describing mechanical design as code rather than GUI operations**.

This design philosophy is called  
**Full Code Mechanical Design**.

---

## ⚠️ The Limitations of GUI CAD

GUI CAD tools are extremely powerful for creating shapes.  
However, they have a major weakness:  
**design intent and reasoning are hard to preserve**.

For example:

- Why was this dimension chosen?
- Which parameters cause the shape to change?
- Can this design be reused elsewhere?

Such information is often buried inside  
operation histories or feature trees.

As a result, designs tend to become  
**one-off artifacts**, making reuse and automation difficult.

---

## 💡 The Idea of Writing Design as Code

When people hear “design as code,” they often think:

> “Are you saying we should abandon CAD?”

That is not the idea.

Code-based design does **not** reject CAD.  
Instead, it means:

- Defining designs as **parameters**
- Expressing design decisions as **conditional logic**
- Preserving design rules as **functions and structures**

The focus shifts from the final shape to  
**the rules that generate the shape**.

---

## 🧠 What Is Full Code Mechanical Design?

In Full Code Mechanical Design:

- Drawings and GUI operations are not the primary deliverables
- The design itself is considered to be the **code**
- CAD is used for visualization and verification

The code explicitly captures:

- Dimensional dependencies
- Constraint conditions
- Design intent

This makes it possible to answer the question:

> “Why does this shape exist in this form?”

even long after the design was created.

---

## 🔍 GUI Operations vs. Code-Based Design

The differences between GUI CAD and code-based design can be summarized as follows:

| Perspective | GUI CAD | Code-Based Design |
|---|---|---|
| Reproducibility | Human-dependent | High |
| Version control | Difficult | Easy with Git |
| Design intent | Hard to preserve | Explicit |
| Reuse | Manual | Parameter-driven |

In particular, **diffability** is a major advantage  
for design reviews and long-term maintenance.

---

## 🎯 Who Is This Approach For?

This philosophy is not suitable for everyone.

It works especially well for people who:

- Rebuild designs repeatedly
- Generate many similar geometries
- Want to share or teach design rules
- Are comfortable with Python or coding in general

For one-off or single-shot designs,  
GUI CAD may still be the faster option.

---

## 🪜 How to Start Small

There is no need to convert everything to code at once.

Good entry points include:

- Writing dimension calculations as code
- Managing parameter tables in code
- Automating only part of the geometry generation

A **hybrid approach**—combining GUI CAD and code—is often the most practical.

---

## 📝 Conclusion

Writing mechanical design as code is not just about efficiency.

It is a way to transform design from  
**a one-time task** into  
**a reusable knowledge asset**.

Rather than rejecting GUI CAD,  
this approach complements it by addressing its limitations.

Simply having “code-based design” as an option  
greatly expands your design freedom.

---

## 📎 Additional Notes

This article focuses on organizing the concept of  
mechanical design as code.

Implementation examples, concrete design code,  
and license management are maintained here:

- [https://samizo-aitl.github.io/full-code-mechanical-design/](https://samizo-aitl.github.io/full-code-mechanical-design/)

---
