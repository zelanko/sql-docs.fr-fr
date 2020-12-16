---
description: Définir ou changer le classement des colonnes
title: Définir ou changer le classement des colonnes | Microsoft Docs
ms.custom: ''
ms.date: 12/05/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tempdb database [SQL Server], collations
- collations [SQL Server], column
ms.assetid: d7a9638b-717c-4680-9b98-8849081e08be
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3f408175a59484aa162c0db654ebf4b1d5656901
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97460582"
---
# <a name="set-or-change-the-column-collation"></a>Définir ou changer le classement des colonnes
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Vous pouvez remplacer le classement de la base de données pour les données **char**, **varchar**, **text**, **nchar**, **nvarchar** et **ntext** en spécifiant un classement différent pour une colonne spécifique d’une table et en utilisant l’un des éléments suivants :  
  
-   Clause COLLATE de [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) et [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md), illustrée dans les exemples ci-dessous. 

    -   **Conversion sur place.** Considérez l’une des tables existantes définies ci-dessous :

        ```sql
        -- NVARCHAR column is encoded in UTF-16 because a supplementary character enabled collation is used
        CREATE TABLE dbo.MyTable (CharCol NVARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC);

        -- VARCHAR column is encoded the Latin code page and therefore is not Unicode capable
        CREATE TABLE dbo.MyTable (CharCol VARCHAR(50) COLLATE Latin1_General_100_CI_AI);
        ```

        Pour convertir la colonne sur place afin d’utiliser UTF-8, exécutez une instruction `ALTER COLUMN` qui définit le type de données nécessaire et un classement UTF-8 :

        ```sql 
        ALTER TABLE dbo.MyTable 
        ALTER COLUMN CharCol VARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC_UTF8
        ```

        Cette méthode est facile à implémenter, mais elle représente potentiellement une opération bloquante qui peut devenir un problème pour les tables volumineuses et les applications occupées.

    -   **Copier et remplacer.** Considérez l’une des tables existantes définies ci-dessous :

        ```sql
        -- NVARCHAR column is encoded in UTF-16 because a supplementary character enabled collation is used
        CREATE TABLE dbo.MyTable (CharCol NVARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC);
        GO

        -- VARCHAR column is encoded using the Latin code page and therefore is not Unicode capable
        CREATE TABLE dbo.MyTable (CharCol VARCHAR(50) COLLATE Latin1_General_100_CI_AI);
        GO
        ```

        Pour convertir la colonne afin d’utiliser le format UTF-8, copiez les données dans une nouvelle table où la colonne cible correspond déjà au type de données nécessaire avec un classement UTF-8, puis remplacez l’ancienne table :

        ```sql
        CREATE TABLE dbo.MyTableNew (CharCol VARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC_UTF8);
        GO
        INSERT INTO dbo.MyTableNew 
        SELECT * FROM dbo.MyTable;
        GO
        DROP TABLE dbo.MyTable;
        GO
        EXEC sp_rename 'dbo.MyTableNew', 'dbo.MyTable';
        GO
        ```

        Cette méthode est beaucoup plus rapide que la conversion sur place. Toutefois, la gestion de schémas complexes avec de nombreuses dépendances (clés étrangères, clés primaires, déclencheurs, contraintes par défaut) et la synchronisation de la fin de la table (si la base de données est en cours d’utilisation) nécessite davantage de planification.
        
    Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md).
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, consultez [Modifier des colonnes (moteur de base de données)](../../relational-databases/tables/modify-columns-database-engine.md#SSMSProcedure).  
  
-   Utilisation de la propriété **Column.Collation** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).  
  
 Vous ne pouvez pas modifier le classement d'une colonne actuellement référencée par l'un des éléments suivants :  
  
