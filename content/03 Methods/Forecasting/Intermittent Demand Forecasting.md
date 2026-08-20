---
title: "Intermittent Demand Forecasting"
aliases:
  - Intermittent Demand
  - Croston's Method
  - ADI Demand Classification
topic_number: 53
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[S1-StatFC_260725_130111]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Intermittent Demand Forecasting

> [!abstract] Summary
> Intermittent demandมีช่วง zeroจำนวนมากสลับ nonzero demand; Croston's methodแยก forecastขนาด nonzero demandกับ intervalระหว่าง demands แล้วรวมเป็น rate.

## Why this concept matters

Standard continuous-demand methodsอาจให้ inventory decisionsแย่เมื่อ demand sparse/lumpy; pattern classificationช่วยเลือกวิธีที่เหมาะ.

## Core Idea

- ADI = average intervalระหว่าง positive demands.
- CV²ของ positive demand sizesวัด variabilityของ nonzero quantities.
- Croston smooths demand sizeและintervalแยกกัน.
- Original Crostonมี bias; มี variantsเช่น SBA/TSBที่แก้บางข้อ.
- Classification thresholdsเป็น heuristicจาก literature ไม่ใช่ physical law.

## Mathematical Formulation / Technical Detail

ให้ positive demand sizes $z_i$ และ intervals $p_i$.

Croston updates smoothed size $\hat z$ และ interval $\hat p$, แล้ว forecast demand rateประมาณ

$$
\hat y=\frac{\hat z}{\hat p}.
$$

ADI:

$$
ADI=\frac1{n_+}\sum_{i=1}^{n_+}p_i.
$$

## Worked / Practical Example

Spare partเช่น transmissionอาจมี demand 0 หลายเดือนแล้วเกิด quantityใหญ่เป็นครั้งคราว. Mean demandอย่างเดียวไม่บอก timing; Crostonแยก event sizeกับwaiting interval.

## Assumptions and Interpretation

- Zerosต้องหมายถึง genuine zero demand ไม่ใช่ stockout/censoring.
- Lectureใช้ Syntetos–Boylan-style thresholds ADI≈1.32 และ CV²≈0.49 เพื่อแบ่ง smooth/intermittent/erratic/lumpy; treat as classification guideline.

## When to use

- spare parts.
- slow-moving inventory.
- low-count demand series.

## When not to use / Limitations

- ถ้า zerosเกิดเพราะไม่มี stock ข้อมูลเป็น censored demandและต้องแก้ก่อน.
- large regular countsไม่จำเป็นต้อง Croston.

## Common Mistakes

- คิดว่า zero sales=zero demandเมื่อ stockout.
- ใช้ threshold 1.32/0.49 เป็น universal rule.
- ใช้ original Crostonโดยไม่รู้เรื่อง bias/obsolescence.

## Cross-check / Correction

> [!warning] Verification note
> Threshold ADI=1.32 และ CV²=0.49 ที่ใช้แบ่ง demand classesควรเก็บเป็น literature-derived heuristic; classificationจริงควรดู data/business context และไม่ควรใช้แทน model validation.

## Quick Review

- **Concept:** Intermittent demandมีช่วง zeroจำนวนมากสลับ nonzero demand; Croston's methodแยก forecastขนาด nonzero demandกับ intervalระหว่าง demands แล้วรวมเป็น rate.
- **สิ่งที่ต้องจำ:** ADI = average intervalระหว่าง positive demands.
- **การใช้งาน:** spare parts.
- **ข้อควรระวัง:** คิดว่า zero sales=zero demandเมื่อ stockout.

## Related Notes

- [[Probabilistic Forecasting]]
- [[Forecast Accuracy Metrics]]
- [[ML Time-Series Feature Engineering]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[S1-StatFC_260725_130111]] | Count data / intermittent demand / Croston section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `S1-StatFC_260725_130111.pdf` — Count data / intermittent demand / Croston section

## External References

- [Croston, J.D. (1972), Forecasting and Stock Control for Intermittent Demands, Operational Research Quarterly 23(3), 289–303.](https://doi.org/10.1057/jors.1972.50)

## Verification Status

**Moderate to high confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
