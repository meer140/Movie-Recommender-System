# Movie Recommendation System

A content-based movie recommender system that leverages metadata similarity to suggest films based on genres, cast, keywords, and plot descriptions. Built with Python and Jupyter Notebook using the TMDB 5000 Movie Dataset, with an interactive Streamlit web interface.

## Overview

This project demonstrates practical machine learning and data engineering concepts through an explainable recommendation engine. It processes 5,000 movies from the TMDB dataset, extracts meaningful features, and computes similarity scores to provide personalized movie recommendations without relying on user history.

## Features

- **Content-Based Filtering**: Recommendations based on genres, cast, crew, keywords, and plot overview
- **Feature Engineering**: Intelligent parsing and extraction from JSON-structured metadata
- **Text Vectorization**: TF-IDF and cosine similarity computation for robust similarity matching
- **Interactive UI**: Streamlit web application for easy movie exploration
- **Scalable Design**: Precomputed similarity matrices for fast lookups

## Technology Stack

- **Language**: Python 3.8+, Jupyter Notebook
- **Libraries**: 
  - `pandas` - Data manipulation and analysis
  - `scikit-learn` - Text vectorization and similarity computation
  - `streamlit` - Interactive web interface
  - `numpy` - Numerical operations
  - `requests` - API integration for movie posters

## Dataset

This project uses the **TMDB 5000 Movie Dataset**, which includes:

- `tmdb_5000_movies.csv` - Movie metadata (genres, keywords, budget, revenue, ratings, etc.)
- `tmdb_5000_credits.csv` - Cast and crew information

**Source**: Available on [Kaggle](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)

### Data License

The TMDB dataset is provided by The Movie Database (TMDB) and is subject to their terms of use. Please review the [TMDB API Terms of Service](https://www.themoviedb.org/settings/api) before using this data.

## Project Structure

```
Movie-Recommendation-System/
├── README.md                    # This file
├── Untitled.ipynb              # Core recommendation engine (Jupyter Notebook)
├── app.py                      # Streamlit web application
├── movies.pkl                  # Preprocessed movies dataframe (generated)
├── similarity.pkl              # Precomputed similarity matrix (generated)
└── tmdb_5000_*.csv            # Dataset files (required - not in repo)
```


## Quick Start

### Prerequisites

- Python 3.8 or higher
- pip package manager
- TMDB API Key (optional, for poster display in the web app)

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/meer140/Movie-Recommendation-System.git
   cd Movie-Recommendation-System
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
   
   Or manually install:
   ```bash
   pip install pandas numpy scikit-learn jupyter streamlit requests
   ```

3. **Download the dataset**:
   - Visit [Kaggle TMDB Dataset](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)
   - Download `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv`
   - Place both files in the repository root directory

### Running the Jupyter Notebook

```bash
jupyter notebook Untitled.ipynb
```

Execute cells in order:
1. Data loading and merging
2. JSON parsing (genres, keywords, cast, crew)
3. Feature preprocessing
4. Vectorization (CountVectorizer or TfidfVectorizer)
5. Similarity matrix computation
6. Test recommendations using `get_recommendations(title, top_n)`

### Running the Streamlit App

First, ensure the notebook has been run to generate `movies.pkl` and `similarity.pkl`.

```bash
streamlit run app.py
```

The app will open at `http://localhost:8501` where you can:
1. Select a movie from the dropdown
2. Click "Recommend" to see 5 similar movies with posters

**Note**: Add your TMDB API key to `app.py` line 17 for poster display, or use a placeholder key.


### Detailed Steps

1. **Data Preparation**:
   - Load and merge movies and credits CSVs
   - Extract structured data from JSON columns
   - Select top 3 cast members and director(s)

2. **Feature Engineering**:
   - Parse genres, keywords, cast, crew from JSON strings
   - Normalize and lowercase all text
   - Concatenate features: `genres + keywords + cast + director + overview`

3. **Vectorization**:
   - Convert text to numerical vectors using TF-IDF
   - Each movie represented as a high-dimensional vector

4. **Similarity Computation**:
   - Calculate cosine similarity between movie vectors
   - Store precomputed similarity matrix for fast lookups

5. **Recommendation**:
   - For a query movie, retrieve its similarity scores
   - Return top-N movies with highest similarity scores


## Known Limitations

- **Content-Based Only**: Cannot recommend movies without similar metadata
- **Cold Start Problem**: Applies to new movies with limited metadata
- **Static Model**: Similarity matrix must be recomputed if dataset updates
- **Text Similarity**: May miss nuanced thematic connections not captured in metadata

## Contributing

Contributions are welcome! Please consider:

- Improving feature engineering techniques
- Adding collaborative filtering
- Enhancing the web interface
- Writing unit tests
- Optimizing performance
- Fixing bugs or typos

## License

This project is provided for **educational purposes**. 

**Dataset Attribution**: 
- The TMDB 5000 Movie Dataset is provided by [The Movie Database (TMDB)](https://www.themoviedb.org/)
- Poster images are sourced from TMDB's API
- Please comply with [TMDB's Terms of Use](https://www.themoviedb.org/settings/api) when redistributing or publishing results

## Acknowledgments

- [The Movie Database (TMDB)](https://www.themoviedb.org/) for the dataset
- [Kaggle](https://www.kaggle.com/) for hosting and distribution
- scikit-learn for ML utilities
- Streamlit for the web framework

## Support & Questions

For questions or issues:
- Open an GitHub issue in this repository
- Check the notebook comments for detailed explanations
- Review the Streamlit documentation for app customization

---

**Last Updated**: July 2026  
**Status**: Active - Educational Project
