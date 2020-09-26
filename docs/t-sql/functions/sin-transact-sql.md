---
description: SIN (Transact-SQL)
title: SIN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SIN_TSQL
- SIN
dev_langs:
- TSQL
helpviewer_keywords:
- SIN function
- sine
ms.assetid: bc1781e9-185f-4981-929b-e77371be6b26
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 98cda2eaebc8dba22cf1784f3f4a4ae1845ce018
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2020
ms.locfileid: "91380584"
---
# <a name="sin-transact-sql"></a>SIN (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Renvoie le sinus trigonométrique de l’angle spécifié en radians et dans une expression numérique approximative, **float**.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
SIN ( float_expression )  
```  
  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
 *float_expression*  
 [Expression](../../t-sql/language-elements/expressions-transact-sql.md) de type **float** ou dont le type peut être implicitement converti en type float, en radians.
  
## <a name="return-types"></a>Types de retour  
 **float**  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant calcule le sinus d'un angle spécifié.  
  
```sql  
DECLARE @angle FLOAT;  
SET @angle = 45.175643;  
SELECT 'The SIN of the angle is: ' + CONVERT(VARCHAR, SIN(@angle));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The SIN of the angle is: 0.929607                         
  
(1 row(s) affected)  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant calcule le sinus d’un angle spécifié.  
  
```sql  
SELECT SIN(45.175643);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
---------  
0.929607
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions mathématiques &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  

