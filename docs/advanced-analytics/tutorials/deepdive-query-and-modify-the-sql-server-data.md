---
title: Interroger et modifier les données de SQL Server à l’aide de RevoScaleR
description: Didacticiel procédure pas à pas sur la façon d’interroger et de modifier des données à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 3fb28d287c7b92e9b399aa7bc0bb606c618eed47
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469796"
---
# <a name="query-and-modify-the-sql-server-data-sql-server-and-revoscaler-tutorial"></a>Interroger et modifier les données de SQL Server (didacticiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette leçon fait partie du [didacticiel RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans la leçon précédente, vous avez chargé les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dans. Dans cette étape, vous pouvez explorer et modifier des données à l’aide de **RevoScaleR**:

> [!div class="checklist"]
> * Retourner des informations de base sur les variables
> * Créer des données catégoriques à partir de données brutes

Les données catégoriques, ou *variables de facteur*, sont utiles pour les visualisations de données exploratoires. Vous pouvez les utiliser en tant qu’entrées dans des histogrammes pour avoir une idée de l’apparence des données de variables.

## <a name="query-for-columns-and-types"></a>Requête pour les colonnes et les types

Utilisez un IDE R ou RGui. exe pour exécuter le script R. 

Obtenez d’abord la liste des colonnes et leurs types de données. Vous pouvez utiliser la fonction [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) et spécifier la source de données que vous souhaitez analyser. Selon votre version de **RevoScaleR**, vous pouvez également utiliser [rxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames). 
  
```R
rxGetVarInfo(data = sqlFraudDS)
```

**Résultats**

```R
Var 1: custID, Type: integer
Var 2: gender, Type: integer
Var 3: state, Type: integer
Var 4: cardholder, Type: integer
Var 5: balance, Type: integer
Var 6: numTrans, Type: integer
Var 7: numIntlTrans, Type: integer
Var 8: creditLine, Type: integer
Var 9: fraudRisk, Type: integer
```

## <a name="create-categorical-data"></a>Créer des données catégoriques

Toutes les variables sont stockées sous forme d’entiers, mais certaines variables représentent des données catégoriques, appelées *variables de facteur* dans R. Par exemple, l' *État* de la colonne contient des nombres utilisés comme identificateurs pour les États 50 plus le district de Columbia. Pour mieux comprendre les données, vous pouvez remplacer les numéros par une liste d’abréviations des noms des états.

Dans cette étape, vous créez un vecteur de chaîne contenant les abréviations, puis mappez ces valeurs catégoriques aux identificateurs entiers d’origine. Ensuite, vous utilisez la nouvelle variable dans l’argument *colInfo* pour spécifier que cette colonne doit être gérée en tant que facteur. Chaque fois que vous analysez les données ou que vous les déplacez, les abréviations sont utilisées et la colonne est traitée comme un facteur.

Le fait de mapper la colonne vers les abréviations avant de l’utiliser comme facteur améliore également les performances. Pour plus d’informations, consultez [R et optimisation des données](../r/r-and-data-optimization-r-services.md).

1. Commencez par créer une variable R, *stateabb que*, et définissez le vecteur de chaînes à ajouter à celle-ci, comme suit.
  
    ```R
    stateAbb <- c("AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC",
        "DE", "FL", "GA", "HI","IA", "ID", "IL", "IN", "KS", "KY", "LA",
        "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NB", "NC", "ND",
        "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI","SC",
        "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY")
    ```

2. Ensuite, créez un objet d’informations de colonne, nommé *ccColInfo*, qui spécifie le mappage des valeurs entières existantes aux niveaux des catégories (les abréviations du nom des états).
  
    Cette instruction crée également des variables de facteur pour gender et cardholder.
  
    ```R
    ccColInfo <- list(
    gender = list(
              type = "factor",
              levels = c("1", "2"),
              newLevels = c("Male", "Female")
              ),
    cardholder = list(
                  type = "factor",
                  levels = c("1", "2"),
                  newLevels = c("Principal", "Secondary")
                   ),
    state = list(
             type = "factor",
             levels = as.character(1:51),
             newLevels = stateAbb
             ),
    balance = list(type = "numeric")
    )
    ```
  
3. Pour créer la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source de données qui utilise les données mises à jour, appelez la fonction **RxSqlServerData** comme avant, mais ajoutez l’argument *colInfo* .
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
    table = sqlFraudTable, colInfo = ccColInfo,
    rowsPerRead = sqlRowsPerRead)
    ```
  
    - Pour le paramètre *table* , passez la variable *sqlFraudTable*qui contient la source de données que vous avez créée.
    - Pour le paramètre *colInfo* , passez la variable *ccColInfo* , qui contient les types de données de colonne et les niveaux de facteur.

4.  Vous pouvez maintenant utiliser la fonction **rxGetVarInfo** pour demander des informations sur les variables dans la nouvelle source de données.
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **Résultats**
    
    ```R
    Var 1: custID, Type: integer
    Var 2: gender  2 factor levels: Male Female
    Var 3: state   51 factor levels: AK AL AR AZ CA ... VT WA WI WV WY
    Var 4: cardholder  2 factor levels: Principal Secondary
    Var 5: balance, Type: integer
    Var 6: numTrans, Type: integer
    Var 7: numIntlTrans, Type: integer
    Var 8: creditLine, Type: integer
    Var 9: fraudRisk, Type: integer
    ```

Les trois variables que vous avez spécifiées (*gender*, *state*et *cardholder*) sont maintenant traitées comme des facteurs.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Définir et utiliser des contextes de calcul](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)