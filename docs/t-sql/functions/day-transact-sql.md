---
title: JOUR (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DAY_TSQL
- DAY
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], DAY
- dates [SQL Server], functions
- DAY function [SQL Server]
- dates [SQL Server], days
- functions [SQL Server], date and time
- dateparts [SQL Server], day
ms.assetid: 2f4410ea-fd3e-4d69-ac4b-3b0091a084bc
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 9edfdc46ede4c090080c09253e2bb213a384816c
ms.contentlocale: fr-fr
ms.lasthandoff: 10/17/2017

---
# <a name="day-transact-sql"></a>DAY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne un entier représentant le jour (jour du mois) de l’objet *date*.
  
Pour une vue d’ensemble de tous les [!INCLUDE[tsql](../../includes/tsql-md.md)] les types de données date et heure et les fonctions, consultez [Date et fonctions et Types de données &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DAY ( date )  
```  
  
## <a name="arguments"></a>Arguments  
*date*  
Est une expression qui peut être résolue en un **temps**, **date**, **smalldatetime**, **datetime**, **datetime2**, ou **datetimeoffset** valeur. Le *date* argument peut être une expression, l’expression de colonne, la variable définie par l’utilisateur ou le littéral de chaîne.
  
## <a name="return-type"></a>Type de retour  
**int**
  
## <a name="return-value"></a>Valeur retournée  
La fonction DAY renvoie la même valeur que [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**jour**, *date*).
  
Si *date* contient uniquement une partie heure, la valeur de retour est 1, le jour de base.
  
## <a name="examples"></a>Exemples  
L'instruction suivante retourne `30`. Il s'agit du numéro du jour.
  
```sql
SELECT DAY('2015-04-30 01:01:01.1234567');  
```  
  
L'instruction suivante retourne `1900, 1, 1`. L’argument pour *date* est le nombre `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprète `0` comme le 1er janvier 1900.
  
```sql
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  



