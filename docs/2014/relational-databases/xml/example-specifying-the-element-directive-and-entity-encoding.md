---
title: 'Exemple : spécification de la directive ELEMENT et de l’encodage d’entité | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
- entity encoding [XML]
ms.assetid: 50cda5c1-7293-4080-93b3-872e3b8d484e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 503cc731ede59b4cc3cf70e9cf2daafec436243c
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82716734"
---
# <a name="example-specifying-the-element-directive-and-entity-encoding"></a>Exemple : spécification de la directive ELEMENT et de l'encodage d'entité
  Cet exemple illustre la différence entre les directives **ELEMENT** et **XML** . La directive **ELEMENT** décompose les données en entités, contrairement à la directive **XML** . L’élément \<Summary> reçoit des données XML, `<Summary>This is summary description</Summary>`, dans la requête.  
  
 Prenons par exemple la requête suivante :  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription!ELEMENT]  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        NULL,  
       '<Summary>This is summary description</Summary>'  
FROM   Production.ProductModel  
WHERE  ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 Voici l'ensemble de résultats. la description résumée est décomposée en entités dans le résultat.  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription><Summary>This is summary description</Summary></SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 Maintenant, si vous spécifiez la directive **XML** dans le nom de colonne ( `Summary!2!SummaryDescription!XML`) au lieu de la directive **ELEMENT** , vous obtenez la description résumée non décomposée en entités.  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <Summary>This is summary description</Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 Au lieu d’affecter une valeur XML statique, la requête suivante utilise la méthode **query()** du type **xml** pour extraire la description résumée des modèles de produit de la colonne CatalogDescription de type **xml** . Le résultat étant de type **xml** , aucune décomposition en entités n'est appliquée.  
  
```  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
       (SELECT CatalogDescription.query('  
            declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
          /pd:ProductDescription/pd:Summary'))  
FROM     Production.ProductModel  
WHERE    CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],Tag  
FOR XML EXPLICIT  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode EXPLICIT avec FOR XML](use-explicit-mode-with-for-xml.md)  
  
  
