---
title: 'Exemple : récupération des informations de modèle de produit au format XML | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RAW mode, retrieving XML information example
ms.assetid: 3828b4ca-3ab2-444f-9c58-8be6e7f064a6
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6c6eead2a8016572cf8fe2491463fb396218e58f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051672"
---
# <a name="example-retrieving-product-model-information-as-xml"></a>Exemple : récupération des informations de modèle de produit au format XML
  La requête suivante retourne des informations sur le modèle d'un produit. `RAW` Le mode est spécifié dans la clause `FOR XML` .  
  
## <a name="example"></a>Exemple  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW;  
GO  
```  
  
 Voici le résultat partiel :  
  
 `<row ProductModelID="122" Name="All-Purpose Bike Stand" />`  
  
 `<row ProductModelID="119" Name="Bike Wash" />`  
  
 Vous pouvez récupérer des données XML centrées sur les éléments en spécifiant la directive `ELEMENTS` .  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 Voici le résultat obtenu :  
  
```  
<row>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</row>  
<row>  
  <ProductModelID>119</ProductModelID>  
  <Name>Bike Wash</Name>  
</row>  
```  
  
 Vous pouvez éventuellement spécifier le `TYPE` pour récupérer les résultats en tant que directive `xml` type. La directive `TYPE` ne modifie pas le contenu des résultats. Seul le type de données des résultats est affecté.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, TYPE ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode RAW avec FOR XML](use-raw-mode-with-for-xml.md)  
  
  