---
title: "Gestion des ressources pour les Services de R | Microsoft Docs"
ms.custom: ""
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 18c9978a-aa55-42bd-9ab3-8097030888c9
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Gestion des ressources pour les Services de R
  Une problématique avec R est que l’analyse de grandes quantités de données de production nécessite du matériel supplémentaire et données sont souvent déplacées en dehors de la base de données sur des ordinateurs non contrôlés par informatique.  Pour effectuer les opérations avancées analytique, les clients veulent pour tirer parti des ressources du serveur de base de données et à protéger leurs données, ils requièrent que ces opérations aux besoins de la conformité au niveau de l’entreprise, telles que la sécurité et les performances.  
  
 Cette section fournit des informations sur comment vous pouvez gérer les ressources utilisées par le runtime R et par les travaux R en cours d’exécution à l’aide de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance comme contexte de calcul.  
  
## Quelle est la gouvernance de ressources ?  
 Gestion des ressources sont conçue pour identifier et empêcher les problèmes communs dans un environnement de serveur de base de données, où il existe souvent plusieurs applications dépendantes et plusieurs services pour prendre en charge et l’équilibrage. Pour [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], la gouvernance de ressources implique les tâches :  
  
-   Identification des scripts qui utilisent les ressources du serveur de manière excessive.  
  
     L’administrateur doit être en mesure d’arrêter ou de limiter les tâches qui consomment trop de ressources.  
  
-   Atténuation des charges de travail imprévisibles.  
  
     Par exemple, si plusieurs travaux R sont exécutent simultanément sur le serveur et les tâches ne sont pas isolés les uns des autres à l’aide de pools de ressources, le conflit de ressources qui en résulte peut entraîner des performances imprévisibles ou menacent d’achèvement de la charge de travail.  
  
-   Hiérarchisation des charges de travail.  
  
     L’administrateur ou un architecte doit être en mesure de spécifier des charges de travail qui doivent prioritaires ou garantir certaines charges de travail de s’exécuter si la contention des ressources.  
  
 Dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], vous pouvez utiliser [du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md) pour gérer les ressources utilisées par le runtime R et par les travaux R à distance.  
  
## Pour utiliser le gouverneur de ressources comment les travaux R gérer  
 En général, vous gérez les ressources allouées aux tâches de R en créant *pools de ressources externe* et en attribuant les charges de travail pour le pool ou des pools. Un pool de ressources externe est un nouveau type de pool de ressources introduite dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], pour aider à gérer le runtime R et autres processus externe au moteur de base de données.  
  
 Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], il existe désormais trois types de pools de ressources par défaut.  
  
-   Le *pool interne* représente les ressources utilisées par le serveur SQL Server lui-même et ne peut pas être modifiés ou restreint.  
  
-   Le *par défaut du pool* est un pool d’utilisateur prédéfini que vous pouvez utiliser pour modifier l’utilisation des ressources pour le serveur dans son ensemble. Vous pouvez également définir des groupes d’utilisateurs qui appartiennent à ce pool, pour gérer l’accès aux ressources.  
  
-   Le *par défaut du pool externe* est un pool d’utilisateur prédéfini pour les ressources externes. En outre, vous pouvez créer de nouveaux pools de ressources externes et définir des groupes d’utilisateurs appartenant à ce pool.  
  
 En outre, vous pouvez créer *pools de ressources définies par l’utilisateur* pour allouer des ressources pour le moteur de base de données ou d’autres applications, créez *pools de ressources externes définies par l’utilisateur* pour gérer les R et autres processus externes.  
  
 Pour une bonne introduction à la terminologie et les concepts généraux, consultez [Pool de ressources du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor-resource-pool.md).  
  
> [!NOTE]  
>  Actuellement les nouvelles propriétés du gouverneur de ressources sont disponibles uniquement via des instructions DDL ou de script ; Impossible de créer des groupes de ressources externes à l’aide de l’interface utilisateur de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
## Gestion des ressources à l’aide du gouverneur de ressources 

   Si vous débutez au gouverneur de ressources, consultez cette rubrique pour un bref aperçu de comment modifier les ressources de l’instance par défaut et créer un nouveau pool de ressources externes :  [Comment faire : créer un Pool de ressources pour R](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)   
  
 Vous pouvez utiliser la *pool de ressources externe* mécanisme permettant de gérer les ressources utilisées par les exécutables R suivants :  
  
-   Processus Rterm.exe et satellites  
  
-   Processus BxlServer.exe et satellites  
  
-   Processus de satellites lancés par LaunchPad  
  
 Toutefois, la gestion directe du service Launchpad à l’aide du gouverneur de ressources n’est pas pris en charge. C’est parce que le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] est un service approuvé que conception peut héberger uniquement les lanceurs sont fournis par Microsoft. Les lanceurs de confiance sont également configurés pour éviter de consommer trop de ressources.  
  
 Nous vous recommandons gérez les processus de satellite à l’aide du gouverneur de ressources et réglez pour répondre aux besoins de la configuration de la base de données individuelle et la charge de travail.  Par exemple, n’importe quel processus satellite individuels peut être créé ou détruit à la demande lors de l’exécution.  
  
## Désactiver l’exécution du Script externe  
 Prise en charge des scripts externes est facultatif dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation. Même après l’installation [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], la possibilité d’exécuter des scripts externes est désactivé par défaut et vous devez manuellement reconfigurer la propriété et redémarrez l’instance pour permettre l’exécution de script.  
  
 Par conséquent, s’il existe un problème de ressources devant être atténuée immédiatement, ou un problème de sécurité, un administrateur peut immédiatement désactiver toute exécution de script externe à l’aide de [sp_configure & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) et en définissant la propriété `external scripts enabled` FALSE ou 0.  
  
## Voir aussi  
 [Gestion et surveillance des Solutions R](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  
 [Comment : Créer un Pool de ressources pour R](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)  
 [Pool de ressources du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
  