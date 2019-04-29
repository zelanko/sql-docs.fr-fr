---
title: Définir ou changer le classement des colonnes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tempdb database [SQL Server], collations
- collations [SQL Server], column
ms.assetid: d7a9638b-717c-4680-9b98-8849081e08be
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4a16794bb2cd61829058d9fac7be11438f563d44
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918970"
---
# <a name="set-or-change-the-column-collation"></a>Définir ou changer le classement des colonnes
  Vous pouvez remplacer le classement de la base de données pour les données `char`, `varchar`, `text`, `nchar`, `nvarchar` et `ntext` en spécifiant un classement différent pour une colonne spécifique d'une table et en utilisant l'un des éléments suivants :  
  
-   Clause COLLATE de [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) et [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql). Exemple :  
  
    ```  
    CREATE TABLE dbo.MyTable  
      (PrimaryKey   int PRIMARY KEY,  
       CharCol      varchar(10) COLLATE French_CI_AS NOT NULL  
      );  
    GO  
    ALTER TABLE dbo.MyTable ALTER COLUMN CharCol  
                varchar(10)COLLATE Latin1_General_CI_AS NOT NULL;  
    GO  
    ```  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](collation-and-unicode-support.md).  
  
-   À l’aide de la `Column.Collation` propriété dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).  
  
 Vous ne pouvez pas modifier le classement d'une colonne actuellement référencée par l'un des éléments suivants :  
  
-   une colonne calculée ;  
  
-   un index ;  
  
-   des statistiques de distribution, générées automatiquement ou à l'aide de l'instruction CREATE STATISTICS ;  
  
-   une contrainte CHECK ;  
  
-   une contrainte FOREIGN KEY.  
  
 Quand vous utilisez **tempdb**, la clause [COLLATE](/sql/t-sql/statements/collations) contient une option *database_default* pour spécifier qu’une colonne de table temporaire utilise, pour la connexion, le classement par défaut de la base de données utilisateur active à la place du classement de **tempdb**.  
  
## <a name="collations-and-text-columns"></a>Classements et colonnes text  
 Vous pouvez insérer ou mettre à jour les valeurs d'une colonne `text` dont le classement est différent de la page de codes du classement par défaut de la base de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertit implicitement les valeurs en fonction du classement de la colonne.  
  
## <a name="collations-and-tempdb"></a>Classements et tempdb  
 La base de données **tempdb** est créée à chaque démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et a le même classement par défaut que la base de données **model** . Il est en général identique au classement par défaut de l'instance. Si vous créez une base de données utilisateur et spécifiez un classement par défaut différent de **model**, la base de données utilisateur a un classement par défaut différent de **tempdb**. Toutes les procédures stockées ou tables temporaires sont créées et stockées dans **tempdb**. En d'autres termes, toutes les colonnes implicites des tables temporaires et toutes les constantes, variables et paramètres modifiables par défaut des procédures stockées temporaires ont d'autres classements que les objets comparables créés dans les tables et procédures stockées permanentes.  
  
 Ceci pourrait provoquer des problèmes de non-correspondance de classement entre les bases de données définies par l'utilisateur et les objets de base de données système. Par exemple, une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise le classement Latin1_General_CS_AS et vous exécutez les instructions suivantes :  
  
```  
CREATE DATABASE TestDB COLLATE Estonian_CS_AS;  
USE TestDB;  
CREATE TABLE TestPermTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
```  
  
 Dans ce système, la base de données **tempdb** utilise le classement Latin1_General_CS_AS avec la page de codes 1252, et `TestDB` et `TestPermTab.Col1` utilisent le classement `Estonian_CS_AS` avec la page de codes 1257. Exemple :  
  
```  
USE TestDB;  
GO  
-- Create a temporary table with the same column declarations  
-- as TestPermTab  
CREATE TABLE #TestTempTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
INSERT INTO #TestTempTab  
         SELECT * FROM TestPermTab;  
GO  
```  
  
 Dans l’exemple précédent, la base de données **tempdb** utilise le classement Latin1_General_CS_AS, et `TestDB` et `TestTab.Col1` utilisent le classement `Estonian_CS_AS` . Exemple :  
  
```  
SELECT * FROM TestPermTab AS a INNER JOIN #TestTempTab on a.Col1 = #TestTempTab.Col1;  
```  
  
 Étant donné que **tempdb** utilise le classement du serveur par défaut et `TestPermTab.Col1` utilise un autre classement, SQL Server affiche l’erreur : « Impossible de résoudre un conflit de classement entre « Latin1_General_CI_AS_KS_WS » et « Chinese_simplified_pinyin_100_ci_as » dans égal à l’opération ».  
  
 Pour éviter l'erreur, vous pouvez utiliser une des solutions suivantes :  
  
-   Spécifiez que la colonne de table temporaire utilise le classement par défaut de la base de données utilisateur à la place de **tempdb**. Cela permet à la table temporaire de fonctionner avec des tables formatées de la même manière dans différentes bases de données, si votre système l'exige.  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE database_default  
       );  
    ```  
  
-   Spécifiez le classement approprié pour la colonne `#TestTempTab` :  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE Estonian_CS_AS  
       );  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Définir ou modifier le classement du serveur](set-or-change-the-server-collation.md)   
 [Définir ou modifier le classement de la base de données](set-or-change-the-database-collation.md)   
 [Prise en charge d’Unicode et du classement](collation-and-unicode-support.md)  
  
  
