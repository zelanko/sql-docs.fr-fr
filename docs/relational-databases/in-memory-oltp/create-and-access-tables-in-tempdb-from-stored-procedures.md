---
title: "Cr&#233;ation de tables et acc&#232;s dans TempDB &#224; partir de proc&#233;dures stock&#233;es compil&#233;es en mode natif | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12be8011-b76c-45c1-8f55-7f46e0e374e9
caps.latest.revision: 9
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 9
---
# Cr&#233;ation de tables et acc&#232;s dans TempDB &#224; partir de proc&#233;dures stock&#233;es compil&#233;es en mode natif
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  La création et l'accès aux tables dans TempDB à partir de procédures stockées compilées en mode natif ne sont pas pris en charge. Au lieu de cela, utilisez des tables optimisées en mémoire avec DURABILITY=SCHEMA_ONLY ou utilisez des types de table et des variables de table. 

Pour plus d’informations sur l’optimisation de la mémoire de la table temporaire et sur les scénarios de variables de table, consultez [Table temporaire et variable de table plus rapides à l’aide de l’optimisation de la mémoire](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md).
  
  L’exemple suivant montre comment l’utilisation d’une table temporaire à trois colonnes (ID, ID produit et Quantité) peut être remplacée par l’utilisation d’une variable de table **@OrderQuantityByProduct** de type **dbo.OrderQuantityByProduct** :  
  
```tsql  
CREATE TYPE dbo.OrderQuantityByProduct   
  AS TABLE   
   (id INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=100000),   
    ProductID INT NOT NULL,   
    Quantity INT NOT NULL) WITH (MEMORY_OPTIMIZED=ON)  
GO  
CREATE PROCEDURE dbo.usp_OrderQuantityByProduct   
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = N'ENGLISH'  
)  
  -- declare table variables for the list of orders   
  DECLARE @OrderQuantityByProduct dbo.OrderQuantityByProduct  
  
  -- populate input  
  INSERT @OrderQuantityByProduct SELECT ProductID, Quantity FROM dbo.[Order Details]  
  end  
```  
  
## Voir aussi  
 [Problèmes de migration pour les procédures stockées compilées en mode natif](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [Les constructions Transact-SQL ne sont pas prises en charge par l'OLTP en mémoire](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  