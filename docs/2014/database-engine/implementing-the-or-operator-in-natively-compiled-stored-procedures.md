---
title: Implémentation de l’opérateur OR opérateur dans les procédures stockées compilées en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f2528e74-2b1c-48cb-861b-c4e57b51ac35
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 64de082cd12c967f3f3c90ca3cb99c51985ed41a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62778910"
---
# <a name="implementing-the-or-operator-in-natively-compiled-stored-procedures"></a>Implémentation de l'opérateur OR dans les procédures stockées compilées en mode natif
  Les opérateurs OR ne sont pas pris en charge dans les prédicats de requête des procédures stockées compilées en mode natif. Les opérateurs NOT n'étant pas pris en charge non plus dans les prédicats de requête des procédures stockées compilées en mode natif, les effets des opérateurs OR ne peuvent pas être simulés en utilisant uniquement des opérateurs logiques équivalents. Toutefois, les effets d'un opérateur OR peuvent être simulés avec des variables de table mémoire optimisée.  
  
## <a name="or-operator-in-where-clause"></a>Opérateur OR dans la clause WHERE  
 Si vous avez un opérateur OR dans une clause WHERE, vous pouvez utiliser la méthode suivante pour simuler son comportement :  
  
1.  Créez une variable de table mémoire optimisée avec le schéma approprié. Cela nécessite un type de table mémoire optimisée prédéfini.  
  
2.  En commençant par l'opérateur OR de niveau supérieur, séparez la clause WHERE en deux parties selon les prédicats joints par l'opérateur OR. Si vous avez plusieurs opérateurs OR dans une clause WHERE, vous devrez peut-être effectuer cette opération plusieurs fois. Répétez cette étape jusqu'à ce qu'il ne reste plus aucun opérateur OR. Prenons l'exemple du prédicat suivant :  
  
    ```  
    pred1 OR (pred2 AND (pred3 OR pred4)) OR (pred5 AND pred6)  
    ```  
  
     Après cette étape, vous devriez avoir les prédicats suivants :  
  
    ```  
    pred1  
    pred5 AND pred6  
    pred2 AND pred3  
    pred2 AND pred4  
    ```  
  
3.  Exécutez une requête avec chacune des deux parties figurant dans l'étape 2 en tant que prédicat. Insérez le résultat de chaque requête dans la variable de table mémoire optimisée créée à l'étape 1.  
  
4.  Si nécessaire, supprimez les doublons de la variable de table mémoire optimisée.  
  
5.  Utilisez le contenu de la variable de table mémoire optimisée comme résultat de la requête.  
  
 L'exemple suivant utilise les tables de la base de données AdventureWorks2012 mises à jour pour [!INCLUDE[hek_2](../includes/hek-2-md.md)]. Pour télécharger les fichiers de cet exemple, goto [bases de données AdventureWorks - 2012, 2008R2 et 2008](http://msftdbprodsamples.codeplex.com/releases/view/93587). Pour appliquer [!INCLUDE[hek_2](../includes/hek-2-md.md)] code échantillon à AdventureWorks2012, accédez à [exemple d’OLTP en mémoire SQL Server 2014](https://msftdbprodsamples.codeplex.com/releases/view/114491).  
  
 Ajoutez la procédure stockée suivante à la base de données. Nous convertirons cette procédure stockée pour utiliser la compilation native.  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_ondisk  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
AS BEGIN  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  WHERE  s.SalesOrderId = @SalesOrderId  
      OR s.SalesOrderDetailId = @SalesOrderDetailId  
      OR s.CarrierTrackingNumber = @CarrierTrackingNumber  
      OR s.ProductID = @ProductId  
      OR (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
END  
GO  
```  
  
 Après la conversion, la table et le schéma de la procédure stockée seront comme suit.  
  
```  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesOrderDetailType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailTempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  recordcount int not null  
  INDEX ix_fuzzySearchSalesOrderDetailTempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_inmem  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.fuzzySearchSalesOrderDetailType  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderId = @SalesOrderId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderDetailId = @SalesOrderDetailId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.CarrierTrackingNumber COLLATE Latin1_General_BIN2 = @CarrierTrackingNumber COLLATE Latin1_General_BIN2   
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.ProductID = @ProductId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
  
  -- After the above statements, there will be duplicates inside @retValue  
  -- Delete the duplicates from @retValue  
  DECLARE @duplicates Sales.fuzzySearchSalesOrderDetailTempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, recordcount)   
  SELECT SalesOrderId, SalesOrderDetailId, COUNT(*) AS recordCount  
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId  
  
  -- Now we have one row per pair  
  -- clear and rebuild the result set  
  DELETE FROM @retValue  
  
  INSERT INTO @retValue  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates d ON s.SalesOrderId = d.SalesOrderId AND s.SalesOrderDetailId = d.SalesOrderDetailId  
  
  -- After this every pair of (SalesOrderId, SalesOrderDetailId) in @retValue should be unique.  
  SELECT SalesorderId, SalesOrderDetailId, ModifiedDate FROM @retValue  
