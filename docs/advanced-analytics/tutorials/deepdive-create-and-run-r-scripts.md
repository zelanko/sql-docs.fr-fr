---
title: 'Calculer des statistiques récapitulatives RevoScaleR didacticiel : SQL Server Machine Learning'
description: Didacticiel pas à pas sur la façon de calculer des statistiques de résumé statistiques à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 883a4afa68571c18e6dcaffe96d12644f611f99a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641338"
---
# <a name="compute-summary-statistics-in-r-sql-server-and-revoscaler-tutorial"></a>Calcul des statistiques de synthèse dans R (didacticiel sur SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie de la [RevoScaleR didacticiel](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Elle utilise les sources de données établie et les contextes de calcul créés dans les leçons précédentes pour exécuter des scripts R hautes performances dans celui-ci. Dans cette leçon, vous allez utiliser des contextes de calcul des serveurs locaux et distants pour les tâches suivantes :

> [!div class="checklist"]
> * Basculer le contexte de calcul vers SQL Server
> * Obtenir des statistiques de synthèse sur les objets de données distante
> * Calcul d’un résumé local

Si vous avez terminé les leçons précédentes, vous devez avoir les contextes de calcul à distance : sqlCompute et sqlComputeTrace. Avance pas, que vous utilisez seront sqlCompute et local contexte de calcul dans les leçons suivantes.

Utiliser un IDE R ou **Rgui** pour exécuter le script R dans cette leçon.

## <a name="compute-summary-statistics-on-remote-data"></a>Calcul des statistiques de synthèse sur les données à distance

Avant de pouvoir exécuter tout code R à distance, vous devez spécifier le contexte de calcul distant. Tous les calculs suivants ont lieu le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur spécifié dans le *sqlCompute* paramètre.

Un contexte de calcul reste actif jusqu'à ce que vous le changiez. Toutefois, tout script R qui *ne peut pas* s’exécutent dans un contexte de serveur distant va automatiquement s’exécuter localement.

Pour voir comment un contexte de calcul fonctionne, générer des statistiques de synthèse sur la source de données sqlFraudDS sur le serveur SQL distant. Cet objet de source de données a été créé dans [leçon deux](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md) et représente la table ccFraudSmall dans la base de données RevoDeepDive. 

1. Basculer le contexte de calcul vers sqlCompute créé dans la leçon précédente :
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```

2. Appelez le [rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) de fonction et passez les arguments nécessaires, tels que la formule et la source de données et attribuez les résultats à la variable `sumOut`.
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    Le langage R fournit de nombreuses fonctions de résumé, mais **rxSummary** dans **RevoScaleR** prend en charge de l’exécution sur les différents contextes de calcul à distance, y compris [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur les fonctions similaires, consultez [des résumés de données à l’aide de RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).
  
3. Imprimer le contenu de sumOut à la console.
  
    ```R
    sumOut
    ```
    > [!NOTE]
    > Si vous obtenez une erreur, patientez quelques minutes pour l’exécution se termine avant de réessayer la commande.

**Résultats**

```R
Summary Statistics Results for: ~gender + balance + numTrans + numIntlTrans + creditLine
Data: sqlFraudDS (RxSqlServerData Data Source)
Number of valid observations: 10000

 Name  Mean    StdDev  Min Max ValidObs    MissingObs
 balance       4075.0318 3926.558714            0   25626 100000
 numTrans        29.1061   26.619923 0     100 10000    0           100000
 numIntlTrans     4.0868    8.726757 0      60 10000    0           100000
 creditLine       9.1856    9.870364 1      75 10000    0          100000
 
 Category Counts for gender
 Number of categories: 2
 Number of valid observations: 10000
 Number of missing observations: 0

 gender Counts
  Male   6154
  Female 3846
```

## <a name="create-a-local-summary"></a>Créer un résumé local

1. Modifiez le contexte de calcul pour effectuer tout votre travail localement.
  
    ```R
    rxSetComputeContext ("local")
    ```
  
2. Lors de l’extraction des données à partir de SQL Server, vous pouvez souvent obtenir de meilleures performances en augmentant le nombre de lignes extraites pour chaque lecture, en supposant que la taille de bloc accrue pouvant être utilisée dans la mémoire. Exécutez la commande suivante pour augmenter la valeur pour le *rowsPerRead* paramètre sur la source de données. Auparavant, la valeur de *rowsPerRead* était 5000.
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```

3. Appelez **rxSummary** sur la nouvelle source de données.
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
   Les résultats doivent être les mêmes que lorsque vous exécutez **rxSummary** dans le contexte de l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Toutefois, l’opération peut être plus rapide ou plus lente. Cela dépend en grande partie de votre connexion à la base de données, car les données sont transférées vers votre ordinateur local pour analyse.

4. Contexte de calcul pour les leçons suivantes plusieurs revenez à l’instance distante.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Visualiser des données SQL Server à l’aide de R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)