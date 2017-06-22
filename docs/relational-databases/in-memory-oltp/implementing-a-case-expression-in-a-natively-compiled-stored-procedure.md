---
title: "Implémentation d’une expression CASE dans une procédure stockée compilée en mode natif | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 04/24/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f82db01-da7e-4a7d-8bc0-48b245e6f768
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 1829f2a3b1d053173145df421ce7d8d35a0e29e3
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="implementing-a-case-expression-in-a-natively-compiled-stored-procedure"></a>Implémentation d’une expression CASE dans une procédure stockée compilée en mode natif
[!INCLUDE[tsql-appliesto-ssvnxt-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

  Les expressions CASE sont pris en charge dans les procédures stockées compilées en mode natif. L’exemple suivant montre une façon d’utiliser l’expression CASE dans une requête. La solution de contournement décrite pour les expressions CASE dans les modules compilés en mode natif s’avère n’est plus nécessaire.

``` 
-- Query using a CASE expression in a natively compiled stored procedure.
CREATE PROCEDURE dbo.usp_SOHOnlineOrderResult  
   WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
   AS BEGIN ATOMIC WITH  (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE=N'us_english')  
   SELECT   
      SalesOrderID,   
      CASE (OnlineOrderFlag)   
      WHEN 1 THEN N'Order placed online by customer'  
      ELSE N'Order placed by sales person'  
      END  
   FROM Sales.SalesOrderHeader_inmem
END  
GO  
  
EXEC dbo.usp_SOHOnlineOrderResult  
GO  
```  


[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Les expressions CASE *ne sont pas* prises en charge dans les procédures stockées compilées en mode natif. L’exemple suivant illustre une méthode permettant d’implémenter les fonctionnalités d’une expression CASE dans une procédure stockée compilée en mode natif.  
  
 Les exemples de code utilisent une variable de table pour construire un jeu de résultats unique. Cela est uniquement adapté en cas de traitement d’un nombre limité de lignes, puisque cela implique la création d’une copie supplémentaire des lignes de données.  
  
 Vous devez tester les performances de cette solution de contournement.  
  
```  
-- original query  
SELECT   
   SalesOrderID,   
   CASE (OnlineOrderFlag)   
   WHEN 1 THEN N'Order placed online by customer'  
   ELSE N'Order placed by sales person'  
   END  
FROM Sales.SalesOrderHeader_inmem  
  
--  workaround for CASE in natively compiled stored procedures  
--  use a table for the single resultset  
CREATE TYPE dbo.SOHOnlineOrderResult AS TABLE  
(  
   SalesOrderID uniqueidentifier not null index ix_SalesOrderID,  
     OrderFlag nvarchar(100) not null  
) with (memory_optimized=on)  
go  
  
-- natively compiled stored procedure that includes the query  
CREATE PROCEDURE dbo.usp_SOHOnlineOrderResult  
   WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
   AS BEGIN ATOMIC WITH  
      (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE=N'us_english')  
  
   -- table variable for creating the single resultset  
   DECLARE @result dbo.SOHOnlineOrderResult  
  
   -- CASE OnlineOrderFlag=1  
   INSERT @result   
   SELECT SalesOrderID, N'Order placed online by customer'  
      FROM Sales.SalesOrderHeader_inmem  
      WHERE OnlineOrderFlag=1  
  
   -- ELSE  
   INSERT @result   
   SELECT SalesOrderID, N'Order placed by sales person'  
      FROM Sales.SalesOrderHeader_inmem  
      WHERE OnlineOrderFlag!=1  
  
   -- return single resultset  
   SELECT SalesOrderID, OrderFlag FROM @result  
END  
GO  
  
EXEC dbo.usp_SOHOnlineOrderResult  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de migration pour les procédures stockées compilées en mode natif](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [Les constructions Transact-SQL ne sont pas prises en charge par l’OLTP en mémoire](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  

