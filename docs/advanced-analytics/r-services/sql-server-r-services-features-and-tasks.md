---
title: "Fonctionnalit&#233;s et t&#226;ches de SQL Server R Services | Microsoft Docs"
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
ms.assetid: 52ad3f10-6d24-477a-aeb6-110456b2ed1c
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 13
---
# Fonctionnalit&#233;s et t&#226;ches de SQL Server R Services
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] combine la puissance et la souplesse du langage R open source avec les outils de niveau entreprise pour le stockage des données et administration, développement de flux de travail et création de rapports et la visualisation. Il prend en charge les besoins des professionnels de quatre des données différentes et des scénarios.  
  
## Chercheurs de données : analyser, modéliser et noter à l’aide de R et de SQL Server  
 Les chercheurs de données ont accès à une série d’outils pour l’analyse de données et l’apprentissage automatique, allant des plateformes open source et Excel familières aux coûteuses suites statistiques qui requièrent des connaissances techniques approfondies. Parmi celles-ci, la solution [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre des avantages uniques, car elle permet aux chercheurs de données d’envoyer des calculs à la base de données, en évitant le déplacement de données et en respectant les stratégies de sécurité d’entreprise. En outre, le code R créé par le chercheur de données peut être facilement déployé en production, et appelé par des outils et solutions répandus au sein des entreprises  : applications basées sur des bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , outils de création de rapports BI et tableaux de bord. À l’aide de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], le chercheur de données peut déployer et mettre à jour une solution d’analyse tout en respectant les spécifications standard pour la gestion des données d’entreprise, notamment en relation avec la sécurité, la facilité de déploiement, la gestion, la surveillance et l’audit d’accès.  
  
-   **Interface utilisateur familière.**  Développez et testez vos solutions à l’aide de l’environnement de développement R de votre choix.  
  
-   **Traitement dans la base de données.**  Exécutez le code R et laissez les calculs s’exécuter sur l’ordinateur qui héberge l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cela élimine le besoin de déplacer des données.  
  
-   **Performances et extensibilité.**  Inclut les packages R évolutives et les API afin que vous ne sont plus limités par l’architecture monothread, liée à la mémoire de R. Vous pouvez travailler avec les jeux de données volumineux et les calculs multicœurs, multithreads et multiprocessus.  
    
-   **Portabilité du code.**  Le même code R que vous exécutez sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données puissent être facilement réutilisées par rapport à d’autres sources de données, telles que Hadoop.  
  
 Pour plus d’informations sur les concepts et tâches connexes, consultez [Exploration des données et modélisation prédictive avec R](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md).  
  
## Application et développeurs de base de données : déployer des solutions R  
 Les développeurs de base de données sont chargés d’intégrer plusieurs technologies et de regrouper les résultats de façon à ce qu’ils puissent être partagés au sein de l’entreprise. Le développeur de base de données coopère avec des développeurs d’applications, des développeurs SQL et des chercheurs de données pour concevoir des solutions, recommander des méthodes de gestion des données ainsi qu’architecturer et déployer des solutions. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre de nombreux avantages aux développeurs qui coopèrent avec des chercheurs de données :  
  
-   **Interagir avec des scripts R à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)].**  Vos développeurs d’états, analystes et développeurs de base de données peuvent invoquer des scripts R en appelant des procédures stockées système. Si votre solution utilise des agrégations complexes ou implique des jeux de données volumineux, vous pouvez avoir des calculs s’exécutent dans base de données, ou utiliser un mélange de R et [!INCLUDE[tsql](../../includes/tsql-md.md)], selon ce qui fournit les meilleures performances. L’intégration sans effort avec  [!INCLUDE[tsql](../../includes/tsql-md.md)] est particulièrement utile lorsque vous devez exécuter à plusieurs reprises des tâches sur de grandes quantités de données, telles que la génération de scores de prédiction sur des données de production.  
  
     L’intégration avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] signifie également que vous pouvez exécuter des scripts R à partir de toute application utilisant [!INCLUDE[tsql](../../includes/tsql-md.md)]. Par exemple, vous pouvez facilement appeler une procédure stockée depuis un [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] rapport pour appeler le script R et générer un graphique, ainsi que les prévisions dans le rapport.  
  
