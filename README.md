# SQL Injection Detection Model

This repository contains a machine learning model to detect SQL injection attacks based on text inputs. The model is trained using a dataset containing labeled SQL statements, and it predicts whether a given sentence is an SQL injection attempt or not.

## Table of Contents

- [Overview](#overview)
- [Installation](#installation)

## Overview

SQL injection (SQLi) is a common attack method where attackers manipulate SQL queries in order to execute arbitrary code on a database. The goal of this project is to train a machine learning model capable of detecting SQL injection attempts based on a given input sentence.

The model uses a dataset of labeled SQL statements, where each entry is classified as either an SQL injection attempt (labeled as `1`) or a benign input (labeled as `0`).

## Installation

To get started with the model training, follow the steps below:

## Clone the repository:

```bash
git clone https://github.com/MITOViXu/sqli-detection.git
cd sql-injection-detection
```

## Random Forest Algorithm

Note: use these files: sql.pkl and tfidf_vectorizer.pkl

```bash
def sql_detect(query):
    with open('sql.pkl', 'rb') as model_file:
        load_model=pickle.load(model_file)

    with open('tfidf_vectorizer.pkl', 'rb') as vectorize_file:
        load_vectorizer = pickle.load(vectorize_file)

    query_tfidf=load_vectorizer.transform([query])

    predict = load_model.predict(query_tfidf)

    return "SQL Injection Detected" if predict[0]==1 else "Safe"

print(sql_detect(" select * from users where id  =  '1' or @ @1  =  1 union select 1,version  (    )   -- 1'"))
```

## Neural Network Algorithm
