---
title: "Hierarchical and Grouped Forecasting"
aliases:
  - Hierarchical Forecasting
  - Grouped Time Series
  - Forecast Reconciliation
topic_number: 52
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

# Hierarchical and Grouped Forecasting

> [!abstract] Summary
> Hierarchical/grouped forecastingจัดการหลาย seriesที่มี aggregation constraints และทำ forecast reconciliationเพื่อให้ forecastsทุกระดับรวมกันได้อย่าง coherent.

## Why this concept matters

ธุรกิจต้องใช้ forecastsพร้อมกันระดับ National→Region→DC→Store หรือ Family→Category→SKU; independent forecastsอาจไม่ add up.

## Core Idea

- Bottom-up forecast bottom seriesก่อนแล้ว sumขึ้น.
- Top-down forecast aggregateก่อนแล้ว allocateลง.
- Middle-outเริ่มจากระดับกลาง.
- Modern reconciliationเริ่มจาก base forecastsทุก seriesแล้ว projectให้ coherent เช่น MinT.
- Grouped structureต่างจาก strict hierarchyเพราะ attributesอาจ crossed.

## Mathematical Formulation / Technical Detail

Aggregation:

$$
y_t=S b_t
$$

โดย $b_t$ คือ bottom-level vector และ $S$ summing matrix.

Reconciled point forecastทั่วไป:

$$
\tilde y_h=S G\hat y_h
$$

สำหรับ reconciliation matrix $G$.

## Worked / Practical Example

National shipments = North+Central+South และแต่ละ region=sum DCs. ถ้า independently forecast National=1000 แต่ regionsรวม=1060 forecastsไม่ coherent; reconciliationปรับให้ constraintsตรงกัน.

## Assumptions and Interpretation

- Accuracyควร evaluateทุกระดับที่ businessใช้.
- Bottom-level noiseสูงอาจทำให้ pure bottom-upไม่ดีที่สุด.

## When to use

- multi-level sales/demand.
- geographic/product hierarchies.
- planningที่ต้อง totalsสอดคล้องกัน.

## When not to use / Limitations

- ถ้า aggregation definitionsเปลี่ยนตลอดต้อง version hierarchy.
- reconciliationไม่แก้ bad base modelsโดยตัวมันเอง.

## Common Mistakes

- สร้าง forecastsทุก levelแยกกันแล้วปล่อยไม่ add up.
- ประเมินเฉพาะ totalแต่ operationใช้ SKU.
- สับสน groupedกับ nested hierarchy.

## Quick Review

- **Concept:** Hierarchical/grouped forecastingจัดการหลาย seriesที่มี aggregation constraints และทำ forecast reconciliationเพื่อให้ forecastsทุกระดับรวมกันได้อย่าง coherent.
- **สิ่งที่ต้องจำ:** Bottom-up forecast bottom seriesก่อนแล้ว sumขึ้น.
- **การใช้งาน:** multi-level sales/demand.
- **ข้อควรระวัง:** สร้าง forecastsทุก levelแยกกันแล้วปล่อยไม่ add up.

## Related Notes

- [[Probabilistic Forecasting]]
- [[Forecast Accuracy Metrics]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[S1-StatFC_260725_130111]] | Forecasting hierarchical and grouped time series section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `S1-StatFC_260725_130111.pdf` — Forecasting hierarchical and grouped time series section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
