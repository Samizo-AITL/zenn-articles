---
layout: default
title: zenn-articles
---

# 【機械設計】🧩 11. コードでアセンブリを定義する ― FreeCADを配置エンジンとして使う

topics: ["機械設計", "CAD", "FreeCAD", "Python", "Assembly", "Git"]

---

## 🏁 はじめに

これまでの記事では、

- 部品形状をコードで生成する  
- ジオメトリを関数として扱う  
- 差分を Git で管理する  

ところまでを扱ってきました。

本稿では、次の事実のみを扱います。

> **複数の部品を、FreeCAD の GUI 操作を使わず、  
> Python コードだけで配置する**

対象は **アセンブリ生成の最小例** です。

---

## 📦 対象リポジトリ

- リポジトリ  
  https://github.com/Samizo-AITL/full-code-mechanical-design

- アセンブリ定義コード  
  src/assembly/demo_assembly.py

---

## 🧱 前提条件

- 各部品は parts/ 以下で単体生成できる  
- 各部品は原点と向きが明示されている  
- 拘束機能は使わない  

---

## 📐 配置は数値で決める

```python
import FreeCAD as App

placement = App.Placement(
    App.Vector(x, y, z),
    App.Rotation(App.Vector(ax, ay, az), angle)
)
```

---

## 🧪 実行方法

### Windows

```powershell
cd src
"C:\Program Files\FreeCAD 0.21\bin\FreeCADCmd.exe" build.py
```

### Linux

```bash
cd src
freecadcmd build.py
```

---

## 🖥 生成結果

![Code-generated mechanical assembly](https://samizo-aitl.github.io/full-code-mechanical-design/fig/01_demo_assembly_generated.png)

---

## 🎯 まとめ

- 部品生成は parts/  
- 配置定義は assembly/  
- 実行は build.py  
