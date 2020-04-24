---
title: ACOS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ACOS
- ACOS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cosine
- ACOS function
- arccosine
ms.assetid: 4ec6b46e-9438-4f0f-8b96-461edd84280a
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fc6896542e2eaca6ecff9cac250581c163a68e1c
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81633463"
---
# <a name="acos-transact-sql"></a>ACOS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Fonction qui retourne l’angle en radians dont le cosinus correspond à l’expression float spécifiée. Cette fonction est également appelée arc cosinus.
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
ACOS ( float_expression )  
```  
  
## <a name="arguments"></a>Arguments  
*float_expression*  
[Expression](../../t-sql/language-elements/expressions-transact-sql.md) de type **float** ou dont le type peut être implicitement converti en float. Seule une valeur comprise entre -1,00 et 1,00 est valide. Les valeurs situées hors de cette plage retournent la valeur NULL et ASIN signale une erreur de domaine.
  
## <a name="return-types"></a>Types de retour  
**float**
  
## <a name="examples"></a>Exemples  
Cet exemple retourne la valeur `ACOS` du nombre transmis.
  
```sql
SET NOCOUNT OFF;  
DECLARE @cos float;  
SET @cos = -1.0;  
SELECT 'The ACOS of the number is: ' + CONVERT(varchar, ACOS(@cos));  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
---------------------------------   
The ACOS of the number is: 3.14159   
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi
[Fonctions mathématiques &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
[Fonctions](../../t-sql/functions/functions.md)
  
  

