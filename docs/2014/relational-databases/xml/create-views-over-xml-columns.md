---
title: Créer des vues sur les colonnes XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d1e37f341c0606947b37eb10e8e3123ad410204
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301318"
---
# <a name="create-views-over-xml-columns"></a>Créer des vues sur les colonnes XML
  Vous pouvez utiliser une colonne de type `xml` pour créer des vues. L'exemple suivant crée une vue dans laquelle la valeur d'une colonne de type `xml` est extraite à l'aide de la méthode `value()` du type de données `xml`.  
  
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
  
 Voici le résultat obtenu :  
  
```  
ProductID   PName        
----------- ------------  
1           SomeName   
```  
  
 Notez les points suivants à propos de l'utilisation du type de données `xml` pour créer des vues :  
  
-   Le type de données XML peut être créé dans une vue matérialisée. Il ne peut pas être basé sur une méthode du type de données xml. En revanche, il peut être converti en une collection de schémas XML différente de la colonne de type xml de la table de base.  
  
-   Le type de données `xml` ne peut pas être utilisé dans les vues partitionnées distribuées.  
  
-   Les prédicats SQL exécutés contre la vue ne seront pas poussés dans le XQuery de la définition de vue.  
  
-   Les méthodes de type de données XML dans une vue ne peuvent pas être mises à jour.  
  
  
