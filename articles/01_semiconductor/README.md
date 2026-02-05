# 01_半導体｜記事インデックス

---

## デバイス物理・構造編（〜Post-CFET）

本セクションでは、MOSデバイスの構造変遷を  
**短チャネル効果・電界制御・配線制約といった物理要因**の観点から整理する。  
性能比較や世代論ではなく、**構造変更が必要になった理由**に焦点を当てる。

- [01. Planar SCE Problem｜プレーナMOSの短チャネル効果](./01_planar_sce_problem.md)
- [02. FinFET Structure｜FinFET構造と電気的特徴](./02_finfet_structure.md)
- [03. Weff Concept｜有効チャネル幅 Weff の考え方](./03_weff_concept.md)
- [04. GAA Structure｜GAA（Gate-All-Around）構造](./04_gaa_structure.md)
- [05. CFET Challenge｜CFETが抱える技術課題](./05_cfet_challenge.md)
- [06. Post-CFET｜Post-CFET時代の本質（次はデバイスではない）](./06_post_cfet.md)

---

## 設計方法論・抽象化

本セクションでは、  
**物理制約をどのレイヤで扱うか**という設計方法論を扱う。  
デバイス・回路・システムの役割分担と、抽象化の前提条件を整理する。

- [07. SystemDK｜SystemDKが前提となる設計世界](./07_systemdk.md)

---

## 設計・モデリング・EDA編 

本セクションでは、  
設計に用いられる **モデル・パラメータ・EDA前提**を整理する。  
モデルが「何を表現し、何を表現していないか」を明確にする。

- [08. SemiDevKit｜半導体設計用DevKit構想](./08_semidevkit.md)

---

## OpenLane / RTL → GDS フロー

本セクションでは、  
オープンソースEDAを用いた **RTLからGDSまでの具体的フロー**を扱う。  
自動化可能な工程と、設計者判断が残る工程を区別して説明する。

- [09. OpenLane Minimal Flow｜最小RTL→GDSフロー](./09_openlane_minimal_rtl_predeclared_flow.md)
- [10. OpenLane Control ASIC｜制御ASICのRTL→GDS](./10_openlane-control-asic-rtl-to-gds.md)
- [11. OpenLane2 SRAM Hard Macro｜SRAMハードマクロ統合](./11_openlane2_sram_hard_macro.md)
- [12. OpenLane1 Setup｜OpenLane v1 環境構築](./12_openlane1_setup.md)
- [13. OpenLane2 Setup｜OpenLane v2 環境構築](./13_openlane2_setup.md)
- [14. OpenLane PDK｜PDK構造と使い方](./14_openlane_pdk.md)

---

## Legacy Technology｜半導体技術史・故障と判断の記録

本セクションでは、  
1990年代後半〜2000年代初頭の実製品を対象に、

- 実際に発生した故障現象
- 対応した物理要因
- 歩留まり回復の限界
- 継続・撤退の判断

を **事実ベースで記録**する。

現行技術への適用やノウハウ展開は目的としない。

- [15. Legacy Technologyとは何か｜物理に支配されていた時代の失敗記録](./15_legacy_intro.md)
- [16. 0.25µm DRAM Pause Refresh異常｜観測された現象](./16_legacy_dram_1.md)
- [17. 0.25µm DRAM Pause Refresh異常｜物理的正体](./17_legacy_dram_2.md)
- [18. PSRAMは何を狙ったメモリだったのか｜DRAM流用という前提](./18_legacy_psram_1.md)
- [19. PSRAMで何が起き、なぜ終わったのか｜Pause×Disturbの現実](./19_legacy_psram_2.md)

---

## 本シリーズの読み方（目的別）

- **デバイス物理から設計前提まで確認したい場合**  
  → 01 → 06 → 07  

- **EDA・設計フローを把握したい場合**  
  → 12 → 09 → 10 → 11 → 13 → 14  

- **実製品での故障と判断を確認したい場合**  
  → 15 → 16 → 17 → 18 → 19  

---

## 本シリーズの対象範囲

- 半導体デバイス物理  
- 設計方法論・抽象化  
- EDAフロー  
- 実製品における故障と判断（Legacy）

以下は扱わない。

- 現行量産プロセスの詳細条件  
- 再現可能な製造レシピ  
- 特定企業の機密情報  

---

## Closing

本インデックスは、  
**半導体技術を「個別テーマ」ではなく、  
物理・設計・ツール・実製品の関係として整理するための入口**である。
