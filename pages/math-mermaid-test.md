---
title: "MathJax & Mermaid 表示テスト"
description: "GitHub Pages上で数式とMermaidが正しく表示されるかの検証"
layout: default
---

[MathJax & Mermaid 表示テストページ](https://samizo-aitl.github.io/zenn-articles/pages/math-mermaid-test/)

# MathJax & Mermaid 表示テスト

## 数式（MathJax）

インライン：\( a^2 + b^2 = c^2 \)

$$
I \propto \frac{W}{L}
$$

$$
W_\mathrm{eff} \simeq 2H_\mathrm{fin} + W_\mathrm{fin}
$$

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
