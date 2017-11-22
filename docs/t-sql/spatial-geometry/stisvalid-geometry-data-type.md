---
title: "STIsValid (Type de données geometry) | Documents Microsoft"
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
- STIsValid (geometry Data Type)
- STIsValid_TSQL
dev_langs: TSQL
helpviewer_keywords: STIsValid (geometry Data Type)
ms.assetid: 6da39bea-0f67-4660-98fc-d7214f9b2138
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2b2d68cd92401a37a5ed19f4cd23165e6c0b9701
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="stisvalid-geometry-data-type"></a>STIsValid (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne true si un **geometry** instance est bien formée, selon son type Open Geospatial Consortium (OGC). Retourne false si un **geometry** instance n’est pas bien formée.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STIsValid ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **bits**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
 Le type OGC d’un **geometry** instance peut être déterminée en appelant [STGeometryType()](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]génère uniquement valide **geometry** instances, mais permet le stockage et la récupération d’instances non valides. Une instance valide qui représente le même ensemble de points de toute instance non valide peut être extraite à l'aide de la méthode `MakeValid()`.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `geometry` et utilise `STIsValid()` pour tester si l'instance est valide.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STIsValid();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STGeometryType &#40; Type de données geometry &#41;](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)   
 [MakeValid &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/makevalid-geometry-data-type.md)   
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

