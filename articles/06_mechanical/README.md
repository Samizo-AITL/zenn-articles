# 06_mechanical / 機械設計・CAD to Code 記事一覧

本ディレクトリでは、  
**機械設計（Mechanical Design）** を  
従来の GUI CAD 作業から切り離し、  
**コードによる再現性・差分管理・構造化設計**へと拡張します。

---

## 🖥 GUI から Code への転換

- [01 GUI CAD から Code へ](./01_gui-cad-to-code.md)

> 形状を「描く」のではなく、  
> **構造として定義する**という発想転換。

---

## 📐 FreeCAD の思想と位置づけ

- [02 FreeCAD とは何か](./02_what-is-freecad.md)

> FreeCAD は  
> CAD ツールではなく  
> **ジオメトリ記述エンジン**である。

---

## 🧠 コードによる設計思考

- [03 FreeCAD コード設計](./03_freecad_code_design.md)
- [04 コードで行う部品設計](./04_part_design_with_code.md)

> 寸法・拘束・意図を  
> **コードで固定することで設計が安定する**。

---

## 🔍 設計差分・履歴管理

- [05 Git Diff による設計管理](./05_git_diff_code_design.md)

> 設計レビューは  
> 図面ではなく **diff** で行う。

---

## 🧩 ジオメトリ表現と再利用

- [06 FreeCAD ジオメトリ表現ショーケース](./06_geometric_showcase_freecad.md)

> ジオメトリは  
> 見せるものではなく  
> **再利用する部品**である。

---

## 🧱 共通コード構造・完成形

- [07 フルコード共通構造（最終形）](./07_full_code_common_structure.md)

> 機械設計を  
> **ソフトウェアと同じレベルで構造化する**。

---

## 🧭 本ディレクトリの位置づけ

- **06_mechanical**：
  - 物理形状をコードで固定する層
  - MEMS・インクジェット以前の「構造定義」
- **03_hardware / 04_mems / 05_inkjet** の土台
- AITL における **Physical Definition Layer**

> **機械設計が曖昧なままでは、  
> その上の制御も知能も成立しない。**

---

## 🔗 関連ディレクトリ

- [03_hardware / ハードウェア・物理制御](../03_hardware/)
- [04_mems / MEMS解析・アナログ物理](../04_mems/)
- [05_inkjet / インクジェット技術](../05_inkjet/)
