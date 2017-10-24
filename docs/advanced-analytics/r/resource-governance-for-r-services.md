---
title: Gouvernance des ressources pour R Services | Microsoft Docs
ms.custom: 
ms.date: 05/31/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18c9978a-aa55-42bd-9ab3-8097030888c9
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5475c2258971c48c2e19bba69d9ec962ae48be87
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="resource-governance-for-r-services"></a>Gouvernance des ressources pour R Services
  L’un des inconvénients de R est que l’analyse de grandes quantités de données de production nécessite du matériel supplémentaire et que les données sont souvent déplacées hors de la base de données sur des ordinateurs qui ne sont pas contrôlées par le service informatique.  Pour effectuer des opérations d’analyse avancée, les clients veulent pouvoir tirer parti des ressources de serveur de bases de données, et pour protéger leurs données, ils souhaitent que ces opérations répondent aux exigences de conformité des grandes entreprises, notamment en matière de sécurité et de performances.  
  
 Cette section fournit des informations sur la manière de gérer les ressources utilisées par le runtime R et par les travaux R s’exécutant en utilisant l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comme contexte de calcul.  
  
## <a name="what-is-resource-governance"></a>Qu’est-ce que la gouvernance des ressources ?  
 La gouvernance des ressources vise à identifier et à prévenir les problèmes courants au sein d’un environnement de serveur de base de données, où coexistent souvent plusieurs applications dépendantes et plusieurs services à prendre en charge et à équilibrer. Pour [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], la gouvernance des ressources implique les tâches suivantes :  
  
-   Identifier les scripts qui utilisent trop de ressources de serveur.  
  
     L’administrateur doit pouvoir arrêter ou limiter les travaux qui consomment trop de ressources.  
  
-   Atténuer les effets de charges de travail imprévisibles.  
  
     Par exemple, si plusieurs travaux R s’exécutent simultanément sur le serveur et que ces travaux ne sont pas isolés les uns des autres au moyen de pools de ressources, le conflit de ressources qui en résulte peut donner lieu à des performances imprévisibles ou menacer l’achèvement de la charge de travail.  
  
-   Hiérarchiser les charges de travail.  
  
     L’administrateur ou l’architecte doit pouvoir spécifier les charges de travail prioritaires ou garantir l’achèvement de certaines charges de travail en cas de conflit de ressources.  
  
 Dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], vous pouvez utiliser [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) pour gérer les ressources utilisées par le runtime R et par les travaux R distants.  
  
## <a name="how-to-use-resource-governor-to-manage-r-jobs"></a>Comment utiliser Resource Governor pour gérer les travaux R  
 En général, gérer des ressources allouées aux travaux R consiste à créer des *pools de ressources externes* et à leur assigner des charges de travail. Un pool de ressources externe est un nouveau type de pool de ressources inauguré dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour faciliter la gestion du runtime R et d’autres processus externes au moteur de base de données.  
  
 Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], il existe désormais trois types de pool de ressources par défaut.  
  
-   Le *pool interne* représente les ressources utilisées par le serveur SQL Server lui-même et ne peut ni être modifié ni être limité.  
  
-   Le *pool par défaut* est un pool d’utilisateurs prédéfini que vous pouvez utiliser pour modifier l’utilisation des ressources pour le serveur dans son ensemble. Vous pouvez aussi définir les groupes d’utilisateurs qui appartiennent à ce pool de façon à gérer l’accès aux ressources.  
  
-   Le *pool externe par défaut* est un pool d’utilisateurs prédéfini pour les ressources externes. Par ailleurs, vous pouvez créer de nouveaux pools de ressources externes et définir les groupes d’utilisateurs qui appartiennent à ces pools.  
  
 Vous pouvez même créer des *pools de ressources définis par l’utilisateur* pour allouer des ressources au moteur de base de données ou à d’autres applications, et créer des *pools de ressources externes définis par l’utilisateur* pour gérer des processus R et d’autres processus externes.  
  
 Vous trouverez une bonne introduction à la terminologie et aux concepts généraux dans la rubrique [Pool de ressources de Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md).  

  
## <a name="resource-management-using-resource-governor"></a>Gestion de ressources avec Resource Governor 

   Si vous êtes un utilisateur novice de Resource Governor, la procédure pas à pas rapide contenue dans la rubrique suivante vous aidera à modifier les ressources par défaut d’une instance et à créer un nouveau pool de ressources externe : [Guide pratique pour créer un pool de ressources pour R](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)   
  
 Vous pouvez utiliser le mécanisme de *pool de ressources externe* pour gérer les ressources utilisées par les exécutables R suivants :  
  
-   Rterm.exe et les processus satellites  
  
-   BxlServer.exe et les processus satellites  
  
-   Processus satellites lancés par LaunchPad  
  
 Cependant, la gestion directe du service Launchpad à l’aide de Resource Governor n’est pas prise en charge. Cela s’explique par le fait que [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] est un service approuvé qui peut par sa conception héberger uniquement les lanceurs fournis par Microsoft. Les lanceurs approuvés sont aussi configurés pour éviter de consommer trop de ressources.  
  
 Nous vous recommandons de gérer les processus satellites à l’aide de Resource Governor et de les paramétrer en fonction des besoins de la configuration de base de données individuelle et de la charge de travail.  Par exemple, n’importe quel processus satellite individuel peut être créé ou détruit à la demande pendant l’exécution.  
  
## <a name="disable-external-script-execution"></a>Désactiver l’exécution de scripts externes  
 La prise en charge des scripts externes est optionnelle dans le programme d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Même après l’installation de [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], la possibilité d’exécuter des scripts externes est désactivée par défaut, et vous devez reconfigurer manuellement la propriété et redémarrer l’instance pour permettre l’exécution de scripts.  
  
 Par conséquent, si vous vous trouvez devant la nécessité d’atténuer au plus vite les effets d’un problème de ressource ou de sécurité, un administrateur peut désactiver immédiatement l’exécution de scripts externes en utilisant [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) et en attribuant à la propriété `external scripts enabled` la valeur FALSE ou 0.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion et surveillance des solutions R](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  
 [Guide pratique pour créer un pool de ressources pour R](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)  
 [Pool de ressources de Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
  


