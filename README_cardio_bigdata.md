# ❤️ Prédiction des maladies cardiovasculaires — Big Data (PySpark)

Pipeline **Big Data de bout en bout** pour prédire la présence d'une maladie cardiovasculaire chez un patient, sur un jeu de **70 000 patients**, en environnement distribué Spark.

> Projet d'équipe — module Big Data, Licence Sciences des Données, Université Chouaïb Doukkali (El Jadida).

## 🔧 Technologies
`PySpark` · `Spark MLlib` · `Spark SQL` · `Hadoop / HDFS` · `Kafka` · `Python` · `pandas` · `matplotlib`

## 📊 Données
- **Jeu de données :** Cardiovascular Disease Dataset (Kaggle)
- **Volume :** 70 000 patients · 13 variables (0 valeur manquante, 0 doublon)
- **Cible :** `cardio` — malade (1) / sain (0)

## 🏗️ Architecture du pipeline
1. **Ingestion** — chargement PySpark + simulation d'un flux **Kafka** (producer/topic)
2. **Stockage** — organisation type **HDFS** (raw / processed / models)
3. **Feature engineering** — calcul de l'**IMC**, conversion de l'âge en années, ratio cholestérol/âge
4. **Prétraitement** — `Spark ML Pipeline` : `VectorAssembler` + `StandardScaler`
5. **Modélisation** — 4 modèles **Spark MLlib** comparés
6. **Analyse exploratoire** — requêtes **Spark SQL** (équivalent Hive) : taux de maladie par cholestérol, IMC, habitudes…
7. **Visualisation** — courbe ROC, matrice de confusion, importance des variables

## 🏆 Résultats

| Modèle | Accuracy | F1 | ROC-AUC |
|---|:---:|:---:|:---:|
| **Gradient Boosted Trees** | **0.733** | **0.732** | **0.802** |
| Random Forest (100 arbres) | 0.725 | 0.724 | 0.795 |
| Régression logistique | 0.719 | 0.719 | 0.784 |
| Arbre de décision | 0.729 | 0.726 | 0.592 |

**Variables les plus prédictives :** pression artérielle systolique (`ap_hi`), diastolique (`ap_lo`) et ratio cholestérol/âge.

**Quelques insights (Spark SQL) :** le taux de maladie passe de **44 %** (cholestérol normal) à **77 %** (cholestérol très élevé), et de **40 %** (IMC normal) à **63 %** (obésité).

## 👥 Équipe
Projet réalisé en équipe (acquisition, prétraitement, modélisation, visualisation).
**Ma contribution :** modèle **Random Forest** + analyse de l'importance des variables.

## ▶️ Lancer le projet
```bash
pip install pyspark pandas matplotlib seaborn scikit-learn
jupyter notebook projetBigData.ipynb
```
