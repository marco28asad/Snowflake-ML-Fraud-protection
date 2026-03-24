# Snowflake-ML-Fraud-protection

Real-Time Fraud Detection with Snowflake ML
A complete end-to-end machine learning pipeline for real-time fraud detection, built on Snowflake using Cortex Code, XGBoost, and Snowpark Container Services (SPCS).
 Project Overview
This project demonstrates how to go from raw idea to a production-grade REST API for fraud detection — covering data generation, EDA, model training, deployment, and live inference benchmarking.
 What's Built
ComponentDetailsDataset10,000 synthetic financial transactions (~0.5% fraud rate)ModelXGBoost classifier with ROC-AUC of 0.97DeploymentSnowpark Container Services (SPCS)APILive REST endpoint with ~60ms median latency
 Pipeline Steps

Synthetic Data Generation — Realistic fraud patterns including stealth fraud and noisy legitimate transactions
Exploratory Data Analysis — Feature correlation analysis, amount distributions, location/merchant patterns
Feature Engineering — 7 engineered features including SUSPICIOUS_SCORE, IS_UNUSUAL_LOCATION, LOG_AMOUNT
Model Training — XGBoost with scale_pos_weight=199 to handle class imbalance; 5-fold cross-validation Mean AUC: 0.93
Model Registry — Logged to Snowflake Model Registry with PREDICT and PREDICT_PROBA endpoints
SPCS Deployment — Containerized inference service running as a live REST API
Latency Benchmarking — 1,000 requests profiled; 86% complete in 50–100ms

 Model Performance
ROC-AUC:        0.9723
Fraud Recall:   94% (47/50 fraud cases caught)
Median Latency: ~60ms per REST request
Throughput:     ~15.7 req/s (single thread)
 Top Features by Importance
SUSPICIOUS_SCORE         0.2341
IS_UNUSUAL_LOCATION      0.1892
IS_SUSPICIOUS_MERCHANT   0.1456
LOG_AMOUNT               0.1203
LOC_MERCH_SUSPICIOUS     0.1098
IS_NIGHT                 0.0812
HOUR                     0.0698
 Tech Stack

Snowflake — Data warehouse, Model Registry, SPCS
Cortex Code — AI-native coding agent (CLI + Snowsight)
XGBoost — Gradient boosted classifier
Snowpark — Python SDK for Snowflake
REST API — Real-time online inference endpoint

 Project Structure
eda_step1_load.py               # Data loading and basic stats
eda_step2_amount.py             # Amount distribution analysis
eda_step3_location_merchant.py  # Location and merchant patterns
eda_step4_time.py               # Time-of-day analysis
eda_step5_features.py           # Feature recommendations
train_fraud_model.py            # XGBoost training script
benchmark_inference.py          # REST API latency profiling
plots/                          # EDA visualizations
 Based On
Snowflake ML Quickstart — Real-Time Fraud Detection with Agentic ML
