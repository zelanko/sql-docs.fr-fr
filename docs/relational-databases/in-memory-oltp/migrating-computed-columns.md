---
title: "Migration de colonnes calculées | Microsoft Docs"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64a9eade-22c3-4a9d-ab50-956219e08df1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f4fda63a6cf7dae045a247eb26163d0e041841b8
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="migrating-computed-columns"></a>Migration de colonnes calculées
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

Les colonnes calculées ne sont pas prises en charge dans les tables optimisées en mémoire. Toutefois, vous pouvez simuler une colonne calculée.

**Applies to:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.  
À partir de [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1, les colonnes calculées sont prises en charge dans les tables optimisées en mémoire et les index.

Pensez à rendre vos colonnes calculées persistantes lorsque vous migrez vos tables sur disque vers des tables optimisées en mémoire. Les performances des tables optimisées en mémoire et des procédures stockées compilées en mode natif peuvent remettre en cause le besoin de persistance.  
  
## <a name="non-persisted-computed-columns"></a>Colonnes calculées non persistantes  
 Pour simuler les effets d'une colonne calculée non persistante, créez une vue sur la table optimisée en mémoire. Dans l'instruction SELECT qui définit la vue, ajoutez la définition de colonne calculée dans la vue. Excepté dans une procédure stockée compilée en mode natif, les requêtes qui utilisent des valeurs de la colonne calculée doivent être lues dans la vue. Dans les procédures stockées compilées en mode natif, vous devez mettre à jour les instructions de sélection (SELECT), de mise à jour (UPDATE) ou de suppression (DELETE) conformément à votre définition de colonne calculée.  
  
```tsql  
-- Schema for the table dbo.OrderDetails:  
-- OrderId int not null primary key,  
-- ProductId int not null,  
-- SalePrice money not null,  
-- Quantity int not null,  
-- Total money not null  
--  
-- Total is computed as SalePrice * Quantity and is not persisted.  
CREATE VIEW dbo.v_order_details AS  
   SELECT  
      OrderId,  
      ProductId,  
      SalePrice,  
      Quantity,  
      Quantity * SalePrice AS Total  
   FROM dbo.order_details  
```  
  
## <a name="persisted-computed-columns"></a>Colonnes calculées persistantes  
 Pour simuler les effets d'une colonne calculée persistante, créez une procédure stockée pour insérer dans la table et une autre pour mettre à jour la table. Lors de l'insertion ou de la mise à jour de la table, appelez ces procédures stockées pour effectuer ces tâches. Dans les procédures stockées, calculez la valeur du champ calculé en fonction des entrées, de façon semblable au mode de définition de la colonne calculée sur la table sur disque d'origine. Ensuite, insérez ou mettez à jour la table selon les besoins dans la procédure stockée.  
  
```tsql  
-- Schema for the table dbo.OrderDetails:  
-- OrderId int not null primary key,  
-- ProductId int not null,  
-- SalePrice money not null,  
-- Quantity int not null,  
-- Total money not null  
--  
-- Total is computed as SalePrice * Quantity and is persisted.  
-- we need to create insert and update procedures to calculate Total.  
CREATE PROCEDURE sp_insert_order_details   
@OrderId int, @ProductId int, @SalePrice money, @Quantity int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (LANGUAGE = N'english', TRANSACTION ISOLATION LEVEL = SNAPSHOT)  
-- compute the value here.   
-- this stored procedure works with single rows only.  
-- for bulk inserts, accept a table-valued parameter into the stored procedure  
-- and use an INSERT INTO SELECT statement.  
DECLARE @total money = @SalePrice * @Quantity  
INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)  
VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
@OrderId int, @ProductId int, @SalePrice money, @Quantity int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (LANGUAGE = N'english', TRANSACTION ISOLATION LEVEL = SNAPSHOT)  
-- compute the value here.   
-- this stored procedure works with single rows only.  
DECLARE @total money = @SalePrice * @Quantity  
UPDATE dbo.OrderDetails   
SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
WHERE OrderId = @OrderId  
END  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Migration vers OLTP en mémoire](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  

