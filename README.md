# housing-price-prediction-linear-regression
End-to-end Data Science project using Linear Regression to predict housing prices, perform statistical diagnostics and identify key economic drivers of real estate value.
# 🏠 Prédiction des prix immobiliers avec la régression linéaire

## 📌 Description du projet

Ce projet vise à prédire la valeur médiane des logements à partir du jeu de données Boston Housing.
L’objectif est de construire un modèle de régression linéaire capable d’estimer le prix des logements en fonction de caractéristiques économiques, sociales, environnementales et géographiques.

Ce projet ne se limite pas à la prédiction : il cherche aussi à comprendre les facteurs qui influencent réellement les prix immobiliers, puis à vérifier la qualité statistique du modèle à travers plusieurs tests.

---

## 🎯 Objectif métier

Dans un contexte immobilier, mieux comprendre les déterminants du prix d’un logement permet de :

* identifier les variables qui valorisent ou dévalorisent un bien ;
* mieux estimer la valeur d’un logement ;
* analyser l’impact du contexte socio-économique sur les prix ;
* construire une base pour des modèles prédictifs plus avancés.

La variable cible est :

**Valeur_med_logement** : valeur médiane des logements.

---

## 🧹 Analyse exploratoire des données

Le jeu de données contient plusieurs variables explicatives, notamment :

* taux de criminalité ;
* proportion de terrains résidentiels ;
* concentration en oxyde nitrique ;
* nombre moyen de pièces ;
* distance aux centres d’emploi ;
* accessibilité aux autoroutes ;
* taux d’imposition foncière ;
* ratio élèves/professeurs ;
* pourcentage de population à faible statut socio-économique.

L’analyse descriptive et les visualisations ont permis d’observer la distribution des variables, la présence de valeurs extrêmes et les premières relations entre les variables explicatives et la valeur médiane des logements.

---

## 🔗 Analyse des corrélations

L’analyse de corrélation montre que certaines variables sont fortement liées à la valeur des logements.

Le **nombre moyen de pièces** présente une relation positive forte avec la valeur des logements. Cela signifie que plus un logement possède de pièces, plus sa valeur médiane a tendance à augmenter.

À l’inverse, le **pourcentage de population à faible statut socio-économique** présente une relation négative forte avec la valeur des logements. Cela indique que les zones socialement moins favorisées sont associées à des valeurs immobilières plus faibles.

Cette observation est cohérente d’un point de vue métier : les prix immobiliers dépendent à la fois des caractéristiques du logement et de l’environnement socio-économique du quartier.

---

## 🤖 Modèle de régression linéaire complet

Un premier modèle de régression linéaire multiple a été entraîné avec l’ensemble des variables explicatives.

### Résultats globaux du modèle

| Indicateur        |    Valeur |
| ----------------- | --------: |
| R²                |     0.751 |
| R² ajusté         |     0.743 |
| F-statistic       |     90.43 |
| Prob(F-statistic) | 6.21e-109 |

### Interprétation

Le modèle explique environ **75,1 % de la variabilité** de la valeur médiane des logements sur les données d’entraînement.
Le R² ajusté de **74,3 %** confirme que le modèle conserve une bonne capacité explicative même après prise en compte du nombre de variables.

La p-value globale du test de Fisher est extrêmement faible, ce qui signifie que le modèle est globalement statistiquement significatif. Autrement dit, les variables explicatives apportent collectivement une information utile pour prédire le prix des logements.

---

## 📈 Performance prédictive

| Métrique |   Train |    Test |
| -------- | ------: | ------: |
| R²       |  0.7509 |  0.6688 |
| MSE      | 21.6414 | 24.2911 |
| RMSE     |  4.6520 |  4.9286 |

### Interprétation

Le modèle obtient un **R² de 0.75 sur les données d’entraînement** et un **R² de 0.67 sur les données de test**.

Cela signifie que le modèle explique environ **67 % de la variabilité des prix sur de nouvelles données**, ce qui représente une performance correcte pour un modèle linéaire simple.

Le RMSE est de **4.65 sur le train** et **4.93 sur le test**. L’écart entre les deux est faible, ce qui indique que le modèle ne souffre pas d’un surapprentissage important.

Le modèle généralise donc raisonnablement bien, même si une partie de la variation des prix reste inexpliquée.

---

## 🧾 Interprétation des coefficients

### Taux de criminalité

Le coefficient du taux de criminalité est négatif :

**Coefficient : -0.113**

