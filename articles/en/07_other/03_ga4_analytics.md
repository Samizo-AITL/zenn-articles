---
layout: default
title: Country-Based Access Analysis of Samizo-AITL Portal | Where Is an English Tech Site Actually Read?
---

# 【Analytics】📊 03. Country-Based Access Analysis of Samizo-AITL Portal  
## Where Is an English Technical Site Actually Read From?
topics: ["analytics", "ga4", "githubpages", "techblog"]

---

## Introduction

Samizo-AITL Portal is a **personally operated technical portal site**  
focused on control systems, semiconductors, and AI architecture (AITL).

In this article, I use **Google Analytics 4 (GA4)** to conduct a simple check on:

> **Which countries are actually reading the site?**

This is not marketing analysis,  
but a lightweight **design verification** of an English technical site.

---

## 🌐 Samizo-AITL Portal (English Site)

The portal provides a **fully maintained English version**.

- English top page  
👉 [https://samizo-aitl.github.io/portal/en/](https://samizo-aitl.github.io/portal/en/)

- Japanese top page  
👉 [https://samizo-aitl.github.io/portal/](https://samizo-aitl.github.io/portal/)

The English site mirrors the Japanese structure and content,  
offering technical documents and architectural explanations in English.

---

## Methodology

- Analytics tool: Google Analytics 4 (GA4)  
- Period analyzed: Last 28 days  
- Metric: Active users  
- Dimension: **Country**

Notes:
- No user profiling or behavior analysis was performed  
- The focus is strictly on **country-level entry distribution**

---

## 📊 User Distribution by Country (GA4, Last 28 Days)

Below is the **country-based active user distribution**  
obtained from GA4’s *User attributes > Overview*.

![Samizo-AITL Portal Country Distribution (Last 28 Days)](https://samizo-aitl.github.io/zenn-books/assets/figs/ga4.png)

---

## ⏱ Real-Time Access Status (GA4)

Next, I checked the **real-time access overview** in GA4.  
The image below is a screenshot from *Realtime Overview*.

![Samizo-AITL Portal Real-Time Access (GA4)](https://samizo-aitl.github.io/zenn-books/assets/figs/ga4_2.png)

### How to Read the Real-Time View

- Blue circles on the map indicate regions with access in the last 30 minutes  
- Larger circles represent more frequent or concurrent access  
- The “last 30 minutes / last 5 minutes” counters show  
  **continuous inbound traffic from overseas**

Note:
- Access from Matsumoto, Japan is mostly the site owner’s own verification traffic

---

## Summary of Results

The top countries by access volume were:

| Country | Notes |
|---|---|
| United States | Overwhelming majority |
| Japan | Small (mostly self-access) |
| United Kingdom / Canada | English-speaking regions |
| China | Likely via technical search |
| Netherlands / Brazil | Minor inflow |

---

## Discussion

### ① English Technical Sites Reach the U.S. More Than Expected

Even for a **Japan-based personal technical portal**,  
simply publishing content in English results in  
**the United States becoming the dominant access source**.

The combination of GitHub Pages and English technical documentation  
naturally propagates through search engines.

---

### ② Why Japan Appears Underrepresented

- A Japanese version does exist  
- However, technical searches often prioritize English pages  
- Most Japanese traffic comes from the site owner  

As a result, Japan appears numerically small in the data.

---

### ③ “Complete English Support” Is Reflected in Real Numbers

English site:  
[https://samizo-aitl.github.io/portal/en/](https://samizo-aitl.github.io/portal/en/)

Without this English version,  
the observed **U.S./UK/Canada-centered distribution** and  
**simultaneous overseas real-time access** would not occur.

It is interesting how directly  
**site design decisions map to analytics results**.

---

## Limitations of This Analysis

This article does **not** address:

- Session duration or bounce rate  
- Article-level popularity  
- Reader expertise or job roles  
- Correlation with GitHub stars or forks  

This is intentionally a  
**minimal check of entry distribution and real-time behavior only**.

---

## Conclusion

- Even a personal technical portal becomes international when written in English  
- GitHub Pages and English technical content are highly compatible  
- Real-time analytics are not for bragging, but for **design validation**

Next steps will involve analyzing:

> **Which technical topics are read in which countries**

at a finer level of granularity.

---

This concludes the country-based and real-time access analysis  
of the Samizo-AITL Portal.
