---
title: "Comment&#160;: Cr&#233;er un Pool de ressources pour R | Microsoft Docs"
ms.custom: ""
ms.date: "10/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7f7f6e4-774d-4b45-b94a-f06c51718475
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 19
---
# Comment&#160;: Cr&#233;er un Pool de ressources pour R
  Cette rubrique décrit comment vous pouvez créer un pool de ressources conçus spécifiquement pour gérer les charges de travail R dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Il part du principe que vous avez déjà installé les Services de R (de base de données) et reconfigurer le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance pour prendre en charge la gestion affinée plus les ressources utilisées par R.  
  
 Pour plus d’informations sur la gestion des ressources du serveur, consultez la page [du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md) et [ressource gouverneur connexes vues de gestion dynamique &#40 ; Transact-SQL &#41 ;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).  
  
 **Étapes**  
  
1.  Contrôle de l’état des pools de ressources existant  
  
2.  Modifier des pools de ressources serveur  
  
3.  Créer un pool de ressources pour les processus externes  
  
4.  Créez une fonction de classification pour identifier les demandes de R  
  
5.  Vérifiez que nouveau pool de ressources externe est en train de capturer les travaux R  
  
##  <a name="bkmk_ReviewStatus"></a> Examinez l’état des pools de ressources existant  
  
1.  Vérifiez tout d’abord, les ressources allouées pour le pool par défaut pour le serveur.  
  
    ```  
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'  
    ```  
     **Résultats**

    |pool_id|name|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|  
    |-|-|-|-|-|-|-|-|-|  
    |2|par défaut|0|100|0|100|100|0|0|  

2.  Vérifiez les ressources allouées à la valeur par défaut **externe** pool de ressources.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'  
    ```  
     
    **Résultats**

    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|par défaut|100|20|0|2|  
 
3.  Ces paramètres par défaut du serveur, le runtime R aura probablement des ressources insuffisantes pour effectuer la plupart des tâches. Pour modifier cela, vous devez modifier l’utilisation des ressources serveur comme suit :  
  
    -   Réduire la mémoire maximale qui peut être utilisée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
    -   Augmentez la mémoire maximale qui peut être utilisée par le processus externe  
  
## Modifier l’utilisation des ressources serveur  
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], exécutez l’instruction suivante pour limiter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisation de la mémoire **60 %** de la valeur dans le paramètre « max server memory ».  
  
    ```  
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);  
    ```  
  
2.  De même, exécutez l’instruction suivante pour limiter l’utilisation de la mémoire par un processus externe à **40 %** des ressources de l’informatique.  
  
    ```  
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);  
    ```  
  
3.  Pour appliquer ces modifications, vous devez reconfigurer et redémarrer le gouverneur de ressources comme suit :  
  
    ```  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
    > [!NOTE]  
    >  Il s’agit des paramètres simplement suggérées pour commencer ; Vous devez évaluer les exigences de R par rapport aux autres processus serveur pour déterminer le solde correct pour votre environnement et de la charge de travail.  
  
## Créer un pool de ressources externes définies par l’utilisateur  
  
1.  Les modifications apportées à la configuration du gouverneur de ressources sont appliquées au sein de l’ensemble du serveur et affectent les charges de travail qui utilisent les pools par défaut pour le serveur, ainsi que les charges de travail qui utilisent les pools externes.  
  
     Par conséquent, pour fournir un contrôle plus précis sur lequel les charges de travail doivent avoir priorité, vous pouvez créer un nouveau pool de ressources externes définies par l’utilisateur. Vous devez également définir une fonction de classification et affectez-le au pool de ressources externes.  
  
     Commencez par créer un nouveau *pool de ressources externes définies par l’utilisateur*. Dans l’exemple suivant, le pool est nommé **ds_ep**.  
  
    ```  
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);  
    ```  
  
     Notez la nouvelle **EXTERNE** (mot clé).  
  
