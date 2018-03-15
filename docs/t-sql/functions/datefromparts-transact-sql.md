---
title: DATEFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/29/2017
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
- DATEFROMPARTS_TSQL
- DATEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATEFROMPARTS function
ms.assetid: 5b885376-87aa-41f1-9e18-04987aead250
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 73d2edfd6f0d19c4383b0bdbe1271d74a0ef2b6f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="datefromparts-transact-sql"></a>DATEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Renvoie une valeur **date** pour l’année, le mois et le jour spécifiés.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATEFROMPARTS ( year, month, day )  
```  
  
## <a name="arguments"></a>Arguments  
*year*  
Expression entière spécifiant une année.
  
*month*  
Expression entière spécifiant un mois, de 1 à 12.
  
*day*  
Expression entière spécifiant un jour.
  
## <a name="return-types"></a>Types de retour
**date**
  
## <a name="remarks"></a>Notes   
**DATEFROMPARTS** renvoie une valeur **date** avec la partie date définie sur l’année, le mois et le jour spécifiés, et la partie heure définie avec la valeur par défaut. Si les arguments ne sont pas valides, une erreur est générée. Si les arguments obligatoires sont NULL, la valeur NULL est retournée.
  
Cette fonction peut être exécutée à distance sur des serveurs [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures. Elle ne peut pas être exécutée à distance avec une version antérieure à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].
  
## <a name="examples"></a>Exemples  
L’exemple suivant illustre la fonction **DATEFROMPARTS**.
  
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
  
  

