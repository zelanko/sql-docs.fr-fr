---
title: "Le&#231;on 4 : Analyser les donn&#233;es dans un contexte de calcul local (Immersion dans la science des donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "10/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 787bb526-4a13-40fa-9343-75d3bf5ba6a2
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Le&#231;on 4 : Analyser les donn&#233;es dans un contexte de calcul local (Immersion dans la science des donn&#233;es)
Bien qu’en règle générale il soit beaucoup plus rapide d’exécuter du code R complexe en utilisant le contexte de serveur, il est parfois plus pratique de récupérer vos données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de les analyser sur votre poste de travail privé.  
  
Dans cette section, vous allez découvrir comment rebasculer vers un contexte de calcul local et déplacer des données entre des contextes pour optimiser les performances.  
  
## Créer un résumé local  
  
1.  Modifiez le contexte de calcul pour effectuer tout votre travail localement.  
  
    ```R  
    rxSetComputeContext ("local")    
    ```  
  
2.  Lors de l’extraction de données à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez souvent obtenir de meilleures performances en augmentant le nombre de lignes extraites pour chaque lecture.  Pour ce faire, augmentez la valeur du paramètre *rowsPerRead* sur la source de données.  
  
    ```R  
    sqlServerDS1 <- RxSqlServerData(  
       connectionString = sqlConnString,        
       table = sqlFraudTable,   
       colInfo = ccColInfo,   
       rowsPerRead = 10000)  
    ```  
  
    Auparavant, la valeur de *rowsPerRead* était 5000.  
  
3.  À présent, appelez *rxSummary* dans la nouvelle source de données.  
  
    ```R  
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)    
    ```  
  
    Les résultats doivent être les mêmes que lorsque vous exécutez *rxSummary* dans le contexte de l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Toutefois, l’opération peut être plus rapide ou plus lente. Cela dépend en grande partie de votre connexion à la base de données, car les données sont transférées vers votre ordinateur local pour analyse.  
  

## Étape suivante  
[Déplacer des données entre SQL Server et un fichier XDF &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/move-data-between-sql-server-and-xdf-file-data-science-deep-dive.md)  
  
## Étape précédente  
[Effectuer une analyse de segmentation à l’aide de rxDataStep &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/perform-chunking-analysis-using-rxdatastep-data-science-deep-dive.md)  
  
  
  
