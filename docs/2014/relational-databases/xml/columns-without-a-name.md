---
title: Colonnes sans nom | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns without
ms.assetid: 440de44e-3a56-4531-b4e4-1533ca933cac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e4d4eccfe7bcad3abd2c6d89f867ac8f88129a6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62637587"
---
# <a name="columns-without-a-name"></a>Colonnes sans nom
  Toute colonne sans nom est insérée. Par exemple, les colonnes calculées ou les requêtes scalaires imbriquées qui ne spécifient pas d'alias de colonne génèrent des colonnes sans nom. Si la colonne est de type `xml`, le contenu de cette instance de type de données est inséré. Sinon, le contenu de la colonne est inséré en tant que nœud de texte.  
  
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
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location ...LocationID="10" ...></MI:Location>`  
  
 `<MI:Location ...LocationID="20" ...></MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode PATH avec FOR XML](use-path-mode-with-for-xml.md)  
  
  
