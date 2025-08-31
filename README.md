# Optimisation de la chaîne de production d’ammoniac

## 📌 Contexte du projet
Ce projet a été réalisé dans le cadre d’un stage au sein du laboratoire **LIMSET**.  
L’objectif principal était **d’optimiser la chaîne de production d’ammoniac** afin de produire **4 tonnes/jour** tout en **réduisant la consommation énergétique**.

## 🎯 Objectifs
- Étudier le procédé de production d’ammoniac (Reformage, Water-Gas Shift, élimination du CO₂, et Haber-Bosch).  
- Développer et entraîner des modèles de **Machine Learning** capables de prédire l’énergie consommée et la production d’ammoniac(Ces modèles sont ensuite intégrés dans la fonction de fitness).  
- Intégrer ces modèles dans un **Algorithme Génétique** pour optimiser les paramètres de fonctionnement.  
- Réduire la consommation énergétique tout en maintenant les contraintes de production et d’émissions de CO₂.

## 🏭 La chaîne de production
Le procédé étudié comporte 4 étapes principales :
1. **Reformeur** → transformation du gaz naturel en H₂ et CO.  
2. **Water-Gas Shift** → conversion du CO en CO₂ et H₂.  
3. **Élimination du CO₂ & méthanation** → purification du H₂.  
4. **Haber-Bosch** → synthèse de l’ammoniac à partir de N₂ et H₂.  

## 🧠 Approche Machine Learning
- Prétraitement des données.
- Sélection des meilleurs prédicteurs pour chaque étape.  
- Entraînement de modèles:
    - **Étapes complexes** : lorsque la relation entre les variables n’était pas évidente, nous avons entraîné des modèles de **Machine Learning**
    - **Étapes simples / données bien distribuées** : dans certains cas, la relation entre entrée et sortie était déjà **quasi-linéaire** ou **suffisamment régulière**.  
  Au lieu d’entraîner un modèle complexe, nous avons choisi **d’interpoler la fonction de la distribution**   
- Sauvegarde des pipelines avec **Joblib** pour une réutilisation facile.  

## 🧬 Algorithme Génétique
1. **Population initiale** : les 100 meilleurs individus issus de nos données initiales.  
2. **Évaluation (Fitness)** : chaque individu est évalué en fonction de la consommation énergétique, de la masse d’ammoniac produite et des émissions de CO₂.  
3. **Sélection des élites** : les **20 meilleures solutions** (celles qui respectent les contraintes et consomment le moins d’énergie) sont retenues.  
4. **Mutation et Croisement** :  
   - **Croisement (Crossover)** : deux "parents" (solutions) sont choisis parmi les élites, puis certaines de leurs valeurs sont échangées pour créer de nouveaux "enfants".  
   - **Mutation** : certaines valeurs des prédicteurs (variables comme température, pression, etc.) sont modifiées aléatoirement à l’intérieur de leurs plages valides, afin d’explorer de nouvelles possibilités.  

Grâce à ce mécanisme :  
- Le **croisement** combine des solutions prometteuses pour générer de nouvelles configurations.  
- La **mutation** évite de rester bloqué dans une solution locale en introduisant de la diversité.  

5. **Répétition** : le processus est répété sur plusieurs générations (500 itérations) jusqu’à obtenir une population optimisée.  

## 🚀 Résultats & Impact
- Réduction significative des coûts énergétiques.   
- Validation des résultats avec **Aspen HYSYS**.  
- Exemple concret de l’apport de l’IA et de l’optimisation dans l’industrie chimique.

