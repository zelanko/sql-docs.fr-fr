---
title: Colonnes sans nom | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns without
ms.assetid: 440de44e-3a56-4531-b4e4-1533ca933cac
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 685be1c7e6c43e28500dd1ee96ea6fe696ad8e20
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664627"
---
# <a name="columns-without-a-name"></a>Colonnes sans nom
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Toute colonne sans nom est insérée. Par exemple, les colonnes calculées ou les requêtes scalaires imbriquées qui ne spécifient pas d'alias de colonne génèrent des colonnes sans nom. Si la colonne est de type **xml** , le contenu de cette instance de type de données est inséré. Sinon, le contenu de la colonne est inséré en tant que nœud de texte.  
  
```  
SELECT 2+2  
FOR XML PATH  
```  
  
 Génère ce document XML. Par défaut, pour chaque ligne de l'ensemble de lignes, un élément <`row`> est généré dans le document XML obtenu. Ce processus rappelle le mode RAW.  
  
 `<row>4</row>`  
  
 La requête suivante renvoie un ensemble de lignes de trois colonnes. La troisième colonne sans nom possède des données XML. Le mode PATH insère une instance du type xml.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ;  
GO  
```  
  
 Voici le résultat partiel :  
  
```xml
<row>
  <ProductModelID>7</ProductModelID>
  <Name>HL Touring Frame</Name>
  <MI:Location ...LocationID="10" ...></MI:Location>
  <MI:Location ...LocationID="20" ...></MI:Location>
  ...
</row>
```

## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode PATH avec FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
