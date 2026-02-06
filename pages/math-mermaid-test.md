---
title: "MathJax & Mermaid 表示テスト"
description: "GitHub Pages上で数式とMermaidが正しく表示されるかの検証"
layout: default
---

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
flowchart LR
  A[Markdown] --> B[Jekyll build]
  B --> C[HTML]
  C --> D[MathJax]
  C --> E[Mermaid]
  D --> F[Rendered Math]
  E --> G[Rendered Diagram]
