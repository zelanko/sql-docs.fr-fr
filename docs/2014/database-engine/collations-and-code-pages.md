---
title: Classements et Pages de codes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c626dcac-0474-432d-acc0-cfa643345372
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1969a3e30b31a21c380559a3e8898f87eb8848b1
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536531"
---
# <a name="collations-and-code-pages"></a>Classements et pages de codes
  [!INCLUDE[hek_2](../includes/hek-2-md.md)] est limité au niveau des pages de codes prises en charge pour les colonnes (var)char dans les tables mémoire optimisées et les classements pris en charge utilisés dans des index et des procédures stockées compilées en mode natif.  
  
 La page de codes d'une valeur (var)char détermine le mappage entre les caractères et la représentation en octets stockée dans la table. Par exemple, dans la page de codes Windows Latin 1 (1252 ; valeur par défaut de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ), le caractère « a » correspond à l'octet 0x61.  
  
 La page de codes d'une valeur (var)char est déterminée par le classement associé à la valeur. Par exemple, le classement SQL_Latin1_General_CP1_CI_AS est associé à la page de codes 1252.  
  
 Le classement d'une valeur est soit hérité du classement de la base de données, soit spécifié explicitement à l'aide du mot clé COLLATE. Le classement de la base de données ne peut pas être modifié si la base de données contient des tables mémoire optimisées ou des procédures stockées compilées en mode natif. L'exemple suivant définit le classement de la base de données et crée une table, qui comporte une colonne avec un classement différent. La base de données utilise un classement non sensible à la casse latine.  
  
 Les index peuvent être créés sur des colonnes de chaîne s'ils utilisent un classement BIN2. La variable LastName utilise le classement BIN2. FirstName utilise la valeur par défaut de la base de données, qui est CI_AS (non sensible à la casse, respect des accents).  
  
> [!IMPORTANT]  
>  Vous ne pouvez pas utiliser « order by » ou « group by » sur les colonnes de chaîne d'index qui n'utilisent pas le classement BIN2.  
  
```sql  
CREATE DATABASE IMOLTP  
  
ALTER DATABASE IMOLTP ADD FILEGROUP IMOLTP_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE IMOLTP ADD FILE( NAME = 'IMOLTP_mod' , FILENAME = 'c:\data\IMOLTP_mod') TO FILEGROUP IMOLTP_mod;  
--GO  
  
--  set the database collations  
ALTER DATABASE IMOLTP COLLATE Latin1_General_100_CI_AS  
GO  
  
--  
USE IMOLTP   
GO  
  
-- create a table with collation  
CREATE TABLE Employees (  
  EmployeeID int NOT NULL ,   
  LastName nvarchar(20) COLLATE Latin1_General_100_BIN2 NOT NULL INDEX IX_LastName NONCLUSTERED,   
  FirstName nvarchar(10) NOT NULL ,  
  CONSTRAINT PK_Employees PRIMARY KEY NONCLUSTERED HASH(EmployeeID)  WITH (BUCKET_COUNT=1024)  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY=SCHEMA_AND_DATA)  
GO  
```  
  
 Les limitations suivantes s'appliquent aux tables mémoire optimisées et aux procédures stockées compilées en mode natif.  
  
-   Les colonnes (var)char dans les tables mémoire optimisées doivent utiliser le classement de la page de codes 1252. Cette restriction ne concerne pas les colonnes n(var)char. Le code suivant récupère tous les classements 1252 :  
  
    ```sql  
    -- all supported collations for (var)char columns in memory-optimized tables  
    select * from sys.fn_helpcollations()  
    where collationproperty(name, 'codepage') = 1252;  
    ```  
  
     Si vous devez stocker des caractères non-latins, utilisez les colonnes n(var)char.  
  
-   Les index sur des colonnes (n)(var)char peuvent être spécifiés avec les classements BIN2 (voir le premier exemple). La requête suivante récupère tous les classements BIN2 pris en charge :  
  
    ```sql  
    -- all supported collations for indexes on memory-optimized tables and   
    -- comparison/sorting in natively compiled stored procedures  
    select * from sys.fn_helpcollations() where name like '%BIN2'  
    ```  
  
     Si vous accédez à la table par le [!INCLUDE[tsql](../includes/tsql-md.md)] interprété, vous pouvez utiliser le mot clé `COLLATE` pour modifier le classement avec des expressions ou des opérations de tri. Consultez le dernier exemple pour obtenir un modèle.  
  
