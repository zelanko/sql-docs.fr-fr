---
title: DATETIMEFROMPARTS (Transact-SQL) | Microsoft Docs
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
- DATETIMEFROMPARTS_TSQL
- DATETIMEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIMEFROMPARTS function
ms.assetid: 6008148b-bf75-4c98-9392-68a89fa0711c
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: ff10c9dff219c3610938f5944fd054b535226afe
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39458003"
---
# <a name="datetimefromparts-transact-sql"></a>DATETIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Cette fonction retourne une valeur **datetime** pour les arguments de date et d’heure spécifiés.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATETIMEFROMPARTS ( year, month, day, hour, minute, seconds, milliseconds )  
```  
  
## <a name="arguments"></a>Arguments  
*year*  
Expression entière qui spécifie une année.
  
*month*  
Expression entière qui spécifie un mois.
  
*day*  
Expression entière qui spécifie un jour.
  
*hour*  
Expression entière qui spécifie des heures.
  
*minute*  
Expression entière qui spécifie des minutes.
  
*secondes*  
Expression entière qui spécifie des secondes.
  
*milliseconds*  
Expression entière qui spécifie des millisecondes.
  
## <a name="return-types"></a>Types de retour
**datetime**
  
## <a name="remarks"></a>Notes   
`DATETIMEFROMPARTS` retourne une valeur **datetime** entièrement initialisée. `DATETIMEFROMPARTS` génère une erreur si au moins un argument obligatoire a une valeur non valide. `DATETIMEFROMPARTS` retourne une valeur Null si au moins un argument obligatoire a une valeur Null.
  
Cette fonction prend en charge la communication à distance vers des serveurs [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et versions ultérieures. Elle ne prend pas en charge la communication à distance vers des serveurs dont la version est antérieure à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Exemples  
  
```sql
SELECT DATETIMEFROMPARTS ( 2010, 12, 31, 23, 59, 59, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
---------------------------  
2010-12-31 23:59:59.000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi
[datetime &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime-transact-sql.md)
  
  

