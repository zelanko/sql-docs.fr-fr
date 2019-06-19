---
title: DIFFERENCE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DIFFERENCE
- DIFFERENCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DIFFERENCE function
- comparing SOUNDEX values
- SOUNDEX values
ms.assetid: c58ca25d-d6ea-48fa-93bb-c9374b0b2a2b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f337707509f3a62a60903a5a97c42bebc7754468
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65947067"
---
# <a name="difference-transact-sql"></a>DIFFERENCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Cette fonction retourne sous la forme d’un entier la différence entre les valeurs [SOUNDEX()](./soundex-transact-sql.md) de deux expressions de caractères différentes.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DIFFERENCE ( character_expression , character_expression )  
```  
  
## <a name="arguments"></a>Arguments  
*expression_caractère*  
[Expression](../../t-sql/language-elements/expressions-transact-sql.md) alphanumérique de données caractères. *character_expression* peut être une constante, une variable ou une colonne.  
  
## <a name="return-types"></a>Types de retour  
**Int**  
 
## <a name="remarks"></a>Notes   
`DIFFERENCE` compare deux valeurs `SOUNDEX` différentes, et retourne une valeur entière. Cette valeur mesure le degré de correspondance des valeurs `SOUNDEX`, sur une échelle de 0 à 4. La valeur 0 indique une similarité faible ou nulle entre les valeurs SOUNDEX ; 4 indique des valeurs SOUNDEX fortement similaires, ou même identiques.  
  
`DIFFERENCE` et `SOUNDEX` respectent le classement.  
  
## <a name="examples"></a>Exemples  
La première partie de l’exemple suivant compare les valeurs `SOUNDEX` de deux chaînes très similaires. Pour un classement Latin1_General, `DIFFERENCE` retourne la valeur `4`. La deuxième partie de l’exemple compare les valeurs `SOUNDEX` de deux chaînes très différentes et, pour un classement Latin1_General, `DIFFERENCE` retourne la valeur `0`.  
  
```  
-- Returns a DIFFERENCE value of 4, the least possible difference.  
SELECT SOUNDEX('Green'), SOUNDEX('Greene'), DIFFERENCE('Green','Greene');  
GO  
-- Returns a DIFFERENCE value of 0, the highest possible difference.  
SELECT SOUNDEX('Blotchet-Halls'), SOUNDEX('Greene'), DIFFERENCE('Blotchet-Halls', 'Greene');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----- ----- -----------   
G650  G650  4             
  
(1 row(s) affected)  
  
----- ----- -----------   
B432  G650  0             
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a> Voir aussi  
 [SOUNDEX &#40;Transact-SQL&#41;](../../t-sql/functions/soundex-transact-sql.md)   
 [Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

