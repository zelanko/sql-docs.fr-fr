---
title: Interroger et modifier les données de SQL Server à l’aide de RevoScaleR - SQL Server Machine Learning
description: Didacticiel pas à pas sur la façon d’interroger et modifier des données à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 6d2768399ecd3d504e5bc51d4c7cbd151488782a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513136"
---
# <a name="query-and-modify-the-sql-server-data-sql-server-and-revoscaler-tutorial"></a>Interroger et modifier les données de SQL Server (didacticiel sur SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie de la [RevoScaleR didacticiel](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans la leçon précédente, vous avez chargé les données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dans cette étape, vous pouvez Explorer et modifier à l’aide des données **RevoScaleR**:

> [!div class="checklist"]
> * Retourner des informations de base sur les variables
> * Créer des données catégoriques à partir des données brutes

Les données catégoriques, ou *variables de facteur*, sont utiles pour les visualisations de données exploratoires. Vous pouvez les utiliser comme entrées dans les histogrammes pour avoir une idée de quelles données de variable ressemblent.

## <a name="query-for-columns-and-types"></a>Requête pour les colonnes et types

Utiliser un IDE R ou dans RGui.exe pour exécuter le script R. 

Obtenez d’abord la liste des colonnes et leurs types de données. Vous pouvez utiliser la fonction [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) et spécifiez la source de données que vous souhaitez analyser. Selon votre version de **RevoScaleR**, vous pouvez également utiliser [rxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames). 
  
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

Toutes les variables sont stockées sous forme d’entiers, mais certaines variables représentent des données catégoriques, appelées *variables de facteur* dans R. Par exemple, la colonne *état* contient des nombres utilisés comme identificateurs pour les 50 états, plus le District de Columbia. Pour mieux comprendre les données, vous pouvez remplacer les numéros par une liste d’abréviations des noms des états.

Dans cette étape, vous créez un vecteur de chaîne qui contient les abréviations, puis mappez ces valeurs de catégorie aux identificateurs entier d’origine. Puis vous utilisez la nouvelle variable dans le *colInfo* argument, pour spécifier que cette colonne doit être gérée comme un facteur. Chaque fois que vous analysez les données ou le déplacer, les abréviations sont utilisées et la colonne est gérée comme un facteur.

Le fait de mapper la colonne vers les abréviations avant de l’utiliser comme facteur améliore également les performances. Pour plus d’informations, consultez [R et les données d’optimisation](../r/r-and-data-optimization-r-services.md).

1. Commencez par créer une variable R, *stateAbb*et définir le vecteur de chaînes à ajouter, comme suit.
  
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
  
3. Pour créer le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source de données qui utilise les données mises à jour, appelez le **RxSqlServerData** fonctionner comme avant, mais ajouter la *colInfo* argument.
  
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