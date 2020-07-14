---
title: 'Exemple : Renommage de l’élément &lt;row&gt; | Microsoft Docs'
description: Consulter un exemple de renommage d’un élément row XML en spécifiant un argument facultatif en mode RAW dans la clause FOR XML.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cc297571daec9825a91d4e35ebbac737d88b5619
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85633046"
---
# <a name="example-renaming-the-ltrowgt-element"></a>Exemple : Renommage de l’élément &lt;row&gt;
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Pour chaque ligne du jeu de résultats, le mode RAW génère un élément `<row>`. Vous pouvez éventuellement spécifier un autre nom pour cet élément en spécifiant un argument facultatif pour le mode RAW, comme illustré dans cette requête. La requête retourne un élément <`ProductModel`> pour chaque ligne de l'ensemble de lignes.  
  
## <a name="example"></a>Exemple  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 Voici l'ensemble de résultats. La directive `ELEMENTS` étant ajoutée à la requête, le résultat est centré sur les éléments.  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode RAW avec FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  
