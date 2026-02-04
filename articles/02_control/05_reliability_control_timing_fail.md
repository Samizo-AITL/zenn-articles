---
layout: default
title: 摩擦劣化下で“タイミングだけ守る制御”が破綻する理由
---

# 【制御:05】摩擦劣化下で“タイミングだけ守る制御”が破綻する理由
topics: ["制御工学", "PID制御", "信頼性", "シミュレーション"]

---

## はじめに

制御系は「動けばOK」ではありません。  
**長期運用では「いつ動くか（タイミング）」が壊れます。**

本記事では、摩擦劣化（1000日相当）を与えたプラントに対し、

- 従来の PID 制御
- AITL（FSM によるゲイン再調整）

を比較し、**一見うまくいった制御が、実は信頼性制御として破綻していた**
という事例を紹介します。

---

## 実験の狙い

目的は **精度向上ではありません**。

> **経年劣化下で、応答タイミング（Δt）を保てるか？**

これを「信頼性（Reliability）」の観点で評価します。

---

## 実験条件（要点のみ）

- 劣化モデル  
  - クーロン摩擦・静止摩擦の増加
  - 劣化量：1000日相当

- 比較対象  
  - **Initial**：day=0 で設計した PID  
  - **PID_only**：劣化後もゲイン固定  
  - **AITL**：FSM によるゲイン再調整（ナイーブ実装）

---

## 結果：タイミング劣化（Δt）

以下が結果の比較図です。

![Timing degradation under friction aging](https://samizo-aitl.github.io/aitl-controller-a-type/data/pid_vs_aitl_friction_aging.png)

- **PID_only**  
  - 応答振幅は保たれる  
  - しかしピーク時刻が徐々に遅れ、Δt が蓄積

- **AITL**  
  - ピークタイミングは初期状態に近い  
  - Δt は抑制される

一見すると、AITL は「成功」に見えます。

---

## しかし、何が起きたか

AITL の応答をよく見ると、

- 振幅が縮小
- 動きが鈍化
- 平坦な区間が現れる

つまり、

> **タイミングは守ったが、可制御性を犠牲にした**

状態になっています。

---

## なぜこうなるのか

原因はシンプルです。

- AITL が **Δt（タイミング）だけ**を目的に最適化している
- 振幅・飽和・制御エネルギを見ていない

その結果、

> **Timing-oriented retuning alone can collapse motion authority.**

（タイミングだけを守る再調整は、運動能力を破壊する）

これは **バグではなく、設計上の必然的な失敗**です。

---

## Reliability Control とは何か

この結果から分かることは明確です。

**Reliability Control = 単一指標の最適化ではない**

- Δt（タイミング）
- 振幅（可制御性）
- 飽和率（健全性）
- 再調整の落ち着き

これらを **制約付きで同時に扱う設計問題**です。

---

## 設計上の教訓

- Δt だけを守っても「信頼性制御」にはならない
- ゲイン再調整は「設計行為」である
- FSM は劣化検知だけでなく **やり過ぎ検知**が必要

---

## 今回はここまで

本記事では、

- ナイーブな AITL が **どこで破綻するか**
- Reliability Control に必要な視点

までを扱いました。

次回は、

> **振幅・飽和を制約とした Reliability FSM の設計**

に進む予定です。

---

## 参考リンク

- GitHub（コード・再現環境）  
  https://github.com/Samizo-AITL/aitl-controller-a-type

- 詳細解析（GitHub Pages）  
  https://samizo-aitl.github.io/aitl-controller-a-type/docs/reliability/demo_friction_aging_analysis.html
