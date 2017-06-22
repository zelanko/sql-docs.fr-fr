---
title: "Créer des vues sur les colonnes XML | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e5f71a5ebacb8af3a58c6eada233c16b955b6ae5
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="create-views-over-xml-columns"></a>Créer des vues sur les colonnes XML
  Vous pouvez utiliser une colonne de type **xml** pour créer des vues. L’exemple suivant crée une vue dans laquelle la valeur d’une colonne de type `xml` est extraite à l’aide de la méthode **value()** du type de données **xml** .  
  
```  
-- Create the table.  
CREATE TABLE T (  
    ProductID          int primary key,   
    CatalogDescription xml)  
GO  
-- Insert sample data.  
INSERT INTO T values(1,'<ProductDescription ProductID="1" ProductName="SomeName" />')  
GO  
-- Create view (note the value() method used to retrieve ProductName   
-- attribute value from the XML).  
CREATE VIEW MyView AS   
  SELECT ProductID,  
         CatalogDescription.value('(/ProductDescription/@ProductName)[1]', 'varchar(40)') AS PName  
  FROM T  
GO   
```  
  
 Exécutez la requête suivante sur la vue :  
  
```  
SELECT *   
FROM   MyView  
```  
  
 Voici le résultat obtenu :  
  
```  
ProductID   PName        
----------- ------------  
1           SomeName   
```  
  
 Notez les points suivants à propos de l'utilisation du type de données **xml** pour créer des vues :  
  
-   Le type de données XML peut être créé dans une vue matérialisée. Il ne peut pas être basé sur une méthode du type de données xml. En revanche, il peut être converti en une collection de schémas XML différente de la colonne de type xml de la table de base.  
  
-   Le type de données **xml** ne peut pas être utilisé dans les vues partitionnées distribuées.  
  
-   Les prédicats SQL exécutés contre la vue ne seront pas poussés dans le XQuery de la définition de vue.  
  
-   Les méthodes de type de données XML dans une vue ne peuvent pas être mises à jour.  
  
  
