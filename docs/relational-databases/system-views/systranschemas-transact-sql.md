---
title: systranschemas (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- systranschemas
- systranschemas_TSQL
dev_langs: TSQL
helpviewer_keywords: systranschemas system table
ms.assetid: 864c3966-cb61-4f2b-8939-ccda112de853
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f5f5c9502b9116bc60797c537edb27fdf79d3080
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="systranschemas-transact-sql"></a>systranschemas (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **systranschemas** table est utilisée pour effectuer le suivi des modifications de schéma dans les articles publiés dans les publications transactionnelles et de capture instantanées. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**tabid**|**int**|Identifie l'article de table sur lequel la modification de schéma s'est produite.|  
|**LSN de début**|**binaire**|Valeur LSN du début de la modification de schéma.|  
|**endlsn**|**binaire**|Valeur LSN de la fin de la modification de schéma.|  
|**typeid**|**int**|Type de modification de schéma.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
