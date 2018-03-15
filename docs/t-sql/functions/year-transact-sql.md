---
title: YEAR (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- YEAR
- YEAR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- dates [SQL Server], years
- date and time [SQL Server], YEAR
- functions [SQL Server], date and time
- YEAR function [SQL Server]
- dateparts [SQL Server], year
ms.assetid: 74aa7ccc-8575-4018-80cf-14aeca379687
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 48dad4b2e38d9e178213aa8ad5ebb9e7608032a2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="year-transact-sql"></a>YEAR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie un entier qui représente l’année de la *date* spécifiée.  
  
 Pour obtenir une vue d’ensemble de tous les types de données et fonctions de date et d’heure [!INCLUDE[tsql](../../includes/tsql-md.md)], consultez [Types de données et fonctions de date et d’heure &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
YEAR ( date )  
```  
  
## <a name="arguments"></a>Arguments  
 *date*  
 Expression qui peut être résolue en une valeur **time**, **date**, **smalldatetime**, **datetime**, **datetime2** ou **datetimeoffset**. L’argument *date* peut être une expression, une expression de colonne, une variable définie par l’utilisateur ou un littéral de chaîne.  
  
## <a name="return-types"></a>Types de retour  
 **Int**  
  
## <a name="return-value"></a>Valeur retournée  
 YEAR renvoie la même valeur que [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**year**, *date*).  
  
 Si *date* contient uniquement une partie heure, la valeur renvoyée est 1900, l’année de base.  
  
## <a name="examples"></a>Exemples  
 L'instruction suivante retourne `2010`. Il s'agit du numéro de l'année.  
  
```  
SELECT YEAR('2010-04-30T01:01:01.1234567-07:00');  
```  
  
 L'instruction suivante retourne `1900, 1, 1`. L’argument pour *date* est le chiffre `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprète `0` comme le 1er janvier 1900.  
  
```  
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'instruction suivante retourne `1900, 1, 1`. L’argument pour *date* est le chiffre `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprète `0` comme le 1er janvier 1900.  
  
```  
SELECT TOP 1 YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="see-also"></a> Voir aussi  
 [CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  

