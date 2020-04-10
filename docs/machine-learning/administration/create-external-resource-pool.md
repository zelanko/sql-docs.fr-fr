---
title: Créer un pool de ressources
description: Découvrez comment vous pouvez créer et utiliser un pool de ressources pour gérer les charges de travail Python et R dans SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2020
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1f8661101fa5b0f859723a168e149ae9747b3da4
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "81119032"
---
# <a name="create-a-resource-pool-for-sql-server-machine-learning-services"></a>Créer un pool de ressources pour SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Découvrez comment vous pouvez créer et utiliser un pool de ressources pour gérer les charges de travail Python et R dans SQL Server Machine Learning Services. 

Le processus comprend plusieurs étapes :

1. Examiner l’état des pools de ressources existants. Il est important de comprendre quels services utilisent les ressources existantes.
2. Modifier des pools de ressources de serveur.
3. Créer un pool de ressources pour des processus externes.
4. Créer une fonction de classification pour identifier les demandes de script externes.
5. Vérifiez que le nouveau pool de ressources externes capture des travaux R ou Python à partir des clients ou des comptes spécifiés.

<a name="bkmk_ReviewStatus"></a>

##  <a name="review-the-status-of-existing-resource-pools"></a>Examiner l’état des pools de ressources existants
  
1.  Utilisez les instructions suivantes pour vérifier les ressources allouées au pool par défaut du serveur.
  
    ```sql
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'
    ```

    **Exemples de résultats**

    |pool_id|name|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|
    |-|-|-|-|-|-|-|-|-|
    |2|default|0|100|0|100|100|0|0|

2.  Vérifiez les ressources allouées au pool de ressources **externe** par défaut.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'
    ```

    **Exemples de résultats**

    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|default|100|20|0|2|
 
3.  Avec ces paramètres de serveur par défaut, il est probable que le runtime externe n’aurait pas suffisamment de ressources pour mener à bien la plupart des tâches. Pour changer cela, vous devez modifier l’utilisation des ressources serveur comme suit :
  
    -   Réduisez la quantité maximale de mémoire de l’ordinateur que peut utiliser le moteur de base de données.
  
    -   Augmentez la quantité maximale de mémoire de l’ordinateur que peut utiliser le processus externe.

## <a name="modify-server-resource-usage"></a>Modifier l’utilisation des ressources serveur

1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], exécutez l’instruction suivante pour limiter l’utilisation de mémoire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à **60 %** de la valeur du paramètre « max server memory ».

    ```sql
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);
    ```
  
2.  De la même manière, exécutez l’instruction suivante pour limiter la quantité de mémoire qu’utilise un processus externe à **40 %** des ressources totales de l’ordinateur.
  
    ```sql
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);
    ```
  
3.  Pour appliquer ces modifications, vous devez reconfigurer et redémarrer Resource Governor comme suit :
  
    ```sql
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
    > [!NOTE]
    >  Il s’agit simplement d’une suggestion de paramétrage qui peut faire office de point de départ ; vous devez évaluer les tâches de Machine Learning par rapport aux autres processus serveur pour déterminer l’équilibre approprié compte tenu de votre environnement et de la charge de travail.

## <a name="create-a-user-defined-external-resource-pool"></a>Créer un pool de ressources externe défini par l’utilisateur
  
1.  Les modifications apportées à la configuration de Resource Governor s’appliquent à l’ensemble du serveur et affectent les charges de travail qui utilisent les pools par défaut du serveur, ainsi que les charges de travail qui utilisent les pools externes.
  
     Par conséquent, pour définir avec plus de précision les charges de travail qui doivent avoir la priorité, vous pouvez créer un nouveau pool de ressources externe défini par l’utilisateur. Vous devez aussi définir une fonction de classification et l’assigner au pool de ressources externe. Le mot clé **EXTERNE** est nouveau.
  
     Commencez par créer un *pool de ressources externe défini par l’utilisateur*. Dans l’exemple suivant, le pool est nommé **ds_ep**.
  
    ```sql
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);
    ```

