---
title: SYSUTCDATETIME (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 12/01/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYSUTCDATETIME
- SYSUTCDATETIME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- system time [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- date and time [SQL Server], SYSUTCDATETIME
- SYSUTCDATETIME function [SQL Server]
- time [SQL Server], system
ms.assetid: f14fc2cd-9ea8-4daf-88f4-418cf523ab55
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: 8055c9410631f303c9f8633fd332e5f7d6f6d763
ms.contentlocale: fr-fr
ms.lasthandoff: 10/06/2017

---
# <a name="sysutcdatetime-transact-sql"></a>SYSUTCDATETIME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne un **datetime2** valeur qui contient la date et l’heure de l’ordinateur sur lequel l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution. La date et l’heure est retourné en tant que l’heure UTC (Coordinated Universal Time). La spécification de la précision de la fraction de seconde a une plage de 1 à 7 chiffres. La précision par défaut est de 7 chiffres.  
  
> [!NOTE]  
>  SYSDATETIME et SYSUTCDATE ont plus de précision en fractions de seconde que GETDATE et GETUTCDATE. SYSDATETIMEOFFSET inclut le décalage de fuseau horaire système. SYSDATETIME, SYSUTCDATE et SYSDATETIMEOFFSET peuvent être assignés à une variable de l'un des types de date et d'heure.  
  
 Pour une vue d’ensemble de tous les [!INCLUDE[tsql](../../includes/tsql-md.md)] les types de données date et heure et les fonctions, consultez [Date et les Types de données et les fonctions](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SYSUTCDATETIME ( )  
```  
  
## <a name="return-type"></a>Type de retour  
 **datetime2**  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]les instructions peuvent faire référence à SYSUTCDATETIME partout où ils peuvent faire référence à un **datetime2** expression.  
  
 SYSUTCDATETIME est une fonction non déterministe. Les vues et expressions qui référencent cette fonction dans une colonne ne peuvent pas être indexées.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Obtient les valeurs de date et d’heure à l’aide de l’API Windows GetSystemTimeAsFileTime(). La précision dépend des composants matériels de l'ordinateur et de la version de Windows sur laquelle s'exécute l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La précision de cette API est fixée à 100 nanosecondes. La précision peut être déterminée à l’aide de l’API Windows GetSystemTimeAdjustment().  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants utilisent les six fonctions système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui retournent les date et heure actuelles pour retourner la date, l'heure ou les deux. Les valeurs sont retournées en séries ; par conséquent, leurs fractions de seconde peuvent être différentes.  
  
### <a name="a-showing-the-formats-that-are-returned-by-the-date-and-time-functions"></a>A. Affichage des formats qui sont retournés par les fonctions de date et d'heure  
 L'exemple suivant illustre les différents formats qui sont retournés par les fonctions de date et d'heure.  
  
```  
SELECT SYSDATETIME() AS SYSDATETIME  
    , SYSDATETIMEOFFSET() AS SYSDATETIMEOFFSET  
    , SYSUTCDATETIME() AS SYSUTCDATETIME  
    , CURRENT_TIMESTAMP AS [CURRENT_TIMESTAMP]
    , GETDATE() AS GETDATE  
    , GETUTCDATE() AS GETUTCDATE;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
| SYSDATETIME | SYSDATETIMEOFFSET | SYSUTCDATETIME | CURRENT_TIMESTAMP | GETDATE | GETUTCDATE |
| --- | --- | --- | --- | --- | --- |
| 2007-04-30 13:10:02.0474381 | 2007-04-30 13:10:02.0474381 -07:00 | 2007-04-30 20:10:02.0474381 | 2007-04-30 13:10:02.047 | 2007-04-30 13:10:02.047 | 2007-04-30 20:10:02.047 |

  
### <a name="b-converting-date-and-time-to-date"></a>B. Conversion de date et d'heure en date  
 L'exemple suivant indique comment convertir des valeurs de date et heure en `date`.  
  
```  
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, SYSDATETIMEOFFSET())  
    ,CONVERT (date, SYSUTCDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE())  
    ,CONVERT (date, GETUTCDATE());  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
```  
  
### <a name="c-converting-date-and-time-values-to-time"></a>C. Conversion des valeurs de date et d'heure en heure  
 L'exemple suivant indique comment convertir des valeurs de date et heure en `time`.  
  
 ```
DECLARE @DATETIME DATETIME = GetDate();
DECLARE @TIME TIME
SELECT @TIME = CONVERT(time, @DATETIME)
SELECT @TIME AS 'Time', @DATETIME AS 'Date Time'
```
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Time             Date Time  
13:49:33.6330000 2009-04-22 13:49:33.633
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Les exemples suivants utilisent les six fonctions système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui retournent les date et heure actuelles pour retourner la date, l'heure ou les deux. Les valeurs sont retournées en séries ; par conséquent, leurs fractions de seconde peuvent être différentes.  
  
### <a name="d-showing-the-formats-that-are-returned-by-the-date-and-time-functions"></a>D. Affichage des formats qui sont retournés par les fonctions de date et d'heure  
 L'exemple suivant illustre les différents formats qui sont retournés par les fonctions de date et d'heure.  
  
```  
SELECT SYSDATETIME() AS SYSDATETIME  
    ,SYSDATETIMEOFFSET() AS SYSDATETIMEOFFSET  
    ,SYSUTCDATETIME() AS SYSUTCDATETIME  
    ,CURRENT_TIMESTAMP AS CURRENT_TIMESTAMP  
    ,GETDATE() AS GETDATE  
    ,GETUTCDATE() AS GETUTCDATE;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
SYSDATETIME()      2007-04-30 13:10:02.0474381
SYSDATETIMEOFFSET()2007-04-30 13:10:02.0474381 -07:00
SYSUTCDATETIME()   2007-04-30 20:10:02.0474381
CURRENT_TIMESTAMP  2007-04-30 13:10:02.047
GETDATE()          2007-04-30 13:10:02.047
GETUTCDATE()       2007-04-30 20:10:02.047
```  
  
### <a name="e-converting-date-and-time-to-date"></a>E. Conversion de date et d'heure en date  
 L'exemple suivant indique comment convertir des valeurs de date et heure en `date`.  
  
```  
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, SYSDATETIMEOFFSET())  
    ,CONVERT (date, SYSUTCDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE())  
    ,CONVERT (date, GETUTCDATE());  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
```  
  
### <a name="f-converting-date-and-time-values-to-time"></a>F. Conversion des valeurs de date et d'heure en heure  
 L'exemple suivant indique comment convertir des valeurs de date et heure en `time`.  
  
 ```
DECLARE @DATETIME DATETIME = GetDate();
DECLARE @TIME TIME
SELECT @TIME = CONVERT(time, @DATETIME)
SELECT @TIME AS 'Time', @DATETIME AS 'Date Time'
```
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Time             Date Time  
13:49:33.6330000 2009-04-22 13:49:33.633
```  
  
## <a name="see-also"></a>Voir aussi  
 [CAST et CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Données de date et heure les fonctions et Types de &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [FUSEAU horaire &AMP; #40 ; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  



