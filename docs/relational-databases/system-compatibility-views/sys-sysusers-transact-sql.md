---
title: Sys.sysusers (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysusers
- sys.sysusers_TSQL
- sysusers_TSQL
- sysusers
dev_langs: TSQL
helpviewer_keywords:
- sysusers system table
- sys.sysusers compatibility view
ms.assetid: 5f0e6a8d-c983-44f6-97e9-aab5bff67d18
caps.latest.revision: "36"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f4c732149e7b7b2aaeb92a6d8930b3f3ecfae388
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syssysusers-transact-sql"></a>sys.sysusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque [!INCLUDE[msCoName](../../includes/msconame-md.md)] utilisateur Windows, le groupe Windows, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisateur, ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rôle dans la base de données.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**UID**|**smallint**|ID d'utilisateur, unique dans cette base de données.<br /><br /> 1 = Propriétaire de la base de données<br /><br /> Déborde ou retourne la valeur NULL si le nombre d'utilisateurs et de rôles dépasse 32 767.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**nom**|**sysname**|Nom d'utilisateur ou de groupe, unique dans cette base de données.|  
|**SID**|**varbinary(85)**|Identificateur de sécurité pour cette entrée.|  
|**rôles**|**varbinary(2048)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**CREATEDATE**|**datetime**|Date de l'ajout du compte.|  
|**updatedate**|**datetime**|Date de la dernière modification du compte.|  
|**altuid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> Déborde ou retourne la valeur NULL si le nombre d'utilisateurs et de rôles dépasse 32 767.|  
|**mot de passe**|**varbinary(256)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**GID**|**smallint**|ID du groupe auquel l'utilisateur appartient. Si **uid** est identique à **gid**, cette entrée définit un groupe. Déborde ou retourne la valeur NULL si le nombre total d'utilisateurs et de groupes dépasse 32 767.|  
|**environ**|**varchar (255)**|Réservé.|  
|**hasdbaccess**|**int**|1 = Le compte a accès à la base de données.|  
|**IsLogin**|**int**|1 = Le compte est un groupe Windows ou un utilisateur Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bénéficiant d'un compte de connexion.|  
|**isntname**|**int**|1 = Le compte est un utilisateur ou groupe Windows.|  
|**isntgroup**|**int**|1 = Le compte est un groupe Windows.|  
|**isntuser**|**int**|1 = Le compte est un utilisateur Windows.|  
|**issqluser**|**int**|1 = Le compte est un utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**isaliased**|**int**|1 = Le compte est l'alias d'un autre utilisateur.|  
|**issqlrole**|**int**|1 = Le compte est un rôle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**isapprole**|**int**|1 = Le compte est un rôle d’application.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système pour les vues système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
