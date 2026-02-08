---
layout: default
title: zenn-articles
---

# 【Mechanical Design】🛠️ 05. When Design Becomes Code, Diffs Gain Meaning — The Fundamental Difference from GUI CAD
topics: ["mechanical design", "cad", "git", "freecad", "design philosophy"]

---

## 🧭 Introduction

In the previous articles, we have covered:

- Describing design as code  
- Generating geometry with FreeCAD  
- Introducing code-based design without abandoning Part Design  

Now comes the final question:

> **Why go this far to turn design into code?**

One clear answer is this:

> **When design is coded, “diffs” become design.**

---

## 🧩 Why Diffs in GUI CAD Rarely Carry Meaning

GUI CAD systems do preserve histories and feature trees.  
Yet many engineers have experienced this:

- You cannot tell what exactly changed  
- You cannot trace why a dimension was modified  
- During reviews, someone asks: *“So… what changed?”*

GUI-based workflows preserve results,  
but **they do not preserve intent well**.

This is a structural limitation.

---

## 🧠 In Code-Based Design, Diffs *Are* Design Changes

In code-based design,  
a design change is simply a **text diff**.

For example, changing the length of a plate:

```diff
- LEN = 120.0  # mm
+ LEN = 160.0  # mm
```

From this alone, you immediately know:

- What changed  
- Where it changed  
- What may be affected  

No additional explanation is required.

---

## 🧪 Design Decisions Themselves Become Diffs

Not only dimensions,  
but **design rules themselves** become visible changes.

```diff
- if LEN > 100:
-     THK = 8.0
+ if LEN > 150:
+     THK = 10.0
```

This is nearly impossible to achieve with GUI CAD.

Here, the diff explicitly records:

- Why the thickness changed  
- Under what condition it changed  

The **design logic itself is preserved**.

---

## 🧾 Design Reviews Become Feasible

Once design is coded and managed with Git,  
**design reviews become real**.

- Reasons for numeric changes can be commented  
- Reviews happen at the diff level  
- Rolling back changes is trivial  

Design shifts from:

> “an ad-hoc operation”

to:

> **a manageable, reviewable artifact**

---

## 📊 Comparison with GUI CAD

| Aspect | GUI CAD | Code-Based Design |
|---|---|---|
| Diff readability | Low | High |
| Intent traceability | Difficult | Explicit |
| Review style | Verbal / screen sharing | Git-based |
| Rollback | Manual | Commit revert |

---

## 🔁 Why Handover Becomes Easier

What gets handed over in code-based design is not操作手順.

Instead, you pass on:

- Design conditions  
- Design decisions  
- Change history  

Because they exist as code,  
future engineers can answer:

> *“Why is it designed this way?”*

by reading the diffs.

---

## ⚖️ You Do Not Need to Code Everything

A critical point:

> **Not everything needs to be coded.**

You do not need to encode:

- Fine aesthetic adjustments  
- Minor geometric tweaks  
- Final cosmetic tuning  

The principle is simple:

> **Only code what you want to preserve as meaningful diffs.**

This balance makes the approach practical.

---

## 🧭 Position Within the Series

This series has shown that:

- Design can be written as code  
- GUI CAD and code can coexist  
- A non-fragile, real-world structure exists  

And finally:

> **Changes become meaningful diffs.**

This is the core conclusion.

---

## 🏁 Conclusion

The greatest value of code-based design  
is not automation or AI.

It is this:

> **Changes remain as meaningful diffs.**

GUI CAD does not need to be rejected.  
But:

- Design decisions  
- Conditions  
- Rules  

should be preserved **as code**.

That alone turns design into a  
**long-term, reusable knowledge asset**.

---

## 📎 Notes

The code snippets in this article  
are illustrative examples for explaining design methodology.

For actual reusable design code and licensing,  
please refer to the following page:

- [Full Code Mechanical Design](https://samizo-aitl.github.io/full-code-mechanical-design/)

---
