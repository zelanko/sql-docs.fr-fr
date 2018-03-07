---
title: MODIFIER le POOL de ressources externes (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 11/13/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_EXTERNAL_RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL RESOURCE POOL statement
ms.assetid: 634c327d-971b-49ba-b8a2-e243a04040db
caps.latest.revision: 
author: jeannt
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb4073a8114e953dc9df87614a63e074ab8c9683
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="alter-external-resource-pool-transact-sql"></a>MODIFIER le POOL de ressources externes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**S’applique à :** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] et [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)][!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Modifie un pool externe du gouverneur de ressources qui spécifie les ressources qui peuvent être utilisées par les processus externes. 

+ Pour [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] dans [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)], le pool externe régit `rterm.exe`, `BxlServer.exe`et les autres processus engendrés par ces derniers.

+ Pour [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] dans SQL Server 2017, le pool externe régit les processus R répertoriées pour la version précédente, ainsi que `python.exe`, `BxlServer.exe`et les autres processus engendrés par ces derniers.

 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

## <a name="syntax"></a>Syntaxe

```sql
ALTER EXTERNAL RESOURCE POOL { pool_name | "default" }
[ WITH (
    [ MAX_CPU_PERCENT = value ]
    [ [ , ] AFFINITY CPU =
            {
                AUTO
              | ( <cpu_range_spec> )
              | NUMANODE = (( <NUMA_node_id> )
            } ]   
    [ [ , ] MAX_MEMORY_PERCENT = value ]
    [ [ , ] MAX_PROCESSES = value ]
    )
]
[ ; ]
  
<CPU_range_spec> ::=
{ CPU_ID | CPU_ID  TO CPU_ID } [ ,...n ]
```  
  
## <a name="arguments"></a>Arguments

{ *pool_name* | « default »}  
Est le nom d’un pool de ressources externes définis par l’utilisateur existant ou le pool de ressources externes par défaut qui est créé lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé.
« default » doit être placé entre guillemets (« ») ou des crochets ([]) lorsqu’il est utilisé avec `ALTER EXTERNAL RESOURCE POOL` pour éviter tout conflit avec `DEFAULT`, qui est un système de mot réservé.


MAX_CPU_PERCENT =*valeur*  
Spécifie la processeur bande passante moyenne maximale que toutes les demandes dans le pool de ressources externes peuvent recevoir des cas de contention du processeur. *valeur* est un entier dont le paramètre par défaut est 100. La plage autorisée pour *valeur* est comprise entre 1 et 100.


AFFINITÉ {UC = AUTO | ( \<CPU_range_spec >) | NUMANODE = (\<NUMA_node_range_spec >)}  
Attachez le pool de ressources externes à des processeurs spécifiques. La valeur par défaut est AUTO.

Affinité du processeur = **(** \<CPU_range_spec > **)** mappe le pool de ressources externes à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unités centrales identifiés par le CPU_IDs donné. Lorsque vous utilisez AFFINITY NUMANODE = **(** \<NUMA_node_range_spec > **)**, le pool de ressources externe est possède une affinité avec le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UC physiques correspondant au nœud NUMA donné ou de la plage de nœuds.


MAX_MEMORY_PERCENT =*valeur*  
Spécifie la mémoire totale du serveur qui peut être utilisée par les demandes dans ce pool de ressources externes. *valeur* est un entier dont le paramètre par défaut est 100. La plage autorisée pour *valeur* est comprise entre 1 et 100.


MAX_PROCESSES =*valeur*  
Spécifie le nombre maximal de processus autorisé pour le pool de ressources externes. Spécifiez 0 pour définir un seuil illimité pour le pool, ce qui est lié par la suite uniquement par les ressources de l’ordinateur. La valeur par défaut est 0.

## <a name="remarks"></a>Notes

Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] implémente le pool de ressources lorsque vous exécutez le [ALTER RESOURCE GOVERNOR RECONFIGURE](../../t-sql/statements/alter-resource-governor-transact-sql.md) instruction.

Pour obtenir des informations générales sur les pools de ressources, consultez [Pool de ressources du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor-resource-pool.md), [sys.resource_governor_external_resource_pools &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), et [sys.dm_resource_governor_external_resource_pool_affinity &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md).  

Pour plus d’informations spécifiques à l’utilisation de pools de ressources externes pour gérer les tâches de machine learning, consultez [la gouvernance de ressources pour l’apprentissage dans SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)...
## <a name="permissions"></a>Permissions

Nécessite l'autorisation `CONTROL SERVER`.

## <a name="examples"></a>Exemples

L’instruction suivante modifie un pool externe, en limitant l’utilisation du processeur à 50 pour cent et la mémoire maximale de 25 pour cent de la mémoire disponible sur l’ordinateur.
  
```sql
ALTER EXTERNAL RESOURCE POOL ep_1
WITH (
    MAX_CPU_PERCENT = 50
    , AFFINITY CPU = AUTO
    , MAX_MEMORY_PERCENT = 25
);
GO
ALTER RESOURCE GOVERNOR RECONFIGURE;
GO
```

## <a name="see-also"></a>Voir aussi

[Gouvernance de ressources pour l’apprentissage dans SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)

[external scripts enabled (option de configuration de serveur)](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)

[SUPPRIMER le POOL de ressources externes &#40; Transact-SQL &#41;](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)

[ALTER RESOURCE POOL &#40; Transact-SQL &#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)

[CRÉER un groupe de charges de travail &#40; Transact-SQL &#41;](../../t-sql/statements/create-workload-group-transact-sql.md)

[Pool de ressources de Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)

[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md) 
