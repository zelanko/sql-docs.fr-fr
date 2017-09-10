---
title: "Guide pratique pour créer un pool de ressources pour R | Microsoft Docs"
ms.custom: 
ms.date: 10/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7f7f6e4-774d-4b45-b94a-f06c51718475
caps.latest.revision: 19
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: be3afb3a1ff5175fbb3d0735cde59bd19bb47f6c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="how-to-create-a-resource-pool-for-r"></a>Guide pratique pour créer un pool de ressources pour R
  Cette rubrique vous explique comment créer un pool de ressources pour gérer les charges de travail R dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Elle part de l’hypothèse que vous avez déjà installé R Services (dans la base de données) et que vous voulez reconfigurer l’instance [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour prendre en charge une gestion plus fine des ressources utilisées par R.  
  
 Pour plus d’informations sur la gestion des ressources serveur, consultez [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) et [Vues de gestion dynamique liées à Resource Governor &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).  
  
 **Étapes**  
  
1.  Examiner l’état des pools de ressources existants  
  
2.  Modifier des pools de ressources de serveur  
  
3.  Créer un pool de ressources pour des processus externes  
  
4.  Créer une fonction de classification pour identifier les demandes R  
  
5.  Vérifier que le nouveau pool de ressources externe capture les travaux R  
  
##  <a name="bkmk_ReviewStatus"></a> Examiner l’état des pools de ressources existants  
  
1.  Dans un premier temps, vérifiez les ressources allouées au pool par défaut du serveur.  
  
    ```  
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'  
    ```  
     **Résultats**

    |pool_id|name|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|  
    |-|-|-|-|-|-|-|-|-|  
    |2|par défaut|0|100|0|100|100|0|0|  

2.  Vérifiez les ressources allouées au pool de ressources **externe** par défaut.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'  
    ```  
     
    **Résultats**

    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|par défaut|100|20|0|2|  
 
3.  Avec ces paramètres de serveur par défaut, il est probable que le runtime R n’aurait pas suffisamment de ressources pour mener à bien la plupart des tâches. Pour changer cela, vous devez modifier l’utilisation des ressources serveur comme suit :  
  
    -   Réduisez la quantité maximale de mémoire de l’ordinateur que peut utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Augmentez la quantité maximale de mémoire de l’ordinateur que peut utiliser le processus externe.  
  
## <a name="modify-server-resource-usage"></a>Modifier l’utilisation des ressources serveur  
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], exécutez l’instruction suivante pour limiter l’utilisation de mémoire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à **60 %** de la valeur du paramètre « max server memory ».  
  
    ```  
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);  
    ```  
  
2.  De la même manière, exécutez l’instruction suivante pour limiter la quantité de mémoire qu’utilise un processus externe à **40 %** des ressources totales de l’ordinateur.  
  
    ```  
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);  
    ```  
  
3.  Pour appliquer ces modifications, vous devez reconfigurer et redémarrer Resource Governor comme suit :  
  
    ```  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
    > [!NOTE]  
    >  Il s’agit simplement d’une suggestion de paramétrage qui peut faire office de point de départ ; vous devez évaluer les exigences de R par rapport aux autres processus serveur pour déterminer l’équilibre approprié compte tenu de votre environnement et de la charge de travail.  
  
## <a name="create-a-user-defined-external-resource-pool"></a>Créer un pool de ressources externe défini par l’utilisateur  
  
1.  Les modifications apportées à la configuration de Resource Governor s’appliquent à l’ensemble du serveur et affectent les charges de travail qui utilisent les pools par défaut du serveur, ainsi que les charges de travail qui utilisent les pools externes.  
  
     Par conséquent, pour définir avec plus de précision les charges de travail qui doivent avoir la priorité, vous pouvez créer un nouveau pool de ressources externe défini par l’utilisateur. Vous devez aussi définir une fonction de classification et l’assigner au pool de ressources externe.  
  
     Commencez par créer un *pool de ressources externe défini par l’utilisateur*. Dans l’exemple suivant, le pool est nommé **ds_ep**.  
  
    ```  
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);  
    ```  
  
     Notez la présence du nouveau mot clé **EXTERNAL**.  
  
