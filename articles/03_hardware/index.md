---
layout: default
title: zenn-articles
---

# 03_hardware / ハードウェア・物理制御 記事一覧

本ディレクトリでは、  
**AITL（Architecture for Integrated Technology Logic）** を  
「物理・ハードウェア層」から捉え直し、  
**なぜ制御できないのか／どこまで制御すべきでないのか** を明確化します。

---

## 📘 物理参照・基準定義

- [01 AITL Physical Reference（物理参照系）](./01_aitl-physical-reference.md)

> 制御設計の前に、  
> **物理とは何か／何を基準に見るのか** を定義する。

---

## 🚫 制御できない理由の明確化

- [02 APN v1 はなぜ制御ではないのか](./02_apn-v1-why-not-control.md)

> 「制御に見えるもの」と  
> **本当の制御の違い**を切り分ける。

---

## 🧱 ハードウェア・アーキテクチャ

- [03 ハードウェアアーキテクチャ v2（物理層）](./03_hardware_architecture_v2_physical.md)

> ソフト以前に、  
> **物理配置・結線・責務分離**が制御性能を決める。

---

## ⚙ 物理制御とAITL

- [04 AITL Physical Control v3](./04_aitl_physical_control_v3.md)

> 物理層における  
> **AITLの成立条件・限界・安全境界**を定義する。

---

## 🧭 本ディレクトリの位置づけ

- **03_hardware**：  
  - 制御以前の「物理・構造・配置」を扱う  
  - PID / FSM / LLM が **触れてはいけない領域**を明示  
- **02_control** と対になる存在  
  - 02 = 論理・制御構造  
  - 03 = 物理・実体構造  

> **制御できないものを制御しようとした瞬間、  
> システムは壊れ始める。**

---

## 🔗 関連ディレクトリ

- [02_control / 制御・AITL](../02_control/)
- [01_semiconductor / 半導体基礎](../01_semiconductor/)

---

