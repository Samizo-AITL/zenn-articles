---
layout: default
title: GF180MCU × OpenLane が成立しない理由を実機検証で確定させた
---

# 【Inkjet】GF180MCU × OpenLane が成立しない理由を実機検証で確定させた
topics: ["semiconductor", "openlane", "pdk", "gf180", "vlsi", "mixed-signal", "high-voltage", "layout"]

---

## 結論（先に）

**GF180MCU Open PDK は OpenLane（OpenPDK 前提フロー）に非対応であり、  
自動合成 → P&R → GDS 生成は成立しない。**

これは推測ではなく、**実環境での検証結果**である。

そして本検証の結果として、  
本プロジェクトは **自動デジタルフローを放棄し、  
高耐圧 MOS（HVMOS）を中心としたレイアウト主導設計へ移行した**。

---

## 背景

GF180MCU は、高電圧デバイスや mixed-signal 設計に適した  
**Open PDK** として公開されている。

インクジェット・プリントヘッドドライバのような  
**HV + mixed-signal 回路**との親和性も高く、

> 「OpenLane で GDS まで行けるのでは？」

という仮説を立て、**実機環境で検証**を行った。

---

## 検証環境（要点）

- OS: Ubuntu（WSL）
- Flow: OpenLane v0.23
- PDK: GF180MCU Open PDK
- 目的: **自動フローによる GDS 生成可否の確認**

---

## 何が起きたか（事実）

OpenLane 実行時、**prep 段階で必ず以下のエラーが発生**した。

```
couldn't read file
.../libs.tech/openlane/config.tcl
```

---

## 技術的な原因

OpenLane は **OpenPDK 形式**を前提としており、  
以下のディレクトリ構造を必須とする。

```
libs.tech/openlane/config.tcl
```

しかし、**GF180MCU Open PDK にはこの構造が存在しない**。

これは単なる設定不足ではなく、  
**PDK 設計思想そのものの違い**による。

---

## 技術的整理

| 項目 | Sky130 | GF180MCU |
|---|---|---|
| OpenLane公式対応 | ✔ | ✘ |
| OpenPDK構造 | ✔ | ✘ |
| 自動GDS生成 | ✔ | ✘ |
| HV / Mixed-signal適性 | △ | ✔ |

つまり、

> **GF180MCU が使えないのではなく、  
> OpenLane の前提と噛み合っていない**

という結論になる。

---

## なぜこれは「失敗」ではないか

本検証で確定した事実は以下。

- GF180MCU は **デジタル自動P&R向け PDK ではない**
- HV / mixed-signal 回路は **レイアウト主導設計が前提**
- OpenLane は **OpenPDK前提のデジタル特化フロー**

これは設計判断として **極めて重要な境界線**であり、  
資料だけでは分からない点を **実機で確定させた**。

---

## 検証の次に行ったこと（重要）

自動フローを諦めた後、本プロジェクトでは次の段階に進んだ。

- OpenLane を完全に切り離し
- **KLayout を用いた手動／半自動レイアウト**
- 高耐圧 MOS（HVMOS）を最小単位とする  
  **GDS レベルの設計探索**

その結果、  
**高耐圧 MOS スイッチ単位（HV_SW_UNIT）の GDS を実際に生成**するに至った。

---

## HVMOS レイアウト成果（実GDS）

以下は、本プロジェクトで生成した  
**GF180MCU ベース高耐圧 MOS スイッチユニット（HV_SW_UNIT）の GDS**である。

- DNWELL による高耐圧アイソレーション
- 連続した P+ ガードリング
- HVMOS を中心とした最小スイッチ構造
- IC が外界（MEMS／アクチュエータ）に提示する
  **物理インタフェースの実体**

<img
  src="https://samizo-aitl.github.io/gf180-inkjet-driver/docs/images/02_hv_sw_unit_gds.png"
  alt="GF180 HV_SW_UNIT GDS (DNWELL + Guard Ring + HVMOS)"
  width="85%"
/>

この時点で、

> **「OpenLane で GDS が出なかった」  
> ではなく  
> 「適切な設計手法を選び直した結果、  
>  実GDSに到達した」**

という状態になっている。

---

## 実務的な示唆

### GF180MCU を使う場合

- Magic / KLayout を用いた **手動・半手動レイアウト**
- 回路とレイアウトを同時に考える設計
- 高電圧・基板・ガードリングを含めた物理思考

### OpenLane を使う場合

- Sky130 などの **OpenPDK対応プロセス**
- デジタル主体の自動P&Rフロー

> **「HV mixed-signal × 自動デジタルフロー」は基本的に交わらない**

---

## 本プロジェクトとの関係

本検証およびその後のレイアウト成果は、  
以下の技術探索プロジェクトの一部である。

### gf180-inkjet-driver

- **目的**: インクジェット・プリントヘッド向け  
  高電圧 mixed-signal ドライバ IC の物理設計探索
- **方針**: 自動化ではなく **レイアウト主導設計**

#### 🔗 Links

- GitHub Repository  
  https://github.com/Samizo-AITL/gf180-inkjet-driver

- GitHub Pages（設計ドキュメント）  
  https://samizo-aitl.github.io/gf180-inkjet-driver/

- Design Docs（GDS / Layout中心）  
  https://samizo-aitl.github.io/gf180-inkjet-driver/docs/

---

## まとめ

> **GF180MCU × OpenLane は成立しない。  
> これは失敗ではなく、設計フロー選定における重要な検証結果である。**

GF180MCU は  
「自動化のためのPDK」ではなく、  
**“人がレイアウトする前提”の PDK**である。

そして、その前提に立てば、  
**HVMOS を中心とした実GDSに到達できることも、  
本検証で示された。**

---

## 付記

同様の誤解で時間を消費する設計者が  
一人でも減ることを願っている。
