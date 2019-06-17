---
title: Migration de déclencheurs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7df393f26523991abafded74ded242390cb0e3b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63071467"
---
# <a name="migrating-triggers"></a>Migration de déclencheurs
  Cette rubrique présente les déclencheurs DDL et DML et les tables mémoire optimisées.  
  
 Les déclencheurs LOGON sont des déclencheurs définis pour se déclencher sur les événements LOGON. Ces déclencheurs n'affectent pas les tables mémoire optimisées.  
  
## <a name="ddl-triggers"></a>Déclencheurs DDL  
 Les déclencheurs DDL sont des déclencheurs définis pour se déclencher lorsqu'une instruction CREATE, ALTER, DROP, GRANT, DENY, REVOKE ou UPDATE STATISTICS est exécutée sur la base de données ou sur le serveur sur lequel elle est définie.  
  
 Il est impossible de créer des tables mémoire optimisées si la base de données ou le serveur contient un ou plusieurs déclencheurs DDL définis sur l'événement CREATE_TABLE ou un groupe d'événements qui inclut cet événement. Il est impossible de supprimer une table mémoire optimisée si la base de données ou le serveur contient un ou plusieurs déclencheurs DDL définis sur l'événement DROP_TABLE ou un groupe d'événements qui inclut cet événement.  
  
 Il est impossible de créer des procédures stockées compilées en mode natif s'il existe un ou plusieurs déclencheurs DDL définis sur les événements CREATE_PROCEDURE, DROP_PROCEDURE ou un groupe d'événements qui inclut ces événements.  
  
## <a name="dml-triggers"></a>Déclencheurs DML  
 Les déclencheurs DML ne peuvent pas être définis sur les tables mémoire optimisées. Cependant, OLTP en mémoire vous permet d'obtenir un effet similaire aux déclencheurs DML si vous utilisez explicitement des procédures stockées pour insérer, mettre à jour ou supprimer des données. Si votre système contient des requêtes ad hoc, convertissez-les de façon à utiliser ces procédures stockées à la place afin de simuler l'effet des déclencheurs DML.  
  
 Selon l'événement déclencheur (FOR/AFTER ou INSTEAD OF), vous pouvez inclure le contenu du déclencheur dans la procédure stockée appropriée qui exécute l'instruction INSERT, UPDATE ou DELETE sur cette table. Par exemple, lorsque vous migrez un déclencheur AFTER INSERT, vous pouvez modifier la procédure stockée qui effectue l'opération d'insertion en ajoutant le contenu du déclencheur après l'instruction INSERT appropriée.  
  
 Utilisez une procédure stockée interprétée ou une procédure stockée compilée en mode natif. La plupart les constructions [!INCLUDE[tsql](../../includes/tsql-md.md)] dans une procédure stockée interprétée s'exécutent sur une table mémoire optimisée. Toutefois, seul un sous-ensemble de constructions [!INCLUDE[tsql](../../includes/tsql-md.md)] est pris en charge dans les procédures stockées compilées en mode natif. Pour plus d'informations sur la prise en charge de [!INCLUDE[tsql](../../includes/tsql-md.md)] sur les tables mémoire optimisées, consultez [Accès aux tables optimisées en mémoire à l’aide du Transact-SQL interprété](accessing-memory-optimized-tables-using-interpreted-transact-sql.md). Pour plus d'informations sur la prise en charge de [!INCLUDE[tsql](../../includes/tsql-md.md)] dans les procédures stockées compilées en mode natif, consultez [Les constructions Transact-SQL ne sont pas prises en charge par l'OLTP en mémoire](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
 Voici un exemple simple de simulation du comportement des déclencheurs DML sur une table mémoire optimisée.  
  
 La base de données contient les objets suivants, définis dans un script en tant qu'instructions CREATE TABLE, CREATE TRIGGER et CREATE PROCEDURE :  
  
```sql  
CREATE TABLE OrderDetails  
(  
   OrderId int not null primary key,  
   ProductId int not null,  
   SalePrice money not null,  
   Quantity int not null,  
   Total money not null,  
   IsDeleted bit not null DEFAULT (0)  
)  
GO  
  
CREATE TRIGGER tr_order_details_insteadof_insert  
ON OrderDetails  
INSTEAD OF INSERT AS  
BEGIN  
   DECLARE @pid int, @qty_buy int, @qty_remain int  
   SELECT @pid = ProductId, @qty_buy = Quantity FROM inserted  
   SELECT @qty_remain = Quantity FROM Inventory WHERE ProductId = @pid  
   IF (@qty_remain <= @qty_buy)  
      THROW 51000, N'Insufficient inventory!', 1  
   ELSE  
   BEGIN  
      INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)   
      SELECT OrderId, ProductId, SalePrice, Quantity, Total FROM inserted  
      UPDATE Inventory SET Quantity = Quantity - @qty_buy WHERE ProductId = @pid  
   END  
END  
GO  
  
CREATE TRIGGER tr_order_details_after_update  
ON OrderDetails  
AFTER UPDATE AS  
BEGIN  
   INSERT INTO UpdateNotifications (OrderId, UpdateTime) SELECT OrderId, GETDATE() FROM inserted     
END  
GO  
  
CREATE PROCEDURE sp_insert_order_details   
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @total money  
AS BEGIN  
   INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)  
   VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @Total money  
AS BEGIN  
   UPDATE dbo.OrderDetails   
   SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
   WHERE OrderId = @OrderId  
END  
GO  
```  
  
 Les objets suivants sont fonctionnellement équivalents à l'état de prémigration :  
  
```sql  
CREATE TABLE OrderDetails  
(  
   OrderId int not null PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT = 1048576),  
   ProductId int not null,  
   SalePrice money not null,  
   Quantity int not null,  
   Total money not null,  
   IsDeleted bit not null DEFAULT (0)  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE TABLE Inventory  
(  
   ProductId int not null PRIMARY KEY NONCLUSTERED,  
   Quantity int not null  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE TABLE UpdateNotifications  
(  
   OrderId int not null,  
   UpdateTime datetime2 not null  
   CONSTRAINT pk_updateNotifications PRIMARY KEY NONCLUSTERED (OrderId, UpdateTime)  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE PROCEDURE sp_insert_order_details   
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @total money  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'English')  
   DECLARE @qty_remain int  
   SELECT @qty_remain = Quantity FROM dbo.Inventory WHERE ProductId = @ProductId  
   IF (@qty_remain <= @Quantity)  
      THROW 51000, N'Insufficient inventory!', 1  
   ELSE  
   BEGIN  
      INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)   
      VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
      UPDATE dbo.Inventory SET Quantity = Quantity - @Quantity WHERE ProductId = @ProductId  
   END  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @Total money  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'English')  
   UPDATE dbo.OrderDetails   
   SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
   WHERE OrderId = @OrderId  
   INSERT INTO dbo.UpdateNotifications (OrderId, UpdateTime) VALUES (@OrderId, GETDATE())  
END  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Migration vers OLTP en mémoire](migrating-to-in-memory-oltp.md)  
  
  
