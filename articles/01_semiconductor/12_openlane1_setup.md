---
layout: default
title: OpenLane1
---

# 【半導体:12】OpenLane1 WSL2 + DockerでRTL→GDSを動かす環境構築（再現性重視）
topics: ["openlane", "asic", "eda", "docker", "wsl2"]

---

## はじめに

OpenLane は、**RTLからGDSIIまでを一気通貫で流せるオープンなASIC設計フロー**です。  
ただし、最初の関門は常に「環境構築」です。

- ツールが多い  
- OS依存がある  
- どこまで動けば「成功」なのか分かりにくい  

この記事では目的を明確に絞ります。

> **OpenLaneを「理解する」前に、まず一度“最後まで流す”**

そのための **OpenLane1（Dockerベース）環境構築**を整理します。

---

## OpenLane1とは何か（本記事の前提）

OpenLane には大きく2系統があります。

- **OpenLane1**：Dockerベースの従来フロー  
- OpenLane2：Pythonベース（Nix推奨）の新系統  

本記事は **OpenLane1** のみを扱います。

OpenLane1 の特徴は以下です。

- Docker により環境が固定される  
- 教育・PoC用途で実績が多い  
- フローを「一周」体験するのに向いている  

👉 **環境理解よりも、設計フロー理解を優先するための選択肢**です。

---

## 想定環境（ここは固定）

再現性確保のため、以下を前提とします。

- Windows 11  
- WSL2  
- Ubuntu 22.04（WSL上）  
- Docker Desktop（WSL integration 有効）

※ macOS / Linux ネイティブ構成でも動作しますが、本記事では扱いません。

---

## 事前準備（要点のみ）

### WSL2

- WSL2 を有効化  
- Ubuntu 22.04 を導入  

詳細手順は Microsoft 公式資料に従ってください。

---

### Docker Desktop

- Docker Desktop をインストール  
- **Settings → Resources → WSL integration** を有効化  
- Ubuntu 22.04 を対象にチェック  

ここが無効だと OpenLane は起動しません。

---

## OpenLane1 の取得とビルド

WSL2 上の Ubuntu で作業します。

```bash
cd ~
git clone https://github.com/The-OpenROAD-Project/OpenLane.git
cd OpenLane
make
```

- Docker イメージのビルドが走ります  
- 初回は時間とディスク容量を要します  

---

## 動作確認（最重要）

必ず **`make test`** を実行してください。

```bash
make test
```

### `make test` の意味

- 合成  
- 配置配線  
- 検証系ツール  

が **一通り起動できるか** を確認するためのテストです。

> これが通らない場合、  
> **その環境では OpenLane は使えません。**

先に進まず、環境を見直してください。

---

## 最初の成功体験（GDS生成）

テストが通ったら、サンプル設計を流します。

```bash
make mount
```

コンテナ内で：

```bash
cd designs/spm
flow.tcl -interactive
```

フローを最後まで流し、`runs/` 以下に **GDS が生成されていること**を確認します。

※ サンプル設計や手順は OpenLane のバージョンにより変わる可能性があります。  
詳細は公式 README を併せて確認してください。

---

## よくあるトラブル（典型例）

### Docker / WSL2
- Docker Desktop が起動していない  
- WSL integration が無効  
- メモリ不足（WSL2の割当）  

### ファイル配置
- Windows 側ディレクトリで実行している  
  → **WSL 内に置く**のが推奨  

### GUI関連
- DISPLAY エラー  
  → 初回は GUI を使わないのが無難  

---

## なぜ OpenLane1 から始めるのか

OpenLane1 は、

- 環境を深く理解しなくても  
- フロー全体を体験できる  

という点で優れています。

> OpenLane1 はEDAツールではなく、  
> **設計フローを一度「最後まで流す」ための教材**です。

---

## 次のステップ

- 自作 RTL を流す  
- 制約（clock / floorplan）を調整する  
- 別系統である OpenLane2 を検討する  

次の記事では、

> **なぜ OpenLane2 が別系統として存在するのか**

を、設計思想の観点から整理します。

---

## まとめ

- OpenLane1 は「まず動かす」ための最短ルート  
- `make test` が通ることが最低条件  
- GDS が出れば成功  
- 深い設計や拡張はその後でよい  

まずは一周、流しましょう。
