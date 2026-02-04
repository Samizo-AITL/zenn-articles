# 02_control / 制御・AITL 記事一覧

本ディレクトリでは、  
**PID制御・FSM・AITL（Architecture for Integrated Technology Logic）** を中心に、  
制御理論・信頼性設計・安全境界・人間設計思想までを体系的に整理しています。

---

## 📘 基本構造・思想

- [01 AITL Controller 概要](./01_aitl-controller.md)
- [02 FSM制御が効かない理由](./02_fsm-control-no-effect.md)
- [03 PIDは想定以上に強力である](./03_pid_is_stronger_than_expected.md)

---

## 🛡 信頼性制御・設計限界

- [04 ロバスト制御を超える信頼性制御](./04_reliability-control-beyond-robust.md)
- [05 信頼性制御がタイミングで破綻する理由](./05_reliability_control_timing_fail.md)
- [06 AITLにおける信頼性FSM](./06_aitl_reliability_fsm.md)

---

## 🔮 将来設計・制御分類

- [07 B-Type制御と将来方向性](./07_btype_future_direction.md)

---

## ⚙ PID × FSM 統合設計

- [08 PID-FSM 10%しきい値設計](./08_pid_fsm_10pct_threshold_design.md)
- [09 人間設計に基づくAITL PID-FSM最終形](./09_aitl_pid_fsm_human_design_final.md)
- [10 エンベロープ設計とリカバリ戦略](./10_envelope_design-recovery.md)

---

## 🚧 A-Type / B-Type 制御制限

- [11 A-Type 制御の限界](./11_aitl_a_type_limit.md)
- [12 B-Type 制御ガード設計](./12_aitl_b_type_guard.md)
- [13 FSM信頼性ガード](./13_fsm_reliability_guard.md)

---

## 🔒 安全境界・パッケージ化

- [14 AITLコントローラ 信頼性境界](./14_aitl_controller_reliability_boundary.md)
- [15 AITL Controller Safety Package（初版）](./15_aitl-controller-safety-package.md)
- [16 AITL Controller Safety Package（統合版）](./16_aitl-controller-safety-package.md)

---

## 🧭 位置づけ

- **PID**：内側の実時間安定化ループ  
- **FSM**：モード・状態遷移の監督層  
- **AITL（LLM）**：異常・劣化時の再設計・再構成層  

> 制御は「強くする」ものではなく、  
> **壊れ方を設計する技術である**。

---


