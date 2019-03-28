---
title: sp_helpdistributiondb (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistributiondb_TSQL
- sp_helpdistributiondb
helpviewer_keywords:
- sp_helpdistributiondb
ms.assetid: a2917020-26d1-4011-99f8-9212d120fd2d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5d143889672754be353b5868e955841d9e2869bc
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533331"
---
# <a name="sphelpdistributiondb-transact-sql"></a>sp_helpdistributiondb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche les propriétés de la base de données de distribution spécifiée. Cette procédure stockée est exécutée au niveau du serveur de distribution sur la base de données de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpdistributiondb [ [ @database= ] 'database_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @database = ] 'database_name'` Est le nom de la base de données pour lequel les propriétés sont retournées. *database_name* est **sysname**, avec une valeur par défaut **%** pour toutes les bases de données associées avec le serveur de distribution et sur lesquelles l’utilisateur dispose d’autorisations.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom de la base de données de distribution.|  
|**min_distretention**|**Int**|Durée minimale de rétention (exprimée en heures) avant la suppression des transactions|  
|**max_distretention**|**Int**|Durée maximale de rétention (exprimée en heures) avant la suppression des transactions|  
|**rétention de l’historique**|**Int**|Nombre d'heures de rétention de l'historique|  
|**history_cleanup_agent**|**sysname**|Nom de l'Agent de nettoyage de l'historique|  
|**distribution_cleanup_agent**|**sysname**|Nom de l'Agent de nettoyage de distribution.|  
|**status**|**Int**|À usage interne uniquement|  
|**data_folder**|**nvarchar(255)**|Nom du répertoire utilisé pour stocker les fichiers de la base de données.|  
|**data_file**|**nvarchar(255)**|Nom du fichier de base de données.|  
|**data_file_size**|**Int**|Taille initiale du fichier de données en mégaoctets.|  
|**log_folder**|**nvarchar(255)**|Nom du répertoire du fichier de base de données.|  
|**log_file**|**nvarchar(255)**|Nom du fichier journal.|  
|**log_file_size**|**Int**|Taille initiale du fichier du journal en mégaoctets.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpdistributiondb** est utilisée dans tous les types de réplication.  
  
## <a name="permissions"></a>Autorisations  
 Membres de la **db_owner** rôle de base de données fixe ou le **replmonitor** rôle dans une base de données de distribution et les utilisateurs dans la liste d’accès d’une publication à l’aide de la base de données de distribution peuvent exécuter. **sp_helpdistributiondb** pour retourner des informations relatives aux fichiers. Membres de la **public** du rôle peuvent exécuter **sp_helpdistributiondb** pour retourner les informations non liées aux fichiers des bases de données de distribution auxquels ils ont accès.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)   
 [sp_changedistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_dropdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
