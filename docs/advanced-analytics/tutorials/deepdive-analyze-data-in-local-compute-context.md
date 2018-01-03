---
title: "Analyser les données dans le contexte de calcul local (SQL et R approfondie) | Documents Microsoft"
ms.date: 12/18/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: 787bb526-4a13-40fa-9343-75d3bf5ba6a2
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: e65a4ad3018cfec6b60dae605945a8641b568c5d
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2017
---
# <a name="analyze-data-in-local-compute-context-sql-and-r-deep-dive"></a>Analyser les données dans le contexte de calcul local (SQL et R approfondie)

Cet article fait partie du didacticiel de présentation approfondie de science des données, sur l’utilisation de [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans cette section, vous allez apprendre à basculer vers un contexte de calcul local et déplacer les données entre les contextes pour optimiser les performances.

Bien que i peut être plus rapide d’exécuter du code R complex en utilisant le contexte de serveur, il est parfois plus pratique d’obtenir vos données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et analyser une station de travail local.

## <a name="create-a-local-summary"></a>Créer un résumé local

1. Modifiez le contexte de calcul pour effectuer tout votre travail localement.
  
    ```R
    rxSetComputeContext ("local")
    ```
  
2. Lors de l’extraction de données à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez souvent obtenir de meilleures performances en augmentant le nombre de lignes extraites pour chaque lecture.  Pour ce faire, augmentez la valeur du paramètre *rowsPerRead* sur la source de données. Auparavant, la valeur de *rowsPerRead* était 5000.
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```

3. Appelez **rxSummary** sur la source de données.
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
    Les résultats doivent être les mêmes que lorsque vous exécutez **rxSummary** dans le contexte de l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  Toutefois, l’opération peut être plus rapide ou plus lente. Cela dépend en grande partie de votre connexion à la base de données, car les données sont transférées vers votre ordinateur local pour analyse.

## <a name="next-step"></a>Étape suivante

[Déplacement des données entre SQL Server et le fichier de XDF](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)

## <a name="previous-step"></a>Étape précédente

[Effectuer une analyse de segmentation à l’aide de rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
