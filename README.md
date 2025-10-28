# Movie Recommender System
**Collaborative Filtering with LightFM**

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/iKrish/RecommenderSystem/HEAD?labpath=movie-recommender-system-a2.ipynb)

---

## Overview

This project implements a personalized movie recommendation system using collaborative filtering with the LightFM library.  System learns user preferences from implicit feedback signals (watch duration, completion rate) to generate top-k movie recommendations.

---

## AI Task Type

**Implicit Collaborative Filtering** with top-k ranking optimization using matrix factorization.

**Key Characteristics:**
- Learns from behavioral signals (watch duration, completion rate)
- Matrix factorization with latent embeddings
- Bayesian Personalized Ranking (BPR) loss for pairwise optimization
- Handles sparse interaction data (~1% matrix density)

---

## How to Run

### Option 1: Run in Browser (One-Click)
1. Click the **"launch binder"** badge at the top
2. Wait for environment to build (~2-3 minutes first time)
3. Open `movie-recommender-system-a2.ipynb`
4. Click **"Run"** → **"Run All Cells"**
5. Review results

**No installation required!** Runs directly in your browser via MyBinder.

### Option 2: Run Locally

**Prerequisites:**
- Python 3.8+
- pip package manager

**Installation:**
```bash
# Clone the repository
git clone https://github.com/iKrish/RecommenderSystem.git
cd RecommenderSystem

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook movie-recommender-system-a2.ipynb
```

**Execute:**
1. Open `movie-recommender-system-a2.ipynb`
2. Click **"Kernel"** → **"Restart & Run All"**
3. Wait for execution (~2-3 minutes)
4. Review results

---

## Project Structure

```
RecommenderSystem/
│
├── movie-recommender-system-a2.ipynb   # Main notebook (22 cells)
├── README.md                            # This file
├── requirements.txt                     # Python dependencies
├── .gitignore                           # Git ignore patterns
│
└── raw_data/                            # Dataset
    ├── users.csv                        # 10,000 user profiles
    ├── movies.csv                       # 1,000 movie metadata
    └── watch_history.csv                # 105,000 watch events
```

---

## Methodology

### 1. Data Preprocessing
- **Aggregate sessions**: Combine multiple viewing sessions per user-movie pair
- **Strength score**: `log(1 + total_minutes) × (0.3 + 0.7 × completion_rate)`
- **Filter sparse data**: Remove users with <3 movies, movies with <5 watchers
- **Result**: 99,420 interactions, 9,975 users, 1,000 movies (~1% density)

### 2. Model Architecture
- **Algorithm**: LightFM with BPR (Bayesian Personalized Ranking) loss
- **Embeddings**: 50-dimensional latent factors for users and movies
- **Training**: 10 epochs, learning rate 0.01, stochastic gradient descent
- **Optimization**: Pairwise ranking learns "watched > unwatched" preferences

### 3. Evaluation
- **Split**: 80/20 random holdout (79,536 train / 19,884 test)
- **Metrics**:
  - **Precision@10**: Accuracy of top-10 recommendations
  - **Recall@10**: Coverage of user's interests in top-10
  - **nDCG@10**: Ranking quality with position weighting
  - **AUC**: Overall ranking quality (0.5=random, 1.0=perfect)

---

## Dataset

**Source**: Synthetic Netflix-style watch history

- **Users**: 10,000 profiles with subscription tiers
- **Movies**: 1,000 titles with genre metadata
- **Interactions**: 105,000 watch events (raw) → 99,420 unique user-movie pairs (processed)
- **Sparsity**: ~1% matrix density (99% of possible interactions are empty)

---


