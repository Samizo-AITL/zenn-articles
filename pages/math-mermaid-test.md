---
title: "MathJax & Mermaid 表示テスト"
description: "GitHub Pages（Jekyll）で数式とMermaidが表示できるかの最終確認"
layout: default
---

[MathJax & Mermaid 表示テストページ](https://samizo-aitl.github.io/zenn-articles/pages/math-mermaid-test/)

# MathJax & Mermaid 表示テスト

## 数式（MathJax）

インライン数式：\( a^2 + b^2 = c^2 \)

$$
I \propto \frac{W}{L}
$$

$$
W_\mathrm{eff} \simeq 2H_\mathrm{fin} + W_\mathrm{fin}
$$

---

## Mermaid（flowchart）

```mermaid
flowchart TD
  A[Markdown] --> B[Jekyll build]
  B --> C[HTML]
  C --> D[MathJax]
  C --> E[Mermaid]
  D --> F[Rendered Math]
  E --> G[Rendered Diagram]
```

---

## Mermaid（sequenceDiagram）

```mermaid
sequenceDiagram
  participant U as User
  participant P as Pages
  participant J as Jekyll
  participant M as MathJax
  participant R as Mermaid

  U->>P: Access
  P->>J: Serve HTML
  J->>M: Typeset
  J->>R: Render
  M-->>U: Math OK
  R-->>U: Diagram OK
```
