---
title: rowversion (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- timestamp_TSQL
- timestamp
dev_langs:
- TSQL
helpviewer_keywords:
- rowversion data type
- size [SQL Server], rowversion
- row version-stamping [SQL Server]
- rowversion columns
- version-stamping table rows
- unique rowversion numbers
- unique timestamp numbers
- timestamp data type
- timestamp columns
- size [SQL Server], timestamp
ms.assetid: 65c9cf0e-3e8a-45f8-87b3-3460d96afb0b
caps.latest.revision: 57
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 47bcf3007657c1cf8f77c364aa21839cdd27d1ba
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="rowversion-transact-sql"></a>rowversion (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Type de données présentant des nombres binaires uniques automatiquement générés à l'intérieur d'une base de données. **rowversion** est généralement utilisé comme un mécanisme de marquage de version des lignes de table. La taille de stockage est de 8 octets. Le **rowversion** est simplement un numéro à incrémentation de type de données et ne conserve pas une date ou une heure. Pour enregistrer une date ou heure, utilisez un **datetime2** type de données.
  
## <a name="remarks"></a>Notes  
Chaque base de données possède un compteur est incrémenté pour chaque instruction insert ou une opération de mise à jour est effectuée sur une table qui contient un **rowversion** colonne dans la base de données. Ce compteur est la base de données rowversion. Il suit une heure relative au sein d'une base de données, et non pas une heure réelle qui peut être associée à une horloge. Une table peut avoir qu’un seul **rowversion** colonne. Chaque fois qu’une ligne avec un **rowversion** colonne est modifiée ou insérée, la valeur incrémentée rowversion est insérée dans le **rowversion** colonne. Cette propriété permet un **rowversion** colonne un candidat peu valable pour les clés, surtout les clés primaires. En effet, toute mise à jour apportée à la ligne a pour effet de changer la valeur rowversion, et par conséquent de modifier la valeur de la clé. Si la colonne se trouve dans une clé primaire, l'ancienne valeur de clé n'est plus valide et les clés étrangères faisant référence à l'ancienne valeur ne sont plus valides. Si la table est référencée dans un curseur dynamique, toutes les mises à jour modifient la position des lignes dans le curseur. Si la colonne est une clé d'index, toutes les mises à jour apportées à la ligne de données génèrent également des mises à jour de l'index.  Le **rowversion** valeur est incrémentée avec n’importe quelle instruction de mise à jour, même si aucune valeur de ligne n’est modifiés. (Par exemple, si une valeur de colonne est de 5 et une instruction update affecte la valeur 5, cette action est considérée comme une mise à jour même s’il n’existe aucune modification et le **rowversion** est incrémenté.)
  
**horodatage** est le synonyme de la **rowversion** type de données et le comportement des données dépend des synonymes de types. Dans les instructions DDL, utilisez **rowversion** au lieu de **timestamp** autant que possible. Pour plus d’informations, consultez [synonymes des types de données &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-type-synonyms-transact-sql.md).
  
Le [!INCLUDE[tsql](../../includes/tsql-md.md)] **timestamp** type de données est différente de la **timestamp** type de données défini dans la norme ISO.
  
> [!NOTE]  
>  Le **timestamp** syntaxe est déconseillée. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
Dans une instruction CREATE TABLE ou ALTER TABLE, vous n’avez pas à spécifier un nom de colonne pour le **timestamp** type de données, par exemple :
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, timestamp);  
```  
  
Si vous ne spécifiez pas un nom de colonne, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] génère le **timestamp** nom de la colonne ; Toutefois, le **rowversion** synonyme ne respecte pas ce comportement. Lorsque vous utilisez **rowversion**, vous devez spécifier un nom de colonne, par exemple :
  
```sql
CREATE TABLE ExampleTable2 (PriKey int PRIMARY KEY, VerCol rowversion) ;  
```  
  
> [!NOTE]  
>  Dupliquer **rowversion** valeurs peuvent être générées à l’aide de l’instruction SELECT INTO dans lequel un **rowversion** colonne se trouve dans la liste de sélection. Nous ne recommandons pas à l’aide de **rowversion** de cette manière.  
  
Un acceptant **rowversion** colonne est sémantiquement équivalente à un **Binary (8)** colonne. Un nullable **rowversion** colonne est sémantiquement équivalente à un **varbinary (8)** colonne.
  
Vous pouvez utiliser la **rowversion** colonne d’une ligne permet de déterminer rapidement si la ligne a eu une instruction update il exécuté depuis la dernière fois qu’il a été lu. Si une instruction update est exécuté sur la ligne, la valeur rowversion est mise à jour. Si aucune mise à jour sont des instructions n’exécuté sur la ligne, la valeur rowversion est le même que lorsqu’elle a été lue précédemment. Pour retourner la valeur actuelle rowversion pour une base de données, utilisez [@@DBTS](../../t-sql/functions/dbts-transact-sql.md).
  
Vous pouvez ajouter un **rowversion** sur une table pour aider à maintenir l’intégrité de la base de données lorsque plusieurs utilisateurs sont à jour les lignes en même temps. Vous pouvez souhaiter également savoir combien de lignes et quelles lignes ont été mises à jour sans réinterroger la table.
  
Par exemple, supposons que vous créez une table nommée `MyTest`. Vous insérez des données dans la table en exécutant la commande suivante [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions.
  
```sql
CREATE TABLE MyTest (myKey int PRIMARY KEY  
    ,myValue int, RV rowversion);  
GO   
INSERT INTO MyTest (myKey, myValue) VALUES (1, 0);  
GO   
INSERT INTO MyTest (myKey, myValue) VALUES (2, 0);  
GO  
```  
  
Vous pouvez utiliser ensuite les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] de l'exemple pour implémenter un contrôle d'accès concurrentiel optimiste sur la table `MyTest` pendant la mise à jour.
  
```sql
DECLARE @t TABLE (myKey int);  
UPDATE MyTest  
SET myValue = 2  
    OUTPUT inserted.myKey INTO @t(myKey)   
WHERE myKey = 1   
    AND RV = myValue;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  
`myValue`est la **rowversion** valeur de colonne pour la ligne qui indique la dernière fois que vous lisez la ligne. Cette valeur doit être remplacée par le texte réel **rowversion** valeur. Un exemple de réelles **rowversion** valeur 0x00000000000007d3.
  
Vous pouvez également mettre les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] de l'exemple dans une transaction. En interrogeant la variable `@t` dans l'étendue de la transaction, vous pouvez extraire la colonne `myKey` mise à jour de la table sans réinterroger la table `MyTes`.
  
Voici le même exemple à l’aide de la **timestamp** syntaxe :
  
```sql
CREATE TABLE MyTest2 (myKey int PRIMARY KEY  
    ,myValue int, TS timestamp);  
GO   
INSERT INTO MyTest2 (myKey, myValue) VALUES (1, 0);  
GO   
INSERT INTO MyTest2 (myKey, myValue) VALUES (2, 0);  
GO  
DECLARE @t TABLE (myKey int);  
UPDATE MyTest2  
SET myValue = 2  
    OUTPUT inserted.myKey INTO @t(myKey)   
WHERE myKey = 1   
    AND TS = myValue;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  
## <a name="see-also"></a>Voir aussi
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)  
[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION &#40; Transact-SQL &#41;](../../t-sql/functions/min-active-rowversion-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)
  
  

