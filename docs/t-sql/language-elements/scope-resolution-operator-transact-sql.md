---
title: ":: (Résolution de portée) (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server (starting with 2008)
dev_langs: TSQL
ms.assetid: 764d8f91-957b-4037-997b-a9b6b533c504
caps.latest.revision: "10"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d4fa0fa1cd5a86ab4dc736803f6d4926b98f4a30
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="-scope-resolution-transact-sql"></a>:: (Résolution de portée) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  L’opérateur de résolution de portée **::** fournit l’accès à des membres statiques d’un type de données composé. Type de données composé est une qui contient plusieurs types de données simples et méthodes, telles que les types CLR intégrés et les Types de SQLCLR User-Defined personnalisé (UDT).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant montre comment utiliser l'opérateur de résolution de portée pour accéder au membre `GetRoot()` du type `hierarchyid`.  
  
```  
DECLARE @hid hierarchyid;  
SELECT @hid = hierarchyid::GetRoot();  
PRINT @hid.ToString();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `/`  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
