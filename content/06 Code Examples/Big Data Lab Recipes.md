---
title: "Big Data Lab Recipes"
type: code-reference
tags:
  - big-data
  - spark
  - hadoop
  - recipes
created: 2026-08-09
updated: 2026-08-09
---

# Big Data Lab Recipes

> [!warning] Legacy-vs-current note
> Commands from DADS6002 labs are intentionally not copied as a current installation guide. The source labs use Cloudera QuickStart, Python 2.7, Kafka 0.9-era commands, `SQLContext`, and RDD-based ML examples. This file keeps **portable learning patterns** only.

## HDFS CLI pattern

```bash
hadoop fs -mkdir -p /user/example/input
hadoop fs -put local.txt /user/example/input/
hadoop fs -ls /user/example/input
hadoop fs -cat /user/example/input/local.txt
```

## PySpark DataFrame pattern

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName("example").getOrCreate()

df = spark.createDataFrame([
    ("Anna", 25, "CA"),
    ("Jack", 22, "TX"),
], ["name", "age", "state"])

df.filter("age >= 23").groupBy("state").count().show()
```

## RDD word-count learning pattern

```python
text = spark.sparkContext.parallelize(["hello spark", "hello data"])
counts = (text
    .flatMap(lambda line: line.split())
    .map(lambda word: (word, 1))
    .reduceByKey(lambda a, b: a + b))
print(counts.collect())
```

## Text feature pipeline pattern

```python
from pyspark.ml import Pipeline
from pyspark.ml.feature import Tokenizer, HashingTF, IDF
from pyspark.ml.classification import LogisticRegression

tok = Tokenizer(inputCol="text", outputCol="words")
tf = HashingTF(inputCol="words", outputCol="tf")
idf = IDF(inputCol="tf", outputCol="features")
lr = LogisticRegression(featuresCol="features", labelCol="label")
pipe = Pipeline(stages=[tok, tf, idf, lr])
```

## Related Notes

- [[HDFS]]
- [[Apache Spark]]
- [[Spark SQL and DataFrames]]
- [[Spark ML and MLlib]]
- [[Text Analytics]]
