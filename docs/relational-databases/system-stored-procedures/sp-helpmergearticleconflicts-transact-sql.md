---
title: sp_helpmergearticleconflicts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergearticleconflicts
- sp_helpmergearticleconflicts_TSQL
helpviewer_keywords:
- sp_helpmergearticleconflicts
ms.assetid: 4678a2b9-9a5f-4193-a20d-2e11fc896c3a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 776f46d1f2e61c0f866352ee9c373e4619a2e282
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893559"
---
# <a name="sp_helpmergearticleconflicts-transact-sql"></a>sp_helpmergearticleconflicts (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Renvoie les articles de la publication qui sont en conflit. Cette procédure stockée est exécutée sur la base de données de publication du serveur de publication ou sur la base de données d'abonnement de fusion de l'Abonné.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpmergearticleconflicts [ [ @publication = ] 'publication' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publsher_db' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication de fusion. *publication* est de **type sysname**, avec la valeur par défaut **%** , qui retourne tous les Articles de la base de données qui ont des conflits.  
  
`[ @publisher = ] 'publisher'`Nom du serveur de publication. *Publisher* est de **type sysname**, avec NULL comme valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'`Nom de la base de données du serveur de publication. *publisher_db* est de **type sysname**, avec NULL comme valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**article**|**sysname**|Nom de l'article.|  
|**source_owner**|**sysname**|Propriétaire de l'objet source.|  
|**source_object**|**nvarchar(386**|Nom de l'objet source.|  
|**conflict_table**|**nvarchar(258)**|Nom de la table stockant les conflits d'insertion ou de mise à jour.|  
|**guidcolname**|**sysname**|Nom du RowGuidCol de l'objet source.|  
|**centralized_conflicts**|**int**|Spécifie si les enregistrements des conflits sont stockés sur le serveur de publication donné.|  
  
 Si l’article n’a que des conflits de suppression et aucune ligne **conflict_table** , le nom du **conflict_table** dans le jeu de résultats est null.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Remarques  
 **sp_helpmergearticleconflicts** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** et du rôle de base de données fixe **db_owner** peuvent exécuter **sp_helpmergearticleconflicts**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
