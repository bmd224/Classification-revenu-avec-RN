# Classification de Revenus avec Réseaux de Neurones (MLP)
On prédit le revenu de clients à partir d’un dataset démographique et transactionnel.  
Deux modèles sont comparés : **classification binaire** et **classification multi-classes**.
---
## Objectifs
- Prétraiter les données (imputation, outliers, encodage, standardisation)  
- Entraîner des réseaux de neurones (MLP)  
- Comparer binaire vs multi-classes  
- Optimiser les hyperparamètres  
- Évaluer les performances (validation croisée, courbes d’apprentissage)  
---
## Dataset : Customer.csv  
**Variables cibles créées :**
- **Binaire :** revenu > moyenne ou ≤ moyenne    
- **Multi-classes :** bas / moyen / élevé via quartiles  
## Méthode
### Prétraitement
- Conversion numérique  
- Imputation (médiane)  
- IQR pour outliers  
- One-Hot Encoding  
- Standardisation  
- Train/test : 80/20  
### Classification binaire  
Prédire si un client génère un revenu supérieur ou inférieur à la moyenne  
#### Architecture :  
- MLP avec 2 couches cachées (50, 50 neurones)  
- Fonction d'activation : ReLU  
- Solver : Stochastic Gradient Descent (**sgd**)  
- Batch size : 250
#### Démarche :  
- Échantillonnage stratifié (2000 observations)  
- Validation croisée à 3 plis  
- Analyse de la courbe d'apprentissage  
- Optimisation des hyperparamètres    
- Évaluation finale sur les données de test
#### Hyperparamètres optimisés :  
- Architecture des couches cachées  
- Nombre d'itérations (max_iter)  
- Taux d'apprentissage (learning_rate)  
- Fonction d'activation (tanh vs relu)  
- Solver (sgd vs adam)  
### Classification multi-classes  
Catégoriser les clients en 3 niveaux de revenus  
#### Discrétisation par quartiles :  
- Revenus bas : ≤ Q1 (25e percentile)  
- Revenus moyens : Q1 < x ≤ Q3  
- Revenus élevés : > Q3 (75e percentile)  
#### Architecture adaptée :  
- MLP avec 1 couche cachée (50 neurones)  
- Fonction de sortie : Softmax (implicite pour multi-classes)   
- Mêmes hyperparamètres de base que le binaire  
#### Démarche similaire :  
- Validation croisée  
- Courbe d'apprentissage  
- Optimisation des hyperparamètres  
- Test  
---
