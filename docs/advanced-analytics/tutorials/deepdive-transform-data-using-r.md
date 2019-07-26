---
title: Transformer des données à l’aide de RevoScaleR rxDataStep
description: Didacticiel procédure pas à pas sur la façon de transformer des données à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 752202a50222b67af659408c259ce29d9c65d703
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469765"
---
# <a name="transform-data-using-r-sql-server-and-revoscaler-tutorial"></a>Transformer des données à l’aide de R (didacticiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette leçon fait partie du [didacticiel RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans cette leçon, Découvrez les fonctions **RevoScaleR** pour transformer des données à différentes étapes de votre analyse.

> [!div class="checklist"]
> * Utiliser **rxDataStep** pour créer et transformer un sous-ensemble de données
> * Utiliser **rxImport** pour transformer des données en transit vers ou à partir d’un fichier XDF ou d’une trame de données en mémoire pendant l’importation

Bien qu’elles ne soient pas spécifiquement conçues pour le déplacement des données, les fonctions **rxSummary**, **rxCube**, **rxLinMod**et **rxLogit** prennent toutes en charge les transformations de données à la volée.

## <a name="use-rxdatastep-to-transform-variables"></a>Utiliser rxDataStep pour transformer des variables

La fonction [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) traite les données segment par segment, en lisant à partir d’une source de données et en écrivant dans une autre. Vous pouvez spécifier les colonnes à transformer, les transformations à charger, etc.

Pour rendre cet exemple intéressant, nous allons utiliser une fonction d’un autre package R pour transformer les données. Le package **boot** est un des packages « recommandés » ; en d’autres termes, **boot** est inclus avec chaque distribution de R, mais n’est pas chargé automatiquement au démarrage. Par conséquent, le package doit déjà être disponible sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’instance configurée pour l’intégration R.

À partir du package de **démarrage** , utilisez la fonction **inv. logit**, qui calcule l’inverse d’un logit. Autrement dit, la fonction **inv.logit** convertit un logit en une probabilité sur l’échelle [0,1].

> [!TIP] 
> Une autre façon d’obtenir des prédictions dans cette échelle consiste à définir le paramètre *type* sur **response** dans l’appel initial à **rxPredict**.

1. Commencez par créer une source de données qui contiendra les données destinées à la `ccScoreOutput`table,.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. Ajoutez une autre source de données pour stocker les données de `ccScoreOutput2`la table.
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    Dans la nouvelle table, stockez toutes les variables de la `ccScoreOutput` table précédente, ainsi que la variable nouvellement créée.
  
3. Définissez le contexte de calcul sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Utilisez la fonction **rxSqlServerTableExists** pour vérifier si la table `ccScoreOutput2` de sortie existe déjà et, si tel est le cas, utilisez la fonction **rxSqlServerDropTable** pour supprimer la table.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput2"))     rxSqlServerDropTable("ccScoreOutput2")
    ```
  
5. Appelez la fonction **rxDataStep** et spécifiez les transformations de votre choix dans une liste.
  
    ```R
    rxDataStep(inData = sqlOutScoreDS,
        outFile = sqlOutScoreDS2,
        transforms = list(ccFraudProb = inv.logit(ccFraudLogitScore)),
        transformPackages = "boot",
        overwrite = TRUE)
    ```

    Quand vous définissez les transformations qui sont appliquées à chaque colonne, vous pouvez également spécifier les packages R supplémentaires qui sont nécessaires pour effectuer les transformations.  Pour plus d’informations sur les types de transformations que vous pouvez effectuer, consultez [Comment transformer et créer des sous-ensembles de données à l’aide de RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-transform).
  
6. Appelez **rxGetVarInfo** pour afficher un récapitulatif des variables dans le nouveau dataset.
  
```R
rxGetVarInfo(sqlOutScoreDS2)
```

**Résultats**

```R
Var 1: ccFraudLogitScore, Type: numeric
Var 2: state, Type: character
Var 3: gender, Type: character
Var 4: cardholder, Type: character
Var 5: balance, Type: integer
Var 6: numTrans, Type: integer
Var 7: numIntlTrans, Type: integer
Var 8: creditLine, Type: integer
Var 9: ccFraudProb, Type: numeric
```

Les scores de logit d’origine sont conservés, mais une nouvelle colonne, *ccFraudProb*, a été ajoutée. Les scores logit y sont représentés sous forme de valeurs comprises entre 0 et 1.

Notez que les variables de facteur ont été écrites dans la `ccScoreOutput2` table en tant que données caractères. Pour les utiliser comme facteurs dans les analyses ultérieures, utilisez le paramètre *colInfo* pour spécifier les niveaux.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Charger des données en mémoire à l’aide de rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)