-   Les procédures stockées compilées en mode natif ne peuvent pas utiliser des paramètres, des variables locales ou des constantes de chaîne de type (var)char si le classement de la base de données n'est pas un classement de page de codes 1252.  
  
-   Toutes les expressions et les opérations de tri à l'intérieur des procédures stockées compilées en mode natif doivent utiliser les classements BIN2. La conséquence est que toutes les comparaisons et les opérations de tri sont basées sur les points de code Unicode des caractères (représentations binaires). Par exemple, tous les tris respectent la casse (« Z » vient avant « a »). Si nécessaire, utilisez le [!INCLUDE[tsql](../includes/tsql-md.md)] interprété pour le tri et la comparaison insensibles à la casse.  
  
-   La troncation des données UTF-16 n'est pas prise en charge dans les procédures stockées compilées en mode natif. Cela signifie que char n (var) (*n*) valeurs ne peut pas être convertis en type n (var) char (*je*), si *je* < *n*, si le classement possède la propriété _SC. Par exemple, ce qui suit n'est pas pris en charge :  
  
    ```sql  
    -- column definition using an _SC collation  
     c2 nvarchar(200) collate Latin1_General_100_CS_AS_SC not null   
    -- assignment to a smaller variable, requiring truncation  
     declare @c2 nvarchar(100) = '';  
     select @c2 = c2  
    ```  
  
     Les fonctions de manipulation de chaîne comme LEN, SUBSTRING, LTRIM, et RTRIM avec des données UTF-16 ne sont pas prises en charge à l'intérieur des procédures stockées compilées en mode natif. Vous ne pouvez pas utiliser les fonctions de manipulation de chaîne pour les valeurs n(var)char qui ont un classement an _SC.  
  
     Déclarez les variables avec des types suffisamment grands pour éviter la troncation.  
  
 L'exemple suivant indique quelques-unes des conséquences et les solutions de contournement concernant les limitations de classement dans OLTP en mémoire. L'exemple utilise la table Employees spécifiée ci-dessus. Cet exemple répertorie tous les employés. Notez que pour LastName, en raison du classement binaire, les noms en majuscules sont triés en minuscules. Par conséquent, « Thomas » précède « nolan » car les caractères en majuscules ont des points de code inférieurs. FirstName a un classement non sensible à la casse. Par conséquent, il est préférable de trier par lettre de l'alphabet, et non par point de code des caractères.  
  
```sql  
-- insert a number of values  
INSERT Employees VALUES (1,'thomas', 'john')  
INSERT Employees VALUES (2,'Thomas', 'rupert')  
INSERT Employees VALUES (3,'Thomas', 'Jack')  
INSERT Employees VALUES (4,'Thomas', 'annie')  
INSERT Employees VALUES (5,'nolan', 'John')  
GO  
  
-- ===========  
SELECT EmployeeID, LastName, FirstName FROM Employees  
ORDER BY LastName, FirstName  
GO  
  
-- ===========  
-- specify collation: sorting uses case-insensitive collation, thus 'nolan' comes before 'Thomas'  
SELECT * FROM Employees  
ORDER BY LastName COLLATE Latin1_General_100_CI_AS, FirstName  
GO  
  
-- ===========  
-- retrieve employee by Name  
-- must use BIN2 collation for comparison in natively compiled stored procedures  
CREATE PROCEDURE usp_EmployeeByName @LastName nvarchar(20), @FirstName nvarchar(10)  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
  LANGUAGE = N'us_english'  
)  
  SELECT EmployeeID, LastName, FirstName FROM dbo.Employees  
  WHERE   
    LastName = @LastName AND  
    FirstName COLLATE Latin1_General_100_BIN2 = @FirstName  
  
END  
GO  
  
-- this does not return any rows, as EmployeeID 1 has first name 'john', which is not equal to 'John' in a binary collation  
EXEC usp_EmployeeByName 'thomas', 'John'  
  
-- this retrieves EmployeeID 1  
EXEC usp_EmployeeByName 'thomas', 'john'  
```  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
