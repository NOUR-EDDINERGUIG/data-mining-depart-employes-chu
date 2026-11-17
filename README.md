# Data Mining – Prédiction du type de départ des employés du CHU Mohammed VI d'Oujda

Mini-projet du module **Data Mining** (Master IASD – Université Mohammed Premier Oujda, 2025-2026), encadré par Pr. A. Kerkour Elmiad.

**Objectif :** classifier le type de départ d'un employé (`Volontaire` vs `Institutionnel`) à partir de données RH, afin d'aider le CHU à anticiper le turn-over.

## Démarche

1. Fusion de deux sources (base historique + départs 2025-2026)
2. Nettoyage : âge, dates incohérentes, situation familiale, villes (normalisation) et création de la variable `REGION`
3. Calcul de l'ancienneté et création de la variable cible `TYPE_DEPART`
4. Exclusion des départs par décès (hors périmètre)
5. Gestion du déséquilibre de classes avec **SMOTE** appliqué *à l'intérieur de chaque fold* (Pipeline `imblearn`, `StratifiedKFold`) pour éviter la fuite de données
6. Comparaison de modèles : Random Forest, Arbre de décision, Naive Bayes (Gaussian)

## Structure

```
notebooks/preparation_et_modelisation.ipynb   # nettoyage + modélisation (Python)
orange/projetdata.ows                         # workflow Orange Data Mining
requirements.txt
```

## Données
Les données RH proviennent du CHU et contiennent des informations personnelles ; elles ne sont **pas publiées** dans ce dépôt. Le notebook attend `Base de donnée des départs par ID.xlsx` et `Départ 2025 2026.xlsx` à la racine et produit `dataset_orange_CHU.csv`.

## Lancement
```bash
pip install -r requirements.txt
jupyter notebook notebooks/preparation_et_modelisation.ipynb
```

## Technologies
Python · Pandas · scikit-learn · imbalanced-learn · Orange Data Mining

## Auteur
Nour-eddine Rguig
