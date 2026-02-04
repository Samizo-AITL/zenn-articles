---
layout: default
title: OpenLane superstable
---

# 【半導体:09】OpenLane superstableを「最小RTL→GDS」で事前宣言検証してみた
topics: ["OpenLane", "SKY130", "EDA", "半導体", "VLSI"]

## はじめに　

OpenLane を触っていると、こんな疑問が出てきます。

- 「結局、このフローは *普通のRTL* でも最後まで流れるのか？」
- 「チューニングしないとダメなんじゃないか？」
- 「成功例って、あとから条件を調整してない？」

EDA フローの紹介記事を見ていると、  
**結果が出たあとで条件が調整されているケース**も少なくありません。

そこで今回は、

> **最小限の自作RTLを「事前に宣言」した状態で OpenLane superstable を流し、  
> RTL → GDS まで本当に完走するのか**

を検証しました。

---

## 今回やったこと（要点）

やったことは非常にシンプルです。

- 自作の **最小RTL（カウンタ）** を用意
- 制約条件を **実行前に固定**
- OpenLane **superstable を改変せず**に実行
- 成否は **「GDSが出るかどうか」だけ**で判断

性能評価や最適化は、  
**今回の検証対象には含めていません。**

---

## 「事前宣言」とは何か

今回のキーワードは **事前宣言** です。

これはツールの正式な用語ではなく、

> **結果を見る前に、  
> RTL・制約・成功条件を決めておくこと**

を意味しています。

### 事前に決めたこと

- RTLの中身（あとから変えない）
- クロック周期・util などの制約（あとからいじらない）
- 成功条件は **「GDSが出ること」だけ**

つまり、

- 「流れなかったら条件を緩める」
- 「通った設定だけを成功例として出す」

といった **後出し解釈をしない**ための約束です。

---

## 設計の中身（最小RTL）

設計は **本当に最小限**です。

| 項目 | 内容 |
|---|---|
| 機能 | フリーランニング・カウンタ |
| FSM | なし |
| クロック | 単一 |
| リセット | なし（simulation-only 初期化） |
| マクロ | 使用しない |

RTL：  
`rtl/spm_min_counter.v`

---

## 事前に固定した制約

| 項目 | 値 |
|---|---|
| クロック周期 | 10ns（100MHz） |
| Core utilization | 30% |
| Aspect ratio | 1.0 |

設定ファイル：  
`openlane/config.tcl`

---

## RTLシミュレーション（テストベンチ）

```
spm_min_counter/
├─ README.md
├─ rtl/
├─ sim/
│  ├─ tb_spm_min_counter.v
│  ├─ run.sh
│  └─ wave/
├─ openlane/
├─ runs/
├─ results/
└─ run_log/
```

### テストベンチ方針

- RTL 非改変
- reset 追加なし
- simulation-only 初期化のみ

---

## GTKWave 波形

<p align="center">
  <img
    src="https://raw.githubusercontent.com/Samizo-AITL/SemiDevKit/main/openlane/openlane-superstable/spm_min_counter/results/gtkwave.png"
    style="width:80%;"
  >
</p>

---

## OpenLane 実行結果

- RTL → GDS 完走
- DRC / LVS Pass

---

## KLayout レイアウト

<p align="center">
  <img
    src="https://raw.githubusercontent.com/Samizo-AITL/SemiDevKit/main/openlane/openlane-superstable/spm_min_counter/results/1_overview.png"
    style="width:80%;"
  >
</p>

---

## まとめ

本検証により、OpenLane superstable は  
**最小RTLでも事前宣言条件下で RTL→GDS を完走可能**であることを確認しました。

---

## 参考リンク

- GitHub Pages  
  [https://samizo-aitl.github.io/SemiDevKit/openlane/openlane-superstable/spm_min_counter](https://samizo-aitl.github.io/SemiDevKit/openlane/openlane-superstable/spm_min_counter)

- GitHub Repository  
  [https://github.com/Samizo-AITL/SemiDevKit/tree/main/openlane/openlane-superstable/spm_min_counter](https://github.com/Samizo-AITL/SemiDevKit/tree/main/openlane/openlane-superstable/spm_min_counter)

