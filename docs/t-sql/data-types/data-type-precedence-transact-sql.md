---
description: Priorités des types de données (Transact-SQL)
title: Priorité des types de données (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/23/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- precedence [SQL Server]
- data types [SQL Server], converting
- data types [SQL Server], precedence
- converting data types [SQL Server], precedence
- precedence [SQL Server], data types
ms.assetid: f4c804ab-ed3f-43b1-a024-c9ac6944b66b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6ed8d2a30d4bcc2cd1adaedc3cccd6642d701533
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459922"
---
# <a name="data-type-precedence-transact-sql"></a>Priorité des types de données (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md.md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Quand un opérateur combine des expressions de types de données différents, le type ayant la priorité plus faible est converti en premier dans le type ayant la priorité plus élevée. Si la conversion n’est pas une conversion implicite prise en charge, une erreur est retournée. Pour un opérateur combinant des expressions d’opérandes ayant le même type de données, le résultat de l’opération a également ce type de données.
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise l'ordre de priorité suivant pour les types de données :
  
1.  types de données définis par l'utilisateur (plus haut niveau de priorité)  
1.  **sql_variant**  
1.  **xml**  
1.  **datetimeoffset**  
1.  **datetime2**  
1.  **datetime**  
1.  **smalldatetime**  
1.  **date**  
1. **time**  
1. **float**  
1. **real**  
1. **decimal**  
1. **money**  
1. **smallmoney**  
1. **bigint**  
1. **int**  
1. **smallint**  
1. **tinyint**  
1. **bit**  
1. **ntext**  
1. **text**  
1. **image**  
1. **timestamp**  
1. **uniqueidentifier**  
1. **nvarchar** (dont **nvarchar(max)** )  
1. **nchar**  
1. **varchar** (dont **varchar(max)** )  
1. **char**  
1. **varbinary** (dont **varbinary(max)** )  
1. **binary** (minimum)  
  
## <a name="see-also"></a>Voir aussi
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
