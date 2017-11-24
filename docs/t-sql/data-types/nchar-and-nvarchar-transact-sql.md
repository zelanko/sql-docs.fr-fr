---
title: NCHAR et nvarchar (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- nvarchar data type
- nchar data type
ms.assetid: 81ee5637-ee31-4c4d-96d0-56c26a742354
caps.latest.revision: "44"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4c3f2e9ad1d63992be8f4e4a4c65d821fae73389
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="nchar-and-nvarchar-transact-sql"></a>nchar et nvarchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Types de données qui sont soit à longueur fixe, caractère **nchar**, ou de longueur variable, **nvarchar**, jeu de caractères de données Unicode et l’utilisation de l’UNICODE UCS-2.
  
## <a name="arguments"></a>Arguments  
**NCHAR** [(n)]  
Données de type chaîne Unicode de longueur fixe. *n*définit la longueur de chaîne et doit être une valeur comprise entre 1 et 4 000. La taille de stockage est le double  *n*  octets. Lorsque la page de codes du classement utilise des caractères codés sur deux octets, la taille de stockage est toujours  *n*  octets. En fonction de la chaîne, la taille de stockage  *n*  octets peut être inférieure à la valeur spécifiée pour  *n* . Les synonymes ISO de **nchar** sont **national char** et **caractères nationaux**...
  
**nvarchar** [(n | **max** )]  
Données de type chaîne Unicode de longueur variable. *n*définit la longueur de chaîne et peut être une valeur comprise entre 1 et 4 000. **max** indique que la taille de stockage maximale est de 2 ^ 31-1 caractères (2 Go). La taille de stockage, en octets, est le double du nombre de la longueur réelle des données entrée plus 2 octets. Les synonymes ISO de **nvarchar** sont **national char varying** et **variable de caractères nationaux**.
  
## <a name="remarks"></a>Notes  
Lorsque  *n*  n’est pas spécifié dans une définition de données ou d’une instruction de déclaration de variable, la longueur par défaut est 1. Lorsque  *n*  n’est pas spécifié avec la fonction CAST, la longueur par défaut est 30.
  
Utilisez **nchar** lorsque les tailles des entrées de données de colonne probablement vont être similaire.
  
Utilisez **nvarchar** lorsque les tailles des entrées de données de colonne sont probablement va varier considérablement.
  
**sysname** est un type de données défini par l’utilisateur système est fonctionnellement équivalent à **nvarchar (128)**, sauf qu’il ne peut pas être null. **sysname** est utilisé pour référencer les noms d’objet de base de données.
  
Objets qui utilisent **nchar** ou **nvarchar** reçoivent le classement par défaut de la base de données, sauf si un classement spécifique est affecté à l’aide de la clause COLLATE.
  
SET ANSI_PADDING est toujours activé pour **nchar** et **nvarchar**. SET ANSI_PADDING OFF ne s’applique pas à la **nchar** ou **nvarchar** des types de données.
  
Préfixe les constantes de chaîne de caractères Unicode avec la lettre N. Sans le préfixe N, la chaîne est convertie en page de codes par défaut de la base de données. Cette page risque de ne pas reconnaître certains caractères.
 
> [!NOTE]  
>  Lorsqu’une constante de chaîne avec la lettre N en ajoutant le préfixe, la conversion implicite entraîne une chaîne Unicode si la constante à convertir ne dépasse pas la longueur maximale pour un type de données de chaîne Unicode (4 000). Sinon, la conversion implicite génère une grand-valeur Unicode (max).
  
> [!WARNING]  
>  Chaque valeur non null **varchar (max)** ou **nvarchar (max)** colonne requiert 24 octets d’allocation fixe supplémentaire calculée par rapport à la limite de 8 060 octets par ligne pendant une opération de tri. Cela peut créer une limite implicite au nombre de non null **varchar (max)** ou **nvarchar (max)** les colonnes qui peuvent être créés dans une table. Aucune erreur spéciale n'est fournie quand la table est créée (mis à part l’avertissement habituel indiquant que la taille maximale de ligne dépasse la taille maximale autorisée de 8 060 octets) ou quand les données sont insérées. Cette grande taille de ligne peut provoquer des erreurs (comme l’erreur 512) au cours des opérations normales, telles que la mise à jour de la clé d’index cluster ou le tri de l’intégralité des colonnes, que les utilisateurs ne peuvent pas anticiper tant qu’elles n’ont pas été effectuées.  
  
## <a name="converting-character-data"></a>Conversion des données de type caractère  
Pour plus d’informations sur la conversion des données de type caractère, consultez [char et varchar &#40; Transact-SQL &#41; ](../../t-sql/data-types/char-and-varchar-transact-sql.md).
  
## <a name="examples"></a>Exemples  
  
```sql
CREATE TABLE dbo.MyTable  
(  
  MyNCharColumn nchar(15)  
,MyNVarCharColumn nvarchar(20)
  
);  
  
GO  
INSERT INTO dbo.MyTable VALUES (N'Test data', N'More test data');  
GO  
SELECT MyNCharColumn, MyNVarCharColumn  
FROM dbo.MyTable;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
MyNCharColumn   MyNVarCharColumn  
--------------- --------------------  
Test data       More test data  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[COLLATE &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[COMME &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)  
[SET ANSI_PADDING &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Prise en charge d'Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)
  
  
