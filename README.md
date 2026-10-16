# AI-in-Education Opinion Mining

> Unsupervised NLP finds four commenter personas in Indonesian YouTube comments.

## Overview

- Solo final exam project for a Text Mining / NLP course, discovering themes in public opinion on AI in education without labels.

## Data / Scope

- 3,518 comments from 13 videos via the YouTube Data API; about 35% mixed Indonesian and English. 3,172 usable after cleaning.

## Workflow

- Removed spam and bots, normalized slang, translated code-mixed text and stemmed words.
- Compared Bag-of-Words, TF-IDF and self-trained Word2Vec with K-Means (k=2 to 10), scored by silhouette.
- Cross-checked clusters with LDA and NMF topic models.

## Results

- Best: Word2Vec with k=4, silhouette 0.075, reported honestly.
- Four personas: critics, general commenters, philosophical reflectors, personal ChatGPT users.
- LDA beat NMF in 5 of 6 configurations; clusters and topics agreed 49.75%.

## Tech Stack

K-Means, Word2Vec, TF-IDF / BoW, LDA / NMF, YouTube Data API

## Repository Structure

```
notebooks/          Notebook: YouTube comment scraping, preprocessing, clustering, topic modelling
requirements.txt    Python dependencies
```

## How to Run

```bash
pip install -r requirements.txt
jupyter notebook notebooks/AI_Pendidikan_Opinion_Mining.ipynb
```
Scraping needs your own YouTube Data API key; set it as an environment variable and never commit it.

## Team

Individual project (Text Mining / NLP course exam).

## Notes

- Collected comments are not redistributed; the notebook shows how to re-collect them.
- Check the notebook for any hard-coded API key before publishing (none should be committed).

## Author

Nadya Angelie Lislie, BINUS University (Computer Science and Statistics). [LinkedIn](https://www.linkedin.com/in/nadya-angelie-lislie/) | [GitHub](https://github.com/Nadya-AngelieLislie)

## Experiment Tracking

`src/experiment_tracking.py` provides an optional MLflow wrapper (`track_run`) for logging parameters, metrics and artifacts; it does nothing when MLflow is not installed. Run `mlflow ui` after logging runs to compare experiments.

## Continuous Integration

GitHub Actions (`.github/workflows/ci.yml`) runs `ruff` and `pytest` repository-health checks on every push; run them locally with `make lint test`.
