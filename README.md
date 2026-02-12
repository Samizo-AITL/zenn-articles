# 🧩📚 zenn-articles

このリポジトリは、Zennに公開する技術記事およびBookを  
**Markdown原稿（一次情報・正本）として管理するためのリポジトリ**です。

Zennは体系的な公開・連載の場、  
GitHubは **設計・編集・履歴管理の場**  
という役割分担を前提としています。

[![Go to Portal (JP)](https://img.shields.io/badge/Go%20to%20Portal-6F42C1?style=for-the-badge&logo=homeassistant&logoColor=white)](https://samizo-aitl.github.io/portal/)

[![Zenn](https://img.shields.io/badge/Zenn-Articles-blue?logo=zenn)](https://zenn.dev/samizo_aitl)
[![Qiita](https://img.shields.io/badge/Qiita-Articles-lightgrey?logo=qiita)](https://qiita.com/ctrl_bug)

---

## 🔗 Links

| Language | GitHub Pages 🌐 | GitHub 💻 |
|----------|----------------|-----------|
| JP 日本語 | [![GitHub Pages JP](https://img.shields.io/badge/GitHub%20Pages-日本語-brightgreen?logo=github)](https://samizo-aitl.github.io/zenn-articles/) | [![GitHub Repo JP](https://img.shields.io/badge/GitHub-日本語-blue?logo=github)](https://github.com/Samizo-AITL/zenn-articles/tree/main) |
| EN English | [![GitHub Pages EN](https://img.shields.io/badge/GitHub%20Pages-English-brightgreen?logo=github)](https://samizo-aitl.github.io/zenn-articles/en/) | [![GitHub Repo JP](https://img.shields.io/badge/GitHub-English-blue?logo=github)](https://github.com/Samizo-AITL/zenn-articles/tree/main/en) |

---

## 🎯 Purpose

- 📝 Zenn記事・Bookの原稿をMarkdownで管理する
- 🧭 技術分野ごとに記事を体系化し、再利用可能な構造を保つ
- 🔁 改稿・再構成・翻訳（英語版）を履歴として残す
- 🧠 記事を「読み物」ではなく **技術資産**として蓄積する

---

## 🗂 Repository Structure

```
zenn-articles/
├─ README.md
├─ index.md
├─ en/
│  ├─ README.md
│  └─ index.md
├─ articles/
│  ├─ 01_semiconductor/
│  ├─ 02_control/
│  ├─ 03_hardware/
│  ├─ 04_mems/
│  ├─ 05_inkjet/
│  ├─ 06_mechanical/
│  ├─ 07_other/
│  └─ en/            # same structure as above
├─ books/
└─ assets/
```

---

## 🧭 Article Classification

本リポジトリでは、記事を以下の技術分野で分類しています。  
※ 各項目は **Samizo-AITL Portal 上の記事一覧（入口）への直接リンク** です。

| No. | 分野 | 主な内容 | 記事一覧（Portal） |
|---:|---|---|---|
| 01 | 🔬 **Semiconductor** | デバイス物理、プロセス、回路、スケーリング | [Semiconductor Articles](https://samizo-aitl.github.io/zenn-articles/articles/01_semiconductor/) |
| 02 | 🎛️ **Control** | PID、FSM、制御構造、AITL（Architecture for Integrated Technology Logic） | [Control Articles](https://samizo-aitl.github.io/zenn-articles/articles/02_control/) |
| 03 | 🧩 **Hardware** | 実装設計、V–I予算、システムアーキテクチャ | [Hardware Articles](https://samizo-aitl.github.io/zenn-articles/articles/03_hardware/) |
| 04 | 🧬 **MEMS** | 圧電アクチュエータ、微細構造、物理モデル | [MEMS Articles](https://samizo-aitl.github.io/zenn-articles/articles/04_mems/) |
| 05 | 💧 **Inkjet** | ドロップ形成、駆動波形、システム統合 | [Inkjet Articles](https://samizo-aitl.github.io/zenn-articles/articles/05_inkjet/) |
| 06 | ⚙️ **Mechanical** | 機械設計、CAD to Code、構造定義 | [Mechanical Articles](https://samizo-aitl.github.io/zenn-articles/articles/06_mechanical/) |
| 07 | 📊 **Other** | 可視化、分析、周辺技術 | [Other Articles](https://samizo-aitl.github.io/zenn-articles/articles/07_other/) |

---

## 📘 Books（体系教材・公式リポジトリ）

以下は、**記事群を体系化した Books 形式の公式教材リポジトリ**です。  
基礎理論から材料・プロセス・応用技術までを一貫した構成で整理しています。

| No. | 教材名 | 位置づけ | リポジトリ |
|---:|---|---|---|
| 01 | 🎓 **Edusemi-v4x** | 半導体基礎（デバイス物理・プロセス・回路・スケーリング） | [Edusemi-v4x](https://samizo-aitl.github.io/Edusemi-v4x/) |
| 02 | ➕ **Edusemi-Plus** | 応用編（材料技術、プロセス拡張、製造・実装関連トピック） | [Edusemi-Plus](https://samizo-aitl.github.io/Edusemi-Plus/) |
| 03 | 🎛️ **EduController** | 制御理論体系（PID・FSM・AITLアーキテクチャ） | [EduController](https://samizo-aitl.github.io/EduController/) |
| 04 | ⚙️ **Production Process for Mechanical Products** | メカ製品化 | [EduMecha/08_production_process](https://samizo-aitl.github.io/EduMecha/08_production_process/) |

---

## 🧪 Writing Policy

- 🏛 GitHub上のMarkdownを正本とする
- 📘 ZennのBook / Articleは本リポジトリから派生させる
- 🔢 記事番号は分野ごとに管理する（001〜）
- 🔁 構成変更・加筆はGitHub側で先に行う

---

## 🔗 Related Repositories（Publishing Channels）

本リポジトリと思想・設計を共有する、  
**別公開チャネル向けの公式原稿リポジトリ**です。

- 📝 **Qiita Articles（単発・実験・観測）**  
  設計思想・ツール検証・可視化など、  
  単発でも成立する技術記事を中心に公開  
  → [https://samizo-aitl.github.io/qiita-articles/](https://samizo-aitl.github.io/qiita-articles/)

※ 本リポジトリ（Zenn）は、  
　連載・体系化・Book化を前提とした構成を扱います。

---

## 👤 Author

| 📌 Item | Details |
|--------|---------|
| **Name** | Shinichi Samizo |
| **Expertise** | Semiconductor devices (logic, memory, high-voltage mixed-signal)<br>Thin-film piezo actuators for inkjet systems<br>Printhead productization, BOM management, ISO training |
| **GitHub** | [![GitHub](https://img.shields.io/badge/GitHub-Samizo--AITL-black?logo=github)](https://github.com/Samizo-AITL) |

---

## 📄 License

[![Hybrid License](https://img.shields.io/badge/license-Hybrid-blueviolet)](https://samizo-aitl.github.io/zenn-articles/#---license)

| 📌 Item | License | Description |
|--------|---------|-------------|
| **Source Code** | [**MIT License**](https://opensource.org/licenses/MIT) | Free to use, modify, and redistribute |
| **Text Materials** | [**CC BY 4.0**](https://creativecommons.org/licenses/by/4.0/) or [**CC BY-SA 4.0**](https://creativecommons.org/licenses/by-sa/4.0/) | Attribution required; share-alike applies for BY-SA |
| **Figures & Diagrams** | [**CC BY-NC 4.0**](https://creativecommons.org/licenses/by-nc/4.0/) | Non-commercial use only |
| **External References** | Follow the original license | Cite the original source properly |

---

## 💬 Feedback

> Suggestions, improvements, and discussions are welcome via GitHub Discussions.

[![💬 GitHub Discussions](https://img.shields.io/badge/💬%20GitHub-Discussions-brightgreen?logo=github)](https://github.com/Samizo-AITL/zenn-articles/discussions)


