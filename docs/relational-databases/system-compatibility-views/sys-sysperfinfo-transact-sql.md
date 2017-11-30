---
title: Sys.sysperfinfo (Transact-SQL) | Documents Microsoft
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
- sysperfinfo_TSQL
- sys.sysperfinfo_TSQL
- sys.sysperfinfo
- sysperfinfo
dev_langs: TSQL
helpviewer_keywords:
- sys.sysperfinfo compatibility view
- sysperfinfo system table
ms.assetid: e22a81cd-27de-4690-9443-6aad6393bd3c
caps.latest.revision: "40"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 45b45736c76ec0da7f1dce103df9fea4ee22507a
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="syssysperfinfo-transact-sql"></a>sys.sysperfinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] la représentation sous forme de compteurs de performance internes qui peuvent être affichés par le biais du Moniteur système Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**object_name**|**NCHAR(128)**|Performances nom d’objet, tel que **SQLServer:LockManager** ou **SQLServer:BufferManager**.|  
|**counter_name**|**NCHAR(128)**|Nom du compteur de performance au sein de l’objet, tel que **Page demandes** ou **Locks Requested**.|  
|**nom_instance**|**NCHAR(128)**|Instance nommée du compteur. Par exemple, il existe des compteurs gérés pour chaque type de verrou, tel que **Table**, **Page**, **clé**, et ainsi de suite. Le nom de l'instance permet de distinguer des compteurs similaires.|  
|**cntr_value**|**bigint**|Valeur réelle du compteur. Souvent, il s'agit d'un compteur croissant de niveau ou monotone qui compte les occurrences de l'événement d'instance.|  
|**cntr_type**|**int**|Type de compteur défini par l'architecture de performances Windows.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système pour les vues système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
