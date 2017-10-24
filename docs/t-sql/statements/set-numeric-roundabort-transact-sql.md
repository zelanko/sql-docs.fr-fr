---
title: SET NUMERIC_ROUNDABORT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NUMERIC_ROUNDABORT
- SET_NUMERIC_ROUNDABORT_TSQL
- SET NUMERIC_ROUNDABORT
- NUMERIC_ROUNDABORT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- rounding expressions
- precision [SQL Server], rounded expressions
- expressions [SQL Server], rounding
- NUMERIC_ROUNDABORT
- SET NUMERIC_ROUNDABORT statement
ms.assetid: d20e74f1-b8da-466c-b180-9d8a8b851a77
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2885429909ebc48294d84d5f3b3a27bccca8abff
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-numericroundabort-transact-sql"></a>SET NUMERIC_ROUNDABORT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Spécifie le niveau de gravité de l'erreur générée lorsqu'un arrondi effectué dans une expression entraîne une perte de précision.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET NUMERIC_ROUNDABORT { ON | OFF }   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET NUMERIC_ROUNDABORT ON;  
```  
  
## <a name="remarks"></a>Notes  
 Si l'option SET NUMERIC_ROUNDABORT est définie à ON (activée), une erreur se produit dès qu'une perte de précision survient dans une expression. Lorsqu'elle est désactivée (OFF), les pertes de précision ne génèrent pas de messages d'erreur et le résultat est arrondi en fonction de la précision de la colonne ou de la variable contenant le résultat.  
  
 Une perte de précision peut se produire lorsque vous tentez de stocker une valeur avec une précision fixe dans une colonne ou une variable dont la précision est moindre.  
  
 Si SET NUMERIC_ROUNDABORT est défini à ON, SET ARITHABORT détermine la gravité de l'erreur générée. Le tableau suivant montre les effets de cette valeur (activée et désactivée), dans le cas d'une perte de précision.  
  
|Paramètre|SET NUMERIC_ROUNDABORT ON|SET NUMERIC_ROUNDABORT OFF|  
|-------------|--------------------------------|---------------------------------|  
|SET ARITHABORT ON|Une erreur est générée ; aucun ensemble de résultats n'est renvoyé.|Pas d'erreur ou d'avertissement ; le résultat est arrondi.|  
|SET ARITHABORT OFF|Un avertissement est renvoyé ; l'expression renvoie la valeur NULL.|Pas d'erreur ou d'avertissement ; le résultat est arrondi.|  
  
 L'option SET NUMERIC_ROUNDABORT est définie lors de l'exécution, et non pas au moment de l'analyse.  
  
 SET NUMERIC_ROUNDABORT doit être désactivée (valeur OFF) lors de la création ou de la modification d'index sur des colonnes calculées ou des vues indexées. Si SET NUMERIC_ROUNDABORT est activé (OFF), les instructions CREATE, UPDATE, INSERT et DELETE dans des tables comportant des index sur des colonnes calculées ou des vues indexées échouent. Pour plus d’informations sur les paramètres des options SET requises avec les vues indexées et des index sur des colonnes calculées, consultez « Considérations lorsque vous utilisez des instructions SET » dans [instructions SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md).  
  
 Pour afficher la valeur actuelle de ce paramètre, exécutez la requête suivante.  
  
```  
DECLARE @NUMERIC_ROUNDABORT VARCHAR(3) = 'OFF';  
IF ( (8192 & @@OPTIONS) = 8192 ) SET @NUMERIC_ROUNDABORT = 'ON';  
SELECT @NUMERIC_ROUNDABORT AS NUMERIC_ROUNDABORT;  
  
```  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant montre l'ajout et le stockage de deux valeurs d'une précision de quatre décimales dans une variable dont la précision est de deux décimales. Les expressions montrent les effets des différents paramètres `SET NUMERIC_ROUNDABORT` et `SET ARITHABORT`.  
  
```  
-- SET NOCOUNT to ON,   
-- SET NUMERIC_ROUNDABORT to ON, and SET ARITHABORT to ON.  
SET NOCOUNT ON;  
PRINT 'SET NUMERIC_ROUNDABORT ON';  
PRINT 'SET ARITHABORT ON';  
SET NUMERIC_ROUNDABORT ON;  
SET ARITHABORT ON;  
GO  
DECLARE @result DECIMAL(5, 2),  
   @value_1 DECIMAL(5, 4),   
   @value_2 DECIMAL(5, 4);  
SET @value_1 = 1.1234;  
SET @value_2 = 1.1234 ;  
SELECT @result = @value_1 + @value_2;  
SELECT @result;  
GO  
  
-- SET NUMERIC_ROUNDABORT to ON and SET ARITHABORT to OFF.  
PRINT 'SET NUMERIC_ROUNDABORT ON';  
PRINT 'SET ARITHABORT OFF';  
SET NUMERIC_ROUNDABORT ON;  
SET ARITHABORT OFF;  
GO  
DECLARE @result DECIMAL(5, 2),  
   @value_1 DECIMAL(5, 4),   
   @value_2 DECIMAL(5, 4);  
SET @value_1 = 1.1234;  
SET @value_2 = 1.1234 ;  
SELECT @result = @value_1 + @value_2;  
SELECT @result;  
GO  
  
-- SET NUMERIC_ROUNDABORT to OFF and SET ARITHABORT to ON.  
PRINT 'SET NUMERIC_ROUNDABORT OFF';  
PRINT 'SET ARITHABORT ON';  
SET NUMERIC_ROUNDABORT OFF;  
SET ARITHABORT ON;  
GO  
DECLARE @result DECIMAL(5, 2),  
   @value_1 DECIMAL(5, 4),   
   @value_2 DECIMAL(5, 4);  
SET @value_1 = 1.1234;  
SET @value_2 = 1.1234 ;  
SELECT @result = @value_1 + @value_2;  
SELECT @result;  
GO  
  
-- SET NUMERIC_ROUNDABORT to OFF and SET ARITHABORT to OFF.  
PRINT 'SET NUMERIC_ROUNDABORT OFF';  
PRINT 'SET ARITHABORT OFF';  
SET NUMERIC_ROUNDABORT OFF;  
SET ARITHABORT OFF;  
GO  
DECLARE @result DECIMAL(5, 2),  
   @value_1 DECIMAL(5, 4),   
   @value_2 DECIMAL(5, 4);  
SET @value_1 = 1.1234;  
SET @value_2 = 1.1234;  
SELECT @result = @value_1 + @value_2;  
SELECT @result;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ARITHABORT &#40; Transact-SQL &#41;](../../t-sql/statements/set-arithabort-transact-sql.md)  
  
  

