# Walmart Store Sales - Analyse et Prédiction

Ce projet vise à **analyser et prédire les ventes hebdomadaires des magasins Walmart** à partir de données historiques et de variables économiques et climatiques.

---

## 1. Objectif

- Comprendre les facteurs influençant les ventes.
- Développer des modèles prédictifs pour estimer les ventes hebdomadaires.
- Évaluer la performance des modèles et identifier le meilleur compromis biais/variance.

---

## 2. Description des données

Le dataset contient les colonnes suivantes :

- `Store` : Identifiant du magasin  
- `Date` : Date de la vente  
- `Weekly_Sales` : Ventes hebdomadaires (cible)  
- `Holiday_Flag` : Indicateur de vacances (0 = non, 1 = oui)  
- `Temperature` : Température (°F)  
- `Fuel_Price` : Prix de l'essence (USD)  
- `CPI` : Indice des prix à la consommation  
- `Unemployment` : Taux de chômage  

Le dataset contient **136 lignes** après nettoyage.

---

## 3. Pré-traitement

- Suppression des valeurs manquantes sur `Weekly_Sales`.
- Imputation des valeurs manquantes sur `Temperature`, `Fuel_Price`, `CPI`, `Unemployment` avec la médiane.
- Transformation de `Date` en variables `Year`, `Month`, `Day`, `Weekday`.
- Remplissage des valeurs manquantes de `Holiday_Flag` en utilisant les informations des autres magasins.
- Standardisation des variables numériques et encodage One-Hot pour les variables catégorielles.

---

## 4. Analyse exploratoire

- **Saisonnalité** : pics de ventes en Novembre/Mai, creux en Janvier/Septembre.
- **Vacances** : périodes de vacances plus stables et légèrement plus élevées.
- **Magasin** : le facteur `Store` est le plus influent sur les ventes.
- **Variables économiques et climatiques** : CPI et Unemployment ont un impact modéré, Temperature montre un léger effet négatif, Fuel_Price faible impact.

---

## 5. Modélisation

**Modèles testés :**

| Modèle              | R² Test | RMSE Test |
|--------------------|---------|-----------|
| Linear Regression  | 0.959   | 136,778   |
| Ridge              | 0.959   | 137,108   |
| Lasso              | 0.957   | 140,239   |

**Observations :**

- La **Linear Regression** est le modèle le plus simple et performant.
- Ridge et Lasso n’apportent pas d’amélioration significative avec ce dataset.
- Les modèles basés sur les arbres (Random Forest, XGBoost) ne sont pas adaptés aux relations essentiellement linéaires.

**RMSE et interprétation :**

- RMSE = 136,778  
- Représente ~11% de la moyenne des ventes et ~20% de l’écart-type  
- Indique que les prédictions sont généralement proches des ventes réelles, avec une marge d’erreur modérée.

---

## 6. Insights principaux

- Les ventes dépendent surtout du **magasin** et des **vacances**, et dans une moindre mesure du **CPI** et du **taux de chômage**.
- Saisonnalité claire : pics en **Novembre/Mai**, creux en **Janvier/Septembre**.
- Modèle **Linear Regression** simple et robuste pour ce dataset.
- RMSE raisonnable par rapport à la variabilité des ventes.

---

## 7. Perspectives / Améliorations possibles

- Ajouter des variables supplémentaires : promotions, événements locaux, météo plus détaillée.  
- Étendre le dataset à plusieurs années pour mieux capturer la saisonnalité.  
- Tester des modèles plus complexes si de nouvelles relations non-linéaires apparaissent.  
- Utiliser des méthodes de feature selection pour identifier les variables les plus pertinentes et réduire la dépendance aux magasins.

---

## 8. Instructions pour exécuter le notebook

1. Cloner le repository :  
```bash
git clone https://github.com/ACombey/Walmart_ML_Project.git
