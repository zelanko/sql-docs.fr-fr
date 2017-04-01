---
title: "Vues de gestion dynamique pour les Services SQL Server R | Microsoft Docs"
ms.custom: ""
ms.date: "11/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3643ea0-d9f3-463f-8ece-572127f32a24
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Vues de gestion dynamique pour les Services SQL Server R

La rubrique répertorie les vues de catalogue système et les vues de gestion dynamique liées à [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]. 


Pour plus d’informations sur les événements étendus, consultez [événements étendus pour les Services SQL Server R](../../advanced-analytics/r-services/extended-events-for-sql-server-r-services.md).

> [!TIP]
> L’équipe de produit a fourni des rapports personnalisés que vous pouvez utiliser pour surveiller les packages et les sessions des Services de R. Pour plus d’informations, consultez [R surveillance des Services à l’aide de rapports personnalisés dans Management Studio](../../advanced-analytics/r-services/monitor-r-services-using-custom-reports-in-management-studio.md).
> 

## <a name="system-configuration-and-system-resources"></a>Configuration du système et des ressources système

Vous pouvez surveiller et analyser les ressources utilisées par les scripts R à l’aide de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] DMV et affichages catalogue système.


**Général**
+ [ Sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)

  Retourne des informations pour les connexions utilisateur et les sessions du système. Vous pouvez identifier les sessions système en examinant le *session_id* colonne ; les valeurs supérieures ou égales à 51 sont des connexions utilisateur et des valeurs inférieures 51 sont des processus système. 



+ [Sys.dm_os_performance_counters (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)

  Renvoie une ligne pour chaque compteur de performance système utilisé par le serveur.  Vous pouvez utiliser ces informations pour afficher le nombre de scripts a été exécuté, les scripts ont été exécutées en utilisant le mode d’authentification ou le nombre d’appels R ont été émis sur l’instance globale.

  Cet exemple obtient uniquement les compteurs liés à un script R :

  ```SQL
  SELECT * from sys.dm_os_performance_counters WHERE object_name LIKE '%Extended Scripts%'
  ```

  Les compteurs suivants sont signalées par cette vue de gestion Dynamique pour les scripts externes par l’instance :

  + **Nombre total d’exécutions**: nombre de R processus démarré par des appels locaux ou distants
  + **Exécutions en parallèle**: nombre de fois où un script inclus le @parallel spécification et que [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] a été en mesure de générer et d’utiliser un plan de requête parallèle
  + **Diffusion en continu des exécutions**: nombre de fois que la fonctionnalité de diffusion en continu a été appelée. 
  + **Exécutions de CC SQL**: les scripts de nombre de R s’exécutent sur lequel l’appel a été instancié à distance et SQL Server est utilisé comme contexte de calcul 
  + **AUTH implicite. Connexions**: nombre de fois où un appel de bouclage ODBC a été effectué à l’aide d’implicite d’authentification, c'est-à-dire, le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] exécuté l’appel au nom de l’utilisateur qui envoie la demande de script
  + **Nombre total de temps d’exécution (ms)**: temps écoulé entre l’appel et l’appel.
  + **Erreurs d’exécution**: nombre de scripts a signalé des erreurs. Ce nombre n’inclut pas les erreurs de R.


+ [Sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)

  Cette DMV signale une seule ligne pour chaque compte de travail qui exécute un script externe. Notez que ce compte est différent dans les informations d’identification de la personne qui envoie le script. Si un seul utilisateur Windows envoie plusieurs demandes de script, qu’un seul compte recevra pour gérer toutes les demandes à partir de cet utilisateur. Si un autre utilisateur de Windows se connecte pour exécuter un script externe, la requête est gérée par un compte de travail distinct. 
  Cette DMV ne retourne pas de résultats si aucun script n’est actuellement en cours d’exécution ; Par conséquent, il est très utile pour l’analyse des scripts de longue. Elle retourne ces valeurs :
  + **external_script_request_id**: GUID, qui est également utilisé comme le nom temporaire du répertoire de travail utilisé pour stocker les scripts et les résultats intermédiaires.  
  + **langue**: une valeur telle que `R` qui indique le langage de script externe.
  + **degree_of_parallelism**: entier indiquant le nombre de parallèle de processus qui ont été utilisés. 
  + **external_user_name**: un compte de travail Launchpad, comme SQLRUser01. 
  

+ [Sys.dm_external_script_execution_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)

  Cette DMV est fournie pour la surveillance interne (télémétrie) effectuer le suivi du nombre d’appels R est effectués sur une instance. Le service de télémétrie démarre lorsque [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et incrémente un compteur de disque chaque fois une fonction R spécifique est appelée.

  Le compteur est incrémenté par un appel à une fonction. Par exemple, si `rxLinMod` est appelé et s’exécute en parallèle, le compteur est incrémenté d’une unité.
  
  En règle générale, les compteurs de performance demeurent valides tant que le processus qui les a générés reste actif. Par conséquent, une demande sur une vue de gestion dynamique ne peut pas faire état des données des services qui ne sont plus en cours d’exécution. Par exemple, si le Launchpad crée plusieurs travaux R parallèles et encore sont exécutées très rapidement et nettoyées par l’objet de travail Windows, une vue de gestion Dynamique ne peut pas afficher toutes les données.
 
  Toutefois, les compteurs de suivi par cette DMV restent en cours d’exécution et l’état pour le compteur de _execution dm_external_script est conservé à l’aide des écritures sur le disque, même si l’instance est fermée.
 
 Pour plus d’informations sur les compteurs de performance système utilisées par [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], consultez la page [utilisation d’objets SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md).

**Vues du gouverneur de ressources**

+ [Sys.resource_governor_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)

  Retourne des informations sur l'état et la configuration actuels des pools de ressources, ainsi que sur leurs statistiques.

  > [!IMPORTANT]
  > 
  > Vous devez modifier les pools de ressources qui s’appliquent à d’autres services serveur avant que vous pouvez allouer des ressources supplémentaires pour les Services de R.


+ [Sys.resource_governor_external_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)

  Une nouvelle vue de catalogue qui affiche les valeurs actuelles de la configuration de pools de ressources externes.
  Dans Enterprise Edition, vous pouvez configurer des pools de ressources externes supplémentaires : par exemple, vous pouvez décider de gestion des ressources pour les travaux en cours d’exécution R [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] séparément de celles qui proviennent d’un client distant. 

  > [!NOTE]
  > 
  > Dans l’Édition Standard, tous les travaux R sont exécutés dans le même pool de ressources externes par défaut.

+ [Sys.resource_governor_workload_groups](../../relational-databases/system-catalog-views/sys-resource-governor-workload-groups-transact-sql.md)

  Retourne les statistiques de groupe de charges de travail et la configuration actuelle du groupe de charges de travail. Cette vue peut être jointe avec sys.dm_resource_governor_resource_pools pour obtenir le nom de pool de ressources.
  Pour les scripts externes, une nouvelle colonne a été ajoutée qui affiche l’id du pool externe associé au groupe de charges de travail. 


+ [Sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)

  Une nouvelle vue de catalogue système qui vous permet de voir les processeurs et les ressources qui sont associés à un pool de ressources particulier.

  Retourne une ligne par planificateur dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] où chaque planificateur est associé à un processeur. Vous pouvez utiliser cette vue pour surveiller la condition d'un planificateur ou pour identifier des tâches d'échappement.

  Sous la configuration par défaut, pools de charges de travail sont automatiquement affectés à des processeurs et par conséquent, il n’y a aucune valeur d’affinité à retourner.

  La planification d’affinité mappe le pool de ressources pour le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] planifications identifiées par l’ID donnés. Ces ID mappage aux valeurs de la colonne scheduler_id dans sys.dm_os_schedulers (Transact-SQL).


