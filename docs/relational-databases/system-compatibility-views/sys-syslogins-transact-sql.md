---
title: Sys.syslogins (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 09/08/2017
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
- syslogins_TSQL
- syslogins
- sys.syslogins
- sys.syslogins_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.syslogins compatibility view
- syslogins system table
ms.assetid: 4cb34f17-a4bb-469f-a218-71f074e6308f
caps.latest.revision: "41"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ea9ceaa622c6ad7b39bed9c3e3d2439e56a57210
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syssyslogins-transact-sql"></a>sys.syslogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque compte de connexion.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**SID**|**varbinary(85)**|Identificateur de sécurité.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**CREATEDATE**|**datetime**|Date d'ajout de la connexion.|  
|**updatedate**|**datetime**|Date de mise à jour de la connexion.|  
|**accdate**|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totcpu**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totio**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**spacelimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**TimeLimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**resultlimit au-delà de laquelle**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**nom**|**sysname**|Nom de connexion de l’utilisateur.|  
|**dbname**|**sysname**|Nom de la base de données par défaut de l'utilisateur lorsqu'une connexion est établie.|  
|**mot de passe**|**nvarchar (128)**|Renvoie NULL.|  
|**langage**|**sysname**|Langue par défaut de l'utilisateur.|  
|**denylogin**|**int**|1 = La connexion concerne un utilisateur ou un groupe [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows et l'accès a été refusé.|  
|**hasaccess**|**int**|1 = La connexion possède les droits d'accès au serveur.|  
|**isntname**|**int**|1 = La connexion est un utilisateur ou un groupe Windows.<br /><br /> 0 = Il s'agit d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**isntgroup**|**int**|1 = La connexion est un groupe Windows.|  
|**isntuser**|**int**|1 = La connexion est un utilisateur Windows.|  
|**sysadmin**|**int**|1 = connexion concerne un membre de la **sysadmin** rôle de serveur.|  
|**securityadmin**|**int**|1 = connexion concerne un membre de la **securityadmin** rôle de serveur.|  
|**serveradmin**|**int**|1 = connexion concerne un membre de la **serveradmin** rôle serveur fixe.|  
|**setupadmin**|**int**|1 = connexion concerne un membre de la **setupadmin** rôle serveur fixe.|  
|**processadmin**|**int**|1 = connexion concerne un membre de la **processadmin** rôle serveur fixe.|  
|**diskadmin**|**int**|1 = connexion concerne un membre de la **diskadmin** rôle serveur fixe.|  
|**dbcreator**|**int**|1 = connexion concerne un membre de la **dbcreator** rôle serveur fixe.|  
|**bulkadmin**|**int**|1 = connexion concerne un membre de la **bulkadmin** rôle serveur fixe.|  
|**LoginName**|**nvarchar (128)**|Nom de connexion de l’utilisateur. Fourni pour la compatibilité ascendante.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système pour les vues système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
