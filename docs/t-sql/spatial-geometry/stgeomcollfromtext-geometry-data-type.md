---
title: "STGeomCollFromText (Type de données geometry) | Documents Microsoft"
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
- STGeomCollFromText_TSQL
- STGeomCollFromText (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeomCollFromText (geometry Data Type)
ms.assetid: 19e757b3-cb2e-4852-87b9-40a815ab707e
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 10c21174dfb176dd08ae30e4752b2f8ecfaa98f5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stgeomcollfromtext-geometry-data-type"></a>STGeomCollFromText (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un **geometry** instance à partir d’une représentation de la réplication continue en cluster (WKT, Open Geospatial Consortium (OGC) Well-Known Text) augmentée des Z (élévation) et les valeurs M (mesure) apportées par l’instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STGeomCollFromText ( 'geometrycollection_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *geometrycollection_tagged_text*  
 Est la représentation WKT de le **geometry** instance à retourner. *geometry_tagged_text* est un **nvarchar (max)** expression.  
  
 *SRID*  
 Est un **int** expression représentant les données spatiales ID de référence (SRID) de la **geometry** instance à retourner.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes  
 Le type OGC de le **geometry** instance retournée par `STGeomCollFromText()` est définie sur l’entrée WKT correspondante.  
  
 Cette méthode lève une exception si l'entrée n'est pas valide.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise `STGeomCollFromText()` pour créer une instance géométrique.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION ( POLYGON((5 5, 10 5, 10 10, 5 5)), POINT(10 10) )', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes géométriques statiques OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  


