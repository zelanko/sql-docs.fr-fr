---
title: "Gestion et surveillance des Solutions R | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d455f22a-190f-4a28-9088-98a843cd5db2
caps.latest.revision: 15
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# Gestion et surveillance des Solutions R
  Les administrateurs de base de données doivent intégrer des projets et priorités concurrents dans un point de contact unique : le serveur de base de données. Il doivent accorder l’accès aux données, non seulement aux chercheurs de données mais aussi aux développeurs de rapports, analystes d’entreprise et autres utilisateurs de données d’entreprise, tout en préservant l’intégrité des magasins de données opérationnelles et de rapport. En entreprise, l’administrateur de base de données est un intervenant essentiel dans la conception et le déploiement d’une infrastructure efficace pour la recherche de données. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre de nombreux avantages à l’administrateur de base de données chargé de rechercher des données.  
  
-   **Sécurité.** L’architecture de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] protège vos bases de données et isole l’exécution des sessions R du fonctionnement de l’instance de base de données.  
  
     Vous pouvez spécifier qui est autorisé à exécuter des scripts R et vous assurer que les données utilisées dans les travaux R sont gérées à l’aide des rôles de sécurité définis dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Fiabilité.** Les sessions R sont exécutées dans un processus séparé pour garantir que votre serveur continue à s’exécuter comme d’habitude, même si la session R rencontre des problèmes. Comptes d’utilisateur physique faibles sont utilisés pour contenir et isoler les instances de R.   
  
-   **Gouvernance des ressources.** Vous pouvez contrôler la quantité de ressources allouées au runtime R afin d’éviter que des calculs massifs ne mettent en péril les performances globales du serveur.  
  
  
## Dans cette section  
 [Surveillance des Services de R](../../advanced-analytics/r-services/monitoring-r-services.md)
 
 [Gestion des ressources pour les Services de R](../../advanced-analytics/r-services/resource-governance-for-r-services.md)
 
[Installation et gestion des Packages R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md)
  
[Configuration](../../advanced-analytics/r-services/configuration-sql-server-r-services.md) 

+ [Configurer et gérer les extensions analytiques avancées](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md)  
  
+  [Modifier le pool de comptes d’utilisateurs pour SQL Server R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md)  

 [Considérations relatives à la sécurité pour le composant d’exécution R dans SQL Server](../../advanced-analytics/r-services/security-considerations-for-the-r-runtime-in-sql-server.md)  
  
 
  
## Voir aussi  
 [Fonctionnalités et tâches de SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)  
  
  