2.  Créez un groupe de charge de travail sous le nom `ds_wg` pour l’utiliser dans la gestion des demandes de session. Pour les requêtes SQL, vous utiliserez le pool par défaut ; les requêtes de tous les processus externes utiliseront le pool `ds_ep`.
  
    ```sql
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";
    ```
  
     Les demandes sont assignées au groupe par défaut chaque fois qu’elles ne peuvent pas être classifiées ou que tout autre échec de classification se produit.
  
     Pour plus d’informations, consultez [Groupe de charge de travail de Resource Governor](../../relational-databases/resource-governor/resource-governor-workload-group.md) et [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md).
  
## <a name="create-a-classification-function-for-machine-learning"></a>Créer une fonction de classification pour le Machine Learning
  
Une fonction de classification vise à examiner les tâches entrantes et à déterminer si elles peuvent être exécutées en utilisant le pool de ressources actif. Les tâches qui ne répondent pas aux critères de la fonction de classification sont réassignées au pool de ressources par défaut du serveur.
  
1. Commencez par préciser qu’une fonction de classification doit être utilisée par Resource Governor pour déterminer les pools de ressources. Vous pouvez assigner une valeur **null** en guise d’espace réservé pour la fonction classifieur.
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
     Pour plus d’informations, consultez [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md).
  
2.  Dans la fonction classifieur de chaque pool de ressources, vous devez définir le type d’instruction ou de demande entrante qui doit être assigné au pool de ressources.
  
     Par exemple, la fonction suivante retourne le nom du schéma assigné au pool de ressources externe défini par l’utilisateur si l’application qui a envoyé la demande est « Microsoft R Host », « RStudio » ou « Mashup » ; sinon, elle retourne le pool de ressources par défaut.
  
    ```sql
    USE master
    GO
    CREATE FUNCTION is_ds_apps()
    RETURNS sysname
    WITH schemabinding
    AS
    BEGIN
        IF program_name() in ('Microsoft R Host', 'RStudio', 'Mashup') RETURN 'ds_wg';
        RETURN 'default'
        END;
    GO
    ```
  
3.  Une fois que la fonction a été créée, reconfigurez le groupe de ressources pour assigner la nouvelle fonction classifieur au groupe de ressources externe que vous avez défini précédemment.
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    GO
    ```

## <a name="verify-new-resource-pools-and-affinity"></a>Vérifier les nouveaux pools de ressources et l’affinité

Pour vérifier que les modifications ont été effectuées, vous devez vérifier la configuration de la mémoire du serveur et du processeur pour chaque groupe de charge de travail associé à ces pools de ressources d’instance :

+ le pool par défaut du serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
+ le pool de ressources par défaut pour les processus externes
+ le pool défini par l’utilisateur pour les processus externes

1. Exécutez l’instruction suivante pour afficher tous les groupes de charges de travail :

    ```sql
    SELECT * FROM sys.resource_governor_workload_groups;
    ```

    **Exemples de résultats**

    |group_id|name|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_id|
    |-|-|-|-|-|-|-|-|-|-|
    |1|interne|Moyenne|25|0|0|0|0|1|2|
    |2|default|Moyenne|25|0|0|0|0|2|2|
    |256|ds_wg|Moyenne|25|0|0|0|0|2|256|
  
2.  Utilisez le nouvel affichage catalogue, [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), pour afficher tous les pools de ressources externes.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools;
    ```

    **Exemples de résultats**
    
    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|default|100|20|0|2|
    |256|ds_ep|100|40|0|1|
  
     Pour plus d’informations, consultez [Affichages catalogue de Resource Governor &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md).
  
3.  Exécutez l’instruction suivante pour renvoyer des informations sur les ressources d’ordinateur qui ont des affinités avec le pool de ressources externe, le cas échéant :
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;
    ```
  
     Dans ce cas, comme les pools ont été créés avec une affinité AUTO, aucune information n’est affichée. Pour plus d’informations, consultez [sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la gestion des ressources de serveur, consultez :

+ [gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md) 
+ [Vues de gestion dynamique relatives au gouverneur de ressources &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)

Pour avoir une vue d’ensemble de la gouvernance des ressources pour le Machine Learning, consultez :

+ [Gérer les charges de travail Python et R avec Resource Governor dans SQL Server Machine Learning Services](resource-governor.md)
