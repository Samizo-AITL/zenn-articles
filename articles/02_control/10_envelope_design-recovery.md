---
title: 【AITL】Envelope Control と Design Recovery Control ― 制御ではなく「境界」と「前提」を扱う
emoji: 🧭
type: tech
topics: [control, design, architecture, ai, llm]
published: true
---

## はじめに

最近、制御や AI を扱う文脈で  
「LLM で制御する」「AI が最適化する」といった話をよく見かけます。

ただ、実際の物理システムやデバイス設計の現場では、

- 制御は **最後に効かせるもの**
- 本当に壊れるのは **設計前提や運用境界**
- AI をリアルタイム制御に入れるのは **危険**

という感覚のほうが支配的です。

この記事では、そうした前提のもとで整理した  
**2つの制御アーキテクチャ概念**を紹介します。

```text
| Envelope Control        | Runtime（運用）の境界を守る |
| Design Recovery Control | Design-time（設計前提）を回復する |
```

どちらも「制御そのもの」ではなく、  
**制御が破綻しないための構造**を扱います。

---

## Envelope Control とは何か

Envelope Control は、

> **不確実性下において、  
> システムを「安全な運転範囲（Envelope）」に拘束する概念**

です。

ここで重要なのは、

- 高性能な制御を目指さない
- 最適化もしない
- 学習もしない

という点です。

やることは非常に単純で、

- 電圧・電流・温度・速度などの**物理量**
- その「超えてはいけない範囲」

を **実行時に守り続ける**こと。

制御器（PID など）はその中で普通に動きますが、  
Envelope を越えそうになった瞬間に **運用が抑制される**。

👉 **「どう動かすか」ではなく  
「どこまでなら動かしていいか」** を決める制御です。

---

## Design Recovery Control とは何か

一方で、Design Recovery Control（DRC）が扱うのは  
**まったく別の時間軸**です。

> **制御が破綻した原因となる  
> 「設計前提そのもの」を回復するための概念**

DRC は以下を**やりません**。

- 制御入力を出さない
- リアルタイムに介入しない
- 学習で最適化しない

代わりにやるのは、

- PID ゲインは「まだ妥当か」
- FSM の遷移条件は「現実と合っているか」
- 運用モード定義は「古くなっていないか」

といった **設計前提の点検と更新**です。

LLM が関与する場合でも、

- 実行はしない
- 提案だけを出す
- 人間やシステムが承認する

という **設計監督の役割**に限定されます。

👉 DRC は **制御ではなく設計レビューの構造化**です。

---

## 2つの関係性（重要）

この2つは **競合しません**。

| 観点 | Envelope Control | Design Recovery Control |
|---|---|---|
| 扱う時間軸 | Runtime（運用中） | Design-time（設計更新） |
| 扱う対象 | 運転範囲（Envelope） | 設計前提・仮定 |
| 制御入力 | 触らない | 触らない |
| AI / LLM | 原則使わない | 設計監督としてのみ |

一言で言えば：

- **Envelope Control**  
  → *「いま、どう抑えて運転するか」*

- **Design Recovery Control**  
  → *「なぜ設計が通らなくなったか」*

この2つが揃って初めて、  
**制御は“普通の制御”のままでいられる**。

---

## 実装ではなく、位置づけの話

ここで強調したいのは、

> これは「制御アルゴリズム」の話ではない

という点です。

どちらも、

- PID がどうとか
- 数式がどうとか
- 安定性証明がどうとか

より前にある、

> **設計として、どこで責任を分けるか**

の話です。

---

## 参考リンク

概念の定義と整理は、以下で公開しています。

- **Envelope Control**  
  🔗 https://samizo-aitl.github.io/envelope-control/  
  🔧 https://github.com/Samizo-AITL/envelope-control

- **Design Recovery Control**  
  🔗 https://samizo-aitl.github.io/design-recovery-control/  
  🔧 https://github.com/Samizo-AITL/design-recovery-control

---

## おわりに

制御を高度化するより先に、

- どこで壊れるのか
- 何が前提だったのか
- いつ設計を見直すのか

を **構造として切り分ける**ほうが、  
現実のシステムではずっと重要です。

Envelope Control と Design Recovery Control は、  
そのための **設計側の道具**です。

制御を「賢くする」前に、  
**制御を壊さない構造**を考える。

その整理として、  
この2つの概念を置いています。
