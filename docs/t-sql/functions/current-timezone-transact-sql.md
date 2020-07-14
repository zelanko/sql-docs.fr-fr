---
title: CURRENT_TIMEZONE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/28/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CURRENT_TIMEZONE
- CURRENT_TIMEZONE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- current time zone [SQL Server]
- current timezone [SQL Server]
- system time zone [SQL Server]
- system timezone [SQL Server]
- functions [SQL Server], time zone
- functions [SQL Server], timezone
- timezone [SQL Server], functions
- time zone [SQL Server], functions
- CURRENT_TIMEZONE function [SQL Server]
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 760da1491a7fbf4633cb02fe1fea8568e7ab9fa1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85684490"
---
# <a name="current_timezone-transact-sql"></a>CURRENT_TIMEZONE (Transact-SQL)

[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

Cette fonction retourne le nom du fuseau horaire observé par un serveur ou une instance. Pour SQL Database Managed Instance, la valeur de retour est basée sur le fuseau horaire de l'instance proprement dite attribué lors de la création de l'instance, et non sur le fuseau horaire du système d'exploitation sous-jacent.
  
> [!NOTE]  
> Pour les bases de données SQL uniques et en pool, le fuseau horaire est toujours défini sur UTC et `CURRENT_TIMEZONE` retourne le nom du fuseau horaire UTC.
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CURRENT_TIMEZONE ( )  
```
  
## <a name="arguments"></a>Arguments

Cette fonction ne prend pas d'arguments.
  
## <a name="return-type"></a>Type de retour  

**varchar**
  
## <a name="remarks"></a>Notes  

`CURRENT_TIMEZONE` est une fonction non déterministe. Les vues et les expressions qui référencent cette colonne ne peuvent pas être indexées.
  
## <a name="example"></a>Exemple

Notez que la valeur retournée reflète le fuseau horaire réel et les paramètres de langue du serveur ou de l’instance.

```sql
SELECT CURRENT_TIMEZONE();  
/* Returned:  
(UTC+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna 
*/
```  
  
## <a name="see-also"></a>Voir aussi

[Fuseau horaire de SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-timezone)

[CURRENT_TIMEZONE_ID()](https://docs.microsoft.com/sql/t-sql/functions/current-timezone-id-transact-sql)
