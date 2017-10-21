---
title: "Types de données (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 9/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system data types [SQL Server]
- data types [SQL Server]
- data types [SQL Server], about data types
ms.assetid: a54f7373-b247-4d61-8fb8-7f2ec7a8d0a4
caps.latest.revision: 45
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: d9a995f7d29fe91e14affa9266a9bce73acc9010
ms.openlocfilehash: 75efc7b5a58b3739a196e36b2c80d4ee37a92003
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---

# <a name="data-types-transact-sql"></a>Types de données (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à chaque colonne, variable locale, expression et paramètre correspond un type de données. Un type de données est un attribut qui spécifie le type de données que l'objet peut contenir : données de type Integer, données caractères, données monétaires, données de date et d'heure, chaînes binaires, et ainsi de suite.
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit un ensemble de types de données système qui définissent tous les types de données utilisables avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez également définir vos propres types de données dans [!INCLUDE[tsql](../../includes/tsql-md.md)] ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Les types de données d'alias sont basés sur les types de données fournis par le système. Pour plus d’informations sur les types de données alias, consultez [CREATE TYPE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-type-transact-sql.md). Les types définis par l'utilisateur tirent leurs caractéristiques des méthodes et des opérateurs d'une classe que vous créez à l'aide de l'un des langages de programmation pris en charge par [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].
  
Lorsqu'un opérateur combine deux expressions qui diffèrent par les types de données, les classements, la précision, l'échelle ou la longueur, les caractéristiques du résultat sont déterminées comme suit :
-   Le type de données du résultat est déterminé par l'application des règles de priorité des types de données aux types de données des expressions entrées. Pour plus d’informations, consultez [Priorités des types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
-   Le classement du résultat est déterminé par les règles de priorité des classements lorsque le type de données de résultat est **char**, **varchar**, **texte**, **nchar**, **nvarchar**, ou **ntext**. Pour plus d’informations, consultez [priorité de classement &#40; Transact-SQL &#41; ](../../t-sql/statements/collation-precedence-transact-sql.md).  
-   Les précision, échelle et longueur du résultat dépendent des précision, échelle et longueur des expressions entrées. Pour plus d’informations, consultez [Précision, échelle et longueur &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]fournit les synonymes des types de données pour la compatibilité ISO. Pour plus d’informations, consultez [synonymes des types de données &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-type-synonyms-transact-sql.md).
  
## <a name="data-type-categories"></a>Catégories de types de données
Types de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont organisées selon les catégories suivantes :
  
|||  
|-|-|  
|Valeurs numériques exactes|Chaînes de caractères Unicode|  
|Valeurs numériques approximatives|Chaînes binaires|  
|Date et heure|Autres types de données|  
|Chaînes de caractères||  
  
Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], en fonction de leurs caractéristiques de stockage, certains types de données sont désignés comme appartenant aux groupes suivants :
-   Types de données de valeur élevée : **varchar (max)**, et **nvarchar (max)**  
-   Types de données LOB : **texte**, **ntext**, **image**, **varbinary (max)**, et **xml**  
  
    > [!NOTE]  
    >  sp_help retourne -1 comme longueur des valeurs élevées et **xml** des types de données.  
  
### <a name="exact-numerics"></a>Valeurs numériques exactes
  
|||  
|-|-|  
|[bigint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|[numeric](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)|  
|[bit](../../t-sql/data-types/bit-transact-sql.md)|[smallint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|  
|[decimal](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)|[smallmoney](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)|  
|[int](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|[tinyint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|  
|[money](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)||  
  
### <a name="approximate-numerics"></a>Valeurs numériques approximatives
  
|||  
|-|-|  
|[float](../../t-sql/data-types/float-and-real-transact-sql.md)|[real](../../t-sql/data-types/float-and-real-transact-sql.md)|  
  
### <a name="date-and-time"></a>Date et heure
  
|||  
|-|-|  
|[date](../../t-sql/data-types/date-transact-sql.md)|[datetimeoffset](../../t-sql/data-types/datetimeoffset-transact-sql.md)|  
|[datetime2](../../t-sql/data-types/datetime2-transact-sql.md)|[smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md)|  
|[datetime](../../t-sql/data-types/datetime-transact-sql.md)|[time](../../t-sql/data-types/time-transact-sql.md)|  
  
### <a name="character-strings"></a>Chaînes de caractères
  
|||  
|-|-|  
|[char](../../t-sql/data-types/char-and-varchar-transact-sql.md)|[varchar](../../t-sql/data-types/char-and-varchar-transact-sql.md)|  
|[text](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)||  
  
### <a name="unicode-character-strings"></a>Chaînes de caractères Unicode
  
|||  
|-|-|  
|[nchar](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)|[nvarchar](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)|  
|[ntext](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)||  
  
### <a name="binary-strings"></a>Chaînes binaires
  
|||  
|-|-|  
|[binaire](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|[varbinary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|  
|[image](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)||  
  
### <a name="other-data-types"></a>Autres types de données
  
|||  
|-|-|  
|[cursor](../../t-sql/data-types/cursor-transact-sql.md)|[rowversion](../../t-sql/data-types/rowversion-transact-sql.md)|  
|[hierarchyid](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)|[uniqueidentifier](../../t-sql/data-types/uniqueidentifier-transact-sql.md)|  
|[sql_variant](../../t-sql/data-types/sql-variant-transact-sql.md)|[xml](../../t-sql/xml/xml-transact-sql.md)|  
|[Types de géométrie spatiale](../../t-sql/spatial-geometry/spatial-types-geometry-transact-sql.md) |[Types Geography spatiale](../../t-sql/spatial-geography/spatial-types-geography.md)|  
|[table](../../t-sql/data-types/table-transact-sql.md) | |
  
## <a name="see-also"></a>Voir aussi
[CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DÉCLARER @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-local-variable-transact-sql.md) 
 [EXECUTE &#40; Transact-SQL &#41;](../../t-sql/language-elements/execute-transact-sql.md)  
[Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[Fonctions &#40; Transact-SQL &#41;](../../t-sql/functions/functions.md)  
[COMME &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)  
[sp_droptype &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-droptype-transact-sql.md)  
[sp_help &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)  
[sp_rename &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)
  
  