Cela signifie qu’une hausse du taux de criminalité est associée à une baisse de la valeur médiane des logements, toutes choses égales par ailleurs.

D’un point de vue métier, cela est cohérent : les zones perçues comme moins sûres sont généralement moins attractives, ce qui exerce une pression à la baisse sur les prix immobiliers.

---

### Bordure de rivière

Le coefficient associé à la proximité de la rivière est positif :

**Coefficient : 2.784**

Les logements situés en bordure de rivière ont tendance à avoir une valeur médiane plus élevée.

Cela peut s’expliquer par un effet de localisation ou d’attractivité environnementale.

---

### Concentration en oxyde nitrique

Le coefficient est fortement négatif :

**Coefficient : -17.203**

Une concentration plus élevée en pollution atmosphérique est associée à une baisse importante de la valeur des logements.

Cela montre que la qualité environnementale joue un rôle important dans la valorisation immobilière.

---

### Nombre moyen de pièces

Le coefficient est positif et très significatif :

**Coefficient : 4.439**

Cela signifie qu’une pièce supplémentaire est associée à une augmentation importante de la valeur médiane du logement.

C’est l’un des facteurs les plus influents du modèle, ce qui est logique : la taille et le confort du logement sont des déterminants majeurs du prix.

---

### Distance aux centres d’emploi

Le coefficient est négatif :

**Coefficient : -1.448**

Dans ce modèle, une hausse de la distance pondérée aux centres d’emploi est associée à une baisse de la valeur médiane des logements.

Cela suggère que l’accessibilité économique et géographique influence fortement les prix.

---

### Accessibilité aux autoroutes

Le coefficient est positif :

**Coefficient : 0.262**

Une meilleure accessibilité aux autoroutes semble associée à une hausse de la valeur des logements.

Cela peut refléter l’importance des infrastructures de transport dans l’attractivité d’une zone.

---

### Taux d’imposition foncière

Le coefficient est négatif :

**Coefficient : -0.0106**

Une fiscalité foncière plus élevée est associée à une légère baisse de la valeur des logements.

Cela peut traduire un effet de coût supplémentaire pour les propriétaires.

---

### Ratio élèves/professeurs

Le coefficient est négatif :

**Coefficient : -0.915**

Un ratio élèves/professeurs plus élevé est associé à une baisse de la valeur des logements.

Ce résultat suggère que la qualité perçue du système éducatif local influence les prix immobiliers.

---

### Pourcentage de population à faible statut socio-économique

Le coefficient est fortement négatif.

Cette variable est l’un des déterminants les plus importants du modèle.

Elle indique que les zones ayant une proportion plus élevée de population défavorisée ont tendance à afficher des valeurs immobilières plus faibles.

---

## ⚠️ Analyse de la multicolinéarité

Le VIF a été utilisé pour détecter la multicolinéarité entre les variables explicatives.

Certaines variables présentent des VIF très élevés :

| Variable                   |   VIF |
| -------------------------- | ----: |
| Ratio_eleve_prof           | 81.23 |
| Nb_pieces_logement         | 77.54 |
| Concentration_NO2          | 74.81 |
| Taux_impot_foncier         | 60.96 |
| Prop_log_construits_av1940 | 20.89 |
| Prop_noirs_ville           | 19.70 |
| Dist_ponderees_emploi      | 15.30 |
| Accessibilite_autoroute    | 15.20 |

### Interprétation

Des VIF aussi élevés montrent une forte redondance entre certaines variables explicatives.

Cela signifie que plusieurs variables portent une information similaire.
Dans ce cas, les coefficients du modèle peuvent devenir instables et difficiles à interpréter individuellement.

Le modèle reste utile pour prédire, mais son interprétation statistique doit être faite avec prudence.

---

## 🔁 Modèle réduit

Pour améliorer l’interprétabilité du modèle, un second modèle a été construit avec un nombre réduit de variables :

* Taux_criminalite
* Prop_terrains_resid
* Bordure_riviere
* Pourcentage_pop_inf
* Nb_pieces_logement

### Résultats du modèle réduit

| Indicateur        |   Valeur |
| ----------------- | -------: |
| R²                |    0.674 |
| R² ajusté         |    0.669 |
| F-statistic       |    164.2 |
| Prob(F-statistic) | 2.14e-94 |

### Interprétation

Le modèle réduit explique environ **67,4 % de la variabilité** des prix immobiliers.

