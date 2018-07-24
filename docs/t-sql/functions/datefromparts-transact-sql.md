---
title: DATEFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 705d31a9f97d8c7894cd70e20993cde65a0d361f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38063717"
---
# <a name="datefromparts-transact-sql"></a>DATEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Cette fonction retourne une valeur **date** qui est mappée aux valeurs de jour, de mois et d’année.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATEFROMPARTS ( year, month, day )  
```  
  
## <a name="arguments"></a>Arguments  
*year*  
Expression entière qui spécifie une année.
  
*month*  
Expression entière qui spécifie un mois, entre 1 et 12.
  
*day*  
Expression entière qui spécifie un jour.
  
## <a name="return-types"></a>Types de retour
**date**
  
## <a name="remarks"></a>Notes   
`DATEFROMPARTS` retourne une valeur **date**, avec la partie date définie sur l’année, le mois et le jour spécifiés, et la partie heure définie avec la valeur par défaut. Pour les arguments non valides, `DATEFROMPARTS` génère une erreur. `DATEFROMPARTS` retourne une valeur Null si au moins un argument obligatoire a une valeur Null.
  
Cette fonction peut gérer la communication à distance vers des serveurs [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures. Il ne peut pas gérer la communication à distance vers des serveurs avec une version antérieure à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].
  
## <a name="examples"></a>Exemples  
L’exemple suivant montre la fonction `DATEFROMPARTS` en action.
  
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
  
  

