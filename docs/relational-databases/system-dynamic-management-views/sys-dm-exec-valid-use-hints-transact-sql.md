---
title: Sys.dm_exec_valid_use_hints (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sys.dm_exec_valid_use_hints
- sys.dm_exec_valid_use_hints_TSQL
- dm_exec_valid_use_hints
- dm_exec_valid_use_hints_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_valid_use_hints management view
ms.assetid: 65d50589-39c2-4046-92b6-0c4587d8c593
caps.latest.revision: "5"
author: pmasl
ms.author: pelopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 61efec0bec550e68ce19e1285c381c0649849450
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecvalidusehints-transact-sql"></a>Sys.dm_exec_valid_use_hints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Retourne [indicateur USE](../../t-sql/queries/hints-transact-sql-query.md) pris en charge les noms de l’indicateur. Il répertorie un nom d’indicateur par ligne.  
  
Utilisez cette vue de gestion dynamique pour afficher la liste de tous les indicateurs pris en charge de la notation de l’indicateur d’utilisation.  
  
|Nom de la colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Le nom de l’indicateur.|

Consultez [indicateurs de requête](../../t-sql/queries/hints-transact-sql-query.md) pour obtenir une description de chaque indicateur.

Introduite dans [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] SP1.
  
## <a name="see-also"></a>Voir aussi  
    
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Base de données associés des vues de gestion dynamique &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

