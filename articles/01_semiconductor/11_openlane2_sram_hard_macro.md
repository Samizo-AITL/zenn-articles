---
layout: default
title: OpenLane2 sram
---

# 【半導体】🧠 11. OpenLane2でSRAMハードマクロを統合しGDSを生成する
topics: ["openlane2", "asic", "physicaldesign", "sram", "sky130"]

---

## 🧭 はじめに

本記事では、**OpenLane2（v2）を用いて SRAM ハードマクロを統合し、  
RTL → GDS まで完走する物理設計フロー**を紹介します。

重要なのは、本記事の目的が  
**SRAM を設計することではない**点です。

SRAM はあくまで **external hard macro** として扱い、  
**SoC 物理設計で一般的な統合手法を明示する**ことを目的としています。

---

## 🧱 なぜ SRAM を「中身を見ない」のか

実務の SoC 設計において SRAM は通常：

- ベンダ提供の **ハードマクロ**
- LEF / GDS / timing model のみが公開
- 内部トランジスタは **検証・修正対象外**

です。

したがって本プロジェクトでも、SRAM は以下のポリシーで扱います。

- Verilog は **blackbox 宣言のみ**
- 配置・配線は **LEF に基づく**
- GDS は **最終マージ用**
- SRAM 内部の DRC / LVS は対象外

これは **逃げではなく、現実的な設計作法**です。

---

## 🛠 OpenLane2 を使う理由

OpenLane（v1）ではなく **OpenLane2** を選んだ理由は以下です。

- 設定が **YAML / JSON ベース**で明示的
- マクロ統合が **構造的に分かりやすい**
- Flow の各段階が **追跡しやすい**

特に **macro-aware floorplanning** の記述性は、  
OpenLane2 の大きな利点です。

---

## 🔄 SRAM ハードマクロ統合の流れ

本プロジェクトで行った手順は以下の通りです。

1. **SRAM blackbox の Verilog 宣言**
2. **LEF / GDS の外部参照**
3. **FIXED 配置によるマクロ配置**
4. **halo / keepout を含むフロアプラン**
5. **標準セルの配置・配線**
6. **最終 GDS の生成**

SRAM は設計変数ではなく、  
**初期条件（制約）として固定**されます。

---

## 🗺 GDS で何が確認できるか

最終的に生成された GDS では、以下が確認できます。

- SRAM が **大きな固定マクロ**として存在
- halo / keepout が正しく守られている
- 標準セルが SRAM の周囲に配置・配線されている
- SRAM 内部のトランジスタは表示されない

これは **正しい結果**です。

「SRAM の中身が見えない」こと自体が、  
**ハードマクロ統合が正しく行われた証拠**になります。

---

## ❓ よくある誤解

### Q. SRAM を設計していないのに意味はある？

→ **あります。**

SoC 設計の難しさは、

- ロジック設計  
よりも  
- **マクロ配置・PDN・配線制約**

にあります。

本プロジェクトは、  
その **現実に一番近い部分**を切り出した教材です。

---

## 📦 この教材の位置づけ

本記事で扱った内容は、  
以下のリポジトリに **再現可能な形で整理**しています。

- **GitHub Pages**  
  [https://samizo-aitl.github.io/openlane2-sram/](https://samizo-aitl.github.io/openlane2-sram/)

- **GitHub Repository**  
  [https://github.com/Samizo-AITL/openlane2-sram](https://github.com/Samizo-AITL/openlane2-sram)

設定ファイル・構成・設計ポリシーを含め、  
**教材として再利用可能**な形で公開しています。

---

## 📝 まとめ

- SRAM は **hard macro として扱う**
- 中身を見ないのは **正しい設計判断**
- OpenLane2 は **マクロ統合に十分使える**
- GDS が出て初めて「やった」と言える

本記事が、  
**「標準セルだけではない現実の ASIC 設計」**に  
一歩踏み出す助けになれば幸いです。
