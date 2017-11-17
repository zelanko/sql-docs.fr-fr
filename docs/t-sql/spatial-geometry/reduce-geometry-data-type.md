---
title: "Réduire (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Reduce_TSQL
- Reduce
dev_langs:
- TSQL
helpviewer_keywords:
- Reduce method
ms.assetid: 132184bf-c4d2-4a27-900d-8373445dce2a
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6e74a2a16806741dda7171ec0327b709fb697cb9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="reduce-geometry-data-type"></a>Reduce (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne une approximation de la donnée **geometry** instance générés par l’exécution d’une extension de l’algorithme de Douglas-Peucker sur l’instance avec la tolérance donnée.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.Reduce ( tolerance )  
```  
  
## <a name="arguments"></a>Arguments  
 *tolérance de panne*  
 Est une valeur de type **float**. *la tolérance de panne* est la tolérance à entrer pour l’algorithme d’approximation.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes  
 Pour les types de collection, cet algorithme fonctionne indépendamment sur chaque **geometry** contenus dans l’instance.  
  
 Cet algorithme ne modifie pas **Point** instances.  
  
 Sur **LineString**, **CircularString**, et **CompoundCurve** instances, l’algorithme d’approximation conserve le début et points de terminaison de l’instance d’origine et il rajoute de manière itérative le point à partir de l’instance d’origine qui dévie plus de résultat jusqu'à ce qu’aucun point dévie plus que la tolérance donnée.  
  
 `Reduce()`Retourne un **LineString**, **CircularString**, ou **CompoundCurve** instance **CircularString** instances.  `Reduce()`Retourne un **CompoundCurve** ou **LineString** instance **CompoundCurve** instances.  
  
 Sur **polygone** instances, l’algorithme d’approximation est appliqué indépendamment à chaque anneau. La méthode produira un `FormatException` si retourné **polygone** instance n’est pas valide ; par exemple, un non valide **MultiPolygon** instance est créée si `Reduce()` est appliquée pour simplifier chaque anneau dans l’instance et l’anneaux résultants se chevauchent.  Sur **CurvePolygon** instances avec un anneau extérieur et sans anneau intérieur, `Reduce()` retourne un **CurvePolygon**, **LineString**, ou **Point** instance.  Si le **CurvePolygon** comporte des anneaux intérieurs un **CurvePolygon** ou **MultiPoint** instance est retournée.  
  
 Lorsqu'un segment d'arc de cercle est rencontré, l'algorithme d'approximation vérifie si l'arc peut se rapprocher par sa pression simultanée dans la moitié de la tolérance donnée.  Si la pression simultanée satisfait à ce critère, l'arc circulaire est remplacé dans les calculs par la pression simultanée. S'il ne respecte pas ce critère, l'arc circulaire est conservé et l'algorithme d'approximation est appliqué aux segments restants.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-reduce-to-simplify-a-linestring"></a>A. Utilisation de Reduce() pour simplifier un LineString  
 L'exemple suivant crée une instance `LineString` et utilise `Reduce()` afin de simplifier l'instance.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0, 2 1, 3 0, 4 1)', 0);  
SELECT @g.Reduce(.75).ToString();  
```  
  
### <a name="b-using-reduce-with-varying-tolerance-levels-on-a-circularstring"></a>B. Utilisation de Reduce() avec variation de niveaux de tolérance sur un CircularString  
 L’exemple suivant utilise `Reduce()` avec trois niveaux de tolérance sur un **CircularString** instance :  
  
```
 DECLARE @g geometry = 'CIRCULARSTRING(0 0, 8 8, 16 0, 20 -4, 24 0)'; 
 SELECT @g.Reduce(5).ToString(); 
 SELECT @g.Reduce(15).ToString(); 
 SELECT @g.Reduce(16).ToString();
 ```  
  
 Cet exemple produit la sortie suivante :  
  
 ```
 CIRCULARSTRING (0 0, 8 8, 16 0, 20 -4, 24 0) 
 COMPOUNDCURVE (CIRCULARSTRING (0 0, 8 8, 16 0), (16 0, 24 0)) 
 LINESTRING (0 0, 24 0)
 ```  
  
 Chacune des instances retournées contient les points de terminaison (0 0) et (24 0).  
  
### <a name="c-using-reduce-with-varying-tolerance-levels-on-a-compoundcurve"></a>C. Utilisation de Reduce() avec variation des niveaux de tolérance sur un CompoundCurve  
 L’exemple suivant utilise `Reduce()` avec deux niveaux de tolérance sur un **CompoundCurve** instance :  
  
```
 DECLARE @g geometry = 'COMPOUNDCURVE(CIRCULARSTRING(0 0, 8 8, 16 0, 20 -4, 24 0),(24 0, 20 4, 16 0))';  
 SELECT @g.Reduce(15).ToString();  
 SELECT @g.Reduce(16).ToString();
 ```  
  
 Dans cet exemple, notez que la seconde **sélectionnez** instruction renvoie la **LineString** instance : `LineString(0 0, 16 0)`.  
  
### <a name="showing-an-example-where-the-original-start-and-end-points-are-lost"></a>Affichage d'un exemple où les points de début et de fin d'origine sont perdus  
 L'exemple suivant affiche comment les points de début et de fin d'origine peuvent ne pas être conservés par l'instance résultante. En effet, en conservant le début d’origine et de points de terminaison non valide se traduirait **LineString** instance.  
  
```  
DECLARE @g geometry = 'LINESTRING(0 0, 4 0, 2 .01, 1 0)';  
DECLARE @h geometry = @g.Reduce(1);  
SELECT @g.STIsValid() AS Valid  
SELECT @g.ToString() AS Original, @h.ToString() AS Reduced;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes de géométrie statiques étendues](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  


