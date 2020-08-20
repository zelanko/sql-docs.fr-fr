---
description: sp_unprepare (Transact-SQL)
title: sp_unprepare (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_unprepare_TSQL
- sp_cursor_unprepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unprepare
ms.assetid: 14320251-c551-49d8-b933-057406114978
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 53d8ec3c7f3976da32bb49d448b76ce96b3f8a3a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492932"
---
# <a name="sp_unprepare-transact-sql"></a>sp_unprepare (Transact-SQL)
[!INCLUDE [sql-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdbmi-asa-pdw.md)]

  Ignore le plan d’exécution créé par la procédure stockée sp_prepare. sp_unprepare est appelée en spécifiant ID = 15 dans un paquet tabular data stream (TDS).  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql  
-- Syntax for SQL Server, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_unprepare handle           
```  
  
## <a name="arguments"></a>Arguments  
 *traitée*  
 Valeur de *handle* retournée par sp_prepare.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant prépare, exécute et annule la préparation d'une instruction simple.  
  
```SQL  
DECLARE @P1 INT;  
EXEC sp_prepare @P1 OUTPUT,   
    N'@P1 NVARCHAR(128), @P2 NVARCHAR(100)',  
    N'SELECT database_id, name FROM sys.databases WHERE name = @P1 AND state_desc = @P2';  
EXEC sp_execute @P1, N'tempdb', N'ONLINE';  
EXEC sp_unprepare @P1;  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'exemple suivant prépare, exécute et annule la préparation d'une instruction simple.  
  
```SQL  
DECLARE @P1 INT;  
EXEC sp_prepare @P1 OUTPUT,   
    N'@P1 NVARCHAR(128), @P2 NVARCHAR(100)',  
    N'SELECT database_id, name FROM sys.databases WHERE name = @P1 AND state_desc = @P2';  
EXEC sp_execute @P1, N'tempdb', N'ONLINE';  
EXEC sp_unprepare @P1;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_prepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   

