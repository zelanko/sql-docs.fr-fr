---
title: SQL_VARIANT_PROPERTY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQL_VARIANT_PROPERTY_TSQL
- SQL_VARIANT_PROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- SQL_VARIANT_PROPERTY function
- sql_variant data type
ms.assetid: 50e5c1d9-4e95-4ed0-9c92-435c872a399e
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 71ca2fac0a6b9f087f9d434c5a701f5656889b9e
ms.openlocfilehash: bd9b181c04a96ee90b0bbb54546a1d925761224f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/13/2017

---
# <a name="sqlvariantproperty-transact-sql"></a>SQL_VARIANT_PROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne le type de base de données et d’autres informations sur un **sql_variant** valeur.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SQL_VARIANT_PROPERTY ( expression , property )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Est une expression de type **sql_variant**.  
  
 *propriété*  
 Contient le nom de la **sql_variant** propriété pour laquelle les informations ne doivent être fournies. *propriété* est **varchar (**128**)**, et peut prendre l’une des valeurs suivantes :  
  
|Valeur| Description|Type de base sql_variant renvoyé|  
|-----------|-----------------|----------------------------------------|  
|**Type de base**|Type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tel que :<br /><br /> **bigint**<br /><br /> **binaire**<br /><br /> **char**<br /><br /> **date**<br /><br /> **datetime**<br /><br /> **datetime2**<br /><br /> **datetimeoffset**<br /><br /> **decimal**<br /><br /> **float**<br /><br /> **int**<br /><br /> **money**<br /><br /> **nchar**<br /><br /> **numeric**<br /><br /> **nvarchar**<br /><br /> **real**<br /><br /> **smalldatetime**<br /><br /> **smallint**<br /><br /> **smallmoney**<br /><br /> **time**<br /><br /> **tinyint**<br /><br /> **uniqueidentifier**<br /><br /> **varbinary**<br /><br /> **varchar**|**sysname**<br /><br /> NULL = Entrée non valide.|  
|**Précision**|Nombre de chiffres du type de données numériques de base :<br /><br /> **DateTime** = 23<br /><br /> **smalldatetime** = 16<br /><br /> **float** = 53<br /><br /> **Real** = 24<br /><br /> **décimal** (p, s) et **numérique** (p, s) = p<br /><br /> **Money** = 19<br /><br /> **smallmoney** = 10<br /><br /> **bigint** = 19<br /><br /> **int** = 10<br /><br /> **smallint** = 5<br /><br /> **tinyint** = 3<br /><br /> **bit** = 1<br /><br /> Tous les autres types = 0|**int**<br /><br /> NULL = Entrée non valide.|  
|**Échelle**|Nombre de chiffres décimaux après la virgule (point) dans le type de données numériques de base :<br /><br /> **décimal** (p, s) et **numérique** (p, s) = s<br /><br /> **Money** et **smallmoney** = 4<br /><br /> **DateTime** = 3<br /><br /> tous les autres types = 0|**int**<br /><br /> NULL = Entrée non valide.|  
|**TotalBytes**|Nombre d'octets requis pour conserver les métadonnées et les données de la valeur. Ces informations seraient utiles pour vérifier la taille maximale des données dans un **sql_variant** colonne. Si la valeur est supérieure à 900, la création d’index échoue.|**int**<br /><br /> NULL = Entrée non valide.|  
|**Classement**|Représente le classement de la particulier **sql_variant** valeur.|**sysname**<br /><br /> NULL = Entrée non valide.|  
|**MaxLength**|Longueur maximale du type de données (en octets). Par exemple, **MaxLength** de **nvarchar (**50**)** est 100, **MaxLength** de **int** est 4.|**int**<br /><br /> NULL = Entrée non valide.|  
  
## <a name="return-types"></a>Types de retour  
 **sql_variant**  
  
## <a name="examples"></a>Exemples  
### <a name="a-using-a-sqlvariant-in-a-table"></a>A. À l’aide d’un sql_variant dans une table  
 L’exemple suivant récupère `SQL_VARIANT_PROPERTY` plus d’informations sur la `colA` valeur `46279.1` où `colB`  = `1689`, étant donné que `tableA` a `colA` qui est de type `sql_variant` et `colB`.  
  
```sql    
CREATE   TABLE tableA(colA sql_variant, colB int)  
INSERT INTO tableA values ( cast (46279.1 as decimal(8,2)), 1689)  
SELECT   SQL_VARIANT_PROPERTY(colA,'BaseType') AS 'Base Type',  
         SQL_VARIANT_PROPERTY(colA,'Precision') AS 'Precision',  
         SQL_VARIANT_PROPERTY(colA,'Scale') AS 'Scale'  
FROM      tableA  
WHERE      colB = 1689  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]Notez que chacune de ces trois valeurs est un **sql_variant**.  
  
```  
Base Type    Precision    Scale  
---------    ---------    -----  
decimal      8           2  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-a-sqlvariant-as-a-variable"></a>B. À l’aide d’un sql_variant en tant que variable   
 L’exemple suivant récupère `SQL_VARIANT_PROPERTY` plus d’informations sur une variable nommée @v1.  
  
```sql    
DECLARE @v1 sql_variant;  
SET @v1 = 'ABC';  
SELECT @v1;  
SELECT SQL_VARIANT_PROPERTY(@v1, 'BaseType');  
SELECT SQL_VARIANT_PROPERTY(@v1, 'MaxLength');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)  
  
  


