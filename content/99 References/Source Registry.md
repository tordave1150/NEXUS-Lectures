---
title: "Source Registry"
type: moc
tags:
  - source
  - registry
created: 2026-08-08
updated: 2026-08-15
---

# Source Registry

> [!info]
> Source notes: **50** lecture/lab PDFs across the current vault batches. Original PDFs remain in Google Drive; this vault stores source metadata, topic mapping, corrections and traceability rather than duplicating the PDFs.

| Source Note | Document / Source Note | Reliability | Canonical Topics Referencing Source |
|---|---|---|---:|
| [[01-TSoverview]] | Introduction to Time Series Forecasting | Moderate → High after cross-check | 3 |
| [[02-TSDecomposition]] | TS Decomposition & Forecasting | Moderate → High after cross-check | 3 |
| [[02-probabilistic-forecast]] | Probabilistic Forecast: Why and How | Moderate → High after cross-check | 4 |
| [[03-FCToolbox]] | Forecaster's Toolbox | Moderate → High after cross-check | 4 |
| [[04-ETS]] | From Exponential Smoothing Methods to ETS Models | Moderate → High after cross-check | 2 |
| [[05-ARIMA_SARIMA]] | ARIMA & SARIMA | Moderate → High after cross-check | 4 |
| [[06-TSRegression_260620_180251]] | Time Series Regression | Moderate → High after cross-check | 4 |
| [[07-Regression-Categorical_260629_205921]] | Regression with Dummy Variables and Categorical Features | Moderate → High after cross-check | 3 |
| [[08-DynamicRegression_260627_151638]] | Dynamic Regression | Moderate → High after cross-check | 3 |
| [[09-ComplexSeasonality_DynamicHarmonicReg_260711_130747]] | Complex Seasonality & Dynamic Harmonic Regression | Moderate → High after cross-check | 4 |
| [[10-NonlinearRegression_260711_160649 (1)]] | Nonlinear Regression | Moderate → High after cross-check | 5 |
| [[11-RegularizedRegression_260718_091112]] | Regularized Regression | Moderate → High after cross-check | 16 |
| [[12-NN_260718_091137]] | Neural Networks / Machine Learning | Moderate → High after cross-check | 5 |
| [[13-probabilistic-forecast_260725_090945]] | Probabilistic Forecast | Moderate → High after cross-check | 3 |
| [[S1-StatFC_260725_130111]] | Statistical Forecasting Models — Selected Topics | Moderate → High after cross-check | 3 |
| [[S2-ML_260725_130143]] | Machine Learning — Selected Topics | Moderate → High after cross-check | 7 |
| [[DADS6003 Week 1 - Introduction]] | DADS6003_week1_intro_260301_153807.pdf | Moderate → High after cross-check | 5 |
| [[DADS6003 Week 10 - Neural Network]] | DADS6003_week10_nn_260424_200018.pdf | Moderate → High after cross-check | 5 |
| [[DADS6003 Week 2 - Simple Linear Regression]] | DADS6003_week2_regression_260117_105205.pdf | Moderate → High after cross-check | 3 |
| [[DADS6003 Week 3 - Multiple Linear Regression]] | DADS6003_week3_MLR_260301_155054.pdf | Moderate → High after cross-check | 6 |
| [[DADS6003 Week 4 - Naive Bayes]] | DADS6003_week7_nb_260516_152015.pdf | Moderate → High after cross-check | 2 |
| [[DADS6003 Week 5 - Logistic Regression]] | DADS6003_week5_logistic_reg_260301_155827.pdf | Moderate → High after cross-check | 1 |
| [[DADS6003 Week 6 - Regularization]] | DADS6003_week6_regularization_v2_260208_114444.pdf | Moderate → High after cross-check | 6 |
| [[DADS6003 Week 7 - Model Training and Evaluation]] | DADS6003_week7_model_evaluation_260301_153251.pdf | Moderate → High after cross-check | 4 |
| [[DADS6003 Week 9 - K-Nearest Neighbors]] | DADS6003_week09_knn_260516_155501.pdf | Moderate → High after cross-check | 4 |
| [[DADS6003 Week 9-2 - Decision Trees]] | DADS6003_week9-2_tree_260516_162056.pdf | Moderate → High after cross-check | 7 |

## Reliability Policy

- **Lecture files:** initial reliability = Moderate; cross-check important definitions, formulas, assumptions, arithmetic, thresholds and implementation claims.
- **External verification:** prefer official technical documentation, original papers, recognized textbooks and authoritative university course material.
- **Correction policy:** preserve the original claim in Source Note when useful, but canonical note uses corrected synthesis and explains the discrepancy.
- **Uncertain claims:** label explicitly instead of inventing certainty.

## DADS6003 Batch Notes

- 10 PDFs currently available: Intro, Simple Regression, Multiple Regression, Naive Bayes, Logistic Regression, Regularization, Model Evaluation, KNN, Decision Trees and Neural Network.
- Week 1 course outline mentions SVM, clustering, PCA/AutoEncoder and association rules, but detailed PDFs for those topics are not present in this folder; no detailed canonical notes were fabricated from outline-only mentions.

