---
title: DATEFROMPARTS (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATEFROMPARTS_TSQL
- DATEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATEFROMPARTS function
ms.assetid: 5b885376-87aa-41f1-9e18-04987aead250
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: a94584788187162e4cd7d433d71653a04c5103e2
ms.contentlocale: fr-fr
ms.lasthandoff: 10/17/2017

---
# <a name="datefromparts-transact-sql"></a>DATEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Retourne un **date** valeur pour l’année, mois et jour.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATEFROMPARTS ( year, month, day )  
```  
  
## <a name="arguments"></a>Arguments  
*année*  
Expression entière spécifiant une année.
  
*mois*  
Expression entière spécifiant un mois, de 1 à 12.
  
*jour*  
Expression entière spécifiant un jour.
  
## <a name="return-types"></a>Types de retour
**date**
  
## <a name="remarks"></a>Notes  
**DATEFROMPARTS** retourne un **date** valeur avec la partie date définie pour l’année, mois et de jour et la partie heure définie à la valeur par défaut. Si les arguments ne sont pas valides, une erreur est générée. Si les arguments obligatoires sont NULL, la valeur NULL est retournée.
  
Cette fonction peut être exécutée à distance sur des serveurs [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures. Elle ne peut pas être exécutée à distance avec une version antérieure à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].
  
## <a name="examples"></a>Exemples  
L’exemple suivant illustre la **DATEFROMPARTS** (fonction).
  
```sql
SELECT DATEFROMPARTS ( 2010, 12, 31 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
----------------------------------  
2010-12-31  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi
[date &#40;Transact-SQL&#41;](../../t-sql/data-types/date-transact-sql.md)
  
  


