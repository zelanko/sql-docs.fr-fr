---
title: sp_helpmergedeleteconflictrows (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergedeleteconflictrows
- sp_helpmergedeleteconflictrows_TSQL
helpviewer_keywords:
- sp_helpmergedeleteconflictrows
ms.assetid: 222be651-5690-4341-9dfb-f9ec1d80c970
author: stevestein
ms.author: sstein
ms.openlocfilehash: 86e8d3d21246cbb308db5b698a29f2b02ce45ac3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68137745"
---
# <a name="sp_helpmergedeleteconflictrows-transact-sql"></a>sp_helpmergedeleteconflictrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie des informations sur les lignes de données ayant perdu des conflits de suppression. Cette procédure stockée est exécutée sur la base de données de publication au niveau du serveur de publication ou sur la base de données d'abonnement au niveau de l'abonné lorsque l'enregistrement décentralisé des conflits est utilisé.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpmergedeleteconflictrows [ [ @publication = ] 'publication']  
    [ , [ @source_object = ] 'source_object']  
    [ , [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publsher_db'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication. *publication* est de **%** **type sysname**, avec la valeur par défaut. Si la publication est spécifiée, tous les conflits qualifiés par la publication sont renvoyés.  
  
`[ @source_object = ] 'source_object'`Nom de l’objet source. *source_object* est de type **nvarchar (386)**, avec NULL comme valeur par défaut.  
  
`[ @publisher = ] 'publisher'`Nom du serveur de publication. *Publisher* est de **type sysname**, avec NULL comme valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'`Nom de la base de données du serveur de publication. *publisher_db* est de **type sysname**, avec NULL comme valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**source_object**|**nvarchar(386**|Objet source du conflit de suppression.|  
|**GuidLigne**|**uniqueidentifier**|Identificateur de ligne associé au conflit de suppression.|  
|**conflict_type**|**int**|Code indiquant le type de conflit :<br /><br /> **1** = UpdateConflict : un conflit est détecté au niveau de la ligne.<br /><br /> **2** = ColumnUpdateConflict : conflit détecté au niveau de la colonne.<br /><br /> **3** = UpdateDeleteWinsConflict : la suppression gagne le conflit.<br /><br /> **4** = UpdateWinsDeleteConflict : le rowguid supprimé qui perd le conflit est enregistré dans cette table.<br /><br /> **5** = UploadInsertFailed : l’insertion à partir de l’abonné n’a pas pu être appliquée sur le serveur de publication.<br /><br /> **6** = DownloadInsertFailed : l’insertion à partir du serveur de publication n’a pas pu être appliquée sur l’abonné.<br /><br /> **7** = UploadDeleteFailed : la suppression sur l’abonné n’a pas pu être téléchargée sur le serveur de publication.<br /><br /> **8** = DownloadDeleteFailed : la suppression sur le serveur de publication n’a pas pu être téléchargée sur l’abonné.<br /><br /> **9** = UploadUpdateFailed : la mise à jour sur l’abonné n’a pas pu être appliquée sur le serveur de publication.<br /><br /> **10** = DownloadUpdateFailed : la mise à jour sur le serveur de publication n’a pas pu être appliquée à l’abonné.|  
|**reason_code**|**Tiers**|Code d'erreur pouvant dépendre du contexte.|  
|**reason_text**|**varchar (720)**|Description de l'erreur qui peut dépendre du contexte.|  
|**origin_datasource**|**varchar(255**|Origine du conflit.|  
|**pubid**|**uniqueidentifier**|Identificateur de publication.|  
|**MSrepl_create_time**|**DATETIME**|Moment où l'information sur les conflits a été ajoutée.|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpmergedeleteconflictrows** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** et du rôle de base de données fixe **db_owner** peuvent exécuter **sp_helpmergedeleteconflictrows**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