## DADS6002 / CI7301 Big Data Analytics

| Source Note | PDF | Type | Reliability |
|---|---|---|---|
| [[BigData 1 - Hadoop]] | `BigData 1 (Hadoop).pdf` | lecture | Moderate (course lecture; architecture concepts useful, version-sensitive details require current-doc verification) |
| [[BigData 1 Lab - Hadoop]] | `BigData 1 Lab.pdf` | lab | Moderate for learning workflow; Legacy environment (Cloudera QuickStart / historical Hadoop Streaming commands) |
| [[BigData 2 - Hive]] | `BigData 2 (Hive).pdf` | lecture | Moderate; core Hive concepts useful, several CLI/engine/index details are version-sensitive |
| [[BigData 2 Lab - Hive]] | `BigData 2 Lab Handout.pdf` | lab | Moderate for concepts; commands reflect a legacy Cloudera/Hive environment |
| [[BigData 3 - HBase]] | `BigData 3 (Hbase).pdf` | lecture | Moderate; HBase data model is useful, architecture/coordination details can vary by release |
| [[BigData 3 Lab - HBase]] | `BigData 3 Lab.pdf` | lab | Moderate for shell concepts; commands should be verified against the installed HBase release |
| [[BigData 4 - Data Ingestion]] | `BigData 4 (Data Ingestion).pdf` | lecture | Moderate; conceptual ingestion patterns useful, Sqoop/Flume/Kafka sections include legacy deployment details |
| [[BigData 4 Lab - Data Ingestion]] | `BigData 4 Lab.pdf` | lab | Legacy lab environment; Kafka 0.9.0.1, ZooKeeper-based commands and old Sqoop/Flume setup must not be treated as current setup guidance |
| [[BigData 5 - Spark]] | `BigData 5 (Spark).pdf` | lecture | Moderate; Spark concepts are foundational, but API examples are RDD-centric and some statements are historical/simplified |
| [[BigData 5 Lab - Spark]] | `BigData 5 lab Handout.pdf` | lab | Moderate for RDD learning; code reflects older PySpark style |
| [[BigData 6 - Spark SQL]] | `BigData 6 (Spark SQL).pdf` | lecture | Moderate; DataFrame concepts are useful, but SQLContext/registerAsTable examples are legacy-style APIs |
| [[BigData 6 Lab - Spark SQL]] | `BigData 6 Lab.pdf` | lab | Moderate for concepts; code uses legacy sqlContext/registerAsTable style |
| [[BigData 7 - Machine Learning with Spark]] | `BigData 7 (Machine Learning)-1.pdf` | lecture | Moderate; RDD-based pyspark.mllib examples are legacy-oriented, but distributed-ML concepts are valuable |
| [[BigData 7 Lab - Machine Learning with Spark]] | `BigData 7 Lab.pdf` | lab | Legacy lab: Python 2.7 and RDD-based pyspark.mllib APIs; preserve only as historical practice, not current setup recommendation |
| [[BigData 8 - Text Analytics]] | `BigData 8 (Text Analytics).pdf` | lecture | Moderate; classical text analytics concepts are useful, code/API details should be release-checked |
| [[BigData 9 - Graph Analytics]] | `BigData 9 (GraphAnalytics)-1.pdf` | lecture | Moderate; graph concepts are strong, GraphX/GraphFrames APIs are version-sensitive |


## Statistics / Statistical Inference

| Source Note | PDF | Type | Reliability |
|---|---|---|---|
| [[1Probability_mod]] | `1Probability_mod.pdf` | lecture | Moderate → High after review; foundational probability/sampling content |
| [[2ConfidenceInterval_mod]] | `2ConfidenceInterval_mod.pdf` | lecture | Moderate → High after review; CI formulas and interpretation |
| [[3Jackknife_Bootstrap]] | `3Jackknife_Bootstrap.pdf` | lecture | Moderate → High after review; classical resampling with original references |
| [[4TestHypo]] | `4TestHypo.pdf` | lecture | Moderate → High after review; several directional hypothesis examples require canonical correction |
| [[5PermutationTest]] | `5PermutationTest.pdf` | lecture | Moderate → High after review; exchangeability/permutation-scheme caveats added |
| [[6ChiSquare_2_68_260328_154515]] | `6ChiSquare_2_68_260328_154515.pdf` | lecture | Moderate → High after review; expected-count/binning heuristics flagged |
| [[7ANOVA_2_68_260425_131156]] | `7ANOVA_2_68_260425_131156.pdf` | lecture | Moderate → High after review; assumptions framed through ANOVA error model |
| [[8Correlation-Regression1_2_68_260502_155920]] | `8Correlation-Regression1_2_68_260502_155920.pdf` | lecture | Moderate → High after review; correlation thresholds and R notation corrected/contextualized |
