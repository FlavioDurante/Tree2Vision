# TreeVision 

**TreeVision** utilise des techniques de machine et deep learning pour identifier, à partir de variables cartographiques seules, le type de couverture forestière d’une cellule de 30 × 30 m dans la forêt nationale Roosevelt (Colorado).

## Table des matières
1. [Présentation](#présentation)
2. [Données](#données)
3. [Structure du projet](#structure-du-projet)
4. [Installation & Usage](#installation--usage)
5. [Modèles entraînés](#modèles-entraînés)
6. [Enjeux & résultats](#enjeux--résultats)
7. [Licence](#licence)

## Données
- **Source** : USFS Region 2 Resource Information System  
- **Fichiers** :  
  - `cover_data.csv` (dataset brut)  
  - `train_data.csv`,`test_data.csv` (issus de cover_data.csv)

| Nom de la variable                                   | Type de donnée | Unité / Mesure             | Description                                                  |
|-------------------------------------------------------|----------------|----------------------------|--------------------------------------------------------------|
| Élévation                                             | Quantitatif    | Mètres                     | Élévation en mètres                                          |
| Orientation                                           | Quantitatif    | Degrés (azimut)            | Orientation en degrés azimutaux                              |
| Pente                                                 | Quantitatif    | Degrés                     | Pente en degrés                                              |
| Distance horizontale à l’hydrologie                   | Quantitatif    | Mètres                     | Distance horizontale jusqu’aux plus proches plans d’eau      |
| Distance verticale à l’hydrologie                     | Quantitatif    | Mètres                     | Distance verticale jusqu’aux plus proches plans d’eau        |
| Distance horizontale aux routes                       | Quantitatif    | Mètres                     | Distance horizontale jusqu’à la route la plus proche         |
| Indice d’ombrage à 9 h                                | Quantitatif    | Indice (0–255)             | Indice d’ombrage à 9 h, solstice d’été                       |
| Indice d’ombrage à midi                               | Quantitatif    | Indice (0–255)             | Indice d’ombrage à midi, solstice d’été                      |
| Indice d’ombrage à 15 h                               | Quantitatif    | Indice (0–255)             | Indice d’ombrage à 15 h, solstice d’été                      |
| Distance horizontale aux points d’allumage d’incendie | Quantitatif    | Mètres                     | Distance horizontale jusqu’aux points d’allumage d’incendie  |
| Zone sauvage (4 colonnes binaires)                    | Qualitatif     | 0 (absence) / 1 (présence) | Désignation de la zone sauvage                               |
| Type de sol (40 colonnes binaires)                    | Qualitatif     | 0 (absence) / 1 (présence) | Désignation du type de sol                                   |
| Type de couverture forestière (7 catégories)          | Entier         | 1 – 7                      | Désignation du type de couverture forestière                 |


## Structure du projet
├── cleaning.ipynb # EDA & preprocessing

├── models.ipynb # Entraînement des modèles 

├── cover_data.csv 

├── train_data.csv 

├── test_data.csv

├── requirements.txt

## Installation & Usage
```bash
git clone https://…/TreeVision.git
cd TreeVision
pip install -r requirements.txt

```
## Extraction train_data et test_data

Executer le code dans cleaning.ipynb

# Lancer MLflow UI
```bash
mlflow ui --port 5000
```
Ouvre ensuite cleaning.ipynb puis models.ipynb dans JupyterLab.

## Modèles entraînés
Logistic Regression

XGBoost

Random Forest

Neural Network (TensorFlow + Keras)

## Enjeux & résultats
Fort déséquilibre entre classes

![image_1](https://github.com/user-attachments/assets/ce2b50c6-76f9-4663-bb21-57b0dec52446)


Impact sur la Logistic Regression → faible recall sur les classes minoritaires.

Meilleure performance obtenue avec Neural Network : précision globale de 81 %, F1-score moyen de 90%.

## Licence
Ce projet est sous licence MIT.
