---
title: "InstanceOf (Type de données geometry) | Documents Microsoft"
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
- InstanceOf
- InstanceOf_TSQL
dev_langs: TSQL
helpviewer_keywords: InstanceOf (geometry Data Type)
ms.assetid: fdea1248-29a4-4bab-a60d-a1b359b5e109
caps.latest.revision: "26"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 524e084112d2b9a8b7fe51188d50e9f518aba488
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="instanceof-geometry-data-type"></a>InstanceOf (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
 [Méthodes étendues sur des instances geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

