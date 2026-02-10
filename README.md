
# Detecting mental-health–related subreddit signals from Reddit post text (Reddit mental-disorder dataset)

## Data source(s)
Kaggle dataset (mental disorder Reddit posts) — https://www.kaggle.com/code/erenakbulut/mental-disorder-reddit-ds-polars-vs-pandas/input

## Overview & Motivation
This project applies the data-project lifecycle to a large (~700k rows) Reddit posts dataset focused on mental-health–related subreddits. The dataset includes post titles, text, timestamps, NSFW flags, and subreddit names.

The project will design a normalized relational schema, ingest and clean the raw data using Python, explore using SQL, perform statistical and text-based analysis with Python, and apply a small classification model using subreddit labels. Ethical considerations will be significant because the content is sensitive (mental health, personal disclosures, misuse or misclassification).

## ER Diagram
```
        +--------------------+
        |    subreddits      |
        |--------------------|
        | subreddit_id  PK   |
        | name (unique)      |
        | description         |
        | created_at          |
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
        | subreddit_id   FK ---> subreddits.subreddit_id
        | text_length         |
        | cleaned_text        |
        | source_file         |
        +----------^-----------+
                   |
                   | many-to-1 (ETL logs)
                   |
        +----------+-----------+
        |    ingestion_logs    |
        |----------------------|
        | log_id        PK     |
        | source_file          |
        | ingest_time          |
        | num_rows             |
        | notes                |
        +----------------------+
```