-   une colonne calculée ;  
-   un index ;  
-   des statistiques de distribution, générées automatiquement ou par l’instruction `CREATE STATISTICS`  
-   une contrainte CHECK ;  
-   une contrainte FOREIGN KEY.  
  
 Quand vous utilisez **tempdb**, la clause [COLLATE](~/t-sql/statements/collations.md) contient une option *database_default* pour spécifier qu’une colonne de table temporaire utilise, pour la connexion, le classement par défaut de la base de données utilisateur active à la place du classement de **tempdb**.  
  
## <a name="collations-and-text-columns"></a>Classements et colonnes text  
 Vous pouvez insérer ou mettre à jour les valeurs d’une colonne **text** dont le classement est différent de la page de codes du classement par défaut de la base de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertit implicitement les valeurs en fonction du classement de la colonne.  
  
## <a name="collations-and-tempdb"></a>Classements et tempdb  
 La base de données **tempdb** est créée à chaque démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et a le même classement par défaut que la base de données **model** . Il est en général identique au classement par défaut de l'instance. Si vous créez une base de données utilisateur et spécifiez un classement par défaut différent de **model**, la base de données utilisateur a un classement par défaut différent de **tempdb**. Toutes les procédures stockées ou tables temporaires sont créées et stockées dans **tempdb**. En d'autres termes, toutes les colonnes implicites des tables temporaires et toutes les constantes, variables et paramètres modifiables par défaut des procédures stockées temporaires ont d'autres classements que les objets comparables créés dans les tables et procédures stockées permanentes.  
  
 Ceci pourrait provoquer des problèmes de non-correspondance de classement entre les bases de données définies par l'utilisateur et les objets de base de données système. Par exemple, une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise le classement Latin1_General_CS_AS et vous exécutez les instructions suivantes :  
  
```sql  
CREATE DATABASE TestDB COLLATE Estonian_CS_AS;  
USE TestDB;  
CREATE TABLE TestPermTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
```  
  
 Dans ce système, la base de données **tempdb** utilise le classement Latin1_General_CS_AS avec la page de codes 1252, et `TestDB` et `TestPermTab.Col1` utilisent le classement `Estonian_CS_AS` avec la page de codes 1257. Par exemple :  
  
```sql  
USE TestDB;  
GO  
-- Create a temporary table with the same column declarations  
-- as TestPermTab  
CREATE TABLE #TestTempTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
INSERT INTO #TestTempTab  
         SELECT * FROM TestPermTab;  
GO  
```  
  
 Dans l’exemple précédent, la base de données **tempdb** utilise le classement Latin1_General_CS_AS, et `TestDB` et `TestTab.Col1` utilisent le classement `Estonian_CS_AS` . Par exemple :  
  
```sql  
SELECT * FROM TestPermTab AS a INNER JOIN #TestTempTab on a.Col1 = #TestTempTab.Col1;  
```  
  
 Comme **tempdb** utilise le classement par défaut du serveur et que `TestPermTab.Col1` utilise un autre classement, SQL Server affiche l’erreur suivante : impossible de résoudre le conflit de classement entre « Latin1_General_100_CI_AS_KS_WS » et « Chinese_Simplified_Pinyin_100_CI_AS » dans l’opération égal à.  
  
 Pour éviter l'erreur, vous pouvez utiliser une des solutions suivantes :  
  
-   Spécifiez que la colonne de table temporaire utilise le classement par défaut de la base de données utilisateur à la place de **tempdb**. Cela permet à la table temporaire de fonctionner avec des tables formatées de la même manière dans différentes bases de données, si votre système l'exige.  
  
    ```sql  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE database_default  
       );  
    ```  
  
-   Spécifiez le classement approprié pour la colonne `#TestTempTab` :  
  
    ```sql  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE Estonian_CS_AS  
       );  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Définir ou modifier le classement du serveur](../../relational-databases/collations/set-or-change-the-server-collation.md)   
 [Définir ou modifier le classement de la base de données](../../relational-databases/collations/set-or-change-the-database-collation.md)   
 [Prise en charge d'Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  
