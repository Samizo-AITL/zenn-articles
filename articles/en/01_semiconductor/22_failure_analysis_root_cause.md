---
layout: default
title: zenn-articles
---

# 【Semiconductor】🔬 22. What Does Failure Analysis (FA) Decide?  
### — A Technique for Determining Corrective Targets, Not Mere Observation
topics: ["Semiconductor", "Failure Analysis", "FA", "OBIRCH", "Quality"]

---

## 🧭 Introduction

Failure Analysis (FA) is not simply  
“an activity to investigate why something broke.”

The objective of FA is explicit:

> **To determine whether an observed failure is caused by  
> process-related factors or design-related factors,  
> and to identify the appropriate corrective target**

In this article, we explain:

- The role of FA in manufacturing  
- Why OBIRCH is a mainstream analysis technique  
- Why failure analysis must not be terminated prematurely  

from the perspective of **the final step in the mass-production quality loop**.

---

## 🔬 Definition and Role of FA

FA takes as its input **failure results** detected in:

- ETEST  
- Wafer testing (WAT)  
- Reliability testing  

and proceeds to **physically identify the root cause** of those failures.

The ultimate purpose of FA is:

> **To determine corrective actions that prevent recurrence**

Corrective actions in this context include decisions on whether to return the issue to:

- Manufacturing process conditions  
- Equipment or materials  
- Design rules or device models  

FA must clearly determine **which domain requires correction**.

---

## 🔦 Why OBIRCH Is Used

Leakage currents and micro-shorts cannot be identified  
by observing layouts or cross-sectional structures alone.

OBIRCH (Optical Beam Induced Resistance Change) is a technique that:

- Maintains the device under bias  
- Irradiates a localized region with an infrared laser  
- Detects resistance changes and localized heating  

This enables visualization of:

- Locations where current is actually flowing  
- Coordinates at which failures are actively occurring  

**while the device is operating**.

In FA, the critical requirement is:

> **To observe failures in the state in which they occur**

In this regard, OBIRCH is an extremely effective technique.

---

## 🧪 Failure Analysis Is Performed Step by Step

FA does not rely on a single method.  
In practice, a **stepwise analysis flow** is typically employed:

1. Localization of the failure site using OBIRCH  
2. Identification of the defective layer through delayering  
3. Surface and structural observation using SEM  
4. Local cross-sectioning using FIB  
5. Elemental composition analysis using EDX  

By accumulating information at each stage,  
possible causes are systematically eliminated until **a definitive conclusion is reached**.

If analysis is stopped prematurely, it increases the risk of:

- Conclusions based on assumptions  
- Incorrect corrective actions  
- Recurrence of the same failure  

---

## 🖼 Overview of Failure Analysis (FA)  
### — Step-by-Step Analysis Flow Centered on OBIRCH —

![FA and OBIRCH overview](https://samizo-aitl.github.io/zenn-articles/articles/figs/fa_obirch.png)

> Figure: The role of Failure Analysis (FA) and the step-by-step analysis flow starting from OBIRCH.  
> The ultimate goal of FA is to determine whether the corrective action should be applied to the **manufacturing process** or to the **design**.

---

## 🧠 What Is the Output of FA?

The outputs of FA are not:

- Microscopy images  
- Analysis reports  

in themselves.

The true output of FA is:

> **A decision on whether corrective action is required  
> in the manufacturing process or in the design**

When this decision is fed back into the production line,  
the quality loop is closed and recurrence prevention is achieved.

---

## 📝 Summary

- FA physically identifies the root cause of observed failures  
- Its objective is not observation, but determination of corrective targets  
- OBIRCH is effective for visualizing failures under operating conditions  
- FA represents the final decision point in the manufacturing quality loop  

---

## 🌐 Official Link (Edusemi-v4x)

- 📂 Chapter 6 Test & Package (Official)  
  [https://samizo-aitl.github.io/Edusemi-v4x/chapter6_test_and_package/](https://samizo-aitl.github.io/Edusemi-v4x/chapter6_test_and_package/)
