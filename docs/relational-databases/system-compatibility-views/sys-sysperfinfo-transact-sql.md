---
description: sys.sysperfinfo (Transact-SQL)
title: sys.sysPerfInfo (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: 1122c224e21fa633c2c04cd156a49878fefc7daa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482102"
---
# <a name="syssysperfinfo-transact-sql"></a>sys.sysperfinfo (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Contient une [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] représentation des compteurs de performance internes qui peuvent être affichés par le biais du moniteur système Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar(128)**|Nom de l’objet de performance, tel que **SqlServer : LockManager** ou **SqlServer : BufferManager**.|  
|**counter_name**|**nchar(128)**|Nom du compteur de performance dans l’objet, par exemple **demandes de page** ou **verrous demandés**.|  
|**instance_name**|**nchar(128)**|Instance nommée du compteur. Par exemple, il existe des compteurs gérés pour chaque type de verrou, tels que **table**, **page**, **clé**, etc. Le nom de l'instance permet de distinguer des compteurs similaires.|  
|**cntr_value**|**bigint**|Valeur réelle du compteur. Souvent, il s'agit d'un compteur croissant de niveau ou monotone qui compte les occurrences de l'événement d'instance.|  
|**cntr_type**|**int**|Type de compteur défini par l'architecture de performances Windows.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage de tables système à des vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
