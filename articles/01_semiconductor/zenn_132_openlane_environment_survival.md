---
title: "【半導体】01. OpenLane 環境で9割決まる｜WSL2・Docker・PDKで踏み抜く地雷の全回避"
emoji: "🧱"
type: "tech"
topics: ["OpenLane", "ASIC", "EDA", "Docker", "WSL"]
published: true
---

## 🧭 はじめに：なぜOpenLaneは「動かない」のか

OpenLaneは、  
**RTLからGDSIIまでを一気通貫で流せるOSSのASIC設計フロー**です。

🔗 公式リポジトリはこちらです。  
[https://github.com/The-OpenROAD-Project/OpenLane](https://github.com/The-OpenROAD-Project/OpenLane)

それにもかかわらず、実際の利用者からは次のような声が頻発します。

- ❌ インストールできない  
- ❌ 途中でフローが止まる  
- ❌ 昨日まで動いていたのに突然壊れた  
- ❌ チュートリアル通りなのに合成できない  

結論から述べます。

> ⚠️ **OpenLaneは環境で9割決まります。**

設計以前に、  
**環境設計そのものが破綻しているケースが圧倒的に多い**のが現実です。

本記事では、  
OpenLane Guide の **Phase 1：Environment Survival** を基に、

- 🧱 なぜ順番厳守なのか  
- 🔀 なぜ OpenLane1 と OpenLane2 を分離する必要があるのか  
- 📦 なぜ PDK を固定しなければならないのか  

を **理由ベース** で解説します。

📘 本記事の元になっている体系的ガイドはこちらです。  
[https://samizo-aitl.github.io/openlane-guide/](https://samizo-aitl.github.io/openlane-guide/)

---

## 🧩 OpenLaneは「ツール」ではなく「環境」である

まず最初に、この認識が必要です。

OpenLaneは単体ツールではありません。

- 🧠 Yosys（論理合成）  
- 🏗 OpenROAD（配置配線）  
- 🧪 Magic / Netgen（DRC / LVS）  
- ⏱ STA / Tcl / Python / Make  

これらを **Dockerコンテナ内で統合した“環境”** です。

つまり、

> 💥 OpenLaneが壊れる  
> ＝ **WSL × Docker × ホストOS × PDK のどこかが壊れている**

という意味になります。

---

## 🐳 WSL2 + Docker Desktop は「妥協」ではない

よくある誤解があります。

- 🤔 Linuxに直入れした方が速いのではないか  
- 🤔 Dockerは不要ではないか  

これは **最初に踏み抜く地雷** です。

### なぜ WSL2 + Docker なのか

理由は以下の3点です。

1. 🧼 **ホストOS差分を完全に消すため**  
2. 🧨 **依存関係地獄を封じるため**  
3. ♻️ **壊れたら捨てる前提で運用するため**

OpenLaneは、  
長期間「育てる」環境ではありません。

> 🔁 **再現可能な箱を、必要に応じて作り直す**

この思想に最も適しているのが  
WSL2 + Docker Desktop です。

---

## 🔀 OpenLane1 と OpenLane2 を分けないと必ず壊れる

ここが **最大の事故ポイント** です。

### 設計思想がそもそも違う

| 項目 | OpenLane1 | OpenLane2 |
|---|---|---|
| 🎯 目的 | 安定運用 | 実験・評価 |
| 🧭 フロー | Makefile | Python |
| 📦 PDK | 固定前提 | 変動あり |
| ♻️ 再現性 | 高 | 低 |

**同居を想定した設計ではありません。**

同一WSL・同一Docker・同一PDKパスで混在させると、  
🚨 **確実に破綻します。**

> 「OpenLane2を試した後にOpenLane1が動かなくなった」

これはバグではなく、  
**設計思想どおりの結果**です。

---

## 📦 PDKは「最新」が最悪の選択

初心者が必ず言います。

> ✨ せっかくなら最新版PDKを使いたい

これは **致命的な判断** です。

### PDKは巨大な前提集合

PDKは単なるデータではありません。

- ⚡ SPICEモデル  
- 📐 LEF / DEF  
- ⏱ タイミングモデル  
- 🧪 DRCルール  

これら全てが **設計前提そのもの** です。

PDKが変わるということは、

> 🔄 **設計条件が全て変わる**

という意味になります。

### 正解はこれだけです

- 📌 PDKは固定  
- 🔗 OpenLaneバージョンとセットで固定  
- 🧪 更新は必ず別環境  

CIや教育用途でOpenLaneを使う場合、  
これを守らないと **再現不能な環境** になります。

---

## ⚖️ 壊れる環境・壊れない環境の差

### 💣 壊れる環境の特徴

- OpenLane1 / 2 を混在  
- PDKを途中で更新  
- Dockerを育てる運用  
- Exportを取らない  

### 🛡 壊れない環境の特徴

- 役割ごとに環境分離  
- PDK固定  
- Dockerは消耗品  
- Export / Import 前提  

---

## 💾 WSL Export / Import は「保険」ではない

WSLの Export / Import は、  
災害復旧用ではありません。

> 🔑 **運用前提の必須機能**です。

- 📤 動いている時点でExport  
- 🧪 実験前にExport  
- 📥 壊れたら即Import  

これを行わない環境は、  
**遅かれ早かれ詰みます。**

---

## 🧱 なぜ順番厳守なのか

OpenLane Guide が  
「順番厳守」「飛ばすな」と明言している理由は明確です。

> ❗ **環境が壊れた状態では、  
> 物理設計もタイミングも全て嘘になる**

---

## 📝 まとめ

- 🧠 OpenLaneは環境が9割  
- 🐳 WSL2 + Docker は必須  
- 🔀 OpenLane1 / OpenLane2 は完全分離  
- 📦 PDKは固定  
- 💾 Export / Import 前提で運用  

これが **Phase 1：Environment Survival** の結論です。

---

## ▶️ 次回予告

次回は **Phase 2：Physical Design Reality**。

- 🏗 なぜ自動フローは失敗するのか  
- ⏱ なぜ timing が突然崩れるのか  
- 👀 GUIで何を見るべきか  

**「OpenLaneは魔法ではない」**  
その現実を、物理設計の視点から解剖します。
