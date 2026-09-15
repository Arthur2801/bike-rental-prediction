# Prédiction des locations de vélos

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-EC6B23?style=flat-square)

Un TP de data science réalisé à l'UTT : explorer **17 379 observations horaires** et prédire le nombre de vélos loués (`cnt`) à partir de l'heure, du calendrier et de la météo.

Le [notebook réalisé](notebooks/TP_velo_realise.ipynb) réunit l'analyse des données, les visualisations, une exploration K-Means/ACP, une variable d'heure de pointe et la comparaison de modèles de régression. Le [rendu HTML](report/TP_velo_realise.html) conserve la version remise ; le notebook éditable a été reconstitué à partir de ce rendu. Le [CSV](data/velo.csv) provient du ZIP fourni pour le TP.

![Nombre moyen de locations selon l'heure et le jour de la semaine](assets/locations-par-heure.png)

Les jours ouvrés montrent deux pics de demande, vers 8 h et 17–18 h ; le profil du week-end est différent.

| Modèle | R² sur `log(cnt)` | RMSE en vélos |
| --- | ---: | ---: |
| Régression linéaire | 0,8056 | 103,75 |
| XGBoost | 0,9086 | 71,08 |
| XGBoost avec régularisation L2 | 0,9112 | 70,67 |
| XGBoost ajusté avec FLAML | 0,9250 | 67,91 |

Ces chiffres proviennent de l'exécution vérifiée du notebook. FLAML peut trouver d'autres paramètres et scores selon la durée de sa recherche ; le rendu HTML archivé indiquait 0,9284 et 65,33 pour ce modèle. Le test utilise une séparation aléatoire des observations ; pour prévoir des heures futures, une validation chronologique donnerait une estimation plus réaliste.

Pour ouvrir le notebook :

```bash
python -m pip install -r requirements.txt
jupyter lab notebooks/TP_velo_realise.ipynb
```

Python 3.12 est le choix de l'environnement utilisé pour le TP. Lancez Jupyter depuis la racine du dépôt afin que le chemin vers `data/velo.csv` fonctionne.
