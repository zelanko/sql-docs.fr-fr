---
title: nchar et nvarchar (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nvarchar data type
- nchar data type
ms.assetid: 81ee5637-ee31-4c4d-96d0-56c26a742354
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4c3f2e9ad1d63992be8f4e4a4c65d821fae73389
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="nchar-and-nvarchar-transact-sql"></a>nchar et nvarchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Types de données basés sur des caractères qui sont des données Unicode de longueur fixe, **nchar**, ou de longueur variable, **nvarchar**, et qui utilisent le jeu de caractères UNICODE UCS-2.
  
## <a name="arguments"></a>Arguments  
**nchar** [ ( n ) ]  
Données de type chaîne Unicode de longueur fixe. *n* définit la longueur de chaîne et doit être une valeur comprise entre 1 et 4 000. La taille de stockage est le double de *n* octets. Quand la page de codes du classement utilise des caractères sur deux octets, la taille de stockage est toujours de *n* octets. En fonction de la chaîne, la taille de stockage de *n* octets peut être inférieure à la valeur spécifiée pour *n*. Les synonymes ISO de **nchar** sont **national char** et **national character**.
  
**nvarchar** [ ( n | **max** ) ]  
Données de type chaîne Unicode de longueur variable. *n* définit la longueur de chaîne et peut être une valeur comprise entre 1 et 4 000. **max** indique que la taille de stockage maximale est de 2^31-1 caractères (2 Go). La taille de stockage, en octets, est le double du nombre de la longueur réelle des données entrée plus 2 octets. Les synonymes ISO de **nvarchar** sont **national char varying** et **national character varying**.
  
## <a name="remarks"></a>Notes   
Quand la valeur de *n* n’est spécifiée ni dans une définition de données ni dans une instruction de déclaration de variable, la longueur par défaut est 1. Quand la valeur de *n* n’est pas précisée avec la fonction CAST, la longueur par défaut est 30.
  
Utilisez **nchar** si vous pensez que les tailles des entrées de données de la colonne seront similaires.
  
Utilisez **nvarchar** si vous pensez que les tailles des entrées de données de la colonne varieront considérablement.
  
**sysname** est un type de données défini par l’utilisateur fourni par le système qui présente la même fonctionnalité que **nvarchar(128)**, à la différence qu’il n’accepte pas la valeur Null. **sysname** est utilisé pour faire référence aux noms des objets de base de données.
  
Les objets qui utilisent **nchar** ou **nvarchar** reçoivent le classement par défaut de la base de données, sauf si un classement spécifique est affecté à l’aide de la clause COLLATE.
  
SET ANSI_PADDING a toujours la valeur ON pour **nchar** et **nvarchar**. SET ANSI_PADDING OFF ne s’applique pas aux types de données **nchar** ni **nvarchar**.
  
Faites précéder les constantes de chaînes de caractères Unicode de la lettre N. Sans le préfixe N, la chaîne est convertie en page de codes par défaut de la base de données. Cette page risque de ne pas reconnaître certains caractères.
 
> [!NOTE]  
>  Quand la lettre N est ajoutée comme préfixe à une constante de chaîne, la conversion implicite aboutit à une chaîne Unicode si la constante à convertir ne dépasse pas la longueur maximale pour un type de données de chaîne Unicode (4 000). Sinon, la conversion implicite génère une valeur élevée (max) Unicode.
  
> [!WARNING]  
>  Chaque colonne **varchar(max)** ou **nvarchar(max)** non Null demande 24 octets d’allocation fixe supplémentaire calculée par rapport à la limite de 8 060 octets par ligne pendant une opération de tri. Cela peut produire une limite implicite du nombre de colonnes **varchar(max)** ou **nvarchar(max)** non Null pouvant être créées dans une table. Aucune erreur spéciale n'est fournie quand la table est créée (mis à part l’avertissement habituel indiquant que la taille maximale de ligne dépasse la taille maximale autorisée de 8 060 octets) ou quand les données sont insérées. Cette grande taille de ligne peut provoquer des erreurs (comme l’erreur 512) au cours des opérations normales, telles que la mise à jour de la clé d’index cluster ou le tri de l’intégralité des colonnes, que les utilisateurs ne peuvent pas anticiper tant qu’elles n’ont pas été effectuées.  
  
## <a name="converting-character-data"></a>Conversion des données de type caractère  
Pour plus d’informations sur la conversion de données caractères, consultez [char et varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md).
  
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
[COLLATE &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)  
[SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Prise en charge d'Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)
  
  
