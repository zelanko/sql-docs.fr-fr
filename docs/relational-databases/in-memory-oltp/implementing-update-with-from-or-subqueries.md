---
title: "Implémentation d’UPDATE avec FROM ou des sous-requêtes | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 138f5b0e-f8a4-400f-b581-8062aebc62b6
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c9f044bbde8edd542e3a2a1017a726b8d939654a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="implementing-update-with-from-or-subqueries"></a>Implémentation d’UPDATE avec FROM ou des sous-requêtes
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

Les modules T-SQL compilés en mode natif ne prennent pas en charge la clause FROM et ne prennent pas en charge les sous-requêtes dans les instructions UPDATE (elles sont prises en charge dans SELECT). Les instructions UPDATE avec la clause FROM sont généralement utilisées pour mettre à jour les informations contenues dans une table basée sur un paramètre table), ou pour mettre à jour les colonnes d’une table dans un déclencheur AFTER. 

Pour le scénario de mise à jour basée sur un paramètre table, consultez [Implémentation de la fonctionnalité MERGE dans une procédure stockée compilée en mode natif](../../relational-databases/in-memory-oltp/implementing-merge-functionality-in-a-natively-compiled-stored-procedure.md). 

L’exemple ci-dessous illustre une mise à jour effectuée dans un déclencheur. La colonne LastUpdated de la table est mise à jour à la date et à l’heure actuelles APRÈS les mises à jour. La solution de contournement utilise une variable de table avec une colonne d’identité, et une boucle WHILE pour itérer au sein des lignes dans la variable de table et effectuer des mises à jour.
  
Voici l’instruction T-SQL UPDATE d’origine :  
  
  
  
  
    UPDATE dbo.Table1  
        SET LastUpdated = SysDateTime()  
        FROM  
            dbo.Table1 t  
            JOIN Inserted i ON t.Id = i.Id;  
  
  
  

L’exemple de code T-SQL dans cette section illustre une solution de contournement qui fournit de bonnes performances. La solution de contournement est implémentée dans un déclencheur compilé en mode natif. Les principaux éléments à remarquer dans le code sont les suivants :  
  
- Le type nommé dbo.Type1, qui est un type de table optimisé en mémoire.  
- La boucle WHILE dans le déclencheur.  
  - La boucle extrait les lignes de Inserted une à la fois.  
  
  
  

    DROP TABLE IF EXISTS dbo.Table1;  
    go  
    DROP TYPE IF EXISTS dbo.Type1;  
    go  
    -----------------------------  
    <a name="---table-and-table-type"></a>-- Table et type de table
    -----------------------------
  
    CREATE TABLE dbo.Table1  
    (  
        Id           INT        NOT NULL  PRIMARY KEY NONCLUSTERED,  
        Column2      INT        NOT NULL,  
        LastUpdated  DATETIME2  NOT NULL  DEFAULT (SYSDATETIME())  
    )  
        WITH (MEMORY_OPTIMIZED = ON);  
    go  
  
  
    CREATE TYPE dbo.Type1 AS TABLE  
    (  
        Id       INT NOT  NULL,  
        
        RowID    INT NOT  NULL  IDENTITY,  
        INDEX ix_RowID HASH (RowID) WITH (BUCKET_COUNT=1024)
    )   
        WITH (MEMORY_OPTIMIZED = ON);  
    go  
    ----------------------------- 
    <a name="---trigger-that-contains-the-workaround-for-update-with-from"></a>-- déclencheur qui contient la solution de contournement pour UPDATE avec FROM 
    -----------------------------  
  
    CREATE TRIGGER dbo.tr_a_u_Table1  
        ON dbo.Table1  
        WITH NATIVE_COMPILATION, SCHEMABINDING  
        AFTER UPDATE  
    AS BEGIN ATOMIC WITH  
        (  
        TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
        LANGUAGE = N'us_english'  
        )  
        
      DECLARE @tabvar1 dbo.Type1;  
    
      INSERT @tabvar1 (Id)   
          SELECT Id FROM Inserted;  
    
      DECLARE  
          @i INT = 1,  @Id INT,  
          @max INT = SCOPE_IDENTITY();  
    
      --- Boucle comme solution de contournement pour simuler un curseur.
    --- Itérer les lignes de la variable de table optimisée  
      --- en mémoire et effectuer une mise à jour pour chaque ligne.  
    
      WHILE @i <= @max  
      BEGIN  
          SELECT @Id = Id  
              FROM @tabvar1  
              WHERE RowID = @i;  
    
          UPDATE dbo.Table1  
              SET LastUpdated = SysDateTime()  
              WHERE Id = @Id;  
    
          SET @i += 1;  
      END  
    END  
    go  
    -----------------------------  
    <a name="---test-to-verify-functionality"></a>-- Tester pour vérifier la fonctionnalité
    -----------------------------  
  
    SET NOCOUNT ON;  
  
    INSERT dbo.Table1 (Id, Column2)  
        VALUES (1,9), (2,9), (3,600);  
    
    SELECT N'BEFORE-Update' AS [BEFORE-Update], *  
        FROM dbo.Table1  
        ORDER BY Id;  
  
    WAITFOR DELAY '00:00:01';  

    UPDATE dbo.Table1  
        SET   Column2 += 1  
        WHERE Column2 <= 99;  
  
    SELECT N'AFTER--Update' AS [AFTER--Update], *  
        FROM dbo.Table1  
        ORDER BY Id;  
    go  
    -----------------------------  
  
    /**** Sortie réelle :  
  
    BEFORE-Update   Id   Column2   LastUpdated  
    BEFORE-Update   1       9      2016-04-20 21:18:42.8394659  
    BEFORE-Update   2       9      2016-04-20 21:18:42.8394659  
    BEFORE-Update   3     600      2016-04-20 21:18:42.8394659  
  
    AFTER--Update   Id   Column2   LastUpdated  
    AFTER--Update   1      10      2016-04-20 21:18:43.8529692  
    AFTER--Update   2      10      2016-04-20 21:18:43.8529692  
    AFTER--Update   3     600      2016-04-20 21:18:42.8394659  
    ****/  
  
  
  

