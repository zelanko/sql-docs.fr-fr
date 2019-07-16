---
title: Sys.sysservers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysservers
- sysservers_TSQL
- sysservers
- sys.sysservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysservers system table
- sys.sysservers compatibility view
ms.assetid: d02f186f-c00f-44a6-b38d-dc78a3d2145b
author: rothja
ms.author: jroth
ms.openlocfilehash: 03875d828940a2baa5d9f30f7beb58adb77abf07
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68018109"
---
# <a name="syssysservers-transact-sql"></a>sys.sysservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque serveur auquel une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut accéder en tant que source de données OLE DB.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**srvid**|**smallint**|ID (pour utilisation locale uniquement) du serveur distant.|  
|**srvstatus**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**srvname**|**sysname**|Nom du serveur.|  
|**srvproduct**|**sysname**|Nom de produit du serveur distant|  
|**ProviderName**|**nvarchar(128)**|Nom du fournisseur OLE DB pour l'accès au serveur.|  
|**datasource**|**nvarchar(4000)**|Valeur de source de données OLE DB.|  
|**location**|**nvarchar(4000)**|Valeur d'emplacement OLE DB.|  
|**ProviderString**|**nvarchar(4000)**|Valeur de chaîne de fournisseur OLE DB.|  
|**schemadate**|**datetime**|Date de la dernière mise à jour de la ligne.|  
|**TopologyX**|**int**|Non utilisé.|  
|**TopologyY**|**int**|Non utilisé.|  
|**catalog**|**sysname**|Catalogue utilisé lors de la connexion à un fournisseur OLE DB.|  
|**srvcollation**|**sysname**|Classement du serveur.|  
|**connecttimeout**|**Int**|Paramètre de délai d'expiration de la connexion serveur.|  
|**querytimeout**|**int**|Paramètre de délai d'expiration des requêtes envoyées au serveur.|  
|**srvnetname**|**char(30)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**isremote**|**bit**|1 = serveur distant<br /><br /> 0 = serveur lié|  
|**rpc**|**bit**|1 = **sp_serveroption@rpc** définie sur **true** ou **sur**.<br /><br /> 0 = **sp_serveroption@rpc** définie sur **false** ou **hors**.|  
|**pub**|**bit**|1 = **sp_serveroption@pub** définie sur **true** ou **sur**.<br /><br /> 0 = **sp_serveroption@pub** définie sur **false** ou **hors**.|  
|**sub**|**bit**|1 = **sp_serveroption@sub** définie sur **true** ou **sur**.<br /><br /> 0 = **sp_serveroption@sub** définie sur **false** ou **hors**.|  
|**dist**|**bit**|1 = **sp_serveroption@dist** définie sur **true** ou **sur**.<br /><br /> 0 = **sp_serveroption@dist** définie sur **false** ou **hors**.|  
|**dpub**|**bit**|1 = **sp_serveroption@dpub** définie sur **true** ou **sur**.<br /><br /> 0 = **sp_serveroption@dpub** définie sur **false** ou **hors**.|  
|**rpcout**|**bit**|1 =  **sp_serveroption@rpc out** définie sur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@rpc out** définie sur **false** ou **hors**.|  
|**dataaccess**|**bit**|1 =  **sp_serveroption@data accès** définie sur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@data accès** définie sur **false** ou **hors**.|  
|**collationcompatible**|**bit**|1 =  **sp_serveroption@collation compatible** définie sur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@collation compatible** définie sur **false** ou **hors**.|  
|**system**|**bit**|1 = **sp_serveroption@system** définie sur **true** ou **sur**.<br /><br /> 0 = **sp_serveroption@system** définie sur **false** ou **hors**.|  
|**useremotecollation**|**bit**|1 =  **sp_serveroption@remote classement** définie sur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@remote classement** définie sur **false** ou **hors**.|  
|**lazyschemavalidation**|**bit**|1 =  **sp_serveroption@lazy validation de schéma** définie sur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@lazy validation de schéma** définie sur **false** ou **hors**.|  
|**classement**|**sysname**|Classement du serveur tel que défini par  **sp_serveroption@collation nom**.|  
|**nonsqlsub**|bit|0 : le serveur est une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> 1 : le serveur n'est pas une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
