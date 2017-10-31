---
title: SET ANSI_PADDING (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ANSI_PADDING_TSQL
- ANSI_PADDING
- SET_ANSI_PADDING_TSQL
- SET ANSI_PADDING
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], short values
- ANSI_PADDING option
- short values [SQL Server]
- SET ANSI_PADDING statement
- trailing blanks
ms.assetid: 92bd29a3-9beb-410e-b7e0-7bc1dc1ae6d0
caps.latest.revision: 47
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 426cbfe673bafe6e1770745ca16ba23fd068fb67
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-ansipadding-transact-sql"></a>SET ANSI_PADDING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contrôle le mode de stockage dans la colonne des valeurs dont la longueur est inférieure à la taille définie pour la colonne et de celles contenant des espaces à droite pour les données de type **char**, **varchar**, **binary**et **varbinary** .  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server  
  
SET ANSI_PADDING { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_PADDING ON;  
```  
  
## <a name="remarks"></a>Notes  
 Colonnes définies avec **char**, **varchar**, **binaire**, et **varbinary** des types de données ont une taille définie.  
  
 Cette valeur affecte uniquement la définition de nouvelles colonnes. Une fois la colonne créée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stocke les valeurs en fonction du paramètre en vigueur lors de la création de la colonne. Les colonnes existantes ne sont pas affectées par toute modification ultérieure du paramètre.  
  
> [!NOTE]  
>  Il est recommandé que l'option SET ANSI_PADDING soit toujours activée (ON).  
  
 Le tableau suivant montre les effets de la valeur de SET ANSI_PADDING lorsque les valeurs sont insérées dans des colonnes avec **char**, **varchar**, **binaire**, et **varbinary** des types de données.  
  
|Paramètre|char (*n*) non NULL ou binary (*n*) non NULL|char (*n*) NULL ou binary (*n*) NULL|varchar (*n*) ou varbinary (*n*)|  
|-------------|----------------------------------------------------|--------------------------------------------|----------------------------------------|  
|ON|Valeur d’origine de remplissage (avec les espaces à droite pour **char** colonnes et avec des zéros pour **binaire** colonnes) à la longueur de la colonne.|Suit les mêmes règles que pour **char (***n***)** ou **binaire (***n***)** NOT NULL lorsque l’option SET ANSI_PADDING est activée.|Les espaces à droite des valeurs de type character insérées dans **varchar** colonnes ne sont pas tronqués. Zéros à droite dans les valeurs binaires insérées dans **varbinary** colonnes ne sont pas tronqués. Les valeurs ne sont pas complétées à concurrence de la longueur de la colonne.|  
|OFF|Valeur d’origine de remplissage (avec les espaces à droite pour **char** colonnes et avec des zéros pour **binaire** colonnes) à la longueur de la colonne.|Suit les mêmes règles que pour **varchar** ou **varbinary** lorsque SET ANSI_PADDING est désactivé.|Les espaces à droite des valeurs de type character insérées dans un **varchar** colonne sont tronqués. Zéros à droite dans les valeurs binaires insérées dans un **varbinary** colonne sont tronqués.|  
  
> [!NOTE]  
>  Lorsque complétées, **char** les colonnes sont complétées par des espaces, et **binaire** colonnes sont complétées avec des zéros. Lorsqu’il est tronqué, **char** colonnes ont des espaces de fin tronqués, et **binaire** colonnes ont les zéros à droite.  
  
 SET ANSI_PADDING doit être activée (valeur ON) lors de la création ou de la modification d'index dans des colonnes calculées ou des vues indexées. Pour plus d’informations sur les paramètres des options SET requises avec les vues indexées et des index sur des colonnes calculées, consultez « Considérations lorsque vous utilisez des instructions SET » dans [instructions SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md).  
  
 La valeur par défaut de SET ANSI_PADDING est ON. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatiquement de set ANSI_PADDING ON lors de la connexion. Cette option peut être configurée dans les sources de données et les attributs de connexion ODBC, ou encore dans les propriétés de connexion OLE DB définies dans l'application avant la connexion. Dans le cas d'applications DB-Library, SET ANSI_PADDING prend par défaut la valeur OFF.  
  
 La valeur de SET ANSI_PADDING n’affecte pas la **nchar**, **nvarchar**, **ntext**, **texte**, **image**, **varbinary (max)**, **varchar (max)**, et **nvarchar (max)** des types de données. Le comportement par défaut est toujours celui de l'option SET ANSI_PADDING ON. Les espaces et les zéros à droite ne sont donc pas tronqués.  
  
 Lorsque SET ANSI_DEFAULTS a la valeur ON, l'option SET ANSI_PADDING est activée.  
  
 La valeur de SET ANSI_PADDING est définie lors de l'exécution, et non durant l'analyse.  
  
 Pour afficher la valeur actuelle de ce paramètre, exécutez la requête suivante.  
  
```  
DECLARE @ANSI_PADDING VARCHAR(3) = 'OFF';  
IF ( (16 & @@OPTIONS) = 16 ) SET @ANSI_PADDING = 'ON';  
SELECT @ANSI_PADDING AS ANSI_PADDING;  
  
```  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle public.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant présente comment l'option affecte les différents types de données.  
  
```  
PRINT 'Testing with ANSI_PADDING ON'  
SET ANSI_PADDING ON;  
GO  
  
CREATE TABLE t1 (  
   charcol CHAR(16) NULL,   
   varcharcol VARCHAR(16) NULL,   
   varbinarycol VARBINARY(8)  
);  
GO  
INSERT INTO t1 VALUES ('No blanks', 'No blanks', 0x00ee);  
INSERT INTO t1 VALUES ('Trailing blank ', 'Trailing blank ', 0x00ee00);  
  
SELECT 'CHAR' = '>' + charcol + '\<', 'VARCHAR'='>' + varcharcol + '\<',  
   varbinarycol  
FROM t1;  
GO  
  
PRINT 'Testing with ANSI_PADDING OFF';  
SET ANSI_PADDING OFF;  
GO  
  
CREATE TABLE t2 (  
   charcol CHAR(16) NULL,   
   varcharcol VARCHAR(16) NULL,   
   varbinarycol VARBINARY(8)  
);  
GO  
INSERT INTO t2 VALUES ('No blanks', 'No blanks', 0x00ee);  
INSERT INTO t2 VALUES ('Trailing blank ', 'Trailing blank ', 0x00ee00);  
  
SELECT 'CHAR' = '>' + charcol + '\<', 'VARCHAR'='>' + varcharcol + '<',  
   varbinarycol  
FROM t2;  
GO  
  
DROP TABLE t1;  
DROP TABLE t2;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sessionproperty-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)  
  
  

