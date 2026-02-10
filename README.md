# Detecting Mental-Health–Related Subreddit Signals from Reddit Post Text

## Data Source
Kaggle dataset: *Mental Disorder Reddit Posts*  
https://www.kaggle.com/code/erenakbulut/mental-disorder-reddit-ds-polars-vs-pandas/input

---

## Overview & Motivation
This project applies the full data-project lifecycle to a large-scale (~700k rows) Reddit posts dataset drawn from mental-health–related subreddits. The dataset includes post titles, post text, timestamps, NSFW flags, and subreddit metadata.

The goal is not to diagnose mental health conditions, but to explore how language patterns differ across mental-health–related communities and how subreddit labels can function as weak, community-level signals for text analysis.

The project emphasizes:
- Robust data modeling and ingestion
- SQL-based exploration over normalized data
- Text preprocessing and statistical analysis in Python
- A small, interpretable text classification model
- Ethical considerations when working with sensitive, user-generated mental health content

---

## Project Scope
This repository demonstrates skills in:
- Relational database design and normalization
- ETL pipelines and data quality logging
- SQL analytics on text-heavy datasets
- NLP preprocessing and feature engineering
- Ethical evaluation of modeling choices and limitations

---

## Entity–Relationship (ER) Diagram

    +--------------------+
    |     subreddits     |
    |--------------------|
    | subreddit_id  PK   |
    | name (unique)      |
    | description        |
    | created_at         |
    +----------^---------+
               |
               | 1-to-many
               |
    +----------+-----------+
    |        posts         |
    |----------------------|
    | post_id        PK    |
    | title               |
    | selftext            |
    | created_utc (ts)    |
    | over_18 (bool)      |
    | subreddit_id   FK   |
    | text_length         |
    | cleaned_text        |
    | source_file         |
    +----------^-----------+
               |
               | many-to-1
               |
    +----------+-----------+
    |   ingestion_logs    |
    |----------------------|
    | log_id        PK     |
    | source_file          |
    | ingest_time          |
    | num_rows             |
    | notes                |
    +----------------------+

```
