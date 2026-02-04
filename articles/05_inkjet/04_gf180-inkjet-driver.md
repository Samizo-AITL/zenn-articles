---
layout: default
title: GF180 Inkjet Driver 設計探索（続編）— 400dpiの限界と300dpiの現実解
---

# 【Inkjet:04】GF180 Inkjet Driver 設計探索（続編）— 400dpiの限界と300dpiの現実解
topics: semiconductor,icdesign,layout,inkjet,gf180

---

# GF180 Inkjet Driver 設計探索（続編）  
## 400dpi の限界と 300dpi への現実解

本記事は、以下の記事の **続編**です。

- 前編：GF180 Inkjet Driver 設計探索  
  https://zenn.dev/samizo_aitl/articles/024_gf180-inkjet-driver

前編では、GF180MCU open PDK を用いて、

- 自動デジタルフロー（OpenLane）が成立しない理由
- 高電圧デバイスを含む設計では **レイアウト主導設計**が不可避であること

を整理しました。

本稿ではその続きとして、

- **HV_SW_UNIT をアレイ化した場合の物理制約**
- **400dpi（63.5µm）という高密度配列の限界**
- **300dpi（約84.7µm）に落とした場合の現実的な見通し**

を、**GDS レイアウトの実例ベース**で整理します。

---

## なぜ「dpi」が重要なのか

インクジェットプリントヘッドでは、  
**dpi = ノズル密度 = ドライバ回路の配列ピッチ**です。

- 400 dpi  
  → 25.4mm / 400 = **63.5 µm**
- 300 dpi  
  → 25.4mm / 300 ≈ **84.7 µm**

この数十 µm の差が、  
**高電圧デバイス・DNWELL・ガードリング**を含む IC では  
致命的な差になります。

---

## HV_SW_UNIT とは何か（再確認）

HV_SW_UNIT は、

- 高電圧 NMOS（プレースホルダ）
- DNWELL による基板分離
- P+ ガードリング
- D / G / S / B ピンの可視化

を含む **最小のスイッチ単位 GDS**です。

回路完成度よりも、

> 「この構造は並べられるのか？」

を評価するための **物理検証用ユニット**として設計しました。

---

※ 本検証では、HV_SW_UNIT を **NMOS 主体・4×2 配列**として評価しています。  
これは GF180MCU において **DNWELL エンクロージャと基板分離が
配列ピッチを最も厳しく制約する条件**を先に踏むためです。  
単セルや 1×N 配列ではなく 4×2 とすることで、
ガードリング共有や DNWELL 連続性を含む  
**アレイ中心部の実効的な物理条件**を確認しています。

---

## 400dpi アレイ検証のステップ

### ステップ1：独立セル（Baseline）

各 HV_SW_UNIT が

- 独立した DNWELL
- 独立した Guard Ring

を持つ構成です。

![HV_SW_UNIT Array – Independent DNWELL and Guard Ring](https://samizo-aitl.github.io/gf180-inkjet-driver/docs/images/03_hv_unit_array_full_gds.png)

この時点で、

- ガードリング外形が支配的
- 63.5µm ピッチに物理的余裕がない

ことが明確になります。

---

### ステップ2：列方向 Guard Ring 共有

次に、**列単位で Guard Ring を共有**し、  
冗長なガードリングを削減しました。

![HV_SW_UNIT Array – Column-wise Guard Ring Sharing](https://samizo-aitl.github.io/gf180-inkjet-driver/docs/images/04_hv_sw_unit_array_gr_shared_FIXED_gds.png)

結果：

- Guard Ring の重複は減少
- しかし依然としてピッチは厳しい

---

### ステップ3：Guard-Ring-Clean（最終確認）

最後に、

- HV_SW_UNIT 内の Guard Ring を完全に除去
- アレイ外側にのみ Guard Ring を配置

という **最小構成**を評価しました。

![HV_SW_UNIT Array – Guard Ring Clean Shared Configuration](https://samizo-aitl.github.io/gf180-inkjet-driver/docs/images/05_hv_sw_unit_array_gr_shared_clean_gds.png)

ここで初めて分かるのが：

> **Guard Ring ではなく DNWELL が最終的な支配要因である**

という事実です。

---

> ※補足  
> 上記 3 つの図は外形的にはほぼ同一に見えますが、  
> 差分は **Guard Ring の配置・共有方法と DNWELL の支配関係**にあります。  
> 本検討はレイアウト形状の大幅変更ではなく、  
> **どの構造が配列ピッチを本質的に制約しているかを切り分けるための比較**です。

---

## 結論：400dpi は GF180 では構造的に厳しい

上記 3 段階の検証から、以下が結論です。

- Guard Ring をどれだけ削っても
- 配置をどれだけ工夫しても

**DNWELL のマージンと分離要件が 63.5µm に収まらない**

つまり、

> **GF180MCU + DNWELL 前提では  
> 400dpi インクジェットドライバは構造的に不成立**

これは推測ではなく、  
**GDS レイアウトという証拠付きの設計判断**です。

---

## では 300dpi ならどうか？

300dpi のピッチは約 **84.7µm**。

これは、PoC 用に設定していた

- HV_SW_UNIT 幅：約 80µm

よりも **明確に大きい**値です。

アレイ生成コード上も、変更点はほぼ 1 行です。

```python
pitch_x = um(84.7, layout.dbu)  # 25.4mm / 300dpi
```

この条件では、

- DNWELL マージンを含めても配置余地が生まれる
- 400dpi と異なり「調整で成立する可能性」がある

という **現実的な設計レンジ**に入ります。

---

## 300dpi で次にやること

300dpi レイアウトが GDS 上で成立した後のステップは：

1. **DRC**  
   - GF180 PDK ルールを満たしているか
2. **PEX**  
   - 配線寄生 R/C の抽出
3. **SPICE**  
   - Id–Vd / Id–Vg の sanity
   - スイッチング過渡の確認
4. **Pad / ESD / HV 配線設計**

ここからは「配置検討」ではなく、  
**IC としての完成度を高めるフェーズ**に入ります。

---

## まとめ

- 400dpi は  
  **GF180MCU + DNWELL 構造では物理的に困難**
- 300dpi は  
  **成立可能性が高く、設計を進める価値がある**
- 本検討は  
  **GDS ベースで限界を見極めた設計探索**

このように、

> 「作れるかどうか」を  
> **実レイアウトで判断する**

こと自体が、本プロジェクトの最大の成果です。

---

## おわりに

高電圧・混載・高密度という条件が重なると、  
設計は必ず **物理に引き戻されます**。

GF180MCU open PDK は、その現実を  
**誰でも確認できる形で学べる**貴重な教材です。

この続きを進めるなら、  
それはもう **300dpi を前提とした別フェーズ**になります。

ここで一度、区切りを付けます。

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

💬 ご意見・議論は GitHub Discussions へ  
https://github.com/Samizo-AITL/gf180-inkjet-driver/discussions
