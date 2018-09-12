---
title: Créer des vues sur les colonnes XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cc4890077c25e98ebff0832423f6d1f0aaabdc46
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889215"
---
# <a name="create-views-over-xml-columns"></a>Créer des vues sur les colonnes XML
  Vous pouvez utiliser un `xml` colonne de type pour créer des vues. L’exemple suivant crée une vue dans laquelle la valeur à partir d’un `xml` colonne de type est récupéré à l’aide de la `value()` méthode de la `xml` type de données.  
  
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
  
 Exécutez la requête suivante sur la vue :  
  
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
  
 Notez les points suivants sur l’utilisation de la `xml` type de données pour créer des vues :  
  
-   Le type de données XML peut être créé dans une vue matérialisée. Il ne peut pas être basé sur une méthode du type de données xml. En revanche, il peut être converti en une collection de schémas XML différente de la colonne de type xml de la table de base.  
  
-   Le `xml` type de données ne peut pas être utilisé dans les vues partitionnées distribuées.  
  
-   Les prédicats SQL exécutés contre la vue ne seront pas poussés dans le XQuery de la définition de vue.  
  
-   Les méthodes de type de données XML dans une vue ne peuvent pas être mises à jour.  
  
  
