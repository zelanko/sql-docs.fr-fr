---
title: LOG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- LOG
- LOG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- float expressions
- logarithm of expression
- LOG function
ms.assetid: f7c39511-cd84-4362-93ba-0d93655217ee
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c93a2a05df661fa0eaf1560249a9331f0b96b78f
ms.sourcegitcommit: 41ff0446bd8e4380aad40510ad579a3a4e096dfa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86465276"
---
# <a name="log-transact-sql"></a>LOG (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Renvoie le logarithme népérien de l’expression **float** spécifiée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
-- Syntax for SQL Server, Azure SQL Database  
  
LOG ( float_expression [, base ] )  
```  
  
```syntaxsql
-- Syntax for Azure Synapse SQL 
  
LOG ( float_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *float_expression*  
 [Expression](../../t-sql/language-elements/expressions-transact-sql.md) de type **float** ou dont le type peut être implicitement converti en type **float**.  
  
 *base*  
 Argument entier facultatif qui définit la base du logarithme.  
  
**S’applique à** : [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et ultérieur
  
## <a name="return-types"></a>Types de retour  
 **float**  
  
## <a name="remarks"></a>Notes  
 Par défaut, **LOG()** renvoie le logarithme népérien. À partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], vous pouvez changer la base du logarithme à l’aide du paramètre facultatif *base*.  
  
 Le logarithme népérien est le logarithme en base **e**, où **e** est une constante irrationnelle environ égale à 2,718281828.  
  
 Le logarithme népérien de l’exponentiel d’un nombre est le nombre lui-même : LOG( EXP( *n* ) ) = *n*. De même, l’exponentiel du logarithme népérien d’un nombre est le nombre lui-même : EXP( LOG( *n* ) ) = *n*.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-calculating-the-logarithm-for-a-number"></a>R. Calcul du logarithme d'un nombre  
 L’exemple suivant calcule le `LOG` de l’expression **float** spécifiée.  
  
```sql  
DECLARE @var FLOAT = 10;  
SELECT 'The LOG of the variable is: ' + CONVERT(VARCHAR, LOG(@var));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------------------------------  
The LOG of the variable is: 2.30259  
  
(1 row(s) affected)  
```  
  
### <a name="b-calculating-the-logarithm-of-the-exponent-of-a-number"></a>B. Calcul du logarithme de l'exposant d'un nombre  
 L’exemple suivant calcule la valeur `LOG` pour l’exposant d’un nombre.  
  
```sql  
SELECT LOG (EXP (10));  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------------------------  
10  
(1 row(s) affected)  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-calculating-the-logarithm-for-a-number"></a>C. Calcul du logarithme d’un nombre  
 L’exemple suivant calcule le `LOG` de l’expression **float** spécifiée.  
  
```sql  
SELECT LOG(10);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ----------------`  
  
 2.30
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions mathématiques &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [EXP &#40;Transact-SQL&#41;](../../t-sql/functions/exp-transact-sql.md)   
 [LOG10 &#40;Transact-SQL&#41;](../../t-sql/functions/log10-transact-sql.md)  
  
  

