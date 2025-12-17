# Comparative Analysis of Clustering Methods for Identifying Environmental Risk Zones

This repository contains a research project on environmental risk assessment for
Russian corporate entities using clustering methods.

The work started from a practical problem: most environmental analyses rely either on
company-level indicators or on spatial information, but rarely consider both together.
The goal of this project was to test how much additional structure can be revealed when
attribute data and geographic location are analyzed separately and then combined.

The focus is not on building a single “best” model, but on comparing different clustering
approaches and understanding their behavior and limitations in this domain.

---

## Data and problem setup

The data represent corporate businesses with environmental characteristics and
geographic coordinates. The task is to group these objects into a small number of
interpretable clusters that may reflect different environmental risk profiles.

---

## Approaches

The analysis was conducted in several stages.

First, standard attribute-based clustering methods were applied without using spatial
information. This step was used as a baseline and to explore the internal structure of
the feature space.

Next, clustering based only on geographic location was tested. This includes scalable
solutions for large datasets and experiments with neural-network-based methods, which
are rarely used for this type of problem.

Finally, attribute and spatial information were combined. For this purpose, an extended
version of the K-means algorithm was implemented. It allows:
- custom distance metrics
- weighting of features and coordinates
- centroid updates that account for both physical attributes and location
- better scalability compared to naive implementations

---

## Evaluations

Different clustering quality metrics were used depending on the stage of the analysis.
The goal was not to optimize a single score, but to compare methods and identify
consistent patterns across approaches.

---

## Evaluation summary

Attribute-based clustering produced usable but moderately separated clusters. Three
clusters were the most stable; adding more generally reduced interpretability. K-means
consistently outperformed other methods and was used to derive risk profiles.

The clusters roughly correspond to heavy industrial emitters, agricultural and trade-related
activities, and urban commercial objects. Differences are mainly driven by discharge
volume, chemical diversity, dominant activities, and regional concentration.

Purely spatial clustering showed weaker separation. HDBSCAN produced fragmented
clusters in dense areas, while CLARA formed more coherent spatial regions and performed
best among spatial methods. SOM results were intermediate and often mixed.

The integrated attribute–location approach improved separation compared to spatial
methods alone and remained computationally efficient. The weighted K-means variant
formed stable clusters even in sparse regions, but results depend on the chosen distance
metric and weighting scheme.

Overall, combining attributes with location yields more interpretable clusters than using
either dimension alone.

---

## Tools and libraries

The analysis was carried out in Python, mainly using:

- numpy, pandas
- matplotlib, seaborn
- geopandas, folium, geopy
- osmnx
- pysal
- hdbscan
- MiniSom
- tqdm, webcolors

---

## Notes

This repository is experimental.

