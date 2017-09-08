---
title: "CollectionAggregate (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CollectionAggregate method (geometry)
ms.assetid: b7c85d59-c841-4b7f-9d46-8b4b7f2a3afe
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2acf5b0fe7f3b6833f56f5264844e4dc9870155f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="collectionaggregate-geometry-data-type"></a>CollectionAggregate (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Crée un **GeometryCollection** instance à partir d’un ensemble de **geometry** types.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CollectionAggregate ( geometry_operand )  
```  
  
## <a name="arguments"></a>Arguments  
 *geometry_operand*  
 Est un **geometry** colonne de table de type qui représente un ensemble de **geometry** objets à répertorier dans le **GeometryCollection** instance.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
## <a name="exceptions"></a>Exceptions  
 Lève un `FormatException` en présence de valeurs d'entrée qui ne sont pas valides. Consultez [STIsValid &#40; Type de données geometry &#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)  
  
## <a name="remarks"></a>Notes  
 Méthode renvoie **null** lorsque l’entrée est vide ou l’entrée a des SRID différents. Consultez [identificateurs de référence spatiale &#40; SRID &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 Méthode ignore **null** entrées.  
  
> [!NOTE]  
>  Méthode renvoie **null** si toutes les valeurs entrées sont **null**.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne une instance `GeometryCollection` qui contient un `CurvePolygon` et un `Polygon`.  
  
 `-- Setup table variable for CollectionAggregate example`  
  
 `DECLARE @Geom TABLE`  
  
 `(`  
  
 `shape geometry,`  
  
 `shapeType nvarchar(50)`  
  
 `)`  
  
 `INSERT INTO @Geom(shape,shapeType) VALUES('CURVEPOLYGON(CIRCULARSTRING(2 3, 4 1, 6 3, 4 5, 2 3))', 'Circle'),`  
  
 `('POLYGON((1 1, 4 1, 4 5, 1 5, 1 1))', 'Rectangle');`  
  
 `-- Perform CollectionAggregate on @Geom.shape column`  
  
 `SELECT geometry::CollectionAggregate(shape).ToString()`  
  
 `FROM @Geom;`  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes de géométrie statiques étendues](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  


