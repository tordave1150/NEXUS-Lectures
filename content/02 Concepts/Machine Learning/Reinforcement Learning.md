---
title: "Reinforcement Learning"
aliases:
  - RL
topic_number: 63
domain:
  - Data Science
  - Machine Learning
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - reinforcement-learning
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Reinforcement Learning

> [!abstract] Summary
> Reinforcement Learning (RL) ให้ agent เรียน policy จาก interaction กับ environment โดยเลือก actions เพื่อ maximize cumulative reward ไม่ใช่เรียนจาก fixed labeled pairs แบบ supervised learning.

## Why this concept matters

ใช้เมื่อ decision มีลำดับเวลาและ action ปัจจุบันเปลี่ยน state/ผลตอบแทนในอนาคต เช่น robotics, control, recommendation policy หรือ resource allocation.

## Core Idea

- องค์ประกอบหลัก: state \(s\), action \(a\), reward \(r\), policy \(\pi(a|s)\).
- เป้าหมายคือ maximize expected discounted return ไม่ใช่ immediate reward อย่างเดียว.
- มี exploration–exploitation tradeoff: ต้องทดลอง action เพื่อเรียน แต่การทดลองมี cost/risk.

## Mathematical Formulation / Technical Detail

\[
G_t=\sum_{k=0}^{\infty}\gamma^k r_{t+k+1},\qquad
\pi^*=\arg\max_\pi \mathbb E_\pi[G_t],
\]

โดย \(0\le\gamma\le1\) เป็น discount factor.

## Worked / Practical Example

Inventory replenishment แบบ sequential: state = stock + demand context, action = order quantity, reward = margin − holding − shortage cost. RL เหมาะเมื่อ action วันนี้กระทบ state วันถัดไป.

## When to use

- Sequential decision making ที่มี feedback loop.
- Simulation/control problems ที่ reward นิยามได้.

## Limitations / Assumptions

- ต้องมี environment/simulator หรือ safe interaction strategy.
- Reward misspecification ทำให้ agent optimize สิ่งผิด.
- Offline RL มี confounding/support issues.

## Common Mistakes

- เรียก contextual supervised prediction ว่า RL ทั้งที่ไม่มี action-feedback.
- ออกแบบ reward ที่ไม่สะท้อน business objective.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** Reinforcement Learning (RL) ให้ agent เรียน policy จาก interaction กับ environment โดยเลือก actions เพื่อ maximize cumulative reward ไม่ใช่เรียนจาก fixed labeled pairs แบบ supervised learning.
- **จำให้ได้:** องค์ประกอบหลัก: state \(s\), action \(a\), reward \(r\), policy \(\pi(a|s)\).
- **ใช้งาน:** Sequential decision making ที่มี feedback loop.
- **ระวัง:** เรียก contextual supervised prediction ว่า RL ทั้งที่ไม่มี action-feedback.

## Related Notes

- [[Machine Learning Fundamentals]]
- [[Supervised Learning]]
- [[Machine Learning Workflow and MLOps]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 1 - Introduction]] | Slide 12 | RL states/actions/rewards/policy intuition |

## External References

- Stanford CS234: https://web.stanford.edu/class/cs234/

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
