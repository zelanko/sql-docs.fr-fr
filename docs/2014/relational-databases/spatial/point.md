---
title: Point | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Point geometry subtype [SQL Server]
- geometry data type [SQL Server], spatial data
ms.assetid: 2a596ec4-8b2f-4962-bcb4-e5c8f77edad5
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e0bc6a80c1ce2fc6e9646114d5d5f856d89bdd04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140708"
---
# <a name="point"></a>Point
  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les données spatiales, un `Point` est un objet dimension 0, qui représente un emplacement unique et peut contenir des valeurs Z (élévation) et M (mesure).  
  
## <a name="geography-data-type"></a>Type de données geography  
 Le type Point pour le type de données geography représente un emplacement unique où *Lat* et *Long* désignent respectivement la latitude et la longitude. Les valeurs de latitude et de longitude sont mesurées en degrés. Les valeurs de latitude sont toujours comprises dans l’intervalle [-90, 90]. Si vous entrez une valeur non comprise dans cette plage, une exception est levée. Les valeurs de longitude sont toujours comprises dans l’intervalle [-180, 180]. Si vous entrez une valeur non comprise dans cette plage, elle est renvoyée pour y être contenue. Par exemple, si vous entrez la valeur 190 pour la longitude, elle est renvoyée à la valeur -170. Le*SRID* représente l’ID de référence spatiale de l’instance **geography** à retourner.  
  
## <a name="geometry-data-type"></a>Type de données geometry  
 Le type Point pour le type de données geometry représente un emplacement unique où *X* et *Y* désignent respectivement les coordonnées X et Y du point généré. Le*SRID* représente l’ID de référence spatiale de l’instance **geometry** à retourner.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée une instance `geometry Point`qui représente le point (3, 4) avec un SRID de 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT (3 4)', 0);  
```  
  
 L’exemple suivant crée une instance `geometry``Point` qui représente le point (3, 4) avec une valeur Z (élévation) de 7, une valeur M (mesure) de 2,5 et le SRID par défaut de 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 7 2.5)');  
```  
  
 Le dernier exemple retourne les valeurs X, Y, Z et M pour l’instance `geometry``Point` .  
  
```  
SELECT @g.STX;  
SELECT @g.STY;  
SELECT @g.Z;  
SELECT @g.M;  
```  
  
 Les valeurs Z et M peuvent être spécifiées explicitement comme NULL, comme illustré dans l'exemple suivant.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 NULL NULL)');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [MultiPoint](multipoint.md)   
 [STX &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stx-geometry-data-type)   
 [STY &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/sty-geometry-data-type)   
 [Données spatiales &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