END  
GO  
```  
  
## <a name="or-operator-in-join-condition"></a>Opérateur OR dans une condition JOIN  
 Si vous avez un opérateur OR dans une condition JOIN d'une instruction SELECT, vous pouvez utiliser la méthode suivante pour simuler son comportement. Si vous avez plusieurs opérateurs OR dans une condition JOIN, ou si vous avez plusieurs conditions JOIN avec des opérateurs OR, vous devrez peut-être effectuer cette opération plusieurs fois.  
  
 Si vous avez des conditions OUTER JOIN, vous pouvez combiner cette solution de contournement avec celle pour les conditions OUTER JOIN.  
  
1.  Créez une variable de table mémoire optimisée avec le schéma approprié. Cela nécessite un type de table mémoire optimisée prédéfini.  
  
2.  Séparez le prédicat dans la condition de jointure en deux parties selon les prédicats joints par l'opérateur OR. Si vous avez plusieurs conditions JOIN, vous devrez peut-être effectuer cette opération pour chaque condition JOIN, puis créer un jeu de combinaisons des fragments résultants. Par exemple, si vous avez trois conditions JOIN avec un opérateur OR dans chaque condition JOIN, vous pouvez avoir 2x2x2=8 prédicats.  
  
3.  Pour chaque prédicat généré par l'étape 2, créez une requête qui insèrera son résultat dans la variable de table mémoire optimisée créée à l'étape 1.  
  
4.  Si nécessaire, supprimez les doublons de la variable de table mémoire optimisée.  
  
5.  Utilisez le contenu de la variable de table mémoire optimisée comme résultat de la requête.  
  
 L'exemple suivant utilise les tables de la base de données AdventureWorks2012 mises à jour pour [!INCLUDE[hek_2](../includes/hek-2-md.md)]. Pour télécharger les fichiers de cet exemple, goto [bases de données AdventureWorks - 2012, 2008R2 et 2008](http://msftdbprodsamples.codeplex.com/releases/view/93587). Pour appliquer [!INCLUDE[hek_2](../includes/hek-2-md.md)] code échantillon à AdventureWorks2012, accédez à [exemple d’OLTP en mémoire SQL Server 2014](https://msftdbprodsamples.codeplex.com/releases/view/114491).  
  
 Ajoutez la procédure stockée suivante à la base de données. Nous convertirons cette procédure stockée pour utiliser la compilation native. Cet exemple utilise des conditions INNER JOIN.  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_ondisk  
  @SpecialOfferId int  
AS BEGIN  
  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  JOIN Sales.SpecialOffer_onDisk offer   
    ON s.SpecialOfferID = offer.SpecialOfferID   
    OR s.ProductID IN (SELECT ProductId FROM Sales.SpecialOfferProduct sop WHERE sop.SpecialOfferID = @SpecialOfferId)  
END  
```  
  
 Après la conversion, la table et le schéma de la procédure stockée seront comme suit.  
  
```  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_Type AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesSpecialOffers_Type NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_TempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  recordcount int null  
  INDEX ix_fuzzySearchSalesSpecialOffers_TempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_inmem  
  @SpecialOfferId int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.FuzzySearchSalesSpecialOffers_Type  
  
  -- Find all special offers matching the conditions  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOffer_inmem offer   
    ON s.SpecialOfferID = offer.SpecialOfferID  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOfferProduct_inmem sop   
    ON sop.SpecialOfferId = @SpecialOfferId AND s.ProductID = sop.ProductId  
  
  -- Now we need to remove the duplicates from @matchingSpecialOffers  
  DECLARE @duplicates Sales.fuzzySearchSalesSpecialOffers_TempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, SpecialOfferid, recordcount)  
  SELECT SalesOrderId, SalesOrderDetailId, SpecialOfferId, COUNT(*)   
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId, SpecialOfferId  
  
  -- now there should be no duplicates within @duplicate  
  -- use @duplicate for join.  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates offer   
    ON    s.SalesOrderId = offer.SalesOrderId   
      AND s.SalesOrderDetailId = offer.SalesOrderDetailID   
      AND s.SpecialOfferId = offer.SpecialOfferId  
END  
GO  
```  
  
## <a name="side-effects"></a>Effets secondaires  
 Si vous avez plusieurs opérateurs OR dans la clause WHERE ou la condition JOIN, le nombre de requêtes que vous devez exécuter pour simuler le comportement peut augmenter de manière exponentielle. Cela peut ralentir les performances des requêtes et augmenter l'utilisation de la mémoire à cause de la nécessité d'utiliser des variables de table mémoire optimisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de migration pour les procédures stockées compilées en mode natif](../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)  
  
  
