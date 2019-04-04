---
title: 'Exemple : Récupération des informations de modèle de produit au format XML | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving XML information example
ms.assetid: 3828b4ca-3ab2-444f-9c58-8be6e7f064a6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b05d07ee1698048f478f2ffce042bbf0c715e7ad
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58509656"
---
# <a name="example-retrieving-product-model-information-as-xml"></a>Exemple : Récupération des informations de modèle de produit au format XML
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  La requête suivante retourne des informations sur le modèle d'un produit. `RAW` Le mode est spécifié dans la clause `FOR XML` .  
  
## <a name="example"></a> Exemple  
  
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
  
 Vous pouvez éventuellement spécifier la directive `TYPE` pour récupérer les résultats en tant que type **xml** . La directive `TYPE` ne modifie pas le contenu des résultats. Seul le type de données des résultats est affecté.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, TYPE ;  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Utiliser le mode RAW avec FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  
