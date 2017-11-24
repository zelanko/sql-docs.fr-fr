---
title: Sys.sysservers (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysservers
- sysservers_TSQL
- sysservers
- sys.sysservers_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sysservers system table
- sys.sysservers compatibility view
ms.assetid: d02f186f-c00f-44a6-b38d-dc78a3d2145b
caps.latest.revision: "27"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e05b06dd6a37f6330f715b374e3fe46515c3f37d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syssysservers-transact-sql"></a>sys.sysservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque serveur auquel une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut accéder en tant que source de données OLE DB.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**srvid avec**|**smallint**|ID (pour utilisation locale uniquement) du serveur distant.|  
|**srvstatus**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**SRVNAME**|**sysname**|Nom du serveur.|  
|**srvproduct**|**sysname**|Nom de produit du serveur distant|  
|**ProviderName**|**nvarchar (128)**|Nom du fournisseur OLE DB pour l'accès au serveur.|  
|**source de données**|**nvarchar(4000)**|Valeur de source de données OLE DB.|  
|**emplacement**|**nvarchar(4000)**|Valeur d'emplacement OLE DB.|  
|**ProviderString**|**nvarchar(4000)**|Valeur de chaîne de fournisseur OLE DB.|  
|**schemadate**|**datetime**|Date de la dernière mise à jour de la ligne.|  
|**TopologyX**|**int**|Non utilisé.|  
|**TopologyY**|**int**|Non utilisé.|  
|**catalogue**|**sysname**|Catalogue utilisé lors de la connexion à un fournisseur OLE DB.|  
|**srvcollation**|**sysname**|Classement du serveur.|  
|**ConnectTimeout**|**int**|Paramètre de délai d'expiration de la connexion serveur.|  
|**QueryTimeout**|**int**|Paramètre de délai d'expiration des requêtes envoyées au serveur.|  
|**srvnetname**|**char (30)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**isremote**|**bit**|1 = serveur distant<br /><br /> 0 = serveur lié|  
|**RPC**|**bit**|1 =  **sp_serveroption@rpc**  la valeur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@rpc**  la valeur **false** ou **hors**.|  
|**pub**|**bit**|1 =  **sp_serveroption@pub**  la valeur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@pub**  la valeur **false** ou **hors**.|  
|**Sub**|**bit**|1 =  **sp_serveroption@sub**  la valeur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@sub**  la valeur **false** ou **hors**.|  
|**serveur de distribution**|**bit**|1 =  **sp_serveroption@dist**  la valeur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@dist**  la valeur **false** ou **hors**.|  
|**dpub**|**bit**|1 =  **sp_serveroption@dpub**  la valeur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@dpub**  la valeur **false** ou **hors**.|  
|**rpcout**|**bit**|1 =  **sp_serveroption@rpc hors** la valeur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@rpc hors** la valeur **false** ou **hors**.|  
|**accès aux données**|**bit**|1 =  **sp_serveroption@data accès** la valeur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@data accès** la valeur **false** ou **hors**.|  
|**collationcompatible**|**bit**|1 =  **sp_serveroption@collation compatible** la valeur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@collation compatible** la valeur **false** ou **hors**.|  
|**système**|**bit**|1 =  **sp_serveroption@system**  la valeur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@system**  la valeur **false** ou **hors**.|  
|**UseRemoteCollation**|**bit**|1 =  **sp_serveroption@remote classement** la valeur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@remote classement** la valeur **false** ou **hors**.|  
|**lazyschemavalidation**|**bit**|1 =  **sp_serveroption@lazy validation de schéma** la valeur **true** ou **sur**.<br /><br /> 0 =  **sp_serveroption@lazy validation de schéma** la valeur **false** ou **hors**.|  
|**classement**|**sysname**|Classement du serveur en tant que jeu par  **sp_serveroption@collation nom**.|  
|**nonsqlsub**|bit|0 : le serveur est une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> 1 : le serveur n'est pas une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système pour les vues système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
