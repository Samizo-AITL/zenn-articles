---
layout: default
title: "【検証】MathJax & Mermaid 表示テスト"
---

[MathJax & Mermaid 表示テストページ](https://samizo-aitl.github.io/zenn-articles/pages/math-mermaid-test/)

# MathJax & Mermaid 表示テスト

本ページは、**GitHub Pages（Jekyll）環境において**  
以下が正しく表示されることを確認するためのテスト用 Markdown です。

- MathJax（数式：インライン／別行）
- Mermaid（flowchart / sequenceDiagram）

---

## 数式（MathJax）

### インライン数式

ピタゴラスの定理は  
$a^2 + b^2 = c^2$  
で表されます。

MOS デバイスでは、電流は  
$I \propto \dfrac{W}{L}$  
に比例します。

---

### 別行数式

$$
I \propto \frac{W}{L}
$$

$$
W_\mathrm{eff} \simeq 2 H_\mathrm{fin} + W_\mathrm{fin}
$$

$$
M \ddot{\mathbf{q}} + C \dot{\mathbf{q}} + K \mathbf{q}
= \mathbf{f}(t)
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

  U->>P: Access page
  P->>J: Serve HTML
  J->>M: Typeset math
  J->>R: Render diagram
  M-->>U: Math rendered
  R-->>U: Diagram rendered
```

---

## 確認ポイント

- `$a^2 + b^2 = c^2$` が **インライン数式**として表示されること  
- `$$ ... $$` が **別行数式**として中央配置で表示されること  
- Mermaid の **flowchart / sequenceDiagram** が SVG として描画されること  

以上がすべて表示されれば、  
**Markdown → Jekyll → MathJax / Mermaid の経路は完全に正常**です。

---

## 運用上の注意（重要）

- 数式は **必ず `$...$` または `$$...$$` のみ使用**
- `\(...\)` や `\[...\]` は **使用しない**
- 数式行の先頭に **余計なインデントを入れない**
- 数式は **`pre` / `code` ブロックに入れない**

---

以上。
