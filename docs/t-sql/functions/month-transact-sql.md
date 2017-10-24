---
title: MOIS (Transact-SQL) | Documents Microsoft
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
- MONTH_TSQL
- MONTH
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], date and time
- dates [SQL Server], functions
- month of year [SQL Server]
- date and time [SQL Server], MONTH
- dateparts [SQL Server], month
- functions [SQL Server], date and time
- dates [SQL Server], MONTH
- MONTH function [SQL Server]
ms.assetid: 9dd8aff7-b0fc-45df-b316-ead14ee9b8b7
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5f3f25d694d7d9757b09d834e9844aad2b2defb3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="month-transact-sql"></a>MONTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne un entier qui représente le mois spécifié *date*.  
  
 Pour une vue d’ensemble de tous les [!INCLUDE[tsql](../../includes/tsql-md.md)] les types de données date et heure et les fonctions, consultez[Date et fonctions et Types de données &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
MONTH ( date )  
```  
  
## <a name="arguments"></a>Arguments  
 *date*  
 Est une expression qui peut être résolue en un **temps**, **date**, **smalldatetime**, **datetime**, **datetime2**, ou **datetimeoffset** valeur. Le *date* argument peut être une expression, l’expression de colonne, variable définie par l’utilisateur ou littéral de chaîne.  
  
## <a name="return-type"></a>Type de retour  
 **int**  
  
## <a name="return-value"></a>Valeur retournée  
 La fonction MONTH renvoie la même valeur que [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**mois**, *date*).  
  
 Si *date* contient uniquement une partie heure, la valeur de retour est 1, le mois de base.  
  
## <a name="examples"></a>Exemples  
 L'instruction suivante retourne `4`. Il s'agit du numéro du mois.  
  
```  
SELECT MONTH('2007-04-30T01:01:01.1234567 -07:00');  
```  
  
 L'instruction suivante retourne `1900, 1, 1`. L’argument pour *date* est le nombre `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprète `0` comme le 1er janvier 1900.  
  
```  
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant renvoie `4`. Il s'agit du numéro du mois.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP 1 MONTH('2007-04-30T01:01:01.1234')   
FROM dbo.DimCustomer;  
```  
  
 L’exemple suivant renvoie `1900, 1, 1`. L’argument pour *date* est le nombre `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprète `0` comme le 1er janvier 1900.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP 1 YEAR(0), MONTH(0), DAY(0) FROM dbo.DimCustomer;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  


