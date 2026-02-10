# 【半導体】📏 07. MOSFETのL/Wスケーリングと短チャネル効果をSPICEで可視化する
topics: ["半導体", "MOSFET", "スケーリング", "短チャネル効果", "BSIM4"]

---

## 🚀 はじめに

MOSFET は、しばしば

> **「小さくすると速くなる」**

と言われます。  
しかし実際には、それと同時に、

- ⚠️ 制御しにくくなる  
- ⚠️ リークが増える  
- ⚠️ 特性ばらつきが顕在化する  

という **別の顔** を見せ始めます。

本記事では、**BSIM4 モデル + SPICE 解析**を用いた  
**L/W 寸法スケーリング解析**を通して、

- なぜ小さくすると特性が変わるのか
- 教科書的な直感と現実がどこでズレるのか

を **シミュレーション結果から確認**します。

---

## 📐 寸法スケーリングとは何か

MOSFET の寸法スケーリングとは、主に次の 2 つを変化させたときの影響を見る解析です。

- チャネル長：$L$
- デバイス幅：$W$

理想的な長チャネル MOSFET では、

- $I_d \propto W$
- $I_d \propto 1/L$

と考えたくなります。  
しかし **実デバイスでは、この関係は簡単に崩れます**。

その破綻の正体が、  
👉 **短チャネル効果（Short-Channel Effects, SCE）** です。

---

## 🧰 使用する環境（SemiDevKit）

本記事では、以下の DIM 解析モジュールを使用します。

- **BSIM4_ANALYZER_DIM**  
  [https://samizo-aitl.github.io/SemiDevKit/bsim/bsim4_analyzer_dim/](https://samizo-aitl.github.io/SemiDevKit/bsim/bsim4_analyzer_dim/)

### 特徴
- Python + ngspice
- BSIM4（130nm 教育モデル）
- 完全自動：
  - L/W 依存モデル生成
  - netlist 作成
  - SPICE 実行
  - CSV / PNG 出力

👉 **寸法依存特性を「手を動かさずに」比較可能**です。

---

## 🔬 チャネル長 L のスケーリング 

### 実行方法

```bash
cd bsim/bsim4_analyzer_dim/run
python run_vg_dim.py
python run_vd_dim.py
```

この解析では、チャネル長 $L$ を段階的に変えながら、

- Vg–Id（転送特性）
- Vd–Id（出力特性）

を比較します。

---

### ⚠️ L を短くすると何が起きるか 

シミュレーション結果から、以下が確認できます。

- 📉 しきい値電圧の低下（Vth roll-off）
- 📉 出力抵抗の低下
- ⚡ DIBL（Drain Induced Barrier Lowering）
- ⚠️ 飽和特性の崩れ

これらを総称して **短チャネル効果（SCE）** と呼びます。

---

### ■ Vg–Id（Lスイープ, NMOS）

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_dim/nmos_vgid.png" width="80%">

👉 **短 L ほど Vth が下がり、リークが増える**  
👉 gm の増加と制御性低下が同時に起きる

---

### ■ Vd–Id（Lスイープ, NMOS）

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_dim/nmos_vdid.png" width="80%">

👉 **飽和が甘くなり、Id が Vd に引きずられる**  
👉 典型的な DIBL の兆候

---

## デバイス幅 W のスケーリング 📏

### 実行方法

```bash
cd bsim/bsim4_analyzer_dim/run
python run_vg_dim.py
python run_vd_dim.py
```

（W 固定条件のみ変更）

---

### 🤔 Wスケーリングの直感と現実 

直感的には、

- W を広げる → 電流が比例して増える

と考えがちですが、実際には：

- 寄生抵抗（Rdsw）
- 寄生容量（Cgg）
- ナロー幅効果

が無視できなくなります。

👉 **「W を広げればすべて解決」ではない**  
👉 標準セル設計で重要なポイントです。

---

## 🧠 BSIM4 が果たす役割 

BSIM4 は、

- Vth ロールオフ
- DIBL
- 移動度劣化
- ナロー幅効果

といった **寸法依存パラメータ** を内部に持っています。

そのため SPICE 解析だけでも、

> **「小さくした結果、何が壊れたか」**

を **端子特性として確認**できます。

---

## 🔗 TCADとの関係 

TCAD では、短チャネル化により：

- 電位分布が歪む
- ドレイン電界がチャネルに侵入する

ことを **空間的に** 観測できます。

一方 BSIM4 の DIM 解析は、

- それらの結果を
- **I–V 特性という形で圧縮表現したもの**

です。

👉 **TCAD と回路設計をつなぐ橋渡し** が BSIM4 です。

---

## 💡 DIM解析の本当の価値 

DIM解析が本領を発揮するのは：

- SRAM の β 比設計
- 標準セルの drive strength 設計
- 高速 / 低リークのトレードオフ検討

といった **回路・アーキ設計の現場**です。

---

## 📝 まとめ 

- 📏 L/W スケーリングは MOSFET 特性を大きく変える  
- ⚠️ L 短縮は短チャネル効果を引き起こす  
- 📐 W 拡大も単純比例では終わらない  
- 🧠 BSIM4 + SPICE で現実的な挙動を確認できる  

MOSFET を **「式」ではなく「デバイス」として理解する**ために、  
DIM 解析は非常に強力な手段です。

---

## 次に読む記事 👉

**08：NBTIとは何か ― MOSFETは時間で劣化する**
