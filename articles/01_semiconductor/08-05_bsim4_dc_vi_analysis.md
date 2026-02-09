---
title: "【半導体】05. BSIM4で読むMOSFETのDC特性 ― Vg–Id / Vd–Id解析"
emoji: "📈"
type: "tech"
topics: ["半導体", "BSIM4", "SPICE", "DC解析", "MOSFET"]
published: true
---

## 🧭 はじめに

前回の記事では、**Paramus による BSIM4 モデル生成**を扱いました。  
モデルカードを作成したら、次に必ず行うべき作業があります。

> **そのモデルが、どのような V–I 特性を示すのかを確認すること**

本記事では、BSIM4 MOSFET モデルを用いた **DC解析**により、

- ゲート電圧掃引： $V_g$ – $I_d$ 特性  
- ドレイン電圧掃引： $V_d$ – $I_d$ 特性  

を実際に可視化し、  
MOSFET の基本動作と **モデルパラメータの意味** を整理します。

---

## 🔍 DC解析とは何か 

DC解析とは、**時間変化を考慮せず、定常状態における電圧–電流（V–I）関係**を求める解析です。

MOSFET に対しては、主に次の 2 種類を確認します。

- **$V_g$ – $I_d$ 特性（転送特性）**
- **$V_d$ – $I_d$ 特性（出力特性）**

これらは、

- デバイス理解  
- モデル検証  
- 回路設計・評価  

すべての出発点となる、最も重要な特性です。

---

## 🧰 使用する環境（SemiDevKit）

本記事では、**SemiDevKit** に含まれる  
**BSIM4 DC Analyzer** を使用します。

🔗 ツールページ  
[BSIM4_ANALYZER_DC | SemiDevKit](https://samizo-aitl.github.io/SemiDevKit/bsim/bsim4_analyzer_dc/)

### 特徴

- BSIM4 モデル × ngspice × Python による **自動 DC解析**
- NMOS / PMOS（130nm）対応
- $V_g$ – $I_d$, $V_d$ – $I_d$ の自動プロット
- **$V_t$ ・ $g_{m,\max}$ ・ $I_{d,\mathrm{lin}}$ ・ $I_{d,\mathrm{sat}}$  の自動抽出**
- 教育用途から **将来の商用解析ツール展開**を見据えた設計

### 前提環境

- BSIM4 モデルカード（Paramus 生成）
- ngspice
- Python 3.10 以上

---

## 📉 Vg–Id解析（ゲート電圧掃引）

### 実行方法

```bash
cd bsim/bsim4_analyzer_dc/run
python run_vgid.py
```

このスクリプトは、以下を自動で実行します。

1. SPICE ネットリスト生成  
2. ngspice 実行  
3. 数値データ取得  
4. 線形・対数プロット生成  

---

### NMOS：$V_g$ – $I_d$ 特性（例）

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_dc/nmos_vgid.png" width="80%">

横軸：ゲート電圧 $V_g$  
縦軸：ドレイン電流 $I_d$

この特性から、次が読み取れます。

- しきい値電圧 $V_t$
- サブスレッショルド領域
- オン電流レベル
- ゲート制御能力（ $g_m = \partial I_d / \partial V_g$ ）

**TCAD で見た「チャネル形成」** が、  
ここでは **V–I 特性として直接現れます**。

---

### PMOS：$V_g$ – $I_d$ 特性

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_dc/pmos_vgid.png" width="80%">

PMOS では SPICE 極性のままプロットされており、  
温度変化による $|V_t|$ や移動度変化も確認できます。

---

## 📊 Vd–Id解析（ドレイン電圧掃引）

### 実行方法

```bash
cd bsim/bsim4_analyzer_dc/run
python run_vdid.py
```

---

### NMOS：$V_d$–$I_d$ 特性（例）

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_dc/nmos_vdid.png" width="80%">

横軸：ドレイン電圧 $V_d$  
縦軸：ドレイン電流 $I_d$

この特性から、

- 線形領域（低 $V_d$）
- 飽和領域
- チャネル長変調（出力抵抗 $r_o$）

といった **MOSFET の動作領域** が明確に読み取れます。

---

### PMOS：$V_d$–$I_d$ 特性

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_dc/pmos_vdid.png" width="80%">

$I_{d,\mathrm{lin}}$ ・ $I_{d,\mathrm{sat}}$  の抽出や、  
短チャネル効果の比較にも有効です。

---

## 🧠 DC特性と物理モデルの対応 

DC解析で得られる V–I 特性は、ブラックボックスではありません。

| DC特性 | 対応する物理要因 |
|------|----------------|
| $V_t$ | ドーピング、酸化膜厚 |
| オン電流 | 移動度、チャネル長 |
| 飽和特性 | 速度飽和、短チャネル効果 |

これらはすべて、

> **TCAD → BSIM4 → SPICE**

という一貫した流れでつながっています。

---

## 🧪 なぜDC解析が重要なのか

DC解析は、単なる特性確認ではなく、

- モデルが破綻していないか  
- パラメータが物理的に妥当か  
- 異常な温度・電圧依存がないか  

を確認する **健全性チェック** です。

AC解析・CV解析・信頼性解析は、  
**DC特性が正しいことが前提条件** になります。

---

## 📝 まとめ

- DC解析は MOSFET 理解の基本
-  $V_g$ – $I_d$ , $V_d$  – $I_d$ は必ず確認する
- BSIM4 の意味は V–I 特性に直接現れる
- SemiDevKit により解析は自動化できる

---

## 次に読む記事 ▶

👉 **06：BSIM4のAC/CV解析 ― 寄生容量と周波数応答**

---

**BSIM4 の理解は、DC解析から始まります。**  
モデルを見る力は、回路と物理をつなぐ力です。
