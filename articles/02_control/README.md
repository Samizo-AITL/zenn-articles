# 🎛️ 02_control / 制御・AITL 記事一覧

本ディレクトリでは、  
**PID制御・FSM・AITL（Architecture for Integrated Technology Logic）** を中核に据え、  
制御理論を「安定化手法」ではなく  
**信頼性・安全性・判断構造を含む設計技術**として再整理する。

数式や制御則そのものよりも、

- どこまでを制御対象とみなすのか  
- どの層が、どの責任を持つのか  
- どの時点で「制御をやめる」と判断すべきか  

といった **設計上の前提と限界**を明確にすることを目的とする。

---

## 📘 基本構造・思想

本セクションでは、  
AITL制御の全体像と、従来制御が抱えてきた前提のズレを整理する。

- [01 AITL Controller 概要](./01_aitl-controller.md)  
  AITL制御アーキテクチャの全体像と、PID・FSM・LLMの役割分担

- [02 FSM制御が効かない理由](./02_fsm-control-no-effect.md)  
  状態遷移制御が現実系で破綻する構造的理由

- [03 PIDは想定以上に強力である](./03_pid_is_stronger_than_expected.md)  
  PID制御が成立し続けてきた本当の理由と、その適用範囲

---

## 🛡 信頼性制御・設計限界

本セクションでは、  
「安定しているように見える制御」が  
**どの条件で静かに壊れるのか**を扱う。

- [04 ロバスト制御を超える信頼性制御](./04_reliability-control-beyond-robust.md)  
  ロバスト性では説明できない劣化・異常の扱い方

- [05 信頼性制御がタイミングで破綻する理由](./05_reliability_control_timing_fail.md)  
  制御周期・判断遅延が致命傷になる瞬間

- [06 AITLにおける信頼性FSM](./06_aitl_reliability_fsm.md)  
  失敗を前提としたFSM設計の考え方

---

## 🔮 将来設計・制御分類

本セクションでは、  
制御系を **万能化しないための分類軸**を導入する。

- [07 B-Type制御と将来方向性](./07_btype_future_direction.md)  
  A-Type / B-Type による制御適用範囲の整理

---

## ⚙ PID × FSM 統合設計

本セクションでは、  
理論ではなく **実装として成立する制御構造**を扱う。

- [08 PID-FSM 10%しきい値設計](./08_pid_fsm_10pct_threshold_design.md)  
  境界を数値で切る設計判断

- [09 人間設計に基づくAITL PID-FSM最終形](./09_aitl_pid_fsm_human_design_final.md)  
  人間が理解・介入できる制御構造

- [10 エンベロープ設計とリカバリ戦略](./10_envelope_design-recovery.md)  
  壊れた後を含めた制御設計

---

## 🚧 A-Type / B-Type 制御制限

本セクションでは、  
「できないこと」を明示する。

- [11 A-Type 制御の限界](./11_aitl_a_type_limit.md)
- [12 B-Type 制御ガード設計](./12_aitl_b_type_guard.md)
- [13 FSM信頼性ガード](./13_fsm_reliability_guard.md)

---

## 🔒 安全境界・パッケージ化

本セクションでは、  
制御系を **製品として成立させるための境界**を定義する。

- [14 AITLコントローラ 信頼性境界](./14_aitl_controller_reliability_boundary.md)
- [15 AITL Controller Safety Package（初版）](./15_aitl-controller-safety-package.md)
- [16 AITL Controller Safety Package（統合版）](./16_aitl-controller-safety-package.md)

---

## 🧾 総括・設計仕様（全体把握用）

本セクションは、  
個別記事を横断するための参照点として用いる。

- [17 AITL制御アーキテクチャ設計仕様](./17_aitl_control_architecture_spec.md)
- [18 AI制御 安全設計チェックリスト（運用用）](./18_ai_control_safety_checklist.md)
- [19 適応制御の適用限界整理（A-Type / B-Type）](./19_adaptive_control_applicability_limits.md)

---

## 🧭 位置づけ

- **PID**：内側の実時間安定化ループ  
- **FSM**：モード・状態遷移の監督層  
- **AITL（LLM）**：異常・劣化時の再設計・再構成層  

> 制御は「強くする」ものではなく、  
> **壊れ方を設計する技術である**。
