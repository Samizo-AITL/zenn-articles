---
layout: default
title: aitl-physical-reference v1：なぜ\"まだ制御しない\"のか
---

# 🧱 【ハードウエア:02】aitl-physical-reference v1：なぜ\"まだ制御しない\"のか
topics: ["hardware", "pcb", "kicad", "control", "aitl"]

---

## 📌 はじめに

aitl-physical-reference v1 は、  
**「制御できそうで、まだ制御しない」**ところに意図的に留めた基板です。

それは未完成だからではありません。  
**設計上の判断です。**

制御を入れる前に、  
まだ固定すべき物理が残っている。  
v1 は、その境界を明確にするためのリファレンスです。

---

## 🔄 v0 から v1 で何が変わったか

v0 では、次を最小構成で固定しました。

- 電圧は測定されるもの  
- 電流は抵抗で制限されるもの  
- 物理的境界は PCB 外形で決まるもの  

v1 では、そこから一歩進みます。

- 論理信号は **外部に出せる**
- 観測点は **より明示的になった**
- しかし **振る舞いは定義していない**

「制御できそう」な状態を、  
**あえて未確定のまま露出させる**。  
それが v1 です。

---

## ❓ なぜ、まだ制御を入れないのか

PID、FSM、AI制御。  
いずれも「出力をどう変えるか」を扱います。

しかしその前に、次が固定されていなければなりません。

- どこを測っているのか  
- その電圧・電流は再現可能か  
- 銅配線という物理制約を越えていないか  

制御は **選択** ですが、  
物理は **前提** です。

v1 は、その前提を曖昧にしないために  
**制御を入れない** という選択をしています。

---

## 1️⃣ Schematic（v1）：論理は出した、振る舞いは書かない

![Schematic v1](https://samizo-aitl.github.io/aitl-physical-reference/docs/img/04_apn_sch_v1.png)

論理信号は、ここで初めて明示的に外部へ出ています。

しかし、

- 状態遷移は定義していない  
- フィードバックも存在しない  
- 時間応答も決めていない  

**「制御できそう」という錯覚** だけを許し、  
制御そのものは、まだ存在しません。

---

## 2️⃣ PCB Layout（v1）：銅配線が自由度を縛る

![PCB v1](https://samizo-aitl.github.io/aitl-physical-reference/docs/img/05_apn_pcb_v1.png)

論理が増えても、  
電流が流れるのは **この銅の上だけ** です。

- 配線長  
- リターンパス  
- 部品配置  
- 基板外形  

これらは、制御ロジックでは回避できません。

**制御の自由度は、物理で静かに制限される。**  
それを可視化するためのレイアウトです。

---

## 3️⃣ 3D View（v1）：実体はある、だが制御は始まらない

![3D v1](https://samizo-aitl.github.io/aitl-physical-reference/docs/img/06_apn_3d_v1.png)

高さがあり、  
触れる部品があり、  
測れる位置がある。

しかし、この基板は  
**まだ何も振る舞いません。**

「実装できた＝制御できる」  
という誤解を、ここで止めます。

---

## 🧭 v1 の正体：境界定義リファレンス

aitl-physical-reference v1 は、

- MCU 評価ボードではありません  
- 制御デモ基板でもありません  

これは、

**論理と物理の境界を確定させるリファレンス**  
です。

- Test Point は「観測境界」  
- 抵抗は「物理制約」  
- PCB outline は「世界の端」  

制御が踏み込む前に、  
**越えてはいけない線を引く板**です。

---

## 🧩 AITL における位置づけ

AITL（Architecture for Integrated Technology Logic）では、

- Physical layer  
- Logical layer  
- Adaptive layer  

を明確に分離します。

v1 は、その最下層。  
**Physical layer の基準点**です。

ここが固定されて初めて、  
上位の制御や推論が意味を持ちます。

---

## ⏭️ 次に来るもの

v2 では、初めて **振る舞い** が入ります。

- しかし、まだ AI ではありません  
- まだ最適化もしません  

まず入るのは、  
**人間が説明できる制御**です。

---

## 🧾 まとめ

制御を入れなかったのは、  
まだ「固定すべき物理」が残っていたからです。

aitl-physical-reference v1 は、  
**制御に進むために、立ち止まる設計**。

制御以前に、  
物理がどう存在するか。

その境界を示すための、  
v1 リファレンスです。

---

## 🔗 リンク

- GitHub Pages  
  [https://samizo-aitl.github.io/aitl-physical-reference/](https://samizo-aitl.github.io/aitl-physical-reference/)

- GitHub Repository  
  [https://github.com/Samizo-AITL/aitl-physical-reference](https://github.com/Samizo-AITL/aitl-physical-reference)
