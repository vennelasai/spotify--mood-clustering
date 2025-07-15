# Spotify Mood Clustering using PSO and K-Means

## Overview
This project clusters Spotify tracks into mood-based categories using unsupervised learning techniques. We apply **K-Means clustering** with **Particle Swarm Optimization (PSO)** to determine the optimal number of clusters. Each cluster is then profiled based on musical features like valence, energy, and danceability to assign mood labels such as *Happy*, *Chill*, *Sad*, or *Energetic*. The results are visualized using **t-SNE** for better interpretability.

---

## Dataset

- **Source**: [Spotify Audio Features Dataset on Kaggle](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset)
- **Rows**: ~200,000 tracks
- **Features Used**:  
  - Numerical: `valence`, `energy`, `danceability`, `acousticness`, `tempo`, `speechiness`, etc.  
  - Metadata: `track_name`, `album_name`, `track_genre`, `popularity`

---

## Problem Statement

Cluster songs based on their audio characteristics to group them by mood.  
Automatically determine the best number of clusters using **nature-inspired optimization (PSO)** rather than choosing it manually.

---

## Approach

### 1. Data Preprocessing
- Removed duplicates and unnecessary columns
- Handled missing values (if any)
- Scaled numerical features using `StandardScaler`
- Sampled 3000 rows for optimization efficiency

### 2. Optimal Clustering via PSO
- Used **Particle Swarm Optimization (PSO)** to find the best `k` (number of clusters)
- Fitness function: **Silhouette Score**

### 3. K-Means Clustering
- Applied K-Means using optimal `k`
- Assigned songs to clusters

### 4. Mood Profiling
- Averaged key features per cluster to assign mood labels
Example mappings:
- High valence + high danceability → "Happy"

- High acousticness → "Calm / Relaxing"

- High energy + low valence → "Energetic but Dark"

- High instrumentalness → "Lo-fi / Instrumental"

### 5. Visualization with t-SNE
- Used t-SNE and PCA for 2D projection of clusters
- Labeled clusters with mood names based on profiling

### 6. Model Explainability with SHAP
- Applied SHAP (SHapley Additive exPlanations) to analyze feature contributions to each cluster.
- Generated summary plots to understand how features like valence, energy, and acousticness influenced mood groupings.

---

## Sample Visualizations

### 1. Cluster Visualization (t-SNE colored by cluster ID)
![Clusters](images/tsne_clusters.png)

### 2. Valence Mood Map (colored by valence value)
![Valence](images/tsne_valence.png)

### 3. Cluster Centers with Mood Labels
![Mood Labels](images/tsne_mood_labels.png)

### 4. Feature Importance using SHAP
![SHAP](images/shap_plot.png)
---

## Tools & Libraries

- Python  
- scikit-learn  
- PySwarms  
- Pandas, NumPy  
- Matplotlib, Seaborn  
- t-SNE  
- Google Colab / Jupyter Notebook

---

## Results

- **Optimal number of clusters: 8**
- Identified moods:
  - Happy / Party Vibes
  
  - Calm / Acoustic
  
  - Energetic but Dark
  
  - Instrumental / Lo-fi
  
  - Sad / Low Energy
  
  - Rap / Spoken Word
  
  - Dance / Upbeat
  
  - Mixed / Undefined

-SHAP explainability shows key features influencing cluster formation

---

## Folder Structure

spotify-mood-clustering/

├── spotify_clustering.ipynb # Main analysis notebook

├── images/ # SHAP & t-SNE plots

└── README.md 

---

## How to Run

1. Clone the repository:
   git clone https://github.com/vennelasai/spotify-mood-clustering.git
Open spotify_clustering.ipynb in Google Colab or Jupyter Notebook

Ensure dataset.csv is loaded correctly

Run all cells to reproduce the analysis and visualizations

## Conclusion
This project demonstrates how unsupervised learning and nature-inspired optimization (PSO) can work together to generate meaningful insights from audio data. Mood-based clustering provides a fun and informative way to explore musical content.
