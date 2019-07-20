---
title: Didacticiel sur le calcul des statistiques de synthèse RevoScaleR
description: Didacticiel procédure pas à pas sur la façon de calculer les statistiques de synthèse statistique à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 5f90cc0e6101e168e15ed7c1145d286f799375ac
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344706"
---
# <a name="compute-summary-statistics-in-r-sql-server-and-revoscaler-tutorial"></a>Calculer les statistiques de synthèse dans R (didacticiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie du [didacticiel RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Il utilise les sources de données et les contextes de calcul établis dans les leçons précédentes pour exécuter les scripts R de haute performance dans celui-ci. Dans cette leçon, vous allez utiliser des contextes de calcul de serveurs locaux et distants pour les tâches suivantes:

> [!div class="checklist"]
> * Basculer le contexte de calcul sur SQL Server
> * Obtenir des statistiques récapitulatives sur des objets de données distants
> * Calculer un résumé local

Si vous avez effectué les leçons précédentes, vous devez disposer de contextes de calcul distants: sqlCompute et sqlComputeTrace. En avançant, vous utilisez sqlCompute et le contexte de calcul local dans les leçons suivantes.

Utilisez un IDE R ou une interface **RGUI** pour exécuter le script r dans cette leçon.

## <a name="compute-summary-statistics-on-remote-data"></a>Calculer les statistiques de synthèse sur les données distantes

Avant de pouvoir exécuter n’importe quel code R à distance, vous devez spécifier le contexte de calcul distant. Tous les calculs suivants ont lieu sur l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur spécifié dans le paramètre *sqlCompute* .

Un contexte de calcul reste actif jusqu’à ce que vous le modifiiez. Toutefois, tous les scripts R qui *ne peuvent pas* s’exécuter dans un contexte de serveur distant s’exécutent automatiquement localement.

Pour voir comment fonctionne un contexte de calcul, générez des statistiques récapitulatives sur la source de données sqlFraudDS sur le SQL Server distant. Cet objet de source de données a été créé dans la [leçon deux](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md) et représente la table ccFraudSmall dans la base de données RevoDeepDive. 

1. Basculez le contexte de calcul sur sqlCompute créé dans la leçon précédente:
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```

2. Appelez la fonction [rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) et transmettez les arguments requis, tels que la formule et la source de données, et assignez `sumOut`les résultats à la variable.
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    Le langage R fournit de nombreuses fonctions de synthèse, mais **rxSummary** dans **RevoScaleR** prend en charge l’exécution sur différents contextes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de calcul distants, y compris. Pour plus d’informations sur les fonctions similaires, consultez synthèses de [données à l’aide de RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).
  
3. Imprimez le contenu de sumOut sur la console.
  
    ```R
    sumOut
    ```
    > [!NOTE]
    > Si vous recevez une erreur, attendez quelques minutes que l’exécution se termine avant de réessayer la commande.

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
  
2. Lorsque vous extrayez des données de SQL Server, vous pouvez souvent obtenir de meilleures performances en augmentant le nombre de lignes extraites pour chaque lecture, en supposant que la taille de bloc accrue peut être prise en charge dans la mémoire. Exécutez la commande suivante pour augmenter la valeur du paramètre *rowsPerRead* sur la source de données. Auparavant, la valeur de *rowsPerRead* était 5000.
  
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

4. Revenez au contexte de calcul distant pour les prochaines leçons.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Visualiser des données SQL Server à l’aide de R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)