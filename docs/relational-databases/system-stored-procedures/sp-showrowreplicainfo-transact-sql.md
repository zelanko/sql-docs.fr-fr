---
title: sp_showrowreplicainfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_showrowreplicainfo_TSQL
- sp_showrowreplicainfo
helpviewer_keywords:
- sp_showrowreplicainfo
ms.assetid: 6a9dbc1a-e1e1-40c4-97cb-8164a2288f76
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0d009b05fea2a2c587f97dc4b2416588932ad0bc
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58530361"
---
# <a name="spshowrowreplicainfo-transact-sql"></a>sp_showrowreplicainfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche des informations concernant une ligne d'une table utilisée en tant qu'article dans une réplication de fusion. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_showrowreplicainfo [ [ @ownername = ] 'ownername' ]  
    [ , [ @tablename =] 'tablename' ]   
        , [ @rowguid =] rowguid   
    [ , [ @show = ] 'show' ]   
```  
  
## <a name="arguments"></a>Arguments  
`[ @ownername = ] 'ownername'` Est le nom du propriétaire de la table. *ownername* est **sysname**, avec NULL comme valeur par défaut. Ce paramètre est utile pour différencier les tables si une base de données contient plusieurs tables du même nom, chacune de ces tables ayant un propriétaire différent.  
  
`[ @tablename = ] 'tablename'` Est le nom de la table qui contient la ligne pour laquelle les informations sont retournées. *TableName* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @rowguid = ] rowguid` Est l’identificateur unique de la ligne. *ROWGUID* est **uniqueidentifier**, sans valeur par défaut.  
  
`[ @show = ] 'show'` Détermine la quantité d’informations à renvoyer dans le jeu de résultats. *afficher* est **nvarchar (20)** avec une valeur par défaut à la fois. Si **ligne**, uniquement les informations de version de ligne sont retournées. Si **colonnes**, uniquement les informations de version de colonne sont retournées. Si **à la fois**, à la fois lignes et les informations de colonne sont retournées.  
  
## <a name="result-sets-for-row-information"></a>Ensemble de résultats pour les informations de ligne  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|Nom du serveur hébergeant la base de données qui a effectué l'entrée de la version de ligne.|  
|**db_name**|**sysname**|Nom de la base de données qui a effectué cette entrée.|  
|**db_nickname**|**binary(6)**|Surnom de la base de données qui a effectué cette entrée.|  
|**version**|**Int**|Version de l'entrée.|  
|**current_state**|**nvarchar(9)**|Retourne des informations sur l'état actuel de la ligne.<br /><br /> **y** -données de la ligne représente l’état actuel de la ligne.<br /><br /> **n** -données de ligne ne représente pas l’état actuel de la ligne.<br /><br /> **\<n/a >** - non applicable.<br /><br /> **\<inconnu >** -Impossible de déterminer l’état actuel.|  
|**rowversion_table**|**nchar(17)**|Indique si les versions de ligne sont stockées dans le [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) table ou la [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) table.|  
|**comment**|**nvarchar(255)**|Informations supplémentaires concernant l'entrée de version de cette ligne. En général, ce champ est vide.|  
  
## <a name="result-sets-for-column-information"></a>Ensemble de résultats pour les informations de colonne  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|Nom du serveur hébergeant la base de données qui a effectué l'entrée de la version de colonne.|  
|**db_name**|**sysname**|Nom de la base de données qui a effectué cette entrée.|  
|**db_nickname**|**binary(6)**|Surnom de la base de données qui a effectué cette entrée.|  
|**version**|**Int**|Version de l'entrée.|  
|**colname**|**sysname**|Nom de la colonne d'article que l'entrée de la version de colonne représente.|  
|**comment**|**nvarchar(255)**|Informations supplémentaires concernant l'entrée de version de cette colonne. En général, ce champ est vide.|  
  
## <a name="result-set-for-both"></a>Ensemble de résultats pour la ligne et la colonne  
 Si la valeur **à la fois** est choisi pour *afficher*, jeux de résultats de la ligne et la colonne est retournée.  
  
## <a name="remarks"></a>Notes  
 **sp_showrowreplicainfo** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 **sp_showrowreplicainfo** peut uniquement être exécutée par les membres de la **db_owner** rôle de base de données fixe sur la base de données de publication ou par les membres de la liste d’accès de publication (PAL) sur la base de données de publication.  
  
## <a name="see-also"></a>Voir aussi  
 [Détecter et résoudre les conflits de réplication de fusion](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
