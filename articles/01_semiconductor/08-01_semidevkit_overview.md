---
layout: default
title: zenn-articles
---

# 【半導体】🧩 08-01. SemiDevKit全体像 ― TCADからSPICE・信頼性までを一本でつなぐ
topics: ["半導体", "TCAD", "BSIM4", "SPICE", "信頼性"]

---

## 🧭 この記事の位置づけ（シリーズ・ハブ）

**SemiDevKit** は、半導体学習で分断されがちな次の領域を

- 🧪 **デバイス物理（TCAD）**
- 🧩 **コンパクトモデル（BSIM4）**
- 🔌 **回路解析（SPICE）**
- ⏳ **信頼性（NBTI / HCI）**

**一本の流れとして体験できる教育用ツールキット**です。  

本記事は、本シリーズの **入口（目次・ハブ）** にあたります。

🔗 SemiDevKit トップページ  
[https://samizo-aitl.github.io/SemiDevKit/](https://samizo-aitl.github.io/SemiDevKit/)

---

## 🤔 なぜ「一気通貫」が必要なのか

半導体の学習は、テーマごとに**断片化**しやすいという課題があります。

- 数式は理解できても **V–I に落ちてこない**
- `.model` が **ブラックボックス** になりがち
- SPICE は **結果を見るだけ** で終わりやすい
- 信頼性は「劣化する」で **思考停止** しがち

SemiDevKit は、この分断を**意図的に壊し**、

> **物理 → モデル → 回路（V–I）→ 劣化**

を「**つながった一本の線**」として理解することを目的に設計されています。

---

## 🧱 SemiDevKit の全体フロー

```
TCAD（Poisson / Drift–Diffusion）
   ↓
BSIM4（コンパクトモデル）
   ↓
SPICE（DC / AC / CV）
   ↓
信頼性（NBTI / HCI）
```

### 🔑 ポイント
- 各レイヤは **単独でも理解可能**
- しかし前段の理解が、後段で **そのまま効いてくる**
- 特に **V–I（電圧–電流）** を共通言語として接続

---

## 📘 各レイヤで何を学ぶか

### ① 🧪 TCAD（Device Physics)
- Poisson 方程式（電位分布）
- Drift–Diffusion（キャリア輸送）
- MOSFET の **V–I 特性が生まれる理由**

🔗 TCAD 解説ページ  
[https://samizo-aitl.github.io/SemiDevKit/tcad/](https://samizo-aitl.github.io/SemiDevKit/tcad/)

---

### ② 🧩 BSIM4（Compact Modeling）
- 物理を「**回路で使える形**」に圧縮
- BSIM4 パラメータの物理的意味
- `.model` が **何を表現しているか** を可視化

🔗 BSIM 解説ページ  
[https://samizo-aitl.github.io/SemiDevKit/bsim/](https://samizo-aitl.github.io/SemiDevKit/bsim/)

---

### ③ 🔌 SPICE（Simulation）
- **DC解析**：$V_g$–$I_d$、$V_d$–$I_d$
- **AC / CV解析**：寄生容量・周波数応答
- **寸法依存**：L/W と短チャネル効果の雰囲気

👉 「モデルがどう **V–I に現れるか**」を体感

---

### ④ ⏳ 信頼性（Reliability）
- **NBTI**：負バイアス × 温度 × 時間 → $V_t$ シフト
- **HCI**：高電界キャリアによる酸化膜劣化

👉 **時間軸** が加わることで、設計の現実に近づく

---

## 📚 シリーズ記事（目次）

- **01**：SemiDevKit 全体像（この記事）
- **02**：TCAD（Poisson / Drift–Diffusion）
- **03**：BSIM4 理論（物理 → モデル）
- **04**：Paramus（BSIM4 モデル生成）
- **05**：DC解析（V–I：$V_g$–$I_d$, $V_d$–$I_d$）
- **06**：AC / CV解析（寄生容量・周波数）
- **07**：寸法スケール（L/W と短チャネル効果）
- **08**：NBTI（時間劣化）
- **09**：HCI（高電界劣化）

---

## 🎯 想定読者

- 半導体を **体系的に理解したい学生**
- BSIM4 / SPICE を **意味のある形で使いたい方**
- 商用 TCAD / EDA なしで **全体フローを体験したい方**

---

## ▶ 次に読む記事

次は、いちばん上流から入ります。

👉 **02：TCADで理解する MOSFET の本質**  
（Poisson / Drift–Diffusion）

---
