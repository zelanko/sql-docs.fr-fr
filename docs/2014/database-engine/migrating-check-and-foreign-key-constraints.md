---
title: Migration des contraintes de vérification et de clé étrangère | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e0a1a1e4-0062-4872-93c3-cd91b7a43c23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2494ab96cc3b4964c26a1ce17593e9b5aece2e7e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62774929"
---
# <a name="migrating-check-and-foreign-key-constraints"></a>Migration des contraintes de validation et de clé étrangère
  Les contraintes de validation et de clés étrangères ne sont pas prises en charge dans [!INCLUDE[hek_2](../includes/hek-2-md.md)] dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]. Ces constructions sont généralement utilisées pour appliquer l'intégrité logique des données au schéma et peuvent être importantes pour conserver la précision fonctionnelle des applications.  
  
 Les contrôles d'intégrité logique sur une table, comme les contraintes de validation et de clés étrangères, nécessitent un traitement supplémentaire sur les transactions et doivent généralement être évités pour les applications sensibles aux performances. Toutefois, si de tels contrôles sont cruciaux pour votre application, il existe deux solutions.  
  
## <a name="checking-constraints-after-an-insert-update-or-delete-operation"></a>Vérification des contraintes après une opération d'insertion, de mise à jour ou de suppression  
 Cette solution est optimiste, basée sur l'hypothèse que la majorité des modifications n'enfreint pas les contraintes. Avec cette solution, les données sont modifiées avant que les contraintes ne soient évaluées. Si une contrainte n'est pas respectée, elle est détectée, mais la modification n'est pas annulée.  
  
 L'avantage de cette solution est qu'elle présente un impact minimal sur les performances, car la modification de données n'est pas bloquée par les vérifications de contraintes. Toutefois, si une modification qui enfreint une ou plusieurs contraintes est apportée, le processus d'annulation de cette modification peut prendre beaucoup de temps.  
  
