---
title: char et varchar (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- varchar
- varchar_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fixed-length data types [SQL Server]
- character data type
- char data type
- varchar(max) data type
- variable-length data types [SQL Server]
- varchar data type
ms.assetid: 282cd982-f4fb-4b22-b2df-9e8478f13f6a
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7c7bcb0e8ad7f8904703bd6c979b00aa30dd5348
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="char-and-varchar-transact-sql"></a>char et varchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Ces types de données sont de longueur fixe ou de longueur variable.  
  
## <a name="arguments"></a>Arguments  
**char** [(  *n*  )] à longueur fixe, les données de chaîne non-Unicode. *n*définit la longueur de chaîne et doit être une valeur comprise entre 1 et 8 000 caractères. La taille de stockage est  *n*  octets. Le synonyme ISO de **char** est **caractère**.
  
**varchar** [(  *n*   |  **max** )] longueur Variable, les données de chaîne non-Unicode. *n*définit la longueur de chaîne et peut être une valeur comprise entre 1 et 8 000 caractères. **max** indique que la taille de stockage maximale est de 2 ^ 31-1 octets (2 Go). La taille mémoire est la longueur réelle des données entrées, plus deux octets. Les synonymes ISO de **varchar** sont **charvarying** ou **charactervarying**.
  
## <a name="remarks"></a>Notes  
Lorsque  *n*  n’est pas spécifié dans une définition de données ou d’une instruction de déclaration de variable, la longueur par défaut est 1. Lorsque  *n*  n’est pas spécifié lorsque vous utilisez les fonctions CAST et CONVERT, la longueur par défaut est 30.
  
Objets qui utilisent **char** ou **varchar** reçoivent le classement par défaut de la base de données, sauf si un classement spécifique est affecté à l’aide de la clause COLLATE. Le classement contrôle la page de codes utilisée pour stocker les données de caractères.
  
Si vous avez des sites qui prennent en charge plusieurs langues, envisagez d’utiliser Unicode **nchar** ou **nvarchar** des types de données afin de réduire les problèmes de conversion de caractères. Si vous utilisez **char** ou **varchar**, nous vous recommandons ce qui suit :
- Utilisez **char** lorsque les tailles des entrées de données de colonne sont cohérentes.  
- Utilisez **varchar** lorsque les tailles des entrées de données de colonne varient considérablement.  
- Utilisez **varchar (max)** lorsque les tailles des entrées de données de colonne varient considérablement, et la taille peut dépasser 8 000 octets.  
  
Si SET ANSI_PADDING est désactivé lorsque CREATE TABLE ou ALTER TABLE est exécutée, un **char** colonne définie comme NULL est considérée comme **varchar**.
  
Lorsque la page de codes du classement utilise des caractères codés sur deux octets, la taille de stockage est toujours  *n*  octets. En fonction de la chaîne de caractères, la taille de stockage  *n*  octets peut être inférieure à  *n*  caractères.

> [!WARNING]
> Chaque varchar (max) non null ou une colonne de nvarchar (max) requiert 24 octets d’allocation fixe supplémentaire calculée par rapport à la limite de 8 060 octets par ligne pendant une opération de tri. Cela peut créer une limite implicite au nombre de colonnes nvarchar (max) qui peuvent être créés dans une table ou de varchar (max) non null.  
Aucune erreur spéciale n'est fournie quand la table est créée (mis à part l’avertissement habituel indiquant que la taille maximale de ligne dépasse la taille maximale autorisée de 8 060 octets) ou quand les données sont insérées. Cette grande taille de ligne peut provoquer des erreurs (comme l’erreur 512) au cours des opérations normales, telles que la mise à jour de la clé d’index cluster ou le tri de l’intégralité des colonnes, que les utilisateurs ne peuvent pas anticiper tant qu’elles n’ont pas été effectuées.
  
##  <a name="_character"></a>Conversion de données de type caractère  
Lorsque des expressions de caractères sont converties en type caractère de taille différente, les valeurs trop longues pour le nouveau type de données sont tronquées. Le **uniqueidentifier** type est considéré comme un type de caractère dans le cadre de la conversion à partir d’une expression de caractères et est donc soumis aux règles de troncation pour la conversion en un type de caractère. Consultez la section Exemples qui suit.
  
Lorsqu’une expression de caractères est convertie en une expression de caractères d’un autre type de données ou la taille, par exemple à partir de **char (5)** à **varchar (5)**, ou **char (20)** à **char (15)**, le classement de la valeur d’entrée est affecté à la valeur convertie. Si une expression de type non caractère est convertie en un type de données caractère, le classement par défaut de la base de données active est affecté à la valeur convertie. Dans les deux cas, vous pouvez affecter un classement spécifique à l’aide de la [COLLATE](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9) clause.
  
> [!NOTE]  
>  Traductions de page de codes sont prises en charge pour **char** et **varchar** des types de données, mais pas pour **texte** type de données. De manière identique aux versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la perte de données lors de l'interprétation d'une page de codes n'est pas mentionnée.  
  
Les expressions qui sont en cours de conversion à un nombre approximatif de caractères **numérique** type de données peut inclure une notation exponentielle facultative (un e minuscule ou un E majuscule suivi d’un signe facultatif plus (+) ou moins (-) signe, puis un nombre).
  
Les expressions qui sont en cours de conversion à un texte exact de caractères **numérique** type de données doit se composer de chiffres, une virgule décimale et d’un signe plus (+) ou moins (-). Les espaces à gauche sont ignorés. Les séparateurs virgule (séparateurs de milliers en notation anglaise comme dans 123,456.00) ne sont pas autorisés dans la chaîne.
  
Expressions de caractères converties à **money** ou **smallmoney** des types de données peuvent également inclure un séparateur décimal facultatif et le signe dollar ($). Les séparateurs virgule (séparateurs de milliers en notation anglaise comme dans $123,456.00) sont autorisés.
  
## <a name="examples"></a>Exemples  
  
### <a name="a-showing-the-default-value-of-n-when-used-in-variable-declaration"></a>A. Affichage de la valeur par défaut de n utilisée dans une déclaration de variable.  
L’exemple suivant montre la valeur par défaut  *n*  est 1 pour le `char` et `varchar` les types de données lorsqu’ils sont utilisés dans la déclaration de variable.
  
```sql
DECLARE @myVariable AS varchar = 'abc';  
DECLARE @myNextVariable AS char = 'abc';  
--The following returns 1  
SELECT DATALENGTH(@myVariable), DATALENGTH(@myNextVariable);  
GO  
```  
  
### <a name="b-showing-the-default-value-of-n-when-varchar-is-used-with-cast-and-convert"></a>B. Affichage de la valeur par défaut de n lorsque varchar est utilisé dans CAST et CONVERT.  
L’exemple suivant montre que la valeur par défaut  *n*  est 30 lorsque les `char` ou `varchar` les types de données sont utilisés avec la `CAST` et `CONVERT` fonctions.
  
```sql
DECLARE @myVariable AS varchar(40);  
SET @myVariable = 'This string is longer than thirty characters';  
SELECT CAST(@myVariable AS varchar);  
SELECT DATALENGTH(CAST(@myVariable AS varchar)) AS 'VarcharDefaultLength';  
SELECT CONVERT(char, @myVariable);  
SELECT DATALENGTH(CONVERT(char, @myVariable)) AS 'VarcharDefaultLength';  
```  
  
### <a name="c-converting-data-for-display-purposes"></a>C. Conversion de données à des fins d'affichage  
L'exemple suivant convertit deux colonnes en types caractères et applique un style qui applique un format spécifique aux données affichées. A **money** type est converti en données de type caractère et le style 1 est appliqué, qui affiche les valeurs par des virgules de tous les trois chiffres à gauche du séparateur décimal et deux chiffres à droite de la virgule décimale. A **datetime** type est converti en données de type caractère et le style 3 est appliqué, qui affiche les données dans le format mm/jj/aa. Dans la clause WHERE, une **money** type est converti en un type de caractère pour effectuer une opération de comparaison de chaînes.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT  BusinessEntityID,   
   SalesYTD,   
   CONVERT (varchar(12),SalesYTD,1) AS MoneyDisplayStyle1,   
   GETDATE() AS CurrentDate,   
   CONVERT(varchar(12), GETDATE(), 3) AS DateDisplayStyle3  
FROM Sales.SalesPerson  
WHERE CAST(SalesYTD AS varchar(20) ) LIKE '1%';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
BusinessEntityID SalesYTD              DisplayFormat CurrentDate             DisplayDateFormat  
---------------- --------------------- ------------- ----------------------- -----------------  
278              1453719.4653          1,453,719.47  2011-05-07 14:29:01.193 07/05/11  
280              1352577.1325          1,352,577.13  2011-05-07 14:29:01.193 07/05/11  
283              1573012.9383          1,573,012.94  2011-05-07 14:29:01.193 07/05/11  
284              1576562.1966          1,576,562.20  2011-05-07 14:29:01.193 07/05/11  
285              172524.4512           172,524.45    2011-05-07 14:29:01.193 07/05/11  
286              1421810.9242          1,421,810.92  2011-05-07 14:29:01.193 07/05/11  
288              1827066.7118          1,827,066.71  2011-05-07 14:29:01.193 07/05/11  
```  
  
### <a name="d-converting-uniqueidentifer-data"></a>D. Conversion de données Uniqueidentifer  
L'exemple suivant convertit une valeur `uniqueidentifier` en type de données `char`.
  
```sql
DECLARE @myid uniqueidentifier = NEWID();  
SELECT CONVERT(char(255), @myid) AS 'char';  
```  
  
L'exemple suivant illustre la troncation des données lorsque la valeur est trop longue pour le type de données vers lequel la conversion est effectuée. Étant donné que la **uniqueidentifier** type est limité à 36 caractères, les caractères qui dépassent cette longueur sont tronqués.
  
```sql
DECLARE @ID nvarchar(max) = N'0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong';  
SELECT @ID, CONVERT(uniqueidentifier, @ID) AS TruncatedValue;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
String                                       TruncatedValue  
-------------------------------------------- ------------------------------------  
0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong    0E984725-C51C-4BF4-9960-E1C80E27ABA0  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi
[nchar et nvarchar &#40;Transact-SQL&#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[COLLATE &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[Conversion de Type de données &#40; moteur de base de données &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Estimer la taille d’une base de données](../../relational-databases/databases/estimate-the-size-of-a-database.md)
  
  

