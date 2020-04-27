---
title: Création et accès aux tables dans TempDB à partir de procédures stockées compilées en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 12be8011-b76c-45c1-8f55-7f46e0e374e9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 188f47efe73edde0ed2e534bd19787c8546e7c18
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62990373"
---
# <a name="creating-and-accessing-tables-in-tempdb-from-natively-compiled-stored-procedures"></a>Création de tables et accès dans TempDB à partir de procédures stockées compilées en mode natif
  La création et l'accès aux tables dans TempDB à partir de procédures stockées compilées en mode natif ne sont pas pris en charge. Utilisez plutôt des types de table et des variables de table. Par exemple :  
  
```sql  
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
    LANGUAGE = 'english'  
)  
  -- declare table variables for the list of orders   
  DECLARE @Input dbo.OrderQuantityByProduct  
  
  -- populate input  
  INSERT @Input SELECT ProductID, Quantity FROM dbo.[Order Details]  
  end  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de migration pour les procédures stockées compilées en mode natif](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Constructions Transact-SQL non prises en charge par l’OLTP en mémoire](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
