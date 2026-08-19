# 🎵 Gnod Song Recommender

## 📌 Project Overview

This project was developed as part of the **Ironhack Data Analytics Bootcamp** and is based on a case study for **Gnod**, a music recommendation website.

Gnod currently uses collaborative filtering to recommend artists based on the preferences of its users. The objective of this project is to explore how Gnod could expand its recommendation system by introducing additional approaches to music discovery.

The project investigates two main possibilities:

1. **Popularity-based recommendations** — recommending songs that are currently popular around the world.
2. **Acoustic similarity recommendations** — recommending songs that have similar musical characteristics to a song selected by the user.

The project combines data collection, data cleaning, exploratory data analysis, feature engineering, dimensionality reduction and machine learning clustering techniques to create an initial song recommendation prototype.

---

## 🎯 Business Problem

Gnod already provides recommendations based on users' musical preferences. However, the company wants to offer users additional ways to discover music.

The project therefore investigates two questions:

> **What songs are currently popular around the world?**

and

> **What songs are acoustically similar to a song selected by the user?**

The goal is not to replace Gnod's existing collaborative-filtering system, but to explore how additional data and analytical techniques could make music discovery more flexible and interesting.

---

## 🎶 Initial Gnoosic Exploration

As part of the initial exploration, I tested Gnoosic using three artists that I already know and enjoy:

* The Killers
* The National
* Anavitória

Gnoosic suggested artists including:

* Rubel
* Jovem Dionisio

This provided an interesting example of how collaborative filtering can identify relationships between artists based on user preferences.

The approach developed in this project is different because it also considers the characteristics of the music itself.

---

# 📊 Data Sources

## Billboard Global 200

The **Billboard Global 200** was used as the source for worldwide music popularity.

It provides information about songs performing strongly across international music markets.

Source:

https://www.billboard.com/charts/billboard-global-200/

A JSON version of the chart was used during the data collection process.

---

## Free Music Archive (FMA)

The **Free Music Archive (FMA)** dataset was used for music metadata and pre-computed audio features.

The dataset contains information that can be used to analyse the characteristics of individual tracks.

Source:

https://github.com/mdeff/fma

Because some FMA files are extremely large, the complete dataset is **not stored in this GitHub repository**.

The `.gitignore` file specifically excludes the FMA metadata directory and the Python virtual environment.

The notebook contains the steps required to work with the dataset.

---

# 🧰 Technologies Used

The project uses:

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **Requests**
* **BeautifulSoup**
* **Jupyter Notebook**
* **Git**
* **GitHub**
* **VS Code**

---

# 🔄 Data Analysis Workflow

The project follows the following analytical workflow:

1. Define the business problem.
2. Collect data from the selected sources.
3. Inspect the datasets.
4. Clean and prepare the data.
5. Perform exploratory data analysis.
6. Select relevant acoustic features.
7. Standardize the selected features.
8. Apply Principal Component Analysis (PCA).
9. Determine suitable numbers of clusters.
10. Apply K-Means clustering.
11. Explore songs within each cluster.
12. Develop a basic recommendation approach.
13. Compare popularity-based and acoustic-similarity recommendations.
14. Identify limitations and possible improvements.

---

# 🤖 Recommendation Approaches

## 1. 🌎 Popularity-Based Recommendation

The Billboard Global 200 is used to identify songs that are currently popular internationally.

This approach does not depend on a user's previous musical preferences.

It can therefore be used to introduce users to songs that are currently successful around the world.

---

## 2. 🎧 Acoustic Similarity Recommendation

The second approach uses audio features from the FMA dataset.

The selected acoustic features are processed and standardized before applying machine learning techniques.

Songs with similar characteristics can then be grouped together and used to generate possible recommendations.

This approach focuses on the characteristics of the music itself rather than only on user preferences.

---

# 🧠 Machine Learning Approach

## K-Means Clustering

The acoustic recommendation prototype uses **K-Means clustering**.

Before applying K-Means:

* Relevant acoustic features are selected.
* Features are standardized.
* PCA is applied to reduce dimensionality.

The objective is to group songs with relatively similar acoustic characteristics.

---

## 📉 Choosing the Number of Clusters

Different numbers of clusters are evaluated using:

### Elbow Method

The elbow method helps identify a point where increasing the number of clusters provides diminishing improvements.

### Silhouette Score

The silhouette score evaluates how well observations fit within their assigned clusters compared with other clusters.

Together, these methods help determine a suitable number of clusters for the recommendation prototype.

---

# 📁 Project Structure

```text
gnod-song-recommender/
│
├── data/
│   ├── billboard_global_200.csv
│   └── billboard_global_200_clean.csv
│
├── Gnod_Song_Recommender.ipynb
│
├── README.md
│
└── .gitignore
```

### Dataset note

The large FMA dataset is intentionally excluded from GitHub because some individual files exceed GitHub's recommended file-size limits.

The repository therefore contains the analytical code and smaller supporting datasets rather than the complete FMA dataset.

---

# 🚀 How to Run the Project

## 1. Clone the repository

```bash
git clone https://github.com/teresamendescoelho-cpu/gnod-song-recommender.git
```

## 2. Enter the project directory

```bash
cd gnod-song-recommender
```

## 3. Create a virtual environment

### Windows

```bash
python -m venv .venv
```

Activate it:

```bash
.venv\Scripts\activate
```

## 4. Install the required libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn requests beautifulsoup4 lxml jupyter
```

## 5. Open Jupyter Notebook

```bash
jupyter notebook
```

Then open:

```text
Gnod_Song_Recommender.ipynb
```

Run the notebook cells in order.

---

# ⚠️ Limitations

This project represents an **initial recommendation prototype**, rather than a production-ready recommendation system.

The main limitations include:

* Billboard and FMA datasets originate from different sources.
* The datasets do not contain exactly the same songs.
* The FMA dataset does not represent the complete commercial music market.
* Acoustic similarity does not necessarily mean that two songs will be equally enjoyable to a particular user.
* The number of clusters can influence the recommendations.
* Popularity-based and acoustic recommendations are currently explored as separate approaches.
* A production system would require a larger and regularly updated dataset.
* Recommendations would need to be evaluated with real users.

---

# 🔮 Future Improvements

If this project were developed further, I would consider:

* Combining collaborative filtering with acoustic similarity.
* Combining popularity with individual user preferences.
* Using a larger and more representative music dataset.
* Testing DBSCAN and hierarchical clustering.
* Developing a more precise song-to-song similarity model.
* Incorporating user feedback.
* Creating an interactive web application.
* Automatically updating popularity data.
* Testing recommendations with real users.
* Exploring integration with music streaming platforms.

The long-term objective would be to develop a **hybrid recommendation system** that considers:

**User preferences + music characteristics + worldwide popularity**

rather than relying on a single recommendation method.

---

# 💡 Conclusion

This project demonstrates how data analysis and machine learning can be used to explore new possibilities for music recommendation.

The **Billboard Global 200** provides a way to identify songs that are currently popular internationally, while the **FMA audio features** provide information that can be used to compare songs based on their acoustic characteristics.

The clustering approach demonstrates how songs can be grouped according to their musical features and how those groups can potentially be used to generate recommendations.

The most interesting next step would be to combine these approaches with Gnod's existing collaborative-filtering system. A hybrid model could consider both **what users like** and **what the music itself sounds like**, potentially creating a more flexible and personalised music discovery experience.

---

# 👩‍💻 Author

**Teresa Mendes Coelho**

Ironhack Data Analytics Bootcamp

GitHub:
https://github.com/teresamendescoelho-cpu