## <a name="enforcing-constraints-before-an-insert-update-or-delete-operation"></a>Application des contraintes avant une opération d'insertion, de mise à jour ou de suppression  
 Cette solution émule le comportement des contraintes [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Les contraintes sont vérifiées avant la modification des données et mettent fin à la transaction si un contrôle échoue. Cette méthode implique une altération des performances lors de la modification de données, mais garantit que les données d'une table respectent toujours les contraintes.  
  
 Utilisez cette solution lorsque l'intégrité logique des données s'avère indispensable pour la précision et que des modifications risquant d'enfreindre une contrainte sont probables. Cependant, pour garantir l'intégrité, toutes les modifications de données doivent se produire dans les procédures stockées qui incluent ces mises en conformité. Les modifications via des requêtes ad hoc et autres procédures stockées n'appliqueront pas ces contraintes et, par conséquent, peuvent ne pas les respecter, sans avertissement.  
  
## <a name="sample-code"></a>Exemple de code  
 Les exemples suivants sont basés sur la base de données AdventureWorks2012. Plus précisément, ces exemples sont basés sur la table [Sales].[SalesOrderDetail] et ses contraintes de validation et de clés étrangères associées, en plus de l'index unique.  
  
 Les procédures stockées spécifiées ici concernent les opérations d'incrustation uniquement. Les procédures stockées pour les opérations de mise à jour et de suppression présentent normalement des structures identiques.  
  
## <a name="table-definition-for-the-workarounds"></a>Définition de table pour les solutions de contournement  
 Avant la conversion en table mémoire optimisée, la définition de [Sales].[SalesOrderDetail] se présente comme suit :  
  
```sql  
USE [AdventureWorks2012]  
GO  
  
CREATE TABLE [Sales].[SalesOrderDetail]([SalesOrderID] [int] NOT NULL,  
   [SalesOrderDetailID] [int] IDENTITY(1,1) NOT NULL,  
   [CarrierTrackingNumber] [nvarchar](25) NULL,  
   [OrderQty] [smallint] NOT NULL,  
   [ProductID] [int] NOT NULL,  
   [SpecialOfferID] [int] NOT NULL,  
   [UnitPrice] [money] NOT NULL,  
   [UnitPriceDiscount] [money] NOT NULL CONSTRAINT [DF_SalesOrderDetail_UnitPriceDiscount]  DEFAULT ((0.0)),  
   [LineTotal]  AS (isnull(([UnitPrice]*((1.0)-[UnitPriceDiscount]))*[OrderQty],(0.0))),  
   [rowguid] [uniqueidentifier] ROWGUIDCOL  NOT NULL CONSTRAINT [DF_SalesOrderDetail_rowguid]  DEFAULT (newid()),  
   [ModifiedDate] [datetime] NOT NULL CONSTRAINT [DF_SalesOrderDetail_ModifiedDate]  DEFAULT (getdate()),  
 CONSTRAINT [PK_SalesOrderDetail_SalesOrderID_SalesOrderDetailID] PRIMARY KEY CLUSTERED   
(  
   [SalesOrderID] ASC,  
   [SalesOrderDetailID] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID] FOREIGN KEY([SalesOrderID])  
REFERENCES [Sales].[SalesOrderHeader] ([SalesOrderID])  
ON DELETE CASCADE  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID]  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID] FOREIGN KEY([SpecialOfferID], [ProductID])  
REFERENCES [Sales].[SpecialOfferProduct] ([SpecialOfferID], [ProductID])  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID]  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [CK_SalesOrderDetail_OrderQty] CHECK  (([OrderQty]>(0)))  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [CK_SalesOrderDetail_OrderQty]  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [CK_SalesOrderDetail_UnitPrice] CHECK  (([UnitPrice]>=(0.00)))  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [CK_SalesOrderDetail_UnitPrice]  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [CK_SalesOrderDetail_UnitPriceDiscount] CHECK  (([UnitPriceDiscount]>=(0.00)))  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [CK_SalesOrderDetail_UnitPriceDiscount]  
GO  
```  
  
 Suite à la conversion en table mémoire optimisée, la définition de [Sales].[SalesOrderDetail] se présente comme suit :  
  
 Notez que rowguid n'est plus un ROWGUIDCOL, car il n'est pas pris en charge dans [!INCLUDE[hek_2](../includes/hek-2-md.md)]. La colonne a été supprimée. En outre, LineTotal est une colonne calculée et n'est pas abordé dans cet article ; il a donc également été supprimé.  
  
```sql  
USE [AdventureWorks2012]  
GO  
  
CREATE TABLE [Sales].[SalesOrderDetail]([SalesOrderID] [int] NOT NULL,  
   [SalesOrderDetailID] [int] IDENTITY(1,1) NOT NULL,  
   [CarrierTrackingNumber] [nvarchar](25) NULL,  
   [OrderQty] [smallint] NOT NULL,  
   [ProductID] [int] NOT NULL,  
   [SpecialOfferID] [int] NOT NULL,  
   [UnitPrice] [money] NOT NULL,  
   [UnitPriceDiscount] [money] NOT NULL CONSTRAINT [DF_SalesOrderDetail_UnitPriceDiscount]  DEFAULT ((0.0)),  
   [ModifiedDate] [datetime] NOT NULL CONSTRAINT [DF_SalesOrderDetail_ModifiedDate]  DEFAULT (getdate()),  
   CONSTRAINT [PK_SalesOrderDetail_SalesOrderID_SalesOrderDetailID] PRIMARY KEY NONCLUSTERED   
   (  
      [SalesOrderID] ASC,  
      [SalesOrderDetailID] ASC  
   ),  
   INDEX [AK_SalesOrderDetail_rowguid] NONCLUSTERED HASH ([rowguid]) WITH (BUCKET_COUNT = 1048576),  
   INDEX [IX_SalesOrderDetail_ProductId] NONCLUSTERED ([ProductId] ASC)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
  
GO  
```  
  
## <a name="checking-constraints-after-an-insert-update-or-delete-operation"></a>Vérification des contraintes après une opération d'insertion, de mise à jour ou de suppression  
  
```sql  
USE AdventureWorks2012  
GO  
  
CREATE PROCEDURE Sales.usp_insert_SalesOrderDetails   
   @SalesOrderId int, @CarrierTrackingNumber nvarchar(25) = null, @OrderQty smallint, @ProductId int, @SpecialOfferID int,   
   @UnitPrice money, @UnitPriceDiscount money = 0.00, @ModifiedDate datetime = null  
AS  
BEGIN  
BEGIN TRANSACTION   
   -- handle defaults for the insert.  
   -- This is to make the insert logic less complex. Default constraints on the table should be in sync with this logic.  
   -- Conversely, you can write an INSERT statement for each case where one or more values for the three columns with default constraints are not specified.  
   IF @ModifiedDate = null SET @ModifiedDate = GETDATE()  
  
   -- Insert the row.  
   INSERT INTO Sales.SalesOrderDetail   
      (SalesOrderID, CarrierTrackingNumber, OrderQty, ProductID, SpecialOfferID, UnitPrice, UnitPriceDiscount, ModifiedDate)  
   VALUES   
      (@SalesOrderId, @CarrierTrackingNumber, @OrderQty, @ProductID, @SpecialOfferID, @UnitPrice, @UnitPriceDiscount, , @ModifiedDate)   
  
   -- Now handle constraints  
   DECLARE @violations TABLE   
   (   
      ConstraintName sysname,  
      ViolatedValue1 sql_variant,  
      ViolatedValue2 sql_variant  
   )  
  
   -- FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID  
   IF NOT EXISTS (SELECT soh.SalesOrderId AS [Exists] FROM Sales.SalesOrderHeader soh WHERE soh.SalesOrderID = @SalesOrderId)   
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID', @SalesOrderId, NULL)  
   -- FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID  
   IF NOT EXISTS (SELECT sop.SpecialOfferID, sop.ProductID FROM [Sales].[SpecialOfferProduct] sop WHERE sop.SpecialOfferID = @SpecialOfferID AND sop.ProductID = @ProductId)  
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID', @SpecialOfferId, @ProductId)  
   -- CK_SalesOrderDetail_OrderQty  
   IF NOT @OrderQty > 0   
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'CK_SalesOrderDetail_OrderQty', @OrderQty, NULL)  
   -- CK_SalesOrderDetail_UnitPrice  
   IF NOT @UnitPrice >= 0.00  
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'CK_SalesOrderDetail_UnitPrice', @UnitPrice, NULL)  
   -- CK_SalesOrderDetail_UnitPriceDiscout  
   IF NOT @UnitPriceDiscount >= 0.00  
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'CK_SalesOrderDetail_UnitPriceDiscount', @UnitPriceDiscount, NULL)  
  
   -- Return a rowset containing violated constraints. On an item that doesn't violate anything, should return an empty rowset.  
   SELECT ConstraintName, ViolatedValue1, ViolatedValue2 FROM @violations  
   COMMIT TRANSACTION  
END  
```  
  
## <a name="enforcing-constraints-before-an-insert-update-or-delete-operation"></a>Application des contraintes avant une opération d'insertion, de mise à jour ou de suppression  
  
```sql  
USE AdventureWorks2012  
GO  
  
CREATE PROCEDURE Sales.usp_insert_SalesOrderDetails   
   @SalesOrderId int, @CarrierTrackingNumber nvarchar(25) = null, @OrderQty smallint, @ProductId int, @SpecialOfferID int,   
   @UnitPrice money, @UnitPriceDiscount money = 0.00, @ModifiedDate datetime = null  
AS  
BEGIN  
BEGIN TRY  
   BEGIN TRANSACTION  
   -- Verify the constraints first.  
   -- FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID  
   IF NOT EXISTS (SELECT soh.SalesOrderId FROM Sales.SalesOrderHeader soh WHERE soh.SalesOrderID = @SalesOrderId)   
      THROW 50547, N'This SalesOrderId does not exist in SalesOrderHeader', 1  
   -- FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID  
   IF NOT EXISTS (SELECT sop.SpecialOfferID, sop.ProductID FROM [Sales].[SpecialOfferProduct] sop WHERE sop.SpecialOfferID = @SpecialOfferID AND sop.ProductID = @ProductId)  
      THROW 50547, N'This combination of SpecialOfferID and ProductID does not exist in SpecialOfferProduct', 1   
   -- CK_SalesOrderDetail_OrderQty  
   IF NOT @OrderQty > 0   
      THROW 50547, N'OrderQty must be greater than zero.', 1  
   -- CK_SalesOrderDetail_UnitPrice  
   IF NOT @UnitPrice >= 0.00  
      THROW 50547, N'UnitPrice cannot be negative.', 1  
   -- CK_SalesOrderDetail_UnitPriceDiscout  
   IF NOT @UnitPriceDiscount >= 0.00  
      THROW 50547, N'UnitPriceDiscount cannot be negative', 1  
  
   -- All verifications have now passed. Proceed to insert.  
  
   -- handle defaults for the insert.  
   -- This is to make the insert logic less complex. Default constraints on the table should be in sync with this logic.  
   -- Conversely, you can write an INSERT statement for each case where one or more values for the three columns with default constraints are not specified.  
  
   IF @ModifiedDate = null SET @ModifiedDate = GETDATE()  
  
   -- Calculate computed columnn and store it.  
   DECLARE @LineTotal numeric(38, 6)  
   SET @LineTotal = (isnull((@UnitPrice * ((1.0) - @UnitPriceDiscount)) * @OrderQty, (0.0)))  
  
   -- Insert the row.  
   INSERT INTO Sales.SalesOrderDetail   
      (SalesOrderID, CarrierTrackingNumber, OrderQty, ProductID, SpecialOfferID, UnitPrice, UnitPriceDiscount, ModifiedDate)  
   VALUES   
      (@SalesOrderId, @CarrierTrackingNumber, @OrderQty, @ProductID, @SpecialOfferID, @UnitPrice, @UnitPriceDiscount, @ModifiedDate)  
   COMMIT TRANSACTION  
END TRY  
BEGIN CATCH  
   IF @@TRANCOUNT > 0  
      ROLLBACK TRANSACTION  
      THROW;  
END CATCH  
END  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Migration vers OLTP en mémoire](../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