2.  Créez un groupe de charges de travail nommé `ds_wg` à utiliser dans la gestion des demandes de session. Pour les requêtes SQL, vous utiliserez le pool par défaut ; pour tous les processus externes requêtes utilisent le `ds_ep` pool.  
  
    ```  
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";  
    ```  
  
     Les demandes sont affectés au groupe par défaut chaque fois que la demande ne peut pas être classée, ou si toute autre défaillance de classification.  
  
     Pour plus d’informations, consultez [groupe de charges de travail du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor-workload-group.md) et [CRÉER UN GROUPE de charges de TRAVAIL &#40 ; Transact-SQL &#41 ;](../../t-sql/statements/create-workload-group-transact-sql.md).  
  
## Création d’une fonction de classification pour R  
  
1.  Une fonction de classification examine les tâches entrantes et détermine si la tâche est une tâche qui peut être exécuté à l’aide de la liste actuelle des ressources. Tâches qui ne répondent pas aux critères de la fonction de classification sont affectées au pool de ressources du serveur par défaut.  
  
     Commencez par spécifier qu’une fonction classifieur doit être utilisée par le gouverneur de ressources pour déterminer les pools de ressources. Vous pouvez affecter une valeur null comme un espace réservé pour la fonction classifieur.  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
     Pour plus d’informations, consultez [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md).  
  
2.  Dans la fonction classifieur pour chaque pool de ressources, vous définissez le type d’instructions ou les demandes entrantes qui doivent être affectés au pool de ressources.  
  
     Par exemple, la fonction suivante retourne le nom du schéma affecté au pool de ressources externes définies par l’utilisateur si l’application qui a envoyé la demande est « Microsoft R Host » ou « RStudio » ; Sinon, elle retourne la liste des ressources par défaut.  
  
    ```  
    USE master  
    GO  
    CREATE FUNCTION is_ds_apps()  
    RETURNS sysname  
    WITH schemabinding  
    AS  
    BEGIN  
        IF program_name() in ('Microsoft R Host', 'RStudio') RETURN 'ds_wg';  
        RETURN 'default'  
        END;  
    GO  
    ```  
  
3.  Quand la fonction a été créée, reconfigurez le groupe de ressources pour attribuer la nouvelle fonction classifieur pour le groupe de ressources externes que vous avez définis précédemment.  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);  
    ALTER RESOURCE GOVERNOR WITH reconfigure;  
    go  
    ```  
  
## Vérifiez l’affinité et les nouveaux pools de ressources  
  
1.  Pour vérifier que les modifications ont été apportées, vérifiez la configuration de la mémoire du serveur et du processeur pour chacun des groupes de charges de travail associés à tous les pools de ressources d’instance : le pool par défaut pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur, le pool de ressources par défaut pour les processus externes et le pool défini par l’utilisateur pour les processus externes.  
  
    ```  
    SELECT * FROM sys.resource_governor_workload_groups;  
    ```  

    **Résultats**

    |group_id|name|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|GROUP_MAX_REQUESTS pool_id|pool_idd|external_pool_idd|  
    |-|-|-|-|-|-|-|-|-|-|  
    | 1|interne|Moyenne|25|0|0|0|0| 1|2|  
    |2|par défaut|Moyenne|25|0|0|0|0|2|2|  
    |256|ds_wg|Moyenne|25|0|0|0|0|2|256|  
  
2.  Vous pouvez utiliser la nouvelle vue de catalogue, [sys.resource_governor_external_resource_pools &#40 ; Transact-SQL &#41 ;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), pour afficher tous les pools de ressources externes.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools;  
    ```  
    **Résultats**
    
    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|par défaut|100|20|0|2|  
    |256|ds_ep|100|40|0| 1|  
  
     Pour plus d’informations, consultez [affichages catalogue du gouverneur de ressources &#40 ; Transact-SQL &#41 ;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md).  
  
3.  L’instruction suivante retourne des informations sur les ressources des ordinateurs qui sont associés au pool de ressources externes.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;  
    ```  
  
     Dans ce cas, les pools ont été ne créés avec une affinité AUTO, aucune information n’est affichée. Pour plus d’informations, consultez [sys.dm_resource_governor_resource_pool_affinity &#40 ; Transact-SQL &#41 ;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).  
  
## Voir aussi  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Gestion des ressources pour les Services de R](../../advanced-analytics/r-services/resource-governance-for-r-services.md)  
  
  