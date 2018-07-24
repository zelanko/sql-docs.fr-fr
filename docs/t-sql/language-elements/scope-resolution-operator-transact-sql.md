---
title: ':: (Résolution d’étendue) (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
dev_langs:
- TSQL
ms.assetid: 764d8f91-957b-4037-997b-a9b6b533c504
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ed1338f3cf8c5de3f532542b57e73533de035a1e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38045730"
---
# <a name="-scope-resolution-transact-sql"></a>:: (Résolution d’étendue) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  L’opérateur de résolution d’étendue **::** fournit l’accès aux membres statiques d’un type de données composé. Un type de données composé est un type qui contient plusieurs types de données et méthodes simples, comme les types CLR intégrés et les UDT (types définis par l’utilisateur) SQLCLR personnalisés.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant montre comment utiliser l'opérateur de résolution de portée pour accéder au membre `GetRoot()` du type `hierarchyid`.  
  
```  
DECLARE @hid hierarchyid;  
SELECT @hid = hierarchyid::GetRoot();  
PRINT @hid.ToString();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `/`  
  
## <a name="see-also"></a> Voir aussi  
 [Opérateurs &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
