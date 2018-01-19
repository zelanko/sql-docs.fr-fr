---
title: "STInteriorRingN (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STInteriorRingN_TSQL
- STInteriorRingN (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: STInteriorRingN (geometry Data Type)
ms.assetid: 47310f9f-2cdb-41e0-a6da-7c3cfbf139ac
caps.latest.revision: "21"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d900e0ca87d0eed56b451927654f427a41de9e11
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="stinteriorringn-geometry-data-type"></a>STInteriorRingN (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne l’anneau intérieur spécifié d’un **Polygongeometry** instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STInteriorRingN ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Est un **int** expression comprise entre 1 et le nombre d’anneaux intérieurs dans le **geometry** instance.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
 Type Open Geospatial Consortium (OGC) : **LineString**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne **null** si le **geometry** instance n’est pas un polygone. Cette méthode lève également une **ArgumentOutOfRangeException** si l’expression est supérieure au nombre d’anneaux. Le nombre d’anneaux peut être retourné à l’aide de `STNumInteriorRing``()`.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée un `Polygon` instance et utilise `STInteriorRingN()` pour retourner l’anneau intérieur du polygone en tant qu’un **LineString**.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STInteriorRingN(1).ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

