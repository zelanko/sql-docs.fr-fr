---
title: "InstanceOf (Type de données geometry) | Documents Microsoft"
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
- InstanceOf
- InstanceOf_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- InstanceOf (geometry Data Type)
ms.assetid: fdea1248-29a4-4bab-a60d-a1b359b5e109
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a7106339cc346cbd49b3cbfc3905ea3a2a941c15
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="instanceof-geometry-data-type"></a>InstanceOf (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Une méthode qui vérifie si le **geometry** instance est le même que le type spécifié. Retourne 1 si le type d’un **geometry** instance est le même que le type spécifié, ou si le type spécifié est un ancêtre du type d’instance ; sinon, retourne 0.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.InstanceOf (geometry_type )  
```  
  
## <a name="arguments"></a>Arguments  
 *geometry_type*  
 Est un **nvarchar (4000)** chaîne spécifiant un des 15 types exposés dans le **geometry** hiérarchie de type.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **bits**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
 L’entrée de la méthode doit être une des valeurs suivantes : **Geometry**, **Point**, **courbe**, **LineString**, **CircularString**, **CompoundCurve**, **Surface**, **polygone**, **CurvePolygon**, **GeometryCollection**, **MultiSurface**, **MultiPolygon**, **MultiCurve**, **MultiLineString**, et **MultiPoint**. Cette méthode lève un **ArgumentException** si toutes les autres chaînes sont utilisées pour l’entrée.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `MultiPoint` et utilise `InstanceOf()` pour voir si l'instance est un `GeometryCollection`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances géométriques](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  