2.  Créez un groupe de charge de travail sous le nom `ds_wg` pour l’utiliser dans la gestion des demandes de session. Pour les requêtes SQL, vous utiliserez le pool par défaut ; les requêtes de tous les processus externes utiliseront le pool `ds_ep`.  
  
    ```  
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";  
    ```  
  
     Les demandes sont assignées au groupe par défaut chaque fois qu’elles ne peuvent pas être classifiées ou que tout autre échec de classification se produit.  
  
     Pour plus d’informations, consultez [Groupe de charge de travail de Resource Governor](../../relational-databases/resource-governor/resource-governor-workload-group.md) et [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md).  
  
## <a name="create-a-classification-function-for-r"></a>Créer une fonction de classification pour R  
  
1.  Une fonction de classification vise à examiner les tâches entrantes et à déterminer si elles peuvent être exécutées en utilisant le pool de ressources actif. Les tâches qui ne répondent pas aux critères de la fonction de classification sont réassignées au pool de ressources par défaut du serveur.  
  
     Commencez par préciser qu’une fonction classifieur doit être utilisée par Resource Governor pour déterminer les pools de ressources. Vous pouvez assigner une valeur null en guise d’espace réservé pour la fonction classifieur.  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
     Pour plus d’informations, consultez [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md).  
  
2.  Dans la fonction classifieur de chaque pool de ressources, vous devez définir le type d’instruction ou de demande entrante qui doit être assigné au pool de ressources.  
  
     Par exemple, la fonction suivante retourne le nom du schéma assigné au pool de ressources externe défini par l’utilisateur si l’application qui a envoyé la demande est soit « Microsoft R Host » soit « RStudio » ; sinon, elle retourne le pool de ressources par défaut.  
  
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
  
3.  Une fois que la fonction a été créée, reconfigurez le groupe de ressources pour assigner la nouvelle fonction classifieur au groupe de ressources externe que vous avez défini précédemment.  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);  
    ALTER RESOURCE GOVERNOR WITH reconfigure;  
    go  
    ```  
  
## <a name="verify-new-resource-pools-and-affinity"></a>Vérifier les nouveaux pools de ressources et l’affinité  
  
1.  Pour vérifier que les modifications ont bien été apportées, vérifiez la configuration de la mémoire et du processeur du serveur pour chaque groupe de charge de travail associé à tous les pools de ressources d’instance : le pool par défaut du serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le pool de ressources par défaut des processus externes et le pool défini par l’utilisateur des processus externes.  
  
    ```  
    SELECT * FROM sys.resource_governor_workload_groups;  
    ```  

    **Résultats**

    |group_id|name|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_idd|  
    |-|-|-|-|-|-|-|-|-|-|  
    | 1|interne|Moyenne|25|0|0|0|0| 1|2|  
    |2|par défaut|Moyenne|25|0|0|0|0|2|2|  
    |256|ds_wg|Moyenne|25|0|0|0|0|2|256|  
  
2.  Vous pouvez utiliser le nouvel affichage catalogue, [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), pour afficher tous les pools de ressources externes.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools;  
    ```  
    **Résultats**
    
    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|par défaut|100|20|0|2|  
    |256|ds_ep|100|40|0| 1|  
  
     Pour plus d’informations, consultez [Affichages catalogue de Resource Governor &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md).  
  
3.  L’instruction suivante retourne des informations sur les ressources d’ordinateur qui ont des affinités avec le pool de ressources externe.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;  
    ```  
  
     Dans ce cas, comme les pools ont été créés avec une affinité AUTO, aucune information n’est affichée. Pour plus d’informations, consultez [sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Gouvernance des ressources pour R Services](../../advanced-analytics/r-services/resource-governance-for-r-services.md)  
  
  