> [!NOTE] 
> 
> Bien que la possibilité de configurer et personnaliser les pools de ressources est disponible uniquement dans Enterprise et Developer éditions, les pools par défaut ainsi que les vues de gestion dynamique sont disponibles dans toutes les éditions. Par conséquent, vous pouvez utiliser ces vues de gestion dynamique dans l’Édition Standard pour déterminer les ressources pour vos travaux R. 

Pour plus d’informations sur la surveillance [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] instances, consultez [affichages catalogue](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) et [ressource gouverneur connexes vues de gestion dynamique](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).

## <a name="r-script-execution-and-monitoring"></a>L’exécution du Script R et surveillance

R les scripts qui s’exécutent dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] sont démarrés par le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] interface. Toutefois, la zone de lancement n’est pas ressource régie ou analysé séparément, il est supposé être un service sécurisé fourni par Microsoft, qui gère les ressources de manière appropriée.

Les scripts R individuels qui s’exécutent sous le service Launchpad sont gérés à l’aide de la [objet de tâche Windows](https://msdn.microsoft.com/library/windows/desktop/ms684161.aspx). Un objet de tâche aux groupes de processus d’être gérés comme une unité. Chaque objet de tâche est hiérarchique et contrôle les attributs de tous les processus associés. Les opérations effectuées sur un objet de traitement affectent tous les processus associés à l’objet de traitement. 

Par conséquent, si vous avez besoin mettre fin à une tâche associée à un objet, sachez que tous les processus connexes seront également arrêtés. Si vous exécutez un script R qui est affecté à un objet de travail Windows et que ce script exécute un travail ODBC qui doit être arrêté, le processus de script R parent sera également terminé. 

Si vous démarrez un script R qui utilise le traitement parallèle, un seul objet de travail Windows gère tous les processus enfants parallèles.

Pour déterminer si un processus s’exécute dans une tâche, utilisez la `IsProcessInJob` (fonction).

## <a name="see-also"></a>Voir aussi
[Gestion et surveillance](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)

