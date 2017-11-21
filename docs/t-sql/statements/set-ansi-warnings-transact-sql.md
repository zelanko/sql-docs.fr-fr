---
title: SET ANSI_WARNINGS (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET ANSI_WARNINGS
- ANSI_WARNINGS_TSQL
- ANSI_WARNINGS
- SET_ANSI_WARNINGS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], ISO standard behavior
- warnings [SQL Server]
- SET ANSI_WARNINGS statement
- ANSI_WARNINGS option
ms.assetid: f82aaab0-334f-427b-89b0-de4af596b4fa
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: feee804808cb9ba8d6e3dd97fb512a3a73301e17
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-ansiwarnings-transact-sql"></a>SET ANSI_WARNINGS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Spécifie le comportement conforme à la norme ISO pour plusieurs conditions d'erreur :  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET ANSI_WARNINGS { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_WARNINGS ON;  
```  
  
## <a name="remarks"></a>Notes  
 SET ANSI_WARNINGS a une incidence sur les conditions suivantes :  
  
-   Lorsque la valeur est définie à ON et que des valeurs NULL figurent dans des fonctions d'agrégation (par exemple, SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP ou COUNT), un message d'avertissement est généré. Lorsque la valeur est définie à OFF, aucun avertissement n'est émis.  
  
-   Lorsque la valeur est définie à ON, les erreurs de division par zéro et de dépassement de capacité arithmétique provoquent l'annulation de l'instruction et l'émission d'un message d'erreur. Lorsque la valeur est définie à OFF, les erreurs de division par zéro et de dépassement arithmétique entraînent le renvoi de valeurs NULL. Dans lequel une erreur de division par zéro ou de dépassement arithmétique provoque le renvoi de valeurs null se produit si une insertion ou une mise à jour est tentée un **caractère**, Unicode, ou **binaire** colonne dans laquelle la longueur d’une nouvelle valeur dépasse la taille maximale de la colonne. Si SET ANSI_WARNINGS a la valeur ON, l’instruction INSERT ou UPDATE est annulée comme spécifié par la norme ISO. Les espaces blancs sont ignorés dans des colonnes de type caractère et les zéros sont ignorés dans les colonnes de type binaire. Lorsque la valeur est définie à OFF, les données sont tronquées de façon à correspondre à la taille de la colonne, et l'instruction s'exécute correctement.  
  
    > [!NOTE]  
    >  Si la troncation se produit dans une conversion vers ou depuis **binaire** ou **varbinary** données, aucun avertissement ou erreur sont émises, quelles que soient les options SET.  
  
    > [!NOTE]  
    >  L'option ANSI_WARNINGS n'est pas reconnue lors d'un passage de paramètres dans une procédure stockée ou dans une fonction définie par l'utilisateur, ou bien lors de la déclaration et de la définition de variables dans une instruction par lot. Par exemple, si une variable est définie en tant que **char (3)**, puis définissez une valeur supérieure à trois caractères, les données sont tronquées à la taille définie et l’insertion ou instruction de mise à jour réussit.  
  
 L'option user options de la procédure stockée sp_configure peut servir à définir la valeur par défaut de ANSI_WARNINGS pour toutes les connexions au serveur. Pour plus d'informations, consultez [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 L'option SET ANSI_WARNINGS doit être activée (valeur ON) lors de la création ou de la manipulation d'index dans des colonnes calculées ou des vues indexées. Si SET ANSI_WARNINGS est désactivé (OFF), les instructions CREATE, UPDATE, INSERT et DELETE dans des tables comportant des index sur des colonnes calculées ou des vues indexées échouent. Pour plus d’informations sur les paramètres des options SET requises avec les vues indexées et des index sur des colonnes calculées, consultez « Considérations lorsque vous utilisez des instructions SET » dans [instructions SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comprend l'option de base de données ANSI_WARNINGS. C'est l'équivalent de SET ANSI_WARNINGS. Lorsque SET ANSI_WARNINGS est défini à ON, des erreurs ou des avertissements sont générés dans le cas d'une division par zéro, d'une chaîne trop longue pour la colonne de la base de données, ou de toute autre erreur similaire. Lorsque SET ANSI_WARNINGS est défini à OFF, ces erreurs et avertissements ne sont pas générés. La valeur par défaut de SET ANSI_WARNINGS dans la base de données model est définie à OFF. Si elle n'est pas spécifiée, la valeur de ANSI_WARNINGS s'applique. Si SET ANSI_WARNINGS est désactivé, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise la valeur de la colonne is_ansi_warnings_on dans le [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vue de catalogue.  
  
 La valeur de ANSI_WARNINGS doit être définie à ON lors de l'exécution de requêtes distribuées.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatiquement valeur On à ANSI_WARNINGS lors de la connexion. Cette option peut être configurée dans les sources de données et les attributs de connexion ODBC, définis dans l'application avant la connexion. La valeur par défaut pour SET ANSI_WARNINGS est OFF lorsqu'il s'agit de connexions à partir d'applications de bibliothèques de bases de données.  
  
 Lorsque SET ANSI_DEFAULTS est défini à ON, l'option SET ANSI_WARNINGS est activée.  
  
 L'option SET ANSI_WARNINGS est appliquée lors de l'exécution, et non pas lors de l'analyse.  
  
 Si la valeur de SET ARITHABORT ou de SET ARITHIGNORE est définie à OFF et que SET ANSI_WARNINGS a la valeur ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renvoie malgré tout un message d'erreur quand il rencontre une erreur de division par zéro ou de dépassement de capacité.  
  
 Pour afficher la valeur actuelle de ce paramètre, exécutez la requête suivante.  
  
```  
DECLARE @ANSI_WARN VARCHAR(3) = 'OFF';  
IF ( (8 & @@OPTIONS) = 8 ) SET @ANSI_WARN = 'ON';  
SELECT @ANSI_WARN AS ANSI_WARNINGS;  
```  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle public.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant illustre les trois cas mentionnés plus haut, avec SET ANSI_WARNINGS prenant la valeur ON ou OFF.  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TABLE T1   
(  
   a int,   
   b int NULL,   
   c varchar(20)  
);  
GO  
  
SET NOCOUNT ON;  
  
INSERT INTO T1   
VALUES (1, NULL, '')   
      ,(1, 0, '')  
      ,(2, 1, '')  
      ,(2, 2, '');  
  
SET NOCOUNT OFF;  
GO  
  
PRINT '**** Setting ANSI_WARNINGS ON';  
GO  
  
SET ANSI_WARNINGS ON;  
GO  
  
PRINT 'Testing NULL in aggregate';  
GO  
SELECT a, SUM(b)   
FROM T1   
GROUP BY a;  
GO  
  
PRINT 'Testing String Overflow in INSERT';  
GO  
INSERT INTO T1   
VALUES (3, 3, 'Text string longer than 20 characters');  
GO  
  
PRINT 'Testing Divide by zero';  
GO  
SELECT a / b AS ab   
FROM T1;  
GO  
  
PRINT '**** Setting ANSI_WARNINGS OFF';  
GO  
SET ANSI_WARNINGS OFF;  
GO  
  
PRINT 'Testing NULL in aggregate';  
GO  
SELECT a, SUM(b)   
FROM T1   
GROUP BY a;  
GO  
  
PRINT 'Testing String Overflow in INSERT';  
GO  
INSERT INTO T1   
VALUES (4, 4, 'Text string longer than 20 characters');  
GO  
SELECT a, b, c   
FROM T1  
WHERE a = 4;  
GO  
  
PRINT 'Testing Divide by zero';  
GO  
SELECT a / b AS ab   
FROM T1;  
GO  
  
DROP TABLE T1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [SESSIONPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  