Même avec seulement cinq variables, il conserve une capacité explicative solide.
Cela montre que quelques variables clés suffisent déjà à expliquer une grande partie des variations de prix.

Le modèle réduit est moins performant que le modèle complet, mais il est plus simple, plus stable et plus interprétable.

---

## ✅ Multicolinéarité du modèle réduit

| Variable            |  VIF |
| ------------------- | ---: |
| Taux_criminalite    | 1.40 |
| Prop_terrains_resid | 1.50 |
| Bordure_riviere     | 1.10 |
| Pourcentage_pop_inf | 4.38 |
| Nb_pieces_logement  | 4.81 |

### Interprétation

Tous les VIF du modèle réduit sont inférieurs à 5.

Cela indique que le problème de multicolinéarité a été fortement réduit.
Le modèle réduit fournit donc des coefficients beaucoup plus stables et plus facilement interprétables.

Ce résultat illustre un compromis important en Data Science : parfois, un modèle légèrement moins performant mais plus interprétable est préférable à un modèle plus complexe difficile à expliquer.

---

## 🧪 Test d’homoscédasticité

Le test de Breusch-Pagan donne :

| Test        | Valeur |
| ----------- | -----: |
| Statistique | 59.189 |
| p-value     |  0.000 |

### Interprétation

La p-value est inférieure à 5 %.
On rejette donc l’hypothèse d’homoscédasticité.

Cela signifie que la variance des erreurs n’est pas constante.
En pratique, le modèle ne fait pas les mêmes erreurs selon le niveau de prix des logements.

Cette hétéroscédasticité peut rendre les intervalles de confiance et les tests statistiques moins fiables.

Une amélioration possible serait d’utiliser des erreurs robustes, une transformation de la variable cible ou un modèle non linéaire.

---

## 📉 Normalité des résidus

Les tests de normalité donnent :

| Test               | Statistique | p-value |
| ------------------ | ----------: | ------: |
| Shapiro-Wilk       |      0.9118 |   0.000 |
| Anderson-Darling   |      7.4128 |     N/A |
| Kolmogorov-Smirnov |      0.3478 |   0.000 |

### Interprétation

Les p-values des tests de Shapiro-Wilk et Kolmogorov-Smirnov sont inférieures à 5 %.
On rejette donc l’hypothèse de normalité des résidus.

Cela signifie que les erreurs du modèle ne suivent pas parfaitement une loi normale.

Ce point n’empêche pas nécessairement le modèle de prédire correctement, mais il limite la fiabilité de certaines conclusions statistiques comme les intervalles de confiance ou les tests sur les coefficients.

---

## 🔄 Autocorrélation des résidus

Le test de Durbin-Watson donne :

**Statistique : 2.114**

### Interprétation

Une valeur proche de 2 indique une absence d’autocorrélation significative des résidus.

C’est un résultat positif : les erreurs du modèle semblent indépendantes les unes des autres.

Cela renforce la validité du modèle sur ce point.

---

## ⚖️ Moyenne des erreurs

La moyenne des résidus est :

**-2.84e-14**

### Interprétation

Cette valeur est pratiquement égale à zéro.

Cela signifie que le modèle ne présente pas de biais moyen important : globalement, il ne surestime ni ne sous-estime systématiquement les prix.

---

## 🧠 Conclusion professionnelle

Ce projet met en œuvre une démarche complète de régression linéaire appliquée à la prédiction des prix immobiliers.

Le modèle complet offre une performance correcte avec un R² test d’environ **0.67** et un RMSE test d’environ **4.93**. Les principales variables explicatives sont le nombre de pièces, le niveau socio-économique du quartier, le taux de criminalité, la pollution, l’accessibilité et la fiscalité locale.

L’analyse statistique montre toutefois certaines limites : présence de multicolinéarité, hétéroscédasticité et non-normalité des résidus. Ces éléments indiquent que le modèle linéaire est utile comme première approche interprétable, mais qu’il pourrait être amélioré par des méthodes plus robustes.

Des pistes d’amélioration pertinentes seraient :

* Régression Ridge pour traiter la multicolinéarité ;
* Régression Lasso pour sélectionner automatiquement les variables ;
* transformation logarithmique de la variable cible ;
* modèles non linéaires comme Random Forest ou Gradient Boosting ;
* validation croisée pour une estimation plus robuste des performances.

Ce projet montre une capacité à aller au-delà du simple entraînement d’un modèle, en combinant analyse exploratoire, modélisation, validation statistique et interprétation métier.
