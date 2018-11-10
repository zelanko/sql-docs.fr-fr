---
title: CircularString | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 9fe06b03-d98c-4337-9f89-54da98f49f9f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 75845ceafbf776eb15a30b3289de97573109c4d8
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018188"
---
# <a name="circularstring"></a>CircularString
  Un `CircularString` est une collection de zéro ou plusieurs segments d'arc de cercle continus. Un segment d'arc de cercle est un segment courbé défini par trois points dans un plan à deux dimensions ; le premier point doit être différent du troisième point. Si les trois points d'un segment d'arc de cercle sont colinéaires, le segment d'arc est traité comme un segment de ligne.  
  
> [!IMPORTANT]  
>  Pour obtenir une description détaillée et des exemples de nouvelles fonctionnalités spatiales introduites dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], y compris le `CircularString` sous-type, téléchargez le livre blanc, [nouvelles fonctionnalités spatiales dans SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=226407).  
  
## <a name="circularstring-instances"></a>Instances CircularString  
 Le dessin suivant montre des instances `CircularString` valides :  
  
 ![](../../database-engine/media/5ff17e34-b578-4873-9d33-79500940d0bc.png "5ff17e34-b578-4873-9d33-79500940d0bc")  
  
### <a name="accepted-instances"></a>Instances acceptées  
 Un `CircularString` instance est acceptée si elle est vide ou contient un nombre impair de points, n, où n > 1. Les instances `CircularString` suivantes sont acceptées.  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';  
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';  
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 2 0, 1 1)';  
```  
  
 `@g3` montre que l'instance `CircularString` peut être acceptée, mais pas valide. La déclaration suivante d'instance de CircularString n'est pas acceptée. Cette déclaration lève une `System.FormatException`.  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1)';  
```  
  
### <a name="valid-instances"></a>Instances valides  
 Une instance `CircularString` valide doit être vide ou avoir les attributs suivants :  
  
-   Elle doit contenir au moins un segment d'arc de cercle (autrement dit, voir un minimum de trois points).  
  
-   Le dernier point de terminaison de chaque segment d'arc de cercle de la séquence, à l'exception du dernier segment, doit correspondre au premier point de terminaison du segment suivant dans la séquence.  
  
-   Elle doit comporter un nombre impair de points.  
  
-   Elle ne peut pas se chevaucher sur un intervalle.  
  
-   Bien que les instances `CircularString` puissent contenir des segments de ligne, ces segments de ligne doivent être définis par trois points colinéaires.  
  
 L'exemple suivant montre des instances `CircularString` valides.  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';  
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';  
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1, 0 1)';  
DECLARE @g4 geometry = 'CIRCULARSTRING(1 1, 2 2, 2 2)';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(),@g4.STIsValid();  
```  
  
 Une instance `CircularString` doit contenir au moins deux segments d'arc de cercle pour définir un cercle complet. Une instance `CircularString` ne peut pas utiliser un seul segment d'arc de cercle (tel que (1 1, 3 1, 1 1)) pour définir un cercle complet. Utilisez (1 1, 2 2, 3 1, 2 0, 1 1) pour définir le cercle.  
  
 L'exemple suivant montre des instances CircularString qui ne sont pas valides.  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING(1 1, 2 0, 1 1)';  
DECLARE @g2 geometry = 'CIRCULARSTRING(0 0, 0 0, 0 0)';  
SELECT @g1.STIsValid(), @g2.STIsValid();  
```  
  
### <a name="instances-with-collinear-points"></a>Instances avec des points colinéaires  
 Dans les cas suivants un segment d'arc de cercle sera traité comme un segment de ligne :  
  
-   lorsque les trois points sont colinéaires (par exemple, (1 3, 4 4, 7 5)) ;  
  
-   lorsque le premier point et le point central sont les mêmes, mais que le troisième point est différent (par exemple, (1 3, 1 3, 7 5)) ;  
  
-   lorsque le point central et le dernier point sont les mêmes, mais que le premier point est différent (par exemple, (1 3, 4 4, 4 4)).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-circularstring"></a>A. Instanciation d'une instance géométrique à l'aide d'un CircularString vide  
 Cet exemple indique comment créer une instance `CircularString` vide :  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CIRCULARSTRING EMPTY');  
```  
  
### <a name="b-instantiating-a-geometry-instance-using-a-circularstring-with-one-circular-arc-segment"></a>B. Instanciation d'une instance géométrique à l'aide d'un CircularString avec un segment d'arc de cercle  
 L'exemple suivant indique comment créer une instance `CircularString` avec un segment d'arc de cercle unique (demi-cercle) :  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry:: STGeomFromText('CIRCULARSTRING(2 0, 1 1, 0 0)', 0);  
SELECT @g.ToString();  
```  
  
### <a name="c-instantiating-a-geometry-instance-using-a-circularstring-with-multiple-circular-arc-segments"></a>C. Instanciation d'une instance géométrique à l'aide d'un CircularString avec plusieurs segments d'arc de cercle  
 L'exemple suivant indique comment créer une instance `CircularString` avec plusieurs segments d'arc de cercle (cercle complet) :  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CIRCULARSTRING(2 1, 1 2, 0 1, 1 0, 2 1)');  
SELECT 'Circumference = ' + CAST(@g.STLength() AS NVARCHAR(10));    
```  
  
 Ce code produit la sortie suivante :  
  
```  
Circumference = 6.28319  
```  
  
 Comparez la sortie lorsque `LineString` est utilisé à la place de `CircularString` :  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(2 1, 1 2, 0 1, 1 0, 2 1)', 0);  
SELECT 'Perimeter = ' + CAST(@g.STLength() AS NVARCHAR(10));  
```  
  
 Ce code produit la sortie suivante :  
  
```  
Perimeter = 5.65685  
```  
  
 Notez que la valeur de la `CircularString` exemple est proche de 2∏, qui est la réelle circonférence du cercle.  
  
### <a name="d-declaring-and-instantiating-a-geometry-instance-with-a-circularstring-in-the-same-statement"></a>D. Déclaration et instanciation d'une instance géométrique avec un CircularString dans la même instruction  
 Cet extrait de code indique comment déclarer et instancier une instance `geometry` avec un `CircularString` dans la même instruction :  
  
```tsql  
DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
```  
  
### <a name="e-instantiating-a-geography-instance-with-a-circularstring"></a>E. Instanciation d'une instance géographique avec un CircularString  
 L'exemple suivant indique comment déclarer et instancier une instance `geography` avec un `CircularString` :  
  
```tsql  
DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
```  
  
### <a name="f-instantiating-a-geometry-instance-with-a-circularstring-that-is-a-straight-line"></a>F. Instanciation d'une instance géométrique avec un CircularString qui est une ligne droite  
 L'exemple suivant indique comment créer une instance `CircularString` qui est une ligne droite :  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('CIRCULARSTRING(0 0, 1 2, 2 4)', 0);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des types de données spatiales](spatial-data-types-overview.md)   
 [CompoundCurve](compoundcurve.md)   
 [MakeValid &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type)   
 [MakeValid &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type)   
 [STIsValid &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)   
 [STIsValid &#40;type de données geography&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type)   
 [STLength &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STStartPoint &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)   
 [STEndPoint &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)   
 [STPointN &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)   
 [STNumPoints &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type)   
 [STIsRing &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type)   
 [STIsClosed &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)   
 [STPointOnSurface &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)   
 [LineString](linestring.md)  
  
  
