# Gnod Song Recommender

## Project Overview

This project was developed as part of the Ironhack Data Analytics Bootcamp.

The project is based on a case study from **Gnod**, a music recommendation website. Gnod currently uses collaborative filtering to recommend artists based on the preferences of other users.

The objective of this project is to explore how Gnod could improve its music recommendations by adding two new possibilities:

1. Recommend songs that are currently popular around the world.
2. Recommend songs that are acoustically similar to a song selected by the user.

For the first prototype, I explored two different data sources:

- **Billboard Global 200** for worldwide song popularity.
- **Free Music Archive (FMA)** for track information and pre-computed audio features.

The project then uses data analysis and clustering techniques to group songs with similar characteristics.

---

## Business Problem

Gnod already provides recommendations based on users' musical tastes. However, the company would like to give users more ways to discover music.

The proposed solution explores two different questions:

> **What songs are popular around the world right now?**

and

> **What songs are acoustically similar to the song I selected?**

The idea is not to replace Gnod's existing recommendation system, but to investigate how additional data and techniques could make the product more flexible and useful.

---

## Gnoosic User Example

As part of the initial exploration, I used the Gnoosic website with three artists that I already know and like:

- The Killers
- The National
- Anavitória

Gnoosic returned **Rubel** and **Jovem Dionisio** as artists that I might also like.

This was interesting because it shows how collaborative filtering can find relationships between artists based on the preferences of other users.

The goal of the new approach is different: instead of relying only on user preferences, it also explores the actual characteristics of songs.

---

## Data Sources

### Billboard Global 200

The Billboard Global 200 is used as the popularity source. It provides a worldwide view of songs that are currently performing strongly across international markets.

Source:

https://www.billboard.com/charts/billboard-global-200/

A JSON version of the chart was used during the data collection stage:

https://github.com/KoreanThinker/billboard-json

### Free Music Archive (FMA)

The Free Music Archive dataset provides music metadata and pre-computed audio features that can be used for music analysis and machine learning.

Source:

https://github.com/mdeff/fma

The project uses the metadata and audio features rather than downloading the full audio collection.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Requests
- BeautifulSoup
- Jupyter Notebook
- GitHub

---

## Data Analysis Workflow

The project follows these main steps:

1. Define the business problem.
2. Collect data from the selected sources.
3. Inspect and clean the datasets.
4. Explore the data using descriptive statistics and visualizations.
5. Select useful acoustic features.
6. Standardize the features.
7. Apply Principal Component Analysis (PCA).
8. Use K-Means clustering to group similar songs.
9. Evaluate different numbers of clusters using the elbow method and silhouette score.
10. Explore the songs contained in each cluster.
11. Build a basic song recommendation function.
12. Compare popularity-based and acoustic-similarity recommendations.
13. Identify limitations and propose future improvements.

---

## Clustering Approach

The acoustic recommendation prototype uses **K-Means clustering**.

Before applying K-Means, the selected audio features are standardized so that variables with different scales do not have an unfair influence on the clustering.

PCA is then used to reduce the dimensionality of the data and make it easier to visualize the groups of songs.

The number of clusters is evaluated using:

- Elbow Method
- Silhouette Score

Songs belonging to the same cluster are treated as songs with relatively similar acoustic characteristics.

---

## Recommendation Approaches

### 1. Popularity-Based Recommendation

The Billboard Global 200 is used to identify songs that are currently popular internationally.

This recommendation does not depend on the user's previous taste. It can therefore introduce users to songs that are currently popular around the world.

### 2. Acoustic Similarity Recommendation

The second approach uses the audio features from the FMA dataset.

After clustering the songs, a selected song can be associated with one of the clusters. Other songs from the same cluster can then be suggested as possible recommendations.

This approach focuses more on the characteristics of the music itself.

---

## Important Limitations

This is an initial prototype and not a production-ready recommendation system.

There are several limitations:

- The Billboard and FMA datasets come from different sources and do not contain exactly the same songs.
- The FMA dataset does not represent the complete commercial music market.
- Acoustic similarity does not necessarily mean that two songs will be equally enjoyable for a particular user.
- The number of clusters can affect the recommendations.
- The popularity and acoustic approaches are currently demonstrated separately.
- A real Gnod product would need a much larger and more regularly updated dataset.
- Recommendations would need to be evaluated with real users before being used in production.

---

## Future Improvements

If this project were developed further, I would consider:

1. Combining collaborative filtering with acoustic similarity.
2. Combining popularity and user preferences.
3. Using a larger and more representative music dataset.
4. Testing additional clustering algorithms such as DBSCAN and hierarchical clustering.
5. Creating a better song-to-song similarity model.
6. Adding user feedback to improve recommendations.
7. Building a simple web interface for the recommender.
8. Updating the popularity data automatically.
9. Testing the recommendations with real users.
10. Exploring possible integrations with music streaming partners.

The long-term goal would be to create a hybrid recommendation system that considers several aspects of music discovery instead of relying on only one method.

---

## Project Structure

```text
gnod-song-recommender/
│
├── data/
│   └── README.md
│
├── Gnod_Song_Recommender.ipynb
│
├── README.md
│
├── requirements.txt
│
└── .gitignore
```

The datasets themselves are not included in this repository because some of the source files are large. The notebook contains the steps used to obtain and process the required data.

---

## How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/teresamendescoelho-cpu/gnod-song-recommender.git
```

### 2. Open the project in VS Code

```bash
cd gnod-song-recommender
code .
```

### 3. Install the required Python libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn requests beautifulsoup4 lxml jupyter
```

### 4. Open the notebook

Open:

```text
Gnod_Song_Recommender.ipynb
```

Run the cells in order.

---

## Conclusion

This project explores how Gnod could expand its current music recommendation system by using additional types of information.

The Billboard data provides a way to discover what is popular around the world, while the FMA audio features provide a way to compare songs based on their characteristics.

The clustering prototype shows how songs can be grouped according to their acoustic features and how those groups could be used to generate recommendations.

For me, the most interesting next step would be to combine these approaches with Gnod's existing collaborative filtering system. This could create recommendations that consider both what other users like and what the music itself sounds like.

---

## Author

**Teresa Mendes Coelho**

Ironhack Data Analytics Bootcamp
