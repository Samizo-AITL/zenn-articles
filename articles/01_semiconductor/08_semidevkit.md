---
layout: default
title: zenn-articles
---

# 【半導体】🧰 08. SemiDevKit  
### ― 半導体デバイス物理〜BSIM4〜SPICE〜物理設計までを一気通貫で学べるオープン教材

---

本記事では、半導体デバイス物理から  
コンパクト・モデル（BSIM4）、SPICE 解析、信頼性評価、  
そして OpenLane を用いた VLSI 物理設計までを  
**一気通貫で学べるオープン教材「SemiDevKit」** を紹介します。

公式サイトおよび GitHub リポジトリ：

- **GitHub Pages（英語ドキュメント）**  
  [https://samizo-aitl.github.io/SemiDevKit/](https://samizo-aitl.github.io/SemiDevKit/)
- **GitHub リポジトリ**  
  [https://github.com/Samizo-AITL/SemiDevKit](https://github.com/Samizo-AITL/SemiDevKit)

---

## 🧭 SemiDevKit とは？

SemiDevKit は、以下のワークフロー全体をカバーする  
**オープンソースの教育用ツールキット**です。

- 半導体デバイス物理（1D Poisson / Drift–Diffusion）
- コンパクト・モデリング（BSIM4）
- SPICE 解析（DC / AC / 次元スケーリング / 信頼性）
- 信頼性評価（NBTI / HCI）
- OpenLane ベースの VLSI 物理設計フロー（RTL → GDSII）

### 🎯 対象者

- 半導体デバイスや VLSI を体系的に学びたい学生  
- デバイスモデリング・SPICE・物理設計を軽量環境で試したい研究者／エンジニア  
- 商用 TCAD/EDA に依存しない教育教材を構築したい方  

---

## ✨ 主な特徴

### 🔬 1. デバイス物理 / TCAD プレイグラウンド

`tcad/` 以下に、  
**1D Poisson / Drift–Diffusion 解法**を中心とした  
TCAD プレイグラウンドを用意しています。

- 1D Poisson & Drift–Diffusion solver  
- MOSFET の Vg–Id / Vd–Id 特性  
- FE（強誘電体）P–E モデル（Landau–Khalatnikov）

市販 TCAD のように巨大でブラックボックスではなく、  
**数式から追える Python 実装**です。

---

### 📐 2. コンパクト・モデリング（BSIM4 Suite）

`bsim/` には BSIM4 モデルを扱うツール群がまとまっています。

- BSIM4 モデルカード自動生成  
- 物理パラメータ抽出  
  - 酸化膜厚 tox  
  - ドーピング Na  
  - フラットバンド電圧 Vfb  
  - 移動度 μ0  
  - チャネル長 L / 幅 W  

**デバイス物理 → コンパクトモデル**を橋渡しする構成です。

---

### ⚡ 3. SPICE 解析（DC / AC / 信頼性）

同じく `bsim/` 内に SPICE 解析スクリプトがまとまっています。

- DC 解析（Vg–Id、Vd–Id）  
- AC 解析（Cgg–Vg など）  
- 寸法スケーリング解析（L, W sweep）  
- 信頼性解析（NBTI / HCI）  

Python + ngspice により、  
**モデル生成 → SPICE 実行 → 可視化**まで自動化されています。

---

### 🧱 4. VLSI 物理設計（OpenLane-Lite）

`openlane/` には教育用途に最適化した  
**OpenLane-Lite 環境**が含まれます。

- OpenLane 2023 ベースの軽量フロー  
- Docker / WSL2 対応  
- `spm` などの最小規模デザイン収録  
- RTL → GDSII まで実行可能  

**商用ツールなしで IC 物理設計フローを体験可能**です。

---

## 🗂 リポジトリ構成（概要）

```
SemiDevKit/
├── tcad/                       # デバイス物理（TCAD Playground）
│   ├── TCAD_PLAYGROUND
│   └── TCAD_PLAYGROUND_PZT
│
├── bsim/                       # コンパクトモデル + SPICE解析
│   ├── Paramus
│   ├── BSIM4_ANALYZER_DC
│   ├── BSIM4_ANALYZER_CV
│   ├── BSIM4_ANALYZER_DIM
│   └── BSIM4_ANALYZER_RELIABILITY
│
├── openlane/                   # 物理設計フロー
│   ├── openlane-lite
│   └── openlane-superstable
│
└── docs/                       # ドキュメント（MathJax 対応）
```

---

## 🚀 セットアップと実行例

### 1️⃣ クローン

```bash
git clone https://github.com/Samizo-AITL/SemiDevKit.git
cd SemiDevKit
```

---

### 2️⃣ 必要環境

- Python 3.10+  
- NumPy / SciPy / Matplotlib  
- ngspice  
- Docker（OpenLane-Lite 用）  
- Windows では WSL2 推奨  

---

### 3️⃣ SPICE DC 解析の実行例

```bash
cd bsim/BSIM4_ANALYZER_DC/run
python run_vd.py
python run_vg.py
```

BSIM4 モデルカードを生成し、  
Vd–Id / Vg–Id の DC 特性を自動プロットします。

---

### 4️⃣ OpenLane-Lite の実行例

```bash
cd openlane/openlane-lite
./docker/run_in_docker.sh
```

実行内容：

1. OpenLane 2023 コンテナ起動  
2. 小規模デザイン読み込み  
3. RTL → GDSII フロー実行  
4. GDS ファイル生成  

---

## 📘 ドキュメント（MathJax 対応）

`docs/` 以下の理論ノートは GitHub Pages で閲覧できます。

含まれる内容：

- デバイス物理（Poisson / DD）  
- コンパクトモデル理論（BSIM4）  
- SPICE 解析（DC / AC / 信頼性）  
- NBTI / HCI 劣化モデル  
- RTL → GDS の物理設計フロー  

**コードと理論が直接リンク**しています。

---

## 📜 ライセンス

| コンポーネント | ライセンス | 説明 |
|----------------|------------|------|
| ソースコード | MIT | 自由に利用・改変・再配布可能 |
| テキスト資料 | CC BY / CC BY-SA | クレジット必須 |
| 図表 | CC BY-NC | 非商用利用のみ |
| 外部リファレンス | 各元ライセンス | - |

---

## 📝 まとめ

**SemiDevKit は、商用 TCAD/EDA に頼らず、  
半導体デバイス物理から IC 物理設計まで  
一気通貫で学べるオープン教材です。**

特に強力な点は：

- 数式レベルで理解できる Python 実装  
- BSIM4 を用いた本格 SPICE 解析  
- OpenLane-Lite による RTL → GDSII フロー  

まずは、

- `bsim/BSIM4_ANALYZER_DC` の DC 解析  
- `openlane/openlane-lite` の GDS フロー  

から試してみてください。

- **GitHub Pages**  
  [https://samizo-aitl.github.io/SemiDevKit/](https://samizo-aitl.github.io/SemiDevKit/)
- **GitHub リポジトリ**  
  [https://github.com/Samizo-AITL/SemiDevKit](https://github.com/Samizo-AITL/SemiDevKit)
