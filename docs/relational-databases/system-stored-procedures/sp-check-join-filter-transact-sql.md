---
title: sp_check_join_filter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- filter_TSQL
- sp_check_TSQL
- sp_check_join_filter
- sp_check_join_filter_TSQL
- join
- join_TSQL
- filter
- sp_check
helpviewer_keywords:
- sp_check_join_filter
ms.assetid: e9699d59-c8c9-45f6-a561-f7f95084a540
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 02c46d74a1e68af322aa50c7b0ac1c3d4f96ee49
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531751"
---
# <a name="spcheckjoinfilter-transact-sql"></a>sp_check_join_filter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  S'utilise pour vérifier un filtre de jointure entre deux tables pour déterminer si la clause du filtre est valide. Cette procédure stockée renvoie également des informations sur le filtre de jointure fourni, y compris s'il est possible de l'utiliser avec des partitions précalculées pour la table donnée. Cette procédure stockée est exécutée sur la base de données du serveur de publication. Pour plus d’informations, consultez [Optimiser les performances des filtres paramétrés avec des partitions précalculées](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_check_join_filter [ @filtered_table = ] 'filtered_table'  
        , [@join_table = ] 'join_table'  
        , [ @join_filterclause = ] 'join_filterclause'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @filtered_table = ] 'filtered_table'` Est le nom d’une table filtrée. *filtered_table* est **nvarchar (400)**, sans valeur par défaut.  
  
`[ @join_table = ] 'join_table'` Est le nom d’une table jointe à *filtered_table*. *join_table* est **nvarchar (400)**, sans valeur par défaut.  
  
`[ @join_filterclause = ] 'join_filterclause'` La clause de filtre de jointure testée. *join_filterclause* est **nvarchar (1000)**, sans valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|Est si la publication est éligible pour les partitions précalculées. où **1** signifie qu’il est partitions peuvent être utilisées, et **0** signifie qu’ils ne peuvent pas être utilisés.|  
|**has_dynamic_filters**|**bit**|Si la clause de filtre fournie comprend au moins une fonction de filtrage paramétré ; où **1** signifie qu’une fonction de filtrage paramétré est utilisée, et **0** signifie qu’une telle fonction n’est pas utilisée.|  
|**dynamic_filters_function_list**|**nvarchar(500)**|Liste des fonctions de la clause du filtre qui définissent un filtrage paramétré pour un article. Chaque fonction est séparée par un point-virgule.|  
|**uses_host_name**|**bit**|Si le [HOST_NAME()](../../t-sql/functions/host-name-transact-sql.md) fonction est utilisée dans la clause de filtre, où **1** signifie que cette fonction est présente.|  
|**uses_suser_sname**|**bit**|Si le [SUSER_SNAME()](../../t-sql/functions/suser-sname-transact-sql.md) fonction est utilisée dans la clause de filtre, où **1** signifie que cette fonction est présente.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_check_join_filter** est utilisé dans la réplication de fusion.  
  
 **sp_check_join_filter** peuvent être exécutées sur toutes les tables associées, même si elles ne sont pas publiées. Cette procédure stockée peut être utilisée pour vérifier une clause de filtre de jointure avant de définir un filtre de jointure entre deux articles.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_check_join_filter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
