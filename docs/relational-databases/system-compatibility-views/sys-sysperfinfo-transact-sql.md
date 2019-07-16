---
title: Sys.sysperfinfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysperfinfo_TSQL
- sys.sysperfinfo_TSQL
- sys.sysperfinfo
- sysperfinfo
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysperfinfo compatibility view
- sysperfinfo system table
ms.assetid: e22a81cd-27de-4690-9443-6aad6393bd3c
author: rothja
ms.author: jroth
ms.openlocfilehash: e6ce86e7be7d54e95c2336691b53ea12ff0d8575
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68076504"
---
# <a name="syssysperfinfo-transact-sql"></a>sys.sysperfinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] représentation sous forme de compteurs de performance internes qui peuvent être affichés par le biais du Moniteur système Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar(128)**|L’objet de performances nom, tel que **SQLServer:LockManager** ou **SQLServer:BufferManager**.|  
|**counter_name**|**nchar(128)**|Nom du compteur de performance au sein de l’objet, tel que **demandes de Page** ou **Locks Requested**.|  
|**instance_name**|**nchar(128)**|Instance nommée du compteur. Par exemple, il existe des compteurs gérés pour chaque type de verrou, tel que **Table**, **Page**, **clé**, et ainsi de suite. Le nom de l'instance permet de distinguer des compteurs similaires.|  
|**cntr_value**|**bigint**|Valeur réelle du compteur. Souvent, il s'agit d'un compteur croissant de niveau ou monotone qui compte les occurrences de l'événement d'instance.|  
|**cntr_type**|**Int**|Type de compteur défini par l'architecture de performances Windows.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