-   **Performances et extensibilité.**  Bien que le langage open source de R connu pour avoir des limitations, le package RevoScaleR API fournie par [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] peuvent opérer sur les jeux de données volumineux et tirer parti de plusieurs cœurs, multi-threads, plusieurs processus calculs dans base de données.  
  
-   **Outils de développement et de gestion standard.**  Aucun des outils supplémentaires pour l’administration ou le déploiement requis ; tous les travaux R peuvent être invoqués en appelant une procédure stockée. En outre, le code R que vous exécutez sur des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut également être exécuté sur d’autres sources de données, telles que Hadoop.  
  
 Pour plus d’informations sur les concepts et tâches connexes, consultez [à mettre en application de votre Code R](../../advanced-analytics/r-services/operationalizing-your-r-code.md).  
  
## Administrateurs de base de données : gestion des solutions d’analyse avancée  
 Les administrateurs de base de données doivent intégrer des projets et priorités concurrents dans un point de contact unique, le serveur de base de données. Il doivent accorder l’accès aux données, non seulement aux chercheurs de données mais aussi aux développeurs de rapports, analystes d’entreprise et autres utilisateurs de données d’entreprise, tout en préservant l’intégrité des magasins de données opérationnelles et de rapport. En entreprise, l’administrateur de base de données est un intervenant essentiel dans la conception et le déploiement d’une infrastructure efficace pour la recherche de données. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre de nombreux avantages à l’administrateur de base de données chargé de rechercher des données :  
  
-   **Sécurité.**  L’architecture de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] protège vos bases de données et isole l’exécution des sessions de R à partir de l’opération de l’instance de base de données.  
  
     Vous pouvez spécifier qui est autorisé à exécuter des scripts de R et de s’assurer que les données utilisées dans les travaux R sont gérées à l’aide des mêmes rôles de sécurité qui sont définis dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Fiabilité.**  Les sessions R sont exécutées dans un processus séparé pour garantir que votre serveur continue à s’exécuter comme d’habitude, même si la session R rencontre des problèmes.  
  
-   **Gouvernance des ressources.**  Vous pouvez contrôler la quantité de ressources allouées au runtime R afin d’éviter que des calculs massifs ne mettent en péril les performances globales du serveur.  
  
 Pour plus d’informations sur les concepts et les tâches connexes, voir [Managing and Monitoring R Solutions](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md).  
  
## Architectes et concepteurs d’extraction, transformation et chargement (ETL) : créer des flux de travail intégrés qui s’étendent sur R et SQL Server  
 Des ingénieurs chargés du traitement des données conçoivent et créent des solutions ETL. Des architectes conçoivent des plateformes de données répondant à des besoins métier concurrents et complémentaires. Étant donné que [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] est profondément intégré avec d’autres outils Microsoft, tels que l’analyse décisionnelle et pile de l’entrepôt de données cloud d’entreprise et outils de mobilité et Hadoop, il fournit un tableau des avantages à l’architecte de données système ou ingénieur souhaitant promouvoir analytique avancée.  
  
-   **Vaste éventail d’outils de développement familiers.**  Lorsque vous développez des solutions R, utilisez [!INCLUDE[tsql](../../includes/tsql-md.md)] et des procédures stockées système pour remplir des jeux de données, exécuter des travaux R ou obtenir des prédictions. Pas de conception supplémentaire de flux de travail parallèles dans les outils de recherche de données ; générez vos pipelines de données dans l’environnement familier de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
     Vous avez besoin d’utiliser les données du cloud ? Prise en charge d’Azure Data Factory et la base de données SQL Azure facilite la transformation et de gérer les données, et utilisent des sources de données cloud dans les workflows seulement, comme ceux sur site [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données.  
  
-   **Créer et gérer des flux de travail.**  Planifier les tâches et créer le flux de travail contenant le script R, à l’aide de procédures stockées système.  
  
 Pour plus d’informations sur les concepts et tâches connexes, consultez [Création de flux de travail que R utilisé dans SQL Server](../../advanced-analytics/r-services/creating-workflows-that-use-r-in-sql-server.md).  
  
## Voir aussi  
 [Prise en main de SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
  
  