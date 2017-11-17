---
title: bit (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bit_TSQL
- bit
dev_langs:
- TSQL
helpviewer_keywords:
- bit data type
ms.assetid: 40adfd08-a31c-49cb-a172-386bcaa6edee
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3817549e5846c68b422fb941907860896b956d9a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="bit-transact-sql"></a>bit (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Données de type entier qui peuvent prendre la valeur 1, 0 ou NULL.  
  
## <a name="remarks"></a>Notes  
Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] optimise le stockage de **bits** colonnes. S’il n’y inférieur ou égal à 8 **bits** colonnes dans une table, les colonnes sont stockées dans 1 octet. S’il existe entre 9 et 16 **bits** colonnes, les colonnes sont stockées dans 2 octets et ainsi de suite.
  
Les valeurs de chaîne TRUE et FALSE peuvent être convertis en **bits** valeurs : TRUE est convertie en 1 et FALSE est convertie en 0.
  
Lors d'une conversion en bit, toute valeur différente de zéro est changée en 1.
  
## <a name="see-also"></a>Voir aussi
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Conversion de Type de données &#40; moteur de base de données &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Sys.types &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  

