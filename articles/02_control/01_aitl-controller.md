---
layout: default
title: AITL-controller
---

# 【制御:01】🧩 AITL-controller  
### ― PID × FSM × LLM による三層制御アーキテクチャの統合フレームワーク

---

本記事では、**AITL-controller** が提供する  
**PID（リアルタイム制御）× FSM（状態遷移）× LLM（知能制御・再設計）**  
という三層制御アーキテクチャについて紹介します。

- 公式サイト：  
  [https://samizo-aitl.github.io/aitl-controller-a-type/](https://samizo-aitl.github.io/aitl-controller-a-type/)

- GitHub リポジトリ：  
  [https://github.com/Samizo-AITL/aitl-controller-a-type](https://github.com/Samizo-AITL/aitl-controller-a-type)

---

## 🧠 AITL-controller とは？

AITL-controller は、  
**クラシカル制御（PID）・形式的制御（FSM）・知能制御（LLM）を統合した三層アーキテクチャ**を、  
教育・研究用途で扱えるようにした軽量フレームワークです。

三層構造は、次のように役割分担されています。

---

## 🧱 三層アーキテクチャ（PID × FSM × LLM）

### 1️⃣ Inner Loop：PID（リアルタイム制御）

- ロボット／プラントの挙動を直接制御する最内層  
- 例：角度保持、速度制御、姿勢制御など  
- **安定性**と**応答性能**を担保するための制御ループ  

PID は従来通り高速に回し、  
**ミリ秒単位の応答**を扱う領域を担当します。

---

### 2️⃣ Middle Loop：FSM（Finite State Machine）

- システム全体の **モード管理** と **状態遷移** を司る中間層  
- 例：  
  - Idle → Running → Fault  
  - Lift → Hold → Place  

PID の集合を「どの状態でどれを使うか」管理する  
**監督レイヤ**です。

FSM は、

- いつ PID を切り替えるか  
- どのパラメータを有効化するか  

を管理します。

---

### 3️⃣ Outer Loop：LLM（知能制御）

- 故障・異常・性能劣化の検知  
- それに対する **再設計** や **推論** を担当  

例：

- PID パラメータの自動再同定  
- 状態遷移ルールの修正提案  
- 動作ログから異常傾向を推論  

このレイヤでは、LLM の強みである

- モデル外挙動への適応  
- 自然言語による説明生成  

といった能力を活かします。

---

## ❓ なぜ三層構造なのか？

従来の制御系は、PID と FSM によって構築できますが、  
次のような課題があります。

- 環境変化に弱い  
- 故障時に人間が原因分析しなければならない  
- パラメータ調整にスキルが必要  

AITL-controller の狙いは、  
これらを LLM に担当させることで、

> **「自律的に改善する制御システム」**

を、教育・研究レベルで構築可能にすることです。

---

## 📦 リポジトリ構成（概要）

```
aitl-controller/
├── core/
│   ├── pid/             # PID モジュール（安定性・性能保証）
│   ├── fsm/             # FSM モジュール（状態遷移）
│   └── llm/             # LLM モジュール（再設計・推論）
│
├── demo/
│   ├── inverted_pendulum/   # 倒立振子デモ
│   ├── quadrotor/           # クワッドロータ制御（例）
│   └── simple_robot/        # 小規模ロボット系
│
├── docs/
│   ├── architecture/        # 三層構造の解説
│   ├── math/                # PID, FSM の数式
│   ├── llm/                 # LLM 制御の設計指針
│   └── examples/            # チュートリアル
│
└── assets/                  # 図・ワークフロー資料
```

フレームワークの中核は **core/** に集約され、  
**demo/** にすぐ動かせるサンプルが用意されています。

---

## 🔄 典型的な制御ループ構成

AITL-controller が想定する制御ループは次の通りです。

```
Sensor → PID → Actuator → Plant
        ↑        ↓
        FSM ← LLM (Outer loop)
```

### 役割整理
- PID：リアルタイム誤差修正  
- FSM：PID の組合せと状態遷移を制御  
- LLM：ログを解析し、PID / FSM を再設計  

---

## 🧪 使用例（倒立振子デモ）

倒立振子デモでは、次のように三層が協調します。

1. **PID**：角度が倒れないよう補正  
2. **FSM**：  
   - Stabilize  
   - Recover  
   - Fault  
   といった状態管理  
3. **LLM**：  
   - 転倒原因の解析  
   - PID ゲイン改善案の提示  
   - 状態遷移ルールの改善案生成  

LLM が直接アクチュエータを動かすことはありません。  
**制御構造そのものを改善する役割**に徹する点が特徴です。

---

## 🧩 LLM 制御の役割（設計方針）

AITL-controller では、LLM に次の 3 つのタスクを割り当てています。

### 1. 監視（Monitoring）
- ログから異常・性能低下を検出

### 2. 診断（Diagnosis）
- 不具合・性能劣化の原因を説明可能な形で特定

### 3. 再設計（Redesign）
- PID ゲイン  
- 状態遷移表  
- 監督ルール  

を、自然言語やコード生成を通じて改善します。

---

## ⚙ セットアップ

```bash
git clone https://github.com/Samizo-AITL/aitl-controller.git
cd aitl-controller
pip install -r requirements.txt
```

ドキュメントは、  
公式サイト（GitHub Pages）にまとまっています。

---

## 🎓 どのような学習・研究に使えるか？

AITL-controller は、以下の用途に向いています。

- 制御工学（PID・FSM）の基礎学習  
- 通常制御系への AI / LLM 統合研究  
- ロボティクス高機能制御の教育  
- 自律システム再設計アルゴリズムの検証  
- 障害時の説明可能 AI（XAI）としての活用  

特に教育用途では、

> **「PID / FSM の基礎理解」  
> →「LLM による改善」**

という流れを自然に学べます。

---

## 📝 まとめ

AITL-controller は、次の三層を統合した制御フレームワークです。

- **PID**：リアルタイム制御  
- **FSM**：状態遷移管理  
- **LLM**：再設計と知能制御  

クラシカル制御を踏まえつつ、  
**AI 時代の新しい制御体系を学び・検証できる  
教育／研究プラットフォーム**  
となることを目指しています。

---

- 公式サイト：  
  [https://samizo-aitl.github.io/aitl-controller-a-type/](https://samizo-aitl.github.io/aitl-controller-a-type/)

- GitHub リポジトリ：  
  [https://github.com/Samizo-AITL/aitl-controller-a-type](https://github.com/Samizo-AITL/aitl-controller-a-type)
