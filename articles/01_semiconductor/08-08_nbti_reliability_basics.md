# 【半導体】⏱️ 08. NBTIとは何か ― MOSFETは時間で劣化する
topics: ["半導体", "NBTI", "信頼性", "MOSFET", "BSIM4"]

---

## ⏱️ はじめに 

これまでの記事では、

- 🧪 **TCAD** による物理理解  
- 📐 **BSIM4** によるモデル化  
- 🔌 **SPICE** による特性評価  

を通して、**「作った直後の MOSFET 特性」** を見てきました。

しかし実デバイスでは、

> **今日よかった特性が、5年後も同じとは限らない**

という現実があります。  

その代表例が  
👉 **NBTI（Negative Bias Temperature Instability）**  
です。

NBTI は、**MOSFET が「時間」で壊れていく** 現象を理解するための、  
最も基本的かつ重要な信頼性問題です。

---

## 🔥 NBTIとは何か 

NBTI は主に **pMOSFET** において、

- 負のゲートバイアス
- 高温環境
- 長時間動作

が重なったときに発生する  
**時間依存の信頼性劣化現象** です。

最大の特徴は：

> **しきい値電圧 $V_t$ が時間とともに変化する**

ことにあります。

---

## 🧠 何が起きているのか（物理像）

NBTI ストレス下では、  
ゲート酸化膜とシリコン界面付近で：

- 界面準位の生成
- トラップの活性化・固定化

が進行します。

その結果：

- 同じ $V_g$ をかけても  
- 同じチャネル電荷が形成されにくくなる  

👉 **MOSFET が「オンになりにくくなる」**

これが、**オン電流低下・遅延増大**として現れます。

---

## 📉 V–I 特性への影響 

NBTI の影響は、**DC 特性にそのまま現れます**。

典型的な変化：
- $V_g$–$I_d$ カーブの **右シフト**
- サブスレッショルド特性の劣化
- 同一 $V_g$ における **$I_d$ 低下**

これらはすべて、

> **しきい値電圧シフト（ΔVth）**

の結果です。

---

## 📐 BSIM4 における NBTI の扱い 

BSIM4 では、NBTI を次のように捉えます。

- 劣化を **モデルパラメータの変化** として表現
- 時間に依存した $V_t$ シフトを想定
- 劣化前後の特性差を比較可能

ただし重要な点として：

> **BSIM4 単体では「時間発展」を直接計算しない**

そのため、SemiDevKit では：

- 🧪 **SPICE：t = 0 の正確な測定**
- 🧮 **Python：t > 0 の劣化モデル**

という **ハイブリッド構成** を採用しています。

---

## 🧰 SemiDevKit による NBTI 解析 

使用するモジュール：

- **BSIM4 Analyzer Reliability**  
  [https://samizo-aitl.github.io/SemiDevKit/bsim/bsim4_analyzer_reliability/](https://samizo-aitl.github.io/SemiDevKit/bsim/bsim4_analyzer_reliability/)

このフレームワークでは：

- 初期 VG–ID 特性の取得
- gmmax 法 / 定電流法による Vth 抽出
- 時間依存劣化モデルの適用
- 劣化後特性の再構築

を **完全自動** で行います。

---

## 🔬 NBTI 解析フロー 

```
t = 0
 ├─ VG–ID sweep
 │     ├→ Vtg0（gmmax 法）
 │     └→ Vtc0（定電流法）
 ├─ DC 抽出
 │     └→ Idlin0 / Idsat0

t > 0
 ├─ ΔVth(t) モデル適用
 ├─ ΔId(t) モデル適用
 ├─ Vtg1 / Vtc1 / Idlin1 / Idsat1 再構築

→ CSV 出力
→ 劣化プロット生成
→ VG–ID 重ね描き
```

---

## 🚀 実行例 

```bash
cd bsim/bsim4_analyzer_reliability/run
python run_nbti_pmos.py
```

---

## 📊 解析結果例 

### ■ PMOS NBTI：Vg–Id 劣化（Linear）

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_reliability/pmos_nbti_vgid.png" width="80%">

👉 **Vg–Id カーブが右にシフト**  
👉 同一ゲート電圧で電流が出なくなる

---

### ■ PMOS NBTI：ΔVtg vs Stress Time

<img src="https://samizo-aitl.github.io/SemiDevKit/assets/bsim4_analyzer_reliability/nbit_dvtg.png" width="80%">

👉 劣化は **時間のべき乗則** に従う  
👉 初期劣化が特に支配的

---

## ⚠️ なぜ NBTI が重要なのか 

NBTI は：

- 動作周波数の低下
- タイミングマージンの消失
- 長期信頼性の破綻

を引き起こします。

特に：

- 低電圧動作
- SRAM / 低 Vdd ロジック
- 長寿命製品（車載・産業）

では、**無視できない制約条件**になります。

---

## 🔗 TCAD / BSIM / SPICE の関係 

NBTI もまた、これまでと同じ流れの上にあります。

- **TCAD**：界面で何が起きているか  
- **BSIM4**：劣化をパラメータ化  
- **SPICE**：回路特性への影響を確認  

👉 **信頼性も「物理 → モデル → 回路」の問題**です。

---

## 📝 まとめ 

- ⏱️ NBTI は時間依存の信頼性劣化現象  
- 🟦 主に pMOSFET で問題になる  
- 📉 しきい値電圧シフトとして現れる  
- 🧪 BSIM4 + SPICE + Python で影響を可視化できる  

MOSFET は、

> **「動くか」ではなく  
> 「何年動き続けるか」**

で評価される時代に入っています。

---

## 次に読む記事 👉

**09：HCIとは何か ― 高電界がMOSFETを壊す理由**
