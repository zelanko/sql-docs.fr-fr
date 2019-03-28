---
title: Comment créer un pool de ressources pour R et Python - SQL Server Machine Learning Services
description: Définir un pool de ressources SQL Server pour les processus R ou Python sur une instance du moteur de base de données SQL Server 2016 ou SQL Server 2017.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: f180f6223f255734f353348c0d5fef58d19b0cbd
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58512086"
---
# <a name="how-to-create-a-resource-pool-for-machine-learning-in-sql-server"></a>Comment créer un pool de ressources pour machine learning dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit comment vous pouvez créer et utiliser un pool de ressources spécifiquement pour la gestion de R et Python machine learning charges de travail dans SQL Server. Il suppose que vous avez déjà installé et activé les fonctionnalités, d’apprentissage et pour reconfigurer l’instance pour prendre en charge une gestion plus fine des ressources utilisées par un processus externe comme R ou Python.

Le processus comprend plusieurs étapes :

1.  Passez en revue l’état de tous les pools de ressources existant. Il est important de comprendre quels services sont à l’aide des ressources existantes.
2.  Modifier les pools de ressources de serveur.
3.  Créer un nouveau pool de ressources pour les processus externes.
4.  Créer une fonction de classification pour identifier les demandes de script externe.
5.  Vérifiez que le nouveau pool de ressources externe capture les travaux R ou Python dans les comptes ou les clients spécifiés.

##  <a name="bkmk_ReviewStatus"></a> Examiner l’état des pools de ressources existants
  
1.  Utilisez une instruction telle que la suivante pour vérifier les ressources allouées au pool par défaut pour le serveur.
  
    ```sql
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'
    ```

    **Exemples de résultats**

    |pool_id|NAME|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|
    |-|-|-|-|-|-|-|-|-|
    |2|par défaut|0|100|0|100|100|0|0|

2.  Vérifiez les ressources allouées au pool de ressources **externe** par défaut.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'
    ```

    **Exemples de résultats**

    |external_pool_id|NAME|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|par défaut|100|20|0|2|
 
3.  Ces paramètres par défaut du serveur, le runtime externe aura probablement des ressources insuffisantes pour effectuer la plupart des tâches. Pour changer cela, vous devez modifier l’utilisation des ressources serveur comme suit :
  
    -   Réduire la mémoire maximale qui peut être utilisée par le moteur de base de données.
  
    -   Augmentez la mémoire maximale qui peut être utilisée par le processus externe.

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
    >  Il s’agit des paramètres simplement suggérées pour commencer ; Vous devez évaluer vos tâches au vu des autres processus serveur pour déterminer l’équilibre correct pour votre environnement et de la charge de travail d’apprentissage.

## <a name="create-a-user-defined-external-resource-pool"></a>Créer un pool de ressources externe défini par l’utilisateur
  
1.  Les modifications apportées à la configuration de Resource Governor s’appliquent à l’ensemble du serveur et affectent les charges de travail qui utilisent les pools par défaut du serveur, ainsi que les charges de travail qui utilisent les pools externes.
  
     Par conséquent, pour définir avec plus de précision les charges de travail qui doivent avoir la priorité, vous pouvez créer un nouveau pool de ressources externe défini par l’utilisateur. Vous devez aussi définir une fonction de classification et l’assigner au pool de ressources externe. Le **externe** mot clé est une nouveauté.
  
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
  
## <a name="create-a-classification-function-for-machine-learning"></a>Créer une fonction de classification pour l’apprentissage
  
Une fonction de classification vise à examiner les tâches entrantes et à déterminer si elles peuvent être exécutées en utilisant le pool de ressources actif. Les tâches qui ne répondent pas aux critères de la fonction de classification sont réassignées au pool de ressources par défaut du serveur.
  
1. Commencez par spécifier qu’une fonction classifieur doit être utilisée par le gouverneur de ressources pour déterminer les pools de ressources. Vous pouvez affecter un **null** comme espace réservé pour la fonction classifieur.
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
     Pour plus d’informations, consultez [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md).
  
2.  Dans la fonction classifieur pour chaque pool de ressources, définissez le type d’instructions ou des demandes entrantes qui doivent être affectés au pool de ressources.
  
     Par exemple, la fonction suivante retourne le nom du schéma assigné au pool de ressources externe défini par l’utilisateur si l’application qui a envoyé la demande est soit « Microsoft R Host » soit « RStudio » ; sinon, elle retourne le pool de ressources par défaut.
  
    ```sql
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
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);
    ALTER RESOURCE GOVERNOR WITH reconfigure;
    GO
    ```

## <a name="verify-new-resource-pools-and-affinity"></a>Vérifier les nouveaux pools de ressources et l’affinité

Pour vérifier que les modifications ont été apportées, vous devez vérifier la configuration de la mémoire du serveur et du processeur pour chacun des groupes de charges de travail associés à ces pools de ressources d’instance :

+ le pool par défaut pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server
+ le pool de ressources par défaut pour les processus externes
+ le pool défini par l’utilisateur pour les processus externes

1. Exécutez l’instruction suivante pour afficher tous les groupes de charges de travail :

    ```sql
    SELECT * FROM sys.resource_governor_workload_groups;
    ```

    **Exemples de résultats**

    |group_id|NAME|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_id|
    |-|-|-|-|-|-|-|-|-|-|
    |1|interne|Moyenne|25|0|0|0|0|1|2|
    |2|par défaut|Moyenne|25|0|0|0|0|2|2|
    |256|ds_wg|Moyenne|25|0|0|0|0|2|256|
  
2.  Utiliser la nouvelle vue de catalogue, [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), pour afficher tous les pools de ressources externes.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools;
    ```

    **Exemples de résultats**
    
    |external_pool_id|NAME|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|par défaut|100|20|0|2|
    |256|ds_ep|100|40|0|1|
  
     Pour plus d’informations, consultez [Affichages catalogue de Resource Governor &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md).
  
3.  Exécutez l’instruction suivante pour retourner des informations sur les ressources des ordinateurs qui sont associés au pool de ressources externe, le cas échéant :
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;
    ```
  
     Dans ce cas, comme les pools ont été créés avec une affinité AUTO, aucune information n’est affichée. Pour plus d’informations, consultez [sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur la gestion des ressources du serveur, consultez :

+  [gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md) 
+ [Vues de gestion dynamique liées à gouverneur de ressources &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)

Pour une vue d’ensemble de la gouvernance de ressources pour machine learning, consultez :

+  [Gouvernance des ressources pour Machine Learning Services](../../advanced-analytics/r/resource-governance-for-r-services.md)
