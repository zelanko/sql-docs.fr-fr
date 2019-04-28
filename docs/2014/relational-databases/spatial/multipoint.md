---
title: MultiPoint | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 36c0268ef87eb4cd9996744f9ff0015bf499a9a2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659972"
---
# <a name="multipoint"></a>MultiPoint
  Un `MultiPoint` est une collection de zéro ou plusieurs points. La limite d'une instance `MultiPoint` est vide.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `geometry MultiPoint` avec un SRID 23 et deux points : un point avec les coordonnées (2, 3), un point avec les coordonnées (7, 8) et une valeur Z de 9.5.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 Cette instance `MultiPoint` peut également être exprimée à l'aide de `STMPointFromText()` comme illustré ci-dessous.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 L'exemple suivant utilise la méthode `STGeometryN()` pour extraire une description du premier point dans la collection.  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Point](point.md)   
 [Données spatiales &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
