---
title: Statistiques de synthèse dans RevoScaleR
description: 'Tutoriel RevoScaleR 5 : Comment calculer des données statistiques de synthèse à l’aide du langage R sur SQL Server.'
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3d8b04d384d7ee5f846197ff3465b9c0914ca94c
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92196313"
---
# <a name="compute-summary-statistics-in-r-sql-server-and-revoscaler-tutorial"></a>Calculer des statistiques de synthèse dans R (tutoriel SQL Server et RevoScaleR)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Il s’agit du tutoriel 5 de la [série de tutoriels RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) qui traite de l’utilisation des [fonctions RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Ce tutoriel utilise les sources de données et les contextes de calcul établis dans les tutoriels précédents pour exécuter des scripts R hautes performances. Dans ce tutoriel, vous utiliserez des contextes de calcul de serveurs locaux et distants pour les tâches suivantes :

> [!div class="checklist"]
> * Définir le contexte de calcul sur SQL Server
> * Obtenir des statistiques de synthèse sur des objets de données distantes
> * Calculer un résumé local

Si vous avez terminé les tutoriels précédents, vous devez disposer des contextes de calcul distants suivants : sqlCompute et sqlComputeTrace. Ensuite, vous utiliserez sqlCompute et le contexte de calcul local dans les tutoriels suivants.

Utilisez un IDE R ou **Rgui** pour exécuter le script R dans ce tutoriel.

## <a name="compute-summary-statistics-on-remote-data"></a>Obtenir des statistiques de synthèse sur des données distantes

Avant de pouvoir exécuter du code R à distance, vous devez spécifier le contexte de calcul distant. Tous les calculs suivants sont effectués sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifié dans le paramètre *sqlCompute*.

Un contexte de calcul reste actif jusqu’à ce que vous le changiez. Cependant, tout script R qui *ne peut pas* être exécuté dans un contexte de serveur distant sera automatiquement exécuté en local.

Pour voir le fonctionnement d’un contexte de calcul, générez des statistiques de synthèse sur la source de données sqlFraudDS sur le serveur distant SQL Server. Cet objet de source de données a été créé au cours du [tutoriel deux](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md) et représente la table ccFraudSmall dans la base de données RevoDeepDive. 

1. Basculez sur le contexte de calcul sqlCompute créé dans le tutoriel précédent :
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```

2. Appelez la fonction [rxSummary](/machine-learning-server/r-reference/revoscaler/rxsummary) et passez les arguments nécessaires, tels que la formule et la source de données, puis attribuez les résultats à la variable `sumOut`.
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    Le langage R fournit de nombreuses fonctions de synthèse, mais **rxSummary** dans **RevoScaleR** prend en charge l’exécution sur les différents contextes de calcul distants, y compris [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour en savoir plus sur les fonctions similaires, consultez [Data summaries using RevoScaleR](/machine-learning-server/r/how-to-revoscaler-data-summaries) (Synthèses de données utilisant RevoScaleR).
  
3. Imprimez le contenu de sumOut sur la console.
  
    ```R
    sumOut
    ```
    > [!NOTE]
    > Si vous recevez une erreur, attendez quelques minutes que l’exécution se termine, puis réessayez d’exécuter la commande.

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
  
2. Lorsque vous extrayez des données de SQL Server, vous pouvez souvent obtenir de meilleures performances en augmentant le nombre de lignes extraites pour chaque lecture, à condition que la mémoire puisse s’adapter à la taille de bloc plus importante. Exécuter la commande suivante pour augmenter la valeur du paramètre *rowsPerRead* de la source de données. Auparavant, la valeur de *rowsPerRead* était 5000.
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```

3. Appelez **rxSummary** dans la nouvelle source de données.
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
   Les résultats doivent être les mêmes que lorsque vous exécutez **rxSummary** dans le contexte de l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Toutefois, l’opération peut être plus rapide ou plus lente. Cela dépend en grande partie de votre connexion à la base de données, car les données sont transférées vers votre ordinateur local pour analyse.

4. Revenez au contexte de calcul distant pour les prochains tutoriels.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Visualiser des données SQL Server à l’aide de R](../../machine-learning/tutorials/deepdive-visualize-sql-server-data-using-r.md)