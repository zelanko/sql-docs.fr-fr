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
manager: craigg
ms.openlocfilehash: e31a8827f940e0dd5a3debe2d03bf675f33df3cd
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591173"
---
# <a name="sphelpmergedeleteconflictrows-transact-sql"></a>sp_helpmergedeleteconflictrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie des informations sur les lignes de données ayant perdu des conflits de suppression. Cette procédure stockée est exécutée sur la base de données de publication au niveau du serveur de publication ou sur la base de données d'abonnement au niveau de l'abonné lorsque l'enregistrement décentralisé des conflits est utilisé.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpmergedeleteconflictrows [ [ @publication = ] 'publication']  
    [ , [ @source_object = ] 'source_object']  
    [ , [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publsher_db'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=**] **'**_publication_**'**  
 Nom de la publication. *publication* est **sysname**, avec une valeur par défaut **%**. Si la publication est spécifiée, tous les conflits qualifiés par la publication sont renvoyés.  
  
 [  **@source_object=**] **'**_source_object_**'**  
 Est le nom de l’objet source. *source_object* est **nvarchar (386)**, avec NULL comme valeur par défaut.  
  
 [  **@publisher=**] **'**_publisher_**'**  
 Est le nom du serveur de publication. *publisher* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@publisher_db=**] **'**_publisher_db_**'**  
 Est le nom de la base de données du serveur de publication. *publisher_db* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**source_object**|**nvarchar(386)**|Objet source du conflit de suppression.|  
|**ROWGUID**|**uniqueidentifier**|Identificateur de ligne associé au conflit de suppression.|  
|**conflict_type**|**Int**|Code indiquant le type de conflit :<br /><br /> **1** = UpdateConflict : le conflit est détecté au niveau de la ligne.<br /><br /> **2** = ColumnUpdateConflict : Conflit est détecté au niveau de la colonne.<br /><br /> **3** = UpdateDeleteWinsConflict : la suppression gagne le conflit.<br /><br /> **4** = UpdateWinsDeleteConflict : le GUID de ligne supprimé qui perd le conflit est enregistré dans cette table.<br /><br /> **5** = UploadInsertFailed : impossibilité d'appliquer sur le serveur de publication l'insertion effectuée sur l'abonné.<br /><br /> **6** = DownloadInsertFailed : impossibilité d'appliquer sur l'abonné l'insertion effectuée sur le serveur de publication.<br /><br /> **7** = UploadDeleteFailed : impossibilité de télécharger vers le serveur de publication la suppression appliquée sur l'abonné.<br /><br /> **8** = DownloadDeleteFailed : impossibilité de télécharger vers l'abonné la suppression appliquée sur le serveur de publication.<br /><br /> **9** = UploadUpdateFailed : impossibilité d'appliquer sur le serveur de publication la mise à jour effectuée sur l'abonné.<br /><br /> **10** = DownloadUpdateFailed : impossibilité d'appliquer sur l'abonné la mise à jour effectuée sur le serveur de publication.|  
|**reason_code**|**Int**|Code d'erreur pouvant dépendre du contexte.|  
|**reason_text**|**varchar(720)**|Description de l'erreur qui peut dépendre du contexte.|  
|**origin_datasource**|**varchar(255)**|Origine du conflit.|  
|**pubid**|**uniqueidentifier**|Identificateur de publication.|  
|**MSrepl_create_time**|**datetime**|Moment où l'information sur les conflits a été ajoutée.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpmergedeleteconflictrows** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe et le **db_owner** rôle de base de données fixe peuvent exécuter **sp_helpmergedeleteconflictrows**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
