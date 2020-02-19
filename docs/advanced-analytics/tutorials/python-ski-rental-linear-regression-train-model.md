---
title: "Tutoriel Python : Effectuer l'apprentissage du modèle"
description: Dans la troisième partie de cette série de didacticiels en quatre parties, vous allez former un modèle de régression en Python afin de prédire les locations de ski dans SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/20/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c564ac26c5706e67d9a633a05f81cb48d00fb771
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75681760"
---
# <a name="python-tutorial-train-a-linear-regression-model-in-sql-server-machine-learning-services"></a>Tutoriel Python : Effectuer l’apprentissage d’un modèle de régression linéaire dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans la troisième partie de cette série de tutoriels qui en compte quatre, vous allez effectuer l’apprentissage d’un modèle de régression linéaire dans Python. Dans la partie suivante de cette série, vous déploierez ce modèle dans une base de données SQL Server avec Machine Learning Services.

Dans cet article, vous allez apprendre à :

> [!div class="checklist"]
> * Effectuer l’apprentissage d’un modèle de régression linéaire
> * Élaborer des prédictions à l’aide d’un modèle de régression linéaire

Dans la [première partie](python-ski-rental-linear-regression.md), vous avez appris à restaurer l’exemple de base de données.

Dans la [deuxième partie](python-ski-rental-linear-regression-prepare-data.md), vous avez appris à charger les données de SQL Server dans une trame de données Python et à préparer les données dans Python.

Dans la [quatrième partie](python-ski-rental-linear-regression-deploy-model.md), vous apprendrez à stocker le modèle dans SQL Server, puis à créer des procédures stockées à partir des scripts Python que vous avez développés dans les parties 2 et 3. Les procédures stockées sont exécutées dans SQL Server pour effectuer des prédictions en fonction de nouvelles données.

## <a name="prerequisites"></a>Conditions préalables requises

* La troisième partie de ce tutoriel suppose que vous avez terminé la [première partie](python-ski-rental-linear-regression.md) et ses conditions préalables.

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

Afin d’élaborer des prédictions, vous devez rechercher une fonction (modèle) qui décrit le mieux la dépendance entre les variables de notre jeu de données. En d’autres termes, il s’agit d’effectuer l’apprentissage du modèle. Le jeu de données d’apprentissage est un sous-ensemble du jeu de données complet de la trame de données pandas **df** que vous avez créée dans la deuxième partie de cette série.

Vous allez effectuer l’apprentissage du modèle **lin_model** à l’aide d’un algorithme de régression linéaire.

```python
# Store the variable we'll be predicting on.
target = "Rentalcount"

# Generate the training set.  Set random_state to be able to replicate results.
train = df.sample(frac=0.8, random_state=1)

# Select anything not in the training set and put it in the testing set.
test = df.loc[~df.index.isin(train.index)]

# Print the shapes of both sets.
print("Training set shape:", train.shape)
print("Testing set shape:", test.shape)

# Initialize the model class.
lin_model = LinearRegression()

# Fit the model to the training data.
lin_model.fit(train[columns], train[target])
```

Vous devez obtenir des résultats similaires à ce qui suit :

```results
Training set shape: (362, 7)
Testing set shape: (91, 7)
```

## <a name="make-predictions"></a>Effectuer des prédictions

Utilisez une fonction Predict pour prédire le nombre de loyers à l’aide du modèle **lin_model**.

```python
# Generate our predictions for the test set.
lin_predictions = lin_model.predict(test[columns])
print("Predictions:", lin_predictions)
# Compute error between our test predictions and the actual values.
lin_mse = mean_squared_error(lin_predictions, test[target])
print("Computed error:", lin_mse)
```

Vous devez obtenir des résultats similaires à ce qui suit :

```results
Predictions: [ 40.  38. 240.  39. 514.  48. 297.  25. 507.  24.  30.  54.  40.  26.
  30.  34.  42. 390. 336.  37.  22.  35.  55. 350. 252. 370. 499.  48.
  37. 494.  46.  25. 312. 390.  35.  35. 421.  39. 176.  21.  33. 452.
  34.  28.  37. 260.  49. 577. 312.  24.  24. 390.  34.  64.  26.  32.
  33. 358. 348.  25.  35.  48.  39.  44.  58.  24. 350. 651.  38. 468.
  26.  42. 310. 709. 155.  26. 648. 617.  26. 846. 729.  44. 432.  25.
  39.  28. 325.  46.  36.  50.  63.]
Computed error: 2.9960763804270902e-27
```

## <a name="next-steps"></a>Étapes suivantes

Dans la troisième partie de cette série de tutoriels, vous avez effectué les étapes suivantes :

* Effectuer l’apprentissage d’un modèle de régression linéaire
* Élaborer des prédictions à l’aide d’un modèle de régression linéaire

Pour déployer le modèle de Machine Learning que vous avez créé, suivez la quatrième partie de cette série de tutoriels :

> [!div class="nextstepaction"]
> [Tutoriel Python : Déployer un modèle Machine Learning](python-ski-rental-linear-regression-deploy-model.md)