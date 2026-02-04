# 🧩📚 zenn-articles

このリポジトリは、Zennに公開する技術記事およびBookを  
**Markdown原稿（一次情報・正本）として管理するためのリポジトリ**です。

Zennは体系的な公開・連載の場、  
GitHubは **設計・編集・履歴管理の場**  
という役割分担を前提としています。

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
│ ├─ README.md
│ └─ index.md
├─ articles/
│ ├─ semiconductor/
│ ├─ control/
│ ├─ mems/
│ ├─ inkjet/
│ ├─ hardware/
│ ├─ other/
│ └─ en/
│ └─（同構造）
├─ books/
│ ├─ aitl-physical-ai/
│ └─ en/
│ └─ aitl-physical-ai/
└─ assets/
```


---

## 🧭 Article Classification

本リポジトリでは、記事を以下の技術分野で分類します。

- **Semiconductor**  
  デバイス物理、プロセス、回路、スケーリング
- **Control**  
  PID、FSM、制御構造、AITL（Architecture for Integrated Technology Logic）
- **MEMS**  
  圧電アクチュエータ、微細構造、物理モデル
- **Inkjet**  
  ドロップ形成、駆動波形、システム統合
- **Hardware**  
  実装設計、V–I予算、システムアーキテクチャ
- **Other**  
  可視化、AI設計、横断的な技術思想

分類は**主軸**であり、Zenn上ではタグやBook構成によって横断的に再構成します。

---

## 🌍 English Articles

英語版記事は翻訳ではなく、  
**日本語版と同等の正本**として `en/` 以下に並行管理します。

---

## 🧪 Writing Policy

- 🏛 GitHub上のMarkdownを正本とする
- 📘 ZennのBook / Articleは本リポジトリから派生させる
- 🔢 記事番号は分野ごとに管理する（001〜）
- 🔁 構成変更・加筆はGitHub側で先に行う

---

## 👤 Author

**Shinichi Samizo**  
Semiconductor / MEMS / Inkjet / Control Architecture  
GitHub: https://github.com/Samizo-AITL

---

## 📄 License

- **Source Code**: MIT License  
- **Text**: CC BY 4.0 / CC BY-SA 4.0  
- **Figures**: CC BY-NC 4.0  

詳細は各記事の記載に従ってください。
