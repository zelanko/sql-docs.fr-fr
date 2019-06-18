---
title: CURRENT_TIMEZONE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/09/2019
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
manager: craigg
ms.openlocfilehash: dcdae3ff107ad1e1e3a7bc58fde4248bb5330223
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62850367"
---
# <a name="currenttimezone-transact-sql"></a>CURRENT_TIMEZONE (Transact-SQL)

[!INCLUDE[tsql-appliesto-ssver15-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssver15-asdb-xxxx-xxx.md)]

Cette fonction retourne le nom du fuseau horaire observé par un serveur ou une instance. Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`CURRENT_TIMEZONE` tire cette valeur du système d’exploitation de l’ordinateur sur lequel l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute. Pour SQL Database Managed Instance, la valeur de retour est basée sur le fuseau horaire de l'instance proprement dite attribué lors de la création de l'instance, et non sur le fuseau horaire du système d'exploitation sous-jacent.
  
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
