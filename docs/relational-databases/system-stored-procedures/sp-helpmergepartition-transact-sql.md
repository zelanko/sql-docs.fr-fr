---
title: sp_helpmergepartition (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergepartition
- sp_helpmergepartition_TSQL
helpviewer_keywords:
- sp_helpmergepartition
ms.assetid: 184188cc-f519-445d-97ce-aae38f1eb550
author: stevestein
ms.author: sstein
ms.openlocfilehash: 01155b1fb294660c92bfa975bc04de8f748b730f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68137661"
---
# <a name="sp_helpmergepartition-transact-sql"></a>sp_helpmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations de partition pour la publication de fusion spécifiée. Cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpmergepartition [ @publication= ] 'publication'   
    [ , [ @suser_sname = ] 'suser_sname' ]  
    [ , [ @host_name = ] 'host_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @suser_sname = ] 'suser_sname'`Valeur SUSER_SNAME utilisée pour définir une partition. *SUSER_SNAME* est de **type sysname**, avec NULL comme valeur par défaut. Précisez ce paramètre pour limiter le jeu de résultats aux seules partitions dans lesquelles SUSER_SNAME correspond à la valeur fournie.  
  
> [!NOTE]  
>  Lorsque *SUSER_SNAME* est fourni, *HOST_NAME* doit avoir la valeur null  
  
`[ @host_name = ] 'host_name'`Valeur HOST_NAME utilisée pour définir une partition. *HOST_NAME* est de **type sysname**, avec NULL comme valeur par défaut. Précisez ce paramètre pour limiter le jeu de résultats aux seules partitions dans lesquelles HOST_NAME correspond à la valeur fournie.  
  
> [!NOTE]  
>  Lorsque *SUSER_SNAME* est fourni, *HOST_NAME* doit avoir la valeur null  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**non**|**int**|Identifie la partition de l'Abonné.|  
|**host_name**|**sysname**|Valeur utilisée lors de la création de la partition pour un abonnement filtré par la valeur de la fonction [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) sur l’abonné.|  
|**suser_sname**|**sysname**|Valeur utilisée lors de la création de la partition pour un abonnement filtré par la valeur de la fonction [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) sur l’abonné.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Emplacement de l'instantané des données filtrées pour la partition de l'Abonné.|  
|**date_refreshed**|**datetime**|Date de la dernière exécution du travail d'instantané visant à générer l'instantané de données filtrées pour la partition.|  
|**dynamic_snapshot_jobid**|**uniqueidentifier**|Identifie le travail qui crée l'instantané de données filtrées pour une partition.|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpmergepartition** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** et du rôle de base de données fixe **db_owner** peuvent exécuter **sp_helpmergepartition**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addmergepartition &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)   
 [sp_dropmergepartition &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql.md)  
  
  
