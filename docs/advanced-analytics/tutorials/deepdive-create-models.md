---
title: Créer des modèles R avec RevoScaleR
description: Tutoriel pas à pas sur la création d’un modèle à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9a23691e8ed4b5ec5290ae666455f789954fa95d
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727271"
---
# <a name="create-r-models-sql-server-and-revoscaler-tutorial"></a>Créer des modèles R (tutoriel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette leçon fait partie du [didacticiel RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation des fonctions [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Vous avez enrichi les données de formation. Il est maintenant temps d’analyser les données à l’aide de la modélisation de régression. Les modèles linéaires sont un outil important dans le monde de l’analyse prédictive. Le package **RevoScaleR** comprend des algorithmes de régression qui peuvent subdiviser la charge de travail et l’exécuter en parallèle.

> [!div class="checklist"]
> * Créer un modèle de régression linéaire
> * Créer un modèle de régression logistique

## <a name="create-a-linear-regression-model"></a>Créer un modèle de régression linéaire

Lors de cette étape, vous allez créer un modèle linéaire simple qui estime le solde de carte de crédit des clients, en utilisant comme variables indépendantes les valeurs des colonnes *gender* et *creditLine*.
  
Pour cela, vous utilisez la fonction [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod), qui prend en charge les contextes de calcul distants.
  
1. Créez une variable R pour stocker le modèle terminé et appelez **rxLinMod** en transmettant une formule appropriée.
  
    ```R
    linModObj <- rxLinMod(balance ~ gender + creditLine,  data = sqlFraudDS)
    ```
  
2. Pour afficher une synthèse des résultats, appelez la fonction **summary** standard de R sur l’objet de modèle.
  
     ```R
     summary(linModObj)
     ```

Il peut vous paraître étrange qu’une simple fonction R comme **summary** fonctionne ici, puisque dans l’étape précédente, vous avez défini le contexte de calcul sur le serveur. Toutefois, même lorsque la fonction **rxLinMod** utilise le contexte de calcul à distance pour créer le modèle, il retourne également un objet qui contient le modèle pour votre station de travail locale et le stocke dans le répertoire partagé.

Par conséquent, vous pouvez exécuter des commandes R standard sur le modèle comme s’il avait été créé en utilisant le contexte « local ».

**Résultats**

```R
Linear Regression Results for: balance ~ gender + creditLineData: sqlFraudDS (RxSqlServerData Data Source)
Dependent variable(s): balance
Total independent variables: 4 (Including number dropped: 1)
Number of valid observations: 10000
Number of missing observations: 0
Coefficients: (1 not defined because of singularities)

Estimate Std. Error t value Pr(>|t|) (Intercept)
3253.575 71.194 45.700 2.22e-16
gender=Male -88.813 78.360 -1.133 0.257
gender=Female Dropped Dropped Dropped Dropped
creditLine 95.379 3.862 24.694 2.22e-16
Signif. codes: 0  0.001  0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 3812 on 9997 degrees of freedom
Multiple R-squared: 0.05765
Adjusted R-squared: 0.05746
F-statistic: 305.8 on 2 and 9997 DF, p-value: < 2.2e-16
Condition number: 1.0184
```

## <a name="create-a-logistic-regression-model"></a>Créer un modèle de régression logistique

Créez ensuite un modèle de régression logistique qui indique si un client particulier présente un risque de fraude. Vous utilisez la fonction **RevoScaleR** [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit), qui prend en charge l’ajustement des modèles de régression logistique dans des contextes de calcul distants.

Conservez le contexte de calcul tel quel. Vous continuez aussi à utiliser la même source de données.

1. Appelez la fonction **rxLogit** , puis passez la formule nécessaire pour définir le modèle.

    ```R
    logitObj <- rxLogit(fraudRisk ~ state + gender + cardholder + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS, dropFirst = TRUE)
    ```
  
    Comme il s’agit d’un modèle de grande taille, contenant 60 variables indépendantes, y compris les trois variables factices qui sont supprimées, vous devrez peut-être attendre que le contexte de calcul retourne l’objet.
    
    La raison pour laquelle la taille du modèle est si importante est que, dans R (et dans le package **RevoScaleR** ), chaque niveau d’une variable de facteur de catégorie est automatiquement traité comme une variable factice distincte.
  
2. Pour afficher un résumé du modèle retourné, appelez la fonction R **summary** .
  
    ```R
    summary(logitObj)
    ```
  
**Résultats partiels**

```R
Logistic Regression Results for: fraudRisk ~ state + gender + cardholder + balance + numTrans + numIntlTrans + creditLine
Data: sqlFraudDS (RxSqlServerData Data Source)
Dependent variable(s): fraudRisk
Total independent variables: 60 (Including number dropped: 3)
Number of valid observations: 10000 -2

LogLikelihood: 2032.8699 (Residual deviance on 9943 degrees of freedom)

Coefficients:
Estimate Std. Error z value Pr(>|z|)     (Intercept)
-8.627e+00  1.319e+00  -6.538 6.22e-11
state=AK                Dropped    Dropped Dropped  Dropped
state=AL             -1.043e+00  1.383e+00  -0.754   0.4511

(other states omitted)

gender=Male             Dropped    Dropped Dropped  Dropped
gender=Female         7.226e-01  1.217e-01   5.936 2.92e-09
cardholder=Principal    Dropped    Dropped Dropped  Dropped
cardholder=Secondary  5.635e-01  3.403e-01   1.656   0.0977
balance               3.962e-04  1.564e-05  25.335 2.22e-16
numTrans              4.950e-02  2.202e-03  22.477 2.22e-16
numIntlTrans          3.414e-02  5.318e-03   6.420 1.36e-10
creditLine            1.042e-01  4.705e-03  22.153 2.22e-16

Signif. codes:  0 '\*\*\*' 0.001 '\*\*' 0.01 '\*' 0.05 '.' 0.1 ' ' 1
Condition number of final variance-covariance matrix: 3997.308
Number of iterations: 15
```

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Affecter un score à de nouvelles données](../../advanced-analytics/tutorials/deepdive-score-new-data.md)