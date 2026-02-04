---
layout: default
title: aitl-physical-reference：制御以前に、物理を固定する
---

# 【ハードウエア:01】aitl-physical-reference：制御以前に、物理を固定する
topics: ["hardware", "pcb", "kicad", "control", "aitl"]

---

## はじめに

**aitl-physical-reference** は、  
抽象的な制御・論理を **実電圧・実電流・実銅配線** に固定するための  
**最小物理リファレンスPCB**です。

これは「制御するための基板」ではありません。  
**制御以前に、物理がどう存在するかを示すための基準点**です。

---

## なぜ作ったか

制御理論やAI、FSM、PIDは、しばしば次を暗黙に仮定します。

- 電圧は理想的に出る  
- 電流は必要なだけ流れる  
- 出力は論理値として扱える  

しかし現実では、

- 電圧は **測らなければ分からない**
- 電流は **抵抗で制限される**
- 境界は **銅配線と基板外形で決まる**

この「当たり前だが省略されがちな層」を  
**最小構成で固定する**のが本基板の目的です。

---

## 構成要素（あえて少なく）

この基板に載っているのは、次の要素だけです。

- **LED**：出力状態の可視化  
- **Resistor**：電流という物理制約  
- **Switch**：離散的な物理イベント入力  
- **Test Point**：電圧・電流の測定点  
- **PCB outline（Edge.Cuts）**：物理的境界  

機能はありません。  
**意味だけがあります。**

---

## Logic → Physics → Copper

### 1️⃣ Schematic（論理 → 物理）

![Schematic](https://samizo-aitl.github.io/aitl-physical-reference/docs/img/01_apr_sch_v0.png)

*抽象ロジックを、測定可能な電圧・電流へ固定する最小回路図。*

---

### 2️⃣ PCB Layout（物理制約の顕在化）

![PCB Layout](https://samizo-aitl.github.io/aitl-physical-reference/docs/img/02_apr_pcb_v0.png)

*銅配線・部品配置・基板外形として定義された「物理的真実」。*

---

### 3️⃣ 3D View（実体としての存在）

![3D View](https://samizo-aitl.github.io/aitl-physical-reference/docs/img/03_apr_3d_v0.png)

*触れる高さ、挿せるコネクタ、測れる位置を持つ実体。*

---

## これは何ではないか

誤解を避けるため、明確に書いておきます。

- MCU評価ボードではありません  
- 高機能デモ基板ではありません  
- 性能最適化の例でもありません  
- 特定アーキテクチャ前提でもありません  

**リファレンス**です。  
それ以上でも以下でもありません。

---

## どう使うか

この基板は、次のような文脈で使えます。

- 制御教材の「物理起点」  
- FSM / PID / AI制御の前提確認  
- 論理設計者への物理感覚の共有  
- AITL（Architecture for Integrated Technology Logic）の基準層  

「まず、ここから始める」ための板です。

---

## まとめ

制御は、物理の上にしか立てません。

aitl-physical-reference は、その **最下層**を  
回路図・銅配線・実体として固定します。

> 制御以前に、物理がどう存在するか。

それを示すための、  
**最小で、逃げ場のないリファレンス**です。

---

## リンク

- GitHub Pages  
  https://samizo-aitl.github.io/aitl-physical-reference/

- GitHub Repository  
  https://github.com/Samizo-AITL/aitl-physical-reference
