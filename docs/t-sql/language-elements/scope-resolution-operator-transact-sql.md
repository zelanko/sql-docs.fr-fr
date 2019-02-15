---
title: ':: (Résolution d’étendue) (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 764d8f91-957b-4037-997b-a9b6b533c504
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b2e6e7d28fb4b04b61c1cd1cf5877d231f220e76
ms.sourcegitcommit: 5ef24b3229b4659ede891b0af2125ef22bd94b96
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759942"
---
# <a name="-scope-resolution-transact-sql"></a>:: (Résolution d’étendue) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  L’opérateur de résolution d’étendue **::** fournit l’accès aux membres statiques d’un type de données composé. Un type de données composé contient plusieurs types de données simples et méthodes. Les types de données composés incluent les types CLR intégrés et les types définis par l’utilisateur SQLCLR personnalisés.  
  
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
 