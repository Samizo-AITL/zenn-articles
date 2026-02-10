# 【半導体】🧠 02. TCADで理解するMOSFETの本質 ― Poisson方程式とDrift–Diffusion
topics: ["半導体", "TCAD", "MOSFET", "Poisson方程式", "DriftDiffusion"]

---

## 🧭 はじめに ― V–I特性はどこから来るのか

MOSFET の **V–I 特性** は、  
回路シミュレーションで突然「与えられる」ものではありません。

その起点は、デバイス内部で起きている

- **電位分布（Electrostatics）**
- **キャリア輸送（Transport）**

という、きわめて物理的な現象です。

本記事では **TCAD（Technology Computer-Aided Design）** の視点から、

- 🧮 **Poisson 方程式**（電位を決める）
- 🚗 **Drift–Diffusion 方程式**（電流を決める）

を軸に、  
👉 **MOSFET の $V$–$I$ 特性が「なぜそうなるのか」** を整理します。

---

## 🔍 TCADとは何か

TCAD は、半導体デバイス内部の物理現象を  
**数値計算で直接解く** シミュレーション手法です。

与えるのは、

- デバイス構造
- ドーピング分布
- 材料定数
- バイアス条件

その結果として、

- 電位分布
- 電界
- キャリア密度
- 電流密度

を **同時に・連続的に** 観測できます。

> 📌 回路シミュレーションが「結果を見る世界」だとすれば、  
> **TCAD は「結果が生まれる瞬間を見る世界」**です。

---

## 🧮 Poisson方程式 ― 電位がすべての起点

Poisson 方程式は、

> **電荷分布 → 電位分布**

を結び付ける、半導体物理の根幹です。

MOS 構造では、

- ゲート電圧
- 酸化膜厚 $t_{ox}$
- 基板ドーピング $N_A$

が **表面電位** を通じて、チャネル形成を支配します。

つまり、

> **チャネルができるかどうかは、まず電位で決まる**

ということです。

---

## 🧱 MOS構造で起きていること（Poissonの役割）

ゲート電圧を上げると、MOS 構造では次の順で変化が起きます。

1. ゲート電圧が印加される  
2. 酸化膜を介して表面電位が変化する  
3. 表面にキャリアが集まる  
4. チャネルが形成される  

ここまでを **支配しているのが Poisson 方程式** です。

👉 **「電位がチャネルを作る」**

---

## 🚗 Drift–Diffusion方程式 ― 電流を決める

チャネルができただけでは、電流は流れません。  
電流を決めるのが **Drift–Diffusion 方程式** です。

- **Drift**：電界によるキャリア移動  
- **Diffusion**：濃度勾配によるキャリア拡散  

これにより、

- なぜ $V_d$ を上げると $I_d$ が増えるのか  
- なぜ低電圧で線形領域になるのか  

が自然に説明できます。

👉 **「輸送方程式が $I_d$ を作る」**

---

## 📈 V–I特性は「物理の積み重ね」

TCAD では、次の量を同時に観測できます。

- 電位分布
- キャリア密度分布
- 電流密度分布

これらが積み重なった **結果として**、

- $V_g$–$I_d$ 特性  
- $V_d$–$I_d$ 特性  

が **自然に立ち上がります**。

---

## 🧪 SemiDevKit：教育用 1D TCAD Playground

SemiDevKit では、教育用途に特化した  
**軽量 1D TCAD 環境** を提供しています。

- Poisson + Drift–Diffusion
- Python 実装
- 数式 ↔ コード ↔ 図が一対一対応

🔗 TCAD トップ  
[https://samizo-aitl.github.io/SemiDevKit/tcad/](https://samizo-aitl.github.io/SemiDevKit/tcad/)

---

## 📊 実例①：MOSCAP C–V 特性（Poissonの結果）

酸化膜厚 $t_{ox}$ を変えると、  
MOS キャパシタの **C–V 特性** がどう変わるか。

![MOSCAP C–V](https://samizo-aitl.github.io/SemiDevKit/assets/tcad_playground/moscap_cv_tox.png)

👉 **電位分布の違いが、容量として観測される**

---

## 📊 実例②：nMOS $V_g$–$I_d$ 特性

酸化膜厚を変えたときの $V_g$–$I_d$ 特性。

![nMOS Vg–Id](https://samizo-aitl.github.io/SemiDevKit/assets/tcad_playground/nmos_vgid_tox.png)

- $t_{ox}$ が薄い → $V_{th}$ 低下  
- 同じ $V_g$ で $I_d$ 増加  

👉 **Poisson → Drift–Diffusion → $I_d$**

---

## 📊 実例③：nMOS $V_d$–$I_d$ 特性

![nMOS Vd–Id](https://samizo-aitl.github.io/SemiDevKit/assets/tcad_playground/nmos_vdid_tox.png)

- 低 $V_d$：線形領域  
- 高 $V_d$：飽和領域  

👉 **輸送方程式が領域分けを自然に生む**

---

## 🔗 TCADはゴールではない

TCAD は非常に強力ですが、

- 計算コストが高い  
- 回路設計には重すぎる  

という制約があります。

そこで次に登場するのが **BSIM4** です。

> **TCADで見た物理を、  
> 回路で“即使える形”に圧縮する**

これが **コンパクトモデル** の役割です。

---

## 📝 まとめ

- MOSFET の $V$–$I$ 特性は Poisson / Drift–Diffusion の結果  
- 電位がチャネルを作り、輸送方程式が電流を決める  
- TCAD は「式が現実になる瞬間」を見せる  

---

## ▶ 次に読む記事

👉 **03：BSIM4とは何か ― 物理を回路に落とすコンパクトモデル**

---

🧩 *SemiDevKit シリーズは  
「TCAD → BSIM → SPICE → 信頼性」へと続きます。*
