---
title: sys.syslogins (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syslogins_TSQL
- syslogins
- sys.syslogins
- sys.syslogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syslogins compatibility view
- syslogins system table
ms.assetid: 4cb34f17-a4bb-469f-a218-71f074e6308f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 54372511cab4cbcc3ecd7d2afe875325e105163d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62671928"
---
# <a name="syssyslogins-transact-sql"></a>sys.syslogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque compte de connexion.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] à la [version actuelle](https://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**sid**|**varbinary(85)**|Identificateur de sécurité.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**createdate**|**datetime**|Date d'ajout de la connexion.|  
|**updatedate**|**datetime**|Date de mise à jour de la connexion.|  
|**accdate**|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totcpu**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totio**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**spacelimit**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**timelimit**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**resultlimit**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**nom**|**sysname**|Nom de connexion de l’utilisateur.|  
|**dbname**|**sysname**|Nom de la base de données par défaut de l'utilisateur lorsqu'une connexion est établie.|  
|**password**|**nvarchar(128)**|Renvoie NULL.|  
|**language**|**sysname**|Langue par défaut de l'utilisateur.|  
|**denylogin**|**Int**|1 = La connexion concerne un utilisateur ou un groupe [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows et l'accès a été refusé.|  
|**hasaccess**|**Int**|1 = La connexion possède les droits d'accès au serveur.|  
|**isntname**|**Int**|1 = La connexion est un utilisateur ou un groupe Windows.<br /><br /> 0 = Il s'agit d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**isntgroup**|**Int**|1 = La connexion est un groupe Windows.|  
|**isntuser**|**Int**|1 = La connexion est un utilisateur Windows.|  
|**sysadmin**|**Int**|1 = connexion concerne un membre de la **sysadmin** rôle de serveur.|  
|**securityadmin**|**Int**|1 = connexion concerne un membre de la **securityadmin** rôle de serveur.|  
|**serveradmin**|**Int**|1 = connexion concerne un membre de la **serveradmin** rôle serveur fixe.|  
|**setupadmin**|**Int**|1 = connexion concerne un membre de la **setupadmin** rôle serveur fixe.|  
|**processadmin**|**Int**|1 = connexion concerne un membre de la **processadmin** rôle serveur fixe.|  
|**diskadmin**|**Int**|1 = connexion concerne un membre de la **diskadmin** rôle serveur fixe.|  
|**dbcreator**|**Int**|1 = connexion concerne un membre de la **dbcreator** rôle serveur fixe.|  
|**bulkadmin**|**Int**|1 = connexion concerne un membre de la **bulkadmin** rôle serveur fixe.|  
|**loginname**|**nvarchar(128)**|Nom de connexion de l’utilisateur. Fourni pour la compatibilité ascendante.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
