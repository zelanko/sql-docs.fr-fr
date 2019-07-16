---
title: Sys.dm_exec_valid_use_hints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_valid_use_hints
- sys.dm_exec_valid_use_hints_TSQL
- dm_exec_valid_use_hints
- dm_exec_valid_use_hints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_valid_use_hints management view
ms.assetid: 65d50589-39c2-4046-92b6-0c4587d8c593
author: pmasl
ms.author: pelopes
ms.openlocfilehash: c6fcaa491f7d42e255ed329a8e16798437aa2c7a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936794"
---
# <a name="sysdmexecvalidusehints-transact-sql"></a>Sys.dm_exec_valid_use_hints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Retourne [USE HINT](../../t-sql/queries/hints-transact-sql-query.md#use_hint) pris en charge des noms d’indicateur. Il répertorie un nom d’indicateur par ligne.  
  
Utilisez cette vue de gestion dynamique pour afficher la liste de tous les indicateurs pris en charge de la notation USE HINT.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Le nom de l’indicateur.|

Consultez [indicateurs de requête](../../t-sql/queries/hints-transact-sql-query.md#use_hint) pour obtenir une description de chaque indicateur.

Introduite dans [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] SP1.
  
## <a name="see-also"></a>Voir aussi  
    
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées à la base de données &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

