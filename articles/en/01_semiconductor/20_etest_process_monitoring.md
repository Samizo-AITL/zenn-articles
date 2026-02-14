---
layout: default
title: zenn-articles
---

# 【Semiconductor】🧪 20. What Is ETEST?  
### — An Evaluation Process for Quantitative Monitoring of Process Variations
topics: ["Semiconductor", "ETEST", "TEG", "Process", "Quality"]

---

## 🧭 Introduction

In semiconductor manufacturing, it is essential to verify  
**whether process conditions are maintained as intended by design**  
*before* product failures become visible.

This role is fulfilled by  
**ETEST (Engineering Test)**.

ETEST is not a product test,  
nor is it a screening step for pass/fail judgment.

In this article, we explain:

- The physical parameters measured by ETEST  
- Why TEGs are used instead of product chips  
- How ETEST data is fed back into design and device models  

from the perspective of **process monitoring**.

---

## 🧪 Definition and Role of ETEST

ETEST is an evaluation process that  
**quantitatively measures electrical parameter variations in wafer fabrication processes**.

The measurement targets are  
**TEGs (Test Element Groups)** placed in scribe-line regions,  
not the product circuits themselves.

Typical parameters measured by ETEST include:

- Threshold voltage (Vth)  
- Saturation current (Idsat)  
- Off-state current (Ioff)  
- Sheet resistance of diffusion, poly, and metal layers  
- Contact resistance  

All of these parameters  
**directly reflect process conditions rather than circuit functionality**.

---

## 📐 Why Product Chips Are Not Measured

Product chips have the following characteristics:

- Complex circuit configurations  
- Multiple operating conditions  
- Mixed failure causes from both circuit and process factors  

As a result, it is difficult to isolate  
**process-induced variations directly from product measurements**.

In contrast, TEGs are designed to be:

- Structurally simple and well-defined  
- Measured under fixed and known conditions  
- Highly sensitive to process variations  

Therefore, ETEST enables:

> **Observation of process variations with circuit effects removed**

---

## 📊 How ETEST Data Is Used

Data obtained through ETEST is continuously used for:

- Monitoring within-wafer and within-lot variations  
- Detecting equipment drift  
- Evaluating the impact of process condition changes  
- Calibrating SPICE model parameters  
- Validating design margins  

A key point is that  
ETEST data serves as a **common quantitative reference shared by design and manufacturing teams**.

---

## 🔁 Difference Between ETEST and Screening Tests

ETEST:

- Does not screen defective chips  
- Does not determine whether a die proceeds to the next process  

This clearly distinguishes ETEST from  
wafer testing (WAT).

The purpose of ETEST is  
**continuous monitoring of process conditions and early detection of abnormal trends**.

Accordingly, ETEST is positioned as:

> A process to *detect changes*, not a process to *stop production*

---

## 📝 Summary

- ETEST is an evaluation process for monitoring electrical parameter variations in manufacturing  
- The measurement targets are TEGs, not product chips  
- ETEST data is fed back into design, modeling, and process control  
- ETEST is a monitoring step, not a quality screening step  

---

## 🌐 Official Link (Edusemi-v4x)

- 📂 Chapter 6 Test & Package (Official)  
  [https://samizo-aitl.github.io/Edusemi-v4x/chapter6_test_and_package/](https://samizo-aitl.github.io/Edusemi-v4x/chapter6_test_and_package/)
