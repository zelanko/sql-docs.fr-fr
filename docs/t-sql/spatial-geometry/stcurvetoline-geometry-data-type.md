---
title: "STCurveToLine (Type de données geometry) | Documents Microsoft"
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
- STCurveToLine method (geometry)
ms.assetid: abc80b32-4152-4e10-b816-798b901e0ac5
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2a0601e93e3763ca184ecf599da2cc7f9b36dd6f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stcurvetoline-geometry-data-type"></a>STCurveToLine (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Retourne une approximation polygonale d’une **geometry** instance qui contient les segments d’arc de cercle.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STCurveToLine ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes  
 Retourne une **GeometryCollection**instance vides **geometry** variables et retourne l’instance **NULL** pour non initialisé **geometry** variables.  
  
 Dépend de l’approximation polygonale que la méthode retourne la **geometry** instance que vous utilisez pour appeler la méthode :  
  
-   Retourne un **LineString** d’instance pour un **CircularString** ou **CompoundCurve** instance.  
  
-   Retourne un **polygone** d’instance pour un **CurvePolygon** instance.  
  
-   Retourne une copie de la **geometry** de l’instance si cette instance n’est pas un **CircularString**, **CompoundCurve**, ou **CurvePolygon** instance. Par exemple, le `STCurveToLine` méthode retourne un **Point** d’instance pour un **geometry** instance qui est un **Point** instance.  
  
 Contrairement à la spécification SQL/MM, la `STCurveToLine` méthode n’utilise pas les valeurs de coordonnée z pour calculer l’approximation polygonale. La méthode ignore toutes les valeurs de coordonnée z présentes dans l’appel **geometry** instance.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-an-uninitialized-geometry-variable-and-empty-instance"></a>A. Utilisation d'une variable Geometry non initialisée et d'une instance vide  
 Dans l’exemple suivant, la première **sélectionnez** instruction utilise un sans être initialisé **geometry** instance pour appeler le `STCurveToLine` (méthode) et le second **sélectionnez** instruction utilise vide **geometry** instance. Par conséquent, la méthode retourne **NULL** à la première instruction et un **GeometryCollection** collection de la deuxième instruction.  
  
```
 DECLARE @g geometry; 
 SET @g = @g.STCurveToLine(); 
 SELECT @g.STGeometryType(); 
 SET @g = geometry::Parse('LINESTRING EMPTY'); 
 SELECT @g.STGeometryType();
 ```  
  
### <a name="b-using-a-linestring-instance"></a>B. Utilisation d'une instance LineString  
 Le **sélectionnez** instruction dans l’exemple suivant utilise un **LineString** instance pour appeler la méthode STCurveToLine. Par conséquent, la méthode retourne un **LineString** instance.  
  
```
 DECLARE @g geometry; 
 SET @g = geometry::Parse('LINESTRING(1 3, 5 5, 4 3, 1 3)'); 
 SET @g = @g.STCurveToLine(); 
 SELECT @g.STGeometryType();
 ```  
  
### <a name="c-using-a-circularstring-instance"></a>C. Utilisation d'une instance CircularString  
 La première **sélectionnez** instruction dans l’exemple suivant utilise un **CircularString** instance pour appeler la méthode STCurveToLine. Par conséquent, la méthode retourne un **LineString** instance. Cela **sélectionnez** instruction compare également les longueurs des deux instances, qui sont approximativement identiques.  Enfin, la seconde **sélectionnez** instruction renvoie le nombre de points pour chaque instance.  Elle retourne uniquement 5 points pour la **CircularString** instance, mais 65 points pour les **LineString**instance.  
  
```
 DECLARE @g1 geometry, @g2 geometry; 
 SET @g1 = geometry::Parse('CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0)'); 
 SET @g2 = @g1.STCurveToLine(); 
 SELECT @g1.STGeometryType() AS [G1 Type], @g2.STGeometryType() AS [G2 Type], @g1.STLength() AS [G1 Perimeter], @g2.STLength() AS [G2 Perimeter], @g2.ToString() AS [G2 Def]; 
 SELECT @g1.STNumPoints(), @g2.STNumPoints();
 ```  
  
### <a name="d-using-a-curvepolygon-instance"></a>D. Utilisation d'une instance CurvePolygon  
 Le **sélectionnez** instruction dans l’exemple suivant utilise un **CurvePolygon** instance pour appeler la méthode STCurveToLine. Par conséquent, la méthode retourne un **polygone** instance.  
  
```
 DECLARE @g1 geometry, @g2 geometry; 
 SET @g1 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0))'); 
 SET @g2 = @g1.STCurveToLine(); 
 SELECT @g1.STGeometryType() AS [G1 Type], @g2.STGeometryType() AS [G2 Type];
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des types de données spatiales](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [STLength &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)   
 [STNumPoints &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stnumpoints-geometry-data-type.md)   
 [STGeometryType &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)  
  
  


