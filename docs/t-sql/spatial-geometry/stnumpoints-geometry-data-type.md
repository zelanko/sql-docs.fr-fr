---
title: "STNumPoints (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STNumPoints_TSQL
- STNumPoints (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STNumPoints (geometry Data Type)
ms.assetid: a19520fc-7f91-4a2c-856f-4d8b99a7e496
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17dc20837c72439fc79fec62170edfb8eca34d9a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stnumpoints-geometry-data-type"></a>STNumPoints (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne la somme du nombre de points dans chacune des figures dans une **geometry** instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STNumPoints ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **int**  
  
 Type de retour CLR : **SqlInt32**  
  
## <a name="remarks"></a>Notes  
 Cette méthode compte les points dans la description d’un **geometry** instance. Les points dupliqués sont comptés. Si cette instance est un **collection** type, cette méthode retourne la somme des points dans chacun de ses éléments.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `LineString` et utilise `STNumPoints()` pour déterminer combien de points ont été utilisés dans la description de l'instance.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STNumPoints();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur les Instances géométriques](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

