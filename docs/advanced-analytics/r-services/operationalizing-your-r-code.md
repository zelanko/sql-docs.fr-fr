---
title: "Op&#233;rationnalisation de votre code R | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f15696b1-2479-4e5f-ac5e-4beaf958a043
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Op&#233;rationnalisation de votre code R
  Les développeurs de base de données sont chargés d’intégrer plusieurs technologies et de les faire fonctionner ensemble afin que toute l’entreprise puisse en bénéficier. Les développeurs de base de données travaillent en collaboration avec des développeurs d’applications, des développeurs SQL et des spécialistes des données pour concevoir des solutions, recommander des méthodes de gestion des données, mais aussi créer et déployer des solutions. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre de nombreux avantages aux développeurs qui travaillent avec des spécialistes des données.  
  
-   **Interagir avec des scripts R à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)].** Application et les développeurs de base de données, ainsi que les analystes qui créent des rapports, peuvent appeler un script R en appelant à partir d’une procédure stockée système.  
  
     Pour plus d’informations sur la syntaxe de base, consultez [sp_execute_external_script & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) et [à l’aide de Code R dans T-SQL](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md).  
 
    Pour obtenir un exemple montrant comment rendre opérationnels R étendu de code à l’aide de procédures stockées, consultez [Analytique dans base de données pour les développeurs SQL](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md).
  
     l’intégration avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] signifie également que vous pouvez exécuter des scripts R à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] et incorporer les résultats dans votre application. Par exemple, vous pouvez créer un rapport [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui exécute un script R, puis afficher les graphiques ainsi que les prédictions dans le rapport.  
  
-   **Performances et extensibilité.** Bien que le langage open source de R connu pour avoir des limitations, le package RevoScaleR API fournie par [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] peuvent opérer sur les jeux de données volumineux et tirer parti de plusieurs cœurs, multi-threads, plusieurs processus calculs dans base de données.  
  
     Si votre solution R utilise des agrégations complexes ou des jeux de données volumineux, vous pouvez tirer parti des index columnstore et des agrégations en mémoire très efficaces de SQL, et utiliser le code R pour les calculs statistiques et les calculs de score.  
  
-   **Outils de développement et de gestion standard.** Vous n’avez besoin d’aucun outil d’administration ou de déploiement supplémentaire : tous les travaux R peuvent être appelés via une procédure stockée.  
  
     En outre, le code R que vous exécutez sur des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut également être exécuté sur d’autres sources de données, telles que Hadoop.  
  
 Cette section décrit les concepts essentiels pour convertir les solutions R et les déployer en production à l’aide de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
## Dans cette section

[Utilisation des types de données R](../../advanced-analytics/r-services/working-with-r-data-types.md)

[Conversion de Code R pour une utilisation dans les Services de R](../../advanced-analytics/r-services/converting-r-code-for-use-in-r-services.md)

##  <a name="bkmk_RelatedTasks"></a> Tâches associées  
  
[Réglage des performances pour SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-performance-tuning.md)
 
## Voir aussi  
 [Fonctionnalités et tâches de SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)   
 [sp_execute_external_script & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  
  