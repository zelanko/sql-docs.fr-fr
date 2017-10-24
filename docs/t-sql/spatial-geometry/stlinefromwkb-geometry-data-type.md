---
title: "STLineFromWKB (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STLineFromWKB (geometry Data Type)
- STLineFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STLineFromWKB (geometry Data Type)
ms.assetid: e674c8c4-c67f-4fc1-9873-d9c2ed46c659
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 39f15ae5d668637ad34920fb6cdd100a6e3fed2a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stlinefromwkb-geometry-data-type"></a>STLineFromWKB (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

Retourne un **geometryLineString** instance à partir d’une représentation de l’Open Geospatial Consortium (OGC) WKB Well-Known Binary ().
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STLineFromWKB ( 'WKB_linestring' , SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *WKB_linestring*  
 Est la représentation WKB de le **geometryLineString** instance à retourner. *WKB_linestring* est un **varbinary (max)** expression.  
  
 *SRID*  
 Est un **int** expression représentant les données spatiales ID de référence (SRID) de la **geometryLineString** instance à retourner.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
 Type OGC : **LineString**  
  
## <a name="remarks"></a>Notes  
 Cette méthode lève un **FormatException** si l’entrée n’est pas correctement mise en forme.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `STLineFromWKB()` pour créer une instance `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STLineFromWKB(0x0102000000020000000000000000005940000000000000594000000000000069400000000000006940, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes géométriques statiques OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  


