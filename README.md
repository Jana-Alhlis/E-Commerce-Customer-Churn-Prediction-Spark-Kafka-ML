# E-Commerce Customer Churn Prediction

**Big Data Analytics with Apache Spark, Kafka-Based Streaming Simulation, and Machine Learning**

## Overview

Understanding why customers abandon purchases or stop engaging with an online store is essential for improving retention and conversion rates.

This project implements a Big Data analytics pipeline that processes approximately **2.76 million e-commerce events** to analyze user behavior, identify potential churn risks, and generate business insights. The workflow combines distributed processing, simulated event streaming, machine learning, and Power BI reporting in an integrated seven-layer architecture.

## Project Goals

- Analyze large-scale customer interaction data using Apache Spark.
- Simulate streaming event ingestion through a Kafka-inspired producer.
- Transform raw events into customer-level behavioral features.
- Evaluate machine learning models for customer risk classification.
- Investigate conversion performance and abandoned shopping carts.
- Translate analytical results into actionable business insights through Power BI.

## Data Source

The analysis uses the publicly available [RetailRocket E-Commerce Dataset](https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset).

| Dataset Attribute | Details |
|---|---|
| Total events | Approximately 2.76 million |
| Unique users | 1,407,580 |
| Data format | CSV |
| Collection period | May–June 2015 |
| Recorded interactions | Product views, cart additions, transactions |

The dataset provides behavioral event records that can be aggregated to examine customer engagement, product interest, and purchasing activity.

## System Architecture

The pipeline is divided into seven functional layers:

1. **Source Data:** RetailRocket event records.
2. **Ingestion:** Simulated streaming through `MockKafkaProducer`.
3. **Raw Data Storage:** Parquet-based storage.
4. **Processing:** Apache Spark for data transformation, aggregation, and feature engineering.
5. **Processed Data Storage:** `MockMongoDB` for demonstrating document-oriented storage.
6. **Analytics:** Spark MLlib for model training and churn-risk analysis.
7. **Reporting:** CSV exports used to build Power BI dashboards.

This design demonstrates how data moves from raw behavioral events to processed analytical outputs.

## Data Engineering and Feature Extraction

PySpark is used to aggregate user interactions and derive features for behavioral analysis. These include:

- Total interaction and product-view counts.
- Cart additions and completed transactions.
- Number of distinct products viewed.
- Conversion rates and engagement scores.

The pipeline also converts the original CSV data into Parquet format to reduce storage requirements and support efficient analytical processing.

| Storage Format | Reported File Size |
|---|---:|
| Original CSV | Approximately 90 MB |
| Converted Parquet | Approximately 34 MB |
| Size reduction | 61.6% |

## Customer Risk Analysis

Users are categorized into four behavioral groups according to the project's defined rules:

- **High Risk:** Added products to their carts without completing a purchase.
- **Medium Risk:** Viewed multiple products without adding items to their carts.
- **Low Risk:** Completed at least one transaction.
- **Unknown Risk:** Had insufficient activity for the defined classification rules.

These categories support the identification of customer segments that may warrant further investigation or targeted retention efforts.

*Note: These are behavior-based risk segments; they should not automatically be interpreted as verified long-term churn labels.*

## Machine Learning Experiments

Three classification algorithms were evaluated using Spark MLlib:

- Logistic Regression
- Decision Tree
- Random Forest

### Reported Model Performance

The Random Forest model achieved the strongest reported results, with approximately **99% accuracy and a 0.99 F1-score**.

View count and engagement score were reported as influential features in the analysis.

These results should be interpreted in the context of the target-label definition, class distribution, and evaluation methodology. High scores alone do not establish that the model can accurately predict future customer churn.

## Key Results and Business Insights

| Indicator | Reported Result |
|---|---:|
| Behavioral events analyzed | 2.76 million |
| Unique users | Approximately 1.4 million |
| High-risk users identified | 27,000 |
| View-to-cart conversion rate | 2.69% |
| Cart abandonment rate | 69% |
| Storage reduction after conversion to Parquet | 61.6% |
| Total pipeline execution time | 12 min 34 sec |
| Projected campaign ROI | 1,769% |

The analysis highlights potential conversion bottlenecks and customer segments that could be considered for retention initiatives.

The projected ROI represents a hypothetical business scenario based on the report's assumptions, not a measured outcome from a real marketing campaign. Similarly, the reported pipeline runtime depends on the execution environment.

## Power BI Reporting

The processed outputs include seven CSV files designed to support interactive Power BI reporting.

The planned analytical views cover:

- Customer activity and behavioral trends.
- The product-view-to-purchase conversion funnel.
- Customer risk distribution.
- Shopping cart abandonment.
- Model performance comparison.
- Potential revenue recovery and projected business impact.
- Risk-based retention opportunities.

These visualizations connect technical model outputs with business-oriented decision support.

## Technology Stack

| Category | Tools |
|---|---|
| Programming | Python |
| Distributed Processing | Apache Spark 3.5.1, PySpark |
| Data Storage | Parquet, MockMongoDB |
| Streaming Simulation | MockKafkaProducer |
| Machine Learning | Spark MLlib |
| Data Analysis | Pandas, NumPy |
| Visualization | Power BI, Matplotlib |
| Development Environment | Kaggle Notebooks |

## Project Resources

- **Implementation:** [Open the Google Colab Notebook](https://colab.research.google.com/drive/1dQEPU3gUa3Bf7npv3mxe2r1Bx8W2z2k6?usp=sharing)
- **Dataset:** [RetailRocket E-Commerce Dataset on Kaggle](https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset)
- **Project Report:** `Customer_Churn_Project_Report.pdf`

## Limitations and Next Steps

The current implementation is an academic prototype. Its streaming and document-storage components are simulations rather than production deployments using live Kafka brokers and MongoDB infrastructure.

Potential extensions include:

- Integrating a real-time event streaming platform.
- Using a production database for processed customer data.
- Defining and validating churn labels against future customer activity.
- Evaluating generalization on an independent test set.
- Testing retention strategies through controlled experiments.
- Deploying the pipeline in a distributed cloud environment.

## Academic Information

- **Course:** DS4511 – Big Data
- **Department:** Data Science
- **College:** College of Computing
- **University:** Umm Al-Qura University
