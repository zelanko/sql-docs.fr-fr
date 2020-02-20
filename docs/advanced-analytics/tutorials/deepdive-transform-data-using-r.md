---
title: Transformer des données à l’aide de RevoScaleR
description: 'Tutoriel RevoScaleR 9 : Comment transformer des données à l’aide du langage R sur SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3e8c28548ba4fa5f5ad661e3b7b0872ad166b812
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "74947183"
---
# <a name="transform-data-using-r-sql-server-and-revoscaler-tutorial"></a>Transformer des données à l’aide de R (didacticiel sur SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Il s’agit du tutoriel 9 de la [série de tutoriels RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) qui traite de l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans ce tutoriel, vous allez découvrir les fonctions **RevoScaleR** pour transformer des données à différents stades de votre analyse.

> [!div class="checklist"]
> * Utilisez **rxDataStep** pour créer et transformer un sous-ensemble de données
> * Utilisez **rxImport** pour transformer des données en transit vers ou à partir d’un fichier XDF ou d’une trame de données en mémoire pendant l’importation

Bien qu’elles ne soient pas spécifiquement conçues pour le déplacement des données, les fonctions **rxSummary**, **rxCube**, **rxLinMod**et **rxLogit** prennent toutes en charge les transformations de données à la volée.

## <a name="use-rxdatastep-to-transform-variables"></a>Utiliser rxDataStep pour transformer des variables

La fonction [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) traite les données segment par segment, en lisant à partir d’une source de données et en écrivant dans une autre. Vous pouvez spécifier les colonnes à transformer, les transformations à charger, etc.

Pour rendre cet exemple intéressant, utilisez une fonction d’un autre package R pour transformer les données. Le package **boot** est un des packages « recommandés » ; en d’autres termes, **boot** est inclus avec chaque distribution de R, mais n’est pas chargé automatiquement au démarrage. Ainsi, le package doit déjà être disponible sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurée pour l’intégration de R.

À partir du package de **démarrage**, utilisez la fonction **inv.logit** pour calculer l’inverse d’un logit. Autrement dit, la fonction **inv.logit** convertit un logit en une probabilité sur l’échelle [0,1].

> [!TIP] 
> Une autre façon d’obtenir des prédictions dans cette échelle consiste à définir le paramètre *type* sur **response** dans l’appel initial à **rxPredict**.

1. Commencez par créer une source de données qui contiendra les données destinées à la table, `ccScoreOutput`.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. Ajoutez une autre source de données qui contiendra les données de la table `ccScoreOutput2`.
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    Dans la nouvelle table, stockez toutes les variables de la table `ccScoreOutput` précédente, ainsi que la variable nouvellement créée.
  
3. Définissez le contexte de calcul sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Utilisez la fonction **rxSqlServerTableExists** pour vérifier si la table de sortie `ccScoreOutput2` existe déjà, et si tel est le cas, utilisez la fonction **rxSqlServerDropTable** pour supprimer la table.
  
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

    Quand vous définissez les transformations qui sont appliquées à chaque colonne, vous pouvez également spécifier les packages R supplémentaires qui sont nécessaires pour effectuer les transformations.  Pour plus d’informations sur les types de transformations que vous pouvez effectuer, consultez [How to transform and subset data using RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-transform)(Transformation de données et création de sous-ensembles de données avec RevoScaleR).
  
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

Notez que les variables de facteur ont été écrites dans la table `ccScoreOutput2` en tant que données de type caractère. Pour les utiliser comme facteurs dans les analyses ultérieures, utilisez le paramètre *colInfo* pour spécifier les niveaux.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Charger des données en mémoire à l’aide de rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)