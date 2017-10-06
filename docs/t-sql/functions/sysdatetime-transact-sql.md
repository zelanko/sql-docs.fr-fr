---
title: SYSDATETIME (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYSDATETIME_TSQL
- SYSDATETIME
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], SYSDATETIME
- current date and time [SQL Server]
- functions [SQL Server], time
- system date and time [SQL Server]
- system time [SQL Server]
- SYSDATETIME function [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- dates [SQL Server], current date and time
- dates [SQL Server], system date and time
- time [SQL Server], system
ms.assetid: cba4999e-a9d4-4742-abc9-4a4f109206b6
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e199d8438ca39ead6e9c299925ba83edd6be7ef5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="sysdatetime-transact-sql"></a>SYSDATETIME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne un **datetime2 (7)** valeur qui contient la date et l’heure de l’ordinateur sur lequel l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution.  
  
> [!NOTE]  
>  SYSDATETIME et SYSUTCDATETIME ont plus de précision en fractions de seconde que GETDATE et GETUTCDATE. SYSDATETIMEOFFSET inclut le décalage de fuseau horaire système. SYSDATETIME, SYSUTCDATETIME et SYSDATETIMEOFFSET peuvent être assignés à une variable de chacun des types de date et d'heure.  
  
 Pour une vue d’ensemble de tous les [!INCLUDE[tsql](../../includes/tsql-md.md)] les types de données date et heure et les fonctions, consultez [Date et fonctions et Types de données &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SYSDATETIME ( )  
```  
  
## <a name="return-type"></a>Type de retour  
 **datetime2(7)**  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]les instructions peuvent faire référence à SYSDATETIME partout où ils peuvent faire référence à un **datetime2 (7)** expression.  
  
 SYSDATETIME est une fonction non déterministe. Les vues et expressions qui référencent cette fonction dans une colonne ne peuvent pas être indexées.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Obtient les valeurs de date et d’heure à l’aide de l’API Windows GetSystemTimeAsFileTime(). La précision dépend des composants matériels de l'ordinateur et de la version de Windows sur laquelle s'exécute l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La précision de cette API est fixée à 100 nanosecondes. La précision peut être déterminée à l’aide de l’API Windows GetSystemTimeAdjustment().  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants utilisent les six [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctions système qui retournent la date et heure actuelles pour retourner la date, heure ou les deux. Les valeurs sont retournées en séries ; par conséquent, leurs fractions de seconde peuvent être différentes.  
  
### <a name="a-getting-the-current-system-date-and-time"></a>A. Obtention de la date système actuelle et l’heure  
  
```  
SELECT SYSDATETIME()  
    ,SYSDATETIMEOFFSET()  
    ,SYSUTCDATETIME()  
    ,CURRENT_TIMESTAMP  
    ,GETDATE()  
    ,GETUTCDATE();  
/* Returned:  
SYSDATETIME()      2007-04-30 13:10:02.0474381  
SYSDATETIMEOFFSET()2007-04-30 13:10:02.0474381 -07:00  
SYSUTCDATETIME()   2007-04-30 20:10:02.0474381  
CURRENT_TIMESTAMP  2007-04-30 13:10:02.047  
GETDATE()          2007-04-30 13:10:02.047  
GETUTCDATE()       2007-04-30 20:10:02.047  
*/
```    
  
### <a name="b-getting-the-current-system-date"></a>B. Obtention de la date système actuelle  
  
```  
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, SYSDATETIMEOFFSET())  
    ,CONVERT (date, SYSUTCDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE())  
    ,CONVERT (date, GETUTCDATE());  
  
/* All returned 2007-04-30 */  
```  
  
### <a name="c-getting-the-current-system-time"></a>C. Obtention de l’heure système actuelle  
  
```  
SELECT CONVERT (time, SYSDATETIME())  
    ,CONVERT (time, SYSDATETIMEOFFSET())  
    ,CONVERT (time, SYSUTCDATETIME())  
    ,CONVERT (time, CURRENT_TIMESTAMP)  
    ,CONVERT (time, GETDATE())  
    ,CONVERT (time, GETUTCDATE());  
  
/* Returned  
SYSDATETIME()      13:18:45.3490361  
SYSDATETIMEOFFSET()13:18:45.3490361  
SYSUTCDATETIME()   20:18:45.3490361  
CURRENT_TIMESTAMP  13:18:45.3470000  
GETDATE()          13:18:45.3470000  
GETUTCDATE()       20:18:45.3470000  
*/  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-getting-the-current-system-date-and-time"></a>D : obtention de la date système actuelle et l’heure  
  
```  
SELECT SYSDATETIME();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
--------------------------  
7/20/2013 2:49:59 PM
```  
  
## <a name="see-also"></a>Voir aussi  
 [CAST et CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Données de date et heure les fonctions et Types de &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)  
  
  


