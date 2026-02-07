---
title: "【半導体】SemiDevKit全体像 ― TCADからSPICE・信頼性までを一本でつなぐ"
emoji: "🧩"
type: "tech"
topics: ["半導体", "TCAD", "BSIM4", "SPICE", "信頼性"]
published: true
---

## この記事の位置づけ（ハブ）

SemiDevKit は、半導体の学習で分断されがちな

- デバイス物理（TCAD）
- コンパクトモデル（BSIM4）
- 回路解析（SPICE）
- 信頼性（NBTI / HCI）

を **一本の流れとして体験できる教育用ツールキット** です。  
本記事はシリーズの **入口（目次・ハブ）** になります。

参照：SemiDevKit  
https://samizo-aitl.github.io/SemiDevKit/

---

## なぜ「一気通貫」が必要なのか

半導体の学習は、テーマごとに分断されやすいです。

- 物理は式が理解できても「V–I に落ちない」
- モデルは `.model` がブラックボックスになりやすい
- SPICE は結果を眺めるだけになりやすい
- 信頼性は「劣化する」で止まりやすい

SemiDevKit は、この分断を意図的に壊し、

> **物理 → モデル → 回路（V–I）→ 劣化**

を「つながった一つの線」として理解することを狙っています。

---

## SemiDevKit の全体フロー

```
TCAD（Poisson / Drift–Diffusion）
   ↓
BSIM4（コンパクトモデル）
   ↓
SPICE（DC / AC / CV）
   ↓
信頼性（NBTI / HCI）
```

ポイントは、各レイヤが **独立して動く** 一方で、  
前段の理解が後段の理解に **そのまま効く** ことです。

---

## 各レイヤで何を学ぶか

### 1) TCAD（Device Physics）
- Poisson 方程式（電位）
- Drift–Diffusion（キャリア輸送）
- MOSFET の V–I 特性が生まれる理由

TCAD ページ：  
https://samizo-aitl.github.io/SemiDevKit/tcad/

---

### 2) BSIM4（Compact Modeling）
- 物理を「回路で使える形」に圧縮する
- BSIM4 パラメータの意味をつかむ
- モデルカード `.model` が何を表しているか

BSIM ページ：  
https://samizo-aitl.github.io/SemiDevKit/bsim/

---

### 3) SPICE（Simulation）
- DC：\(V_g\)–\(I_d\)、\(V_d\)–\(I_d\)
- AC / CV：寄生容量・周波数応答
- 寸法スケール：L/W 依存（短チャネル効果の雰囲気）

---

### 4) 信頼性（Reliability）
- NBTI：負バイアス＋温度＋時間で \(V_t\) が動く
- HCI：高電界でキャリアが酸化膜を壊す

---

## シリーズ記事（目次）

- 01：SemiDevKit 全体像（この記事）
- 02：TCAD（Poisson / Drift–Diffusion）
- 03：BSIM4 理論（物理→モデル）
- 04：Paramus（BSIM4 モデル生成）
- 05：DC解析（V–I：\(V_g\)–\(I_d\), \(V_d\)–\(I_d\)）
- 06：AC/CV解析（寄生容量・周波数）
- 07：寸法スケール（L/W と短チャネル効果）
- 08：NBTI（時間劣化）
- 09：HCI（高電界劣化）

---

## 想定読者

- 半導体を体系的に学びたい学生
- BSIM4 / SPICE を「意味のある形」で使いたい方
- 商用 TCAD/EDA なしで流れを体験したい方

---

## 次に読む記事

次は上流から入ります。

👉 **02：TCADで理解するMOSFETの本質（Poisson / Drift–Diffusion）**

---
