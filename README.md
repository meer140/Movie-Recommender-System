# Movie Recommendation System

A content-based movie recommender implemented as a Jupyter Notebook using the TMDB 5000 dataset (movies + credits). This repository demonstrates how to extract and combine movie metadata (genres, keywords, top cast, director, and overview) to build a lightweight, explainable recommendation engine.

---

## Table of Contents

- [Why this project](#why-this-project)
- [Features](#features)
- [Dataset](#dataset)
- [Prerequisites](#prerequisites)
- [Quickstart](#quickstart)
- [Notebook overview](#notebook-overview)
- [How it works (high level)]
- [Repository structure](#repository-structure)
- [Extending the project](#extending-the-project)
- [License & attribution](#license--attribution)

---

## Why this project

This repository is an educational implementation of a content-based movie recommender. It is useful for learning the following concepts:

- Basic data cleaning and JSON parsing in pandas
- Feature engineering from structured metadata
- Text vectorization (Count/Tf-idf) and similarity computation
- Building an explainable recommender that uses metadata signals (genres, cast, director, keywords)

It is intentionally lightweight and suitable for small-to-medium datasets and experimentation.

## Features

- Parse and merge TMDB movies and credits CSVs
- Extract genres, keywords, top cast members, and director from JSON-like columns
- Build a combined "metadata" text field per movie
- Vectorize metadata and compute cosine similarity
- Lookup by movie title and return top-N similar movies

## Dataset

This project expects the TMDB 5000 Movie Dataset CSVs in the notebook working directory:

- `tmdb_5000_movies.csv`
- `tmdb_5000_credits.csv`

These files are commonly available from public data sources such as Kaggle (search for "TMDB 5000 Movie Dataset"). Place both files in the same directory as the notebook before running the notebook.

## Prerequisites

- Python 3.8+ (recommended)
- Jupyter Notebook or JupyterLab

Typical Python packages used in the notebook (install into a virtual environment):

pip install -r requirements.txt

If you don't have a requirements file, you can install the essentials directly:

pip install pandas numpy scikit-learn jupyter

(If you add a requirements.txt to the repo, update this section to reference it.)

## Quickstart

1. Clone the repository:

   git clone https://github.com/meer140/Movie-Recommendation-System.git
   cd Movie-Recommendation-System

2. Make sure the dataset CSVs (`tmdb_5000_movies.csv` and `tmdb_5000_credits.csv`) are in the repository root (or the notebook working directory).

3. Start Jupyter and open the notebook:

   jupyter notebook
   
   Open `Untitled.ipynb` and run the cells in order.

4. Explore the example usage cells. The notebook exposes the recommendation lookup (for example, `get_recommendations(title, top_n)`) which returns the most similar movies for a given title.

## Notebook overview

The included Jupyter Notebook (`Untitled.ipynb`) contains the following sections:

- Data loading and inspection
- Parsing JSON-like columns (`genres`, `keywords`, `cast`, `crew`) and extracting desired fields
- Cleaning and transforming metadata
- Combining features into a single metadata string
- Vectorization (CountVectorizer or TfidfVectorizer)
- Cosine similarity computation
- Example lookups and evaluation/demonstration cells

If you rename the notebook, please update references in this README accordingly.

## How it works (high level)

1. Load the CSV files and merge the credits into the movies dataframe.
2. Select and parse relevant columns: `movie_id`, `title`, `overview`, `genres`, `keywords`, `cast`, `crew`.
3. Extract structured fields from JSON-like strings (e.g., genre names, top 3 cast members, director).
4. Preprocess text:
   - Lowercase and normalize tokens
   - Optionally remove stop words and punctuation
   - Flatten lists into space-separated tokens
5. Concatenate fields into a single metadata string for each movie (e.g., `genres keywords cast director overview`).
6. Vectorize the metadata using `CountVectorizer` or `TfidfVectorizer`.
7. Compute cosine similarity between movie vectors.
8. Given a movie title, retrieve its index and return the top-N most similar movies by similarity score.

## Repository structure

- Untitled.ipynb — primary Jupyter Notebook with the full implementation and examples
- README.md — this file

(You may add `requirements.txt`, example scripts, or a small web app (Flask/Streamlit) to make recommendations accessible outside the notebook.)

## Extending the project

Ideas to make this repository production-ready or more feature-rich:

- Add a `requirements.txt` and a reproducible environment (poetry / pipenv)
- Refactor notebook code into Python modules (e.g., `recommender/` package) and provide CLI or API endpoints
- Persist precomputed vectors and similarity matrices for faster lookups
- Add tests and CI for preprocessing and recommendation functions
- Add evaluation (e.g., human-annotated similarity or proxy metrics)
- Build a simple web UI using Streamlit or Flask to demo recommendations interactively

## License & attribution

This repository is provided for educational purposes. If you add a license, include it in the repo root (e.g., `LICENSE`).

Dataset attribution: The recommendation pipeline uses the TMDB 5000 Movie Dataset (movies + credits). Please follow the dataset provider's terms (e.g., Kaggle / TMDB) when redistributing or publishing derived data.

---

If you'd like, I can also:

- Add a `requirements.txt` with the exact packages used in the notebook
- Rename and clean the notebook contents and refactor code into a script/module
- Add a small Streamlit app that exposes the recommendation function

