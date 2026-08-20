---
title: "R Forecasting Recipes"
type: code
tags:
  - r
  - forecasting
  - code
created: 2026-08-08
updated: 2026-08-08
---

# R Forecasting Recipes

> [!warning]
> โค้ดเป็น pattern สำหรับทบทวนแนวคิด ไม่ใช่ production pipeline สำเร็จรูป ควรเปลี่ยนชื่อ column/index และตรวจ package versions ก่อนใช้จริง

## Benchmark Models with fable

```r
library(fpp3)

fit <- train_data |>
  model(
    Mean   = MEAN(y),
    Naive  = NAIVE(y),
    SNaive = SNAIVE(y),
    Drift  = RW(y ~ drift())
  )

fc <- fit |> forecast(h = 4)
accuracy(fc, test_data)
```

## ETS and ARIMA

```r
fit <- train_data |>
  model(
    ETS   = ETS(y),
    ARIMA = ARIMA(y)
  )

report(fit)
fc <- forecast(fit, h = 12)
accuracy(fc, test_data)
```

## Rolling-Origin Time-Series CV

```r
cv <- data |>
  stretch_tsibble(.init = 24, .step = 1)

cv_fc <- cv |>
  model(ARIMA = ARIMA(y)) |>
  forecast(h = 1)

accuracy(cv_fc, data)
```

## Dynamic Regression with ARIMA Errors

```r
fit <- train_data |>
  model(
    dyn = ARIMA(y ~ x1 + x2 + x3)
  )

future_x <- new_data(train_data, 8) |>
  mutate(
    x1 = ...,
    x2 = ...,
    x3 = ...
  )

forecast(fit, new_data = future_x)
```

## Dynamic Harmonic Regression

```r
fit <- train_data |>
  model(
    dhr = ARIMA(y ~ fourier(K = 3))
  )
```

เลือก `K` จาก training/CV/AICc และตรวจ residual diagnostics ห้ามเลือกจาก final test set

## Leakage-safe Rolling Features

ถ้าจะ predict `y_t`, rolling target feature ต้องใช้ **อดีตเท่านั้น**

```r
library(slider)

df <- df |>
  arrange(time) |>
  mutate(
    lag1 = lag(y, 1),
    lag2 = lag(y, 2),
    ma4_past = slide_dbl(
      lag(y, 1),
      mean,
      .before = 3,
      .complete = TRUE
    )
  )
```

`ma4_past` ใช้ `y[t-1]` ถึง `y[t-4]` และไม่รวม `y[t]`.

## Related Notes

- [[Benchmark Forecasting Methods]]
- [[Time Series Cross Validation]]
- [[Exponential Smoothing and ETS]]
- [[ARIMA]]
- [[Dynamic Regression ARIMAX]]
- [[Dynamic Harmonic Regression]]
- [[ML Time-Series Feature Engineering]]
