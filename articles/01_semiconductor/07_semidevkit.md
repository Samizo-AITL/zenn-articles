

# 07. SemiDevKit: 半導体デバイス物理〜BSIM4〜SPICE〜物理設計までを一気通貫で学べるオープン教材

---

本記事では、半導体デバイス物理からコンパクト・モデル（BSIM4）、SPICE 解析、信頼性評価、そして OpenLane を用いた VLSI 物理設計までを **一気通貫で学べるオープン教材「SemiDevKit」** を紹介します。

公式サイトおよび GitHub リポジトリ:

- GitHub Pages（英語ドキュメント）  
  https://samizo-aitl.github.io/SemiDevKit/
- GitHub リポジトリ  
  https://github.com/Samizo-AITL/SemiDevKit

---

# SemiDevKit とは？

SemiDevKit は、以下のワークフロー全体をカバーするオープンソースの教育用ツールキットです。

- 半導体デバイス物理（1D Poisson / Drift–Diffusion）
- コンパクト・モデリング（BSIM4）
- SPICE 解析（DC / AC / 次元スケーリング / 信頼性）
- 信頼性評価（NBTI / HCI）
- OpenLane ベースの VLSI 物理設計フロー（RTL → GDSII）

対象者：

- 半導体デバイスや VLSI を体系的に学びたい学生
- デバイスモデリング・SPICE・物理設計を軽量な環境で試したい研究者/エンジニア
- 教育用に商用 TCAD/EDA に依存しない教材を構築したい方

---

# 主な特徴

## 1. デバイス物理 / TCAD プレイグラウンド

`tcad/` 以下に、シンプルな 1D Poisson / Drift–Diffusion 解法を中心としたプレイグラウンドが用意されています。

- 1D Poisson & Drift–Diffusion solver
- MOSFET の Vg–Id / Vd–Id 特性
- FE（強誘電体）P–E モデル（Landau–Khalatnikov）

市販 TCAD のように巨大でブラックボックスではなく、**数式から追える Python 実装**になっています。

---

## 2. コンパクト・モデリング（BSIM4 Suite）

`bsim/` には BSIM4 モデルを扱うツール群がまとめられています。

- BSIM4 モデルカード自動生成
- 物理パラメータ抽出
  - 酸化膜厚 tox  
  - ドーピング Na  
  - フラットバンド電圧 Vfb  
  - 移動度 μ0  
  - チャネル長 L / 幅 W

デバイス物理で学んだものをコンパクトモデルに橋渡しする構成です。

---

## 3. SPICE 解析（DC / AC / 信頼性）

同じく `bsim/` 内に SPICE 解析スクリプトがまとまっています。

- DC 解析（Vg–Id、Vd–Id）
- AC 解析（Cgg–Vg など）
- 寸法スケーリング解析（L, W sweep）
- 信頼性（NBTI / HCI）

Python と ngspice の組み合わせで、**モデル生成 → SPICE 実行 → 可視化**まで自動化できます。

---

## 4. VLSI 物理設計（OpenLane-Lite）

`openlane/` には教育用に最適化された OpenLane-Lite 環境があります。

- OpenLane 2023 ベースの軽量フロー
- Docker / WSL2 で動作
- `spm` などの最小規模デザインを収録
- RTL → GDSII までのフローを実行可能

**商用ツールなしで IC 物理設計フローを体験できる**のが大きな特徴です。

---

# リポジトリ構成（概要）

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

# セットアップと動かし方（例）

## 1. クローン

```bash
git clone https://github.com/Samizo-AITL/SemiDevKit.git
cd SemiDevKit
```

## 2. 必要環境

- Python 3.10+
- NumPy / SciPy / Matplotlib
- ngspice
- Docker（OpenLane-Lite 用）
- Windows では WSL2 推奨

---

## 3. SPICE DC 解析の実行例

```bash
cd bsim/BSIM4_ANALYZER_DC/run
python run_vd.py
python run_vg.py
```

BSIM4 モデルカードを生成し、Vd–Id / Vg–Id の DC 特性を自動プロットします。

---

## 4. OpenLane-Lite の実行例

```bash
cd openlane/openlane-lite
./docker/run_in_docker.sh
```

このフローで以下が実行されます：

1. OpenLane 2023 コンテナ起動  
2. 小規模デザインの読み込み  
3. RTL → GDSII フローを実行  
4. 結果として GDS ファイルを生成

---

# ドキュメント（MathJax 対応）

`docs/` 以下の理論ノートは GitHub Pages で閲覧できます。

含まれる内容：

- デバイス物理（Poisson / DD）
- コンパクトモデル理論（BSIM4）
- SPICE 解析（DC / AC / 信頼性）
- NBTI / HCI の劣化モデル
- RTL → GDS の物理設計フロー

**コードと理論がリンクしている**ため、学習と実践を行き来できます。

---

# ライセンス

SemiDevKit は以下のようにコンポーネント別ライセンス構成です。

| コンポーネント | ライセンス | 説明 |
|----------------|------------|------|
| ソースコード | MIT | 自由に利用・改変・再配布可能 |
| テキスト資料 | CC BY / CC BY-SA | クレジット必須、一部継承条件あり |
| 図表 | CC BY-NC | 非商用利用のみ |
| 外部リファレンス | それぞれの元ライセンスに従う | - |

---

# まとめ

**SemiDevKit は、商用 TCAD/EDA に頼ることなく、半導体デバイス物理から IC 物理設計まで一気通貫で学べる教材です。**

以下の 3 点が特に教育・研究用途で強力です：

- 数式レベルで理解できる Python 実装  
- BSIM4 モデルを用いた本格的 SPICE 解析  
- OpenLane-Lite による RTL → GDSII フロー

まずは `bsim/BSIM4_ANALYZER_DC` の DC 解析、  
または `openlane/openlane-lite` の GDS フローから試してみてください。

- GitHub Pages: https://samizo-aitl.github.io/SemiDevKit/  
- GitHub: https://github.com/Samizo-AITL/SemiDevKit

