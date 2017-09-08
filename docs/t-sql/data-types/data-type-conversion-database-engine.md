---
title: "Types de données (moteur de base de données) | Documents Microsoft"
ms.custom: 
ms.date: 07/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CAST function
- converting data types [SQL Server]
- CONVERT function
- data types [SQL Server], converting
- implicit data type conversions
- explicit data type conversions [SQL Server]
- converting data types [SQL Server], about converting data types
ms.assetid: ffacf45e-a488-48d0-9bb0-dcc7fd365299
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c0ed7f8e0e681de9f962e3eb963c0af315a0c25c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="data-type-conversion-database-engine"></a>Conversion de type de données (moteur de base de données)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Les types de données peuvent être convertis dans les scénarios suivants :
-   Lorsque les données d'un objet sont déplacées dans les données d'un autre objet, sont comparées ou combinées à ces dernières, les données d'un objet doivent être converties du type de données d'un objet en type de données de l'autre.  
-   Lorsque les données à partir d’un [!INCLUDE[tsql](../../includes/tsql-md.md)] colonne de résultats, code de retour ou paramètre de sortie est déplacé vers une variable de programme, les données doivent être converties à partir de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données système pour le type de données de la variable.  
  
Lors de la conversion entre une variable d'application et une colonne du jeu de résultats, un code de retour, un paramètre ou un marqueur de paramètre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les conversions de types de données acceptées sont définies par l'API de base de données.
  
## <a name="implicit-and-explicit-conversion"></a>Conversions implicites et explicites
Les types de données peuvent être convertis implicitement ou explicitement.
  
Les conversions implicites sont invisibles pour l'utilisateur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertit automatiquement les données d'un type de données en un autre. Par exemple, lorsqu’un **smallint** est comparée à une **int**, le **smallint** est implicitement converti en **int** avant la comparaison se poursuit.
  
**GETDATE()** convertit implicitement date en style 0. **SYSDATETIME()** convertit implicitement en date en style 21.
  
Les conversions explicites utilisent les fonctions CAST ou CONVERT.
  
Le [CAST et CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md) fonctions convertissent une valeur (une variable locale, une colonne ou une autre expression) à partir d’un type de données à un autre. Par exemple, la fonction `CAST` convertit la valeur numérique de `$157.27` en une chaîne de caractères `'157.27'` :
  
```sql
CAST ( $157.27 AS VARCHAR(10) )  
```  
  
Utilisez CAST au lieu de CONVERT si vous souhaitez que le code de programmation [!INCLUDE[tsql](../../includes/tsql-md.md)] soit compatible avec la norme ISO. Utilisez la fonction CONVERT et non la fonction CAST pour bénéficier de la fonctionnalité style de la fonction CONVERT.
  
L'illustration ci-dessous reprend toutes les conversions de types de données explicites et implicites autorisées pour les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournis par le système. Ceux-ci incluent **xml**, **bigint**, et **sql_variant**. Il n’existe aucune conversion implicite lors de l’attribution de la **sql_variant** type de données, mais il existe une conversion implicite vers **sql_variant**.
  
![Table de conversion de types de données](../../t-sql/data-types/media/lrdatahd.png "table de conversion de types de données")
  
## <a name="data-type-conversion-behaviors"></a>Comportements de conversion de type de données
Lors de la conversion du type de données d'un objet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en un autre, certaines conversions de types de données implicites et explicites ne sont pas prises en charge. Par exemple, un **nchar** valeur ne peut pas être convertie en un **image** valeur. Un **nchar** peut uniquement être converti en **binaire** à l’aide d’une conversion explicite, une conversion implicite vers **binaire** n’est pas pris en charge. Toutefois, un **nchar** peut être converti explicitement ou implicitement en **nvarchar**.
  
Les rubriques suivantes décrivent les comportements de conversion propres aux types de données correspondants :
  
 - [binary et varbinary &#40;Transact-SQL&#41;](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)  
 - [datetime2 &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime2-transact-sql.md)  
 - [Money et smallmoney &#40; Transact-SQL &#41;](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)  
 - [bits &#40; Transact-SQL &#41;](../../t-sql/data-types/bit-transact-sql.md)  
 - [datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
 - [smalldatetime &#40; Transact-SQL &#41;](../../t-sql/data-types/smalldatetime-transact-sql.md)  
 - [char et varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md)  
 - [Decimal et numeric &#40; Transact-SQL &#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)  
 - [sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)  
 - [date &#40;Transact-SQL&#41;](../../t-sql/data-types/date-transact-sql.md)  
 - [float et real &#40; Transact-SQL &#41;](../../t-sql/data-types/float-and-real-transact-sql.md)  
 - [temps &#40; Transact-SQL &#41;](../../t-sql/data-types/time-transact-sql.md)  
 - [DateTime &#40; Transact-SQL &#41;](../../t-sql/data-types/datetime-transact-sql.md)  
 - [int, bigint, smallint, tinyint et #40 ; Transact-SQL &#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)  
 - [uniqueidentifier &#40; Transact-SQL &#41;](../../t-sql/data-types/uniqueidentifier-transact-sql.md)  
  
###  <a name="converting-data-types-by-using-ole-automation-stored-procedures"></a>Conversion de types de données à l'aide des procédures stockées OLE Automation  
Étant donné que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise les types de données [!INCLUDE[tsql](../../includes/tsql-md.md)] et qu'OLE Automation utilise les types de données [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], les procédures stockées OLE Automation doivent convertir les données qu'elles s'échangent.
  
Le tableau suivant décrit la conversion des types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en types de données [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].
  
|Type de données SQL Server|Type de données Visual Basic|  
|--------------------------|----------------------------|  
|**char**, **varchar**, **texte**, **nvarchar**, **ntext**|**Chaîne**|  
|**décimal**, **numérique**|**Chaîne**|  
|**bit**|**Booléen**|  
|**binaire**, **varbinary**, **image**|Unidimensionnel **Byte()** tableau|  
|**int**|**Long**|  
|**smallint**|**Entier**|  
|**tinyint**|**Octets**|  
|**float**|**Double**|  
|**real**|**Unique**|  
|**money**, **smallmoney**|**Monétaire (Currency)**|  
|**DateTime**, **smalldatetime**|**Date**|  
|Tout type qui prend la valeur NULL|**Variant** la valeur Null|  
  
Tout seul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valeurs sont converties en un seul [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] valeur à l’exception de **binaire**, **varbinary**, et **image** valeurs. Ces valeurs sont converties en une dimension **Byte()** de tableau dans [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. Ce tableau a une plage de **octets (**0 à *longueur*1**)** où *longueur* est le nombre d’octets dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **binaire**, **varbinary**, ou **image** valeurs.
  
Il s'agit des conversions des types de données [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] en types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
|Type de données Visual Basic|Type de données SQL Server|  
|----------------------------|--------------------------|  
|**Long**, **entier**, **octets**, **booléenne**, **objet**|**int**|  
|**Double**, **unique**|**float**|  
|**Monétaire (Currency)**|**money**|  
|**Date**|**datetime**|  
|**Chaîne** de 4000 caractères ou moins|**varchar**/**nvarchar**|  
|**Chaîne** avec plus de 4000 caractères|**texte**/**ntext**|  
|Unidimensionnel **Byte()** tableau de 8 000 octets ou moins|**varbinary**|  
|Unidimensionnel **Byte()** tableau avec plus de 8 000 octets.|**image**|  
  
## <a name="see-also"></a>Voir aussi
[Procédures stockées OLE Automation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[COLLATE &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)
  
  

