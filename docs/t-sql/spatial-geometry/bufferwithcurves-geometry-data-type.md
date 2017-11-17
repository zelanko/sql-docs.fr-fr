---
title: "BufferWithCurves (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 06/10/2016
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
dev_langs:
- TSQL
helpviewer_keywords:
- BufferWithCurves method (geometry)
ms.assetid: 8ffaba3f-d2dd-4e57-9f41-3ced9f14b600
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a88ea4010ec1cfd48661b34e990634fe371141f3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="bufferwithcurves-geometry-data-type"></a>BufferWithCurves (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Retourne un **geometry** instance qui représente le jeu de tous les points dont la distance à partir de l’appel **geometry** instance est inférieure ou égale à la *distance* paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.BufferWithCurves ( distance )  
```  
  
## <a name="arguments"></a>Arguments  
 *distance*  
 Est un **float** indiquant la distance maximale qui pointe forment la mémoire tampon peut être à partir de la **geometry** instance.  
  
## <a name="return-types"></a>Types de retour  
Type de retour de SQL Server : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="exceptions"></a>Exceptions  
 Les critères suivants lèveront un **ArgumentException**.  
  
-   Aucun paramètre n’est passé à la méthode, telles que`@g.BufferWithCurves()`  
  
-   Un paramètre non numérique est passé à la méthode, telles que`@g.BufferWithCurves('a')`  
  
-   **NULL** est passé à la méthode, telles que`@g.BufferWithCurves(NULL)`  
  
## <a name="remarks"></a>Notes  
 L'illustration suivante montre un exemple d'une instance géométrique retournée par cette méthode.  
  
 ![BufferedCurve](../../t-sql/spatial-geometry/media/bufferedcurve.gif)
  
 Le tableau suivant affiche les résultats retournés pour différentes valeurs de distance.  
  
|Valeur de distance|Dimensions de type|Type spatial retourné|  
|--------------------|---------------------|---------------------------|  
|distance < 0|Zéro ou un|Vide **GeometryCollection** instance|  
|distance < 0|Deux ou plus|A **CurvePolygon** ou **GeometryCollection** instance avec une mémoire tampon négative. **Remarque :** une mémoire tampon négative peut créer vide **GeometryCollection**|  
|distance = 0|Toutes les dimensions|Copie de l’appel de **geometry** instance|  
|distance > 0|Toutes les dimensions|**CurvePolygon** ou **GeometryCollection** instance|  
  
> [!NOTE]  
>  Étant donné que *distance* est un **float**, une valeur très petite peut être équivalente à zéro dans les calculs. Lorsque cela produit ensuite une copie de l’appel **geometry** instance est retournée. Consultez [float et real &#40; Transact-SQL &#41; ](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
 Une mémoire tampon négative supprime tous les points compris dans la distance donnée de la limite de la géométrie. L'illustration suivante montre une mémoire tampon négative sous la forme d'une zone hachurée plus claire du cercle. Le trait en pointillé représente la limite du polygone d'origine et la ligne continue la limite du polygone obtenu.  
  
 Si un **chaîne** paramètre est passé à la méthode, puis elle sera convertie en un **float** ou il lèvera un `ArgumentException`.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-calling-bufferwithcurves-with-a-parameter-value--0-on-one-dimensional-geometry-instance"></a>A. Appel de BufferWithCurves() avec une valeur de paramètre < 0 sur une instance géométrique unidimensionnelle  
 L'exemple suivant retourne une instance `GeometryCollection` vide :  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(-1).ToString(); 
 ```
  
### <a name="b-calling-bufferwithcurves-with-a-parameter-value--0-on-a-two-dimensional-geometry-instance"></a>B. Appel de BufferWithCurves() avec une valeur de paramètre < 0 sur une instance géométrique bidimensionnelle  
 L'exemple suivant retourne une instance `CurvePolygon` avec une mémoire tampon négative :  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.BufferWithCurves(-1).ToString()
 ```  
  
### <a name="c-calling-bufferwithcurves-with-a-parameter-value--0-that-returns-an-empty-geometrycollection"></a>C. Appel de BufferWithCurves() avec une valeur de paramètre < 0 qui retourne un GeometryCollection vide  
 L’exemple suivant montre ce qui se produit lorsque le *distance* paramètre est égal à -2 :  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.BufferWithCurves(-2).ToString();
 ```  
  
 Cela **sélectionnez** retourne d’instruction`GEOMETRYCOLLECTION EMPTY`  
  
### <a name="d-calling-bufferwithcurves-with-a-parameter-value--0"></a>D. Appel de BufferWithCurves() avec une valeur de paramètre = 0  
 L’exemple suivant retourne une copie de l’appel **geometry** instance :  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(0).ToString();
 ```  
  
### <a name="e-calling-bufferwithcurves-with-a-non-zero-parameter-value-that-is-extremely-small"></a>E. Appel de BufferWithCurves() avec une valeur de paramètre non nulle extrêmement petite  
 L’exemple suivant retourne également une copie de l’appel **geometry** instance :  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 DECLARE @distance float = 1e-20; 
 SELECT @g.BufferWithCurves(@distance).ToString();
 ```  
  
### <a name="f-calling-bufferwithcurves-with-a-parameter-value--0"></a>F. Appel de BufferWithCurves() avec une valeur de paramètre > 0  
 L'exemple suivant retourne une instance `CurvePolygon` :  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(2).ToString();
 ```  
  
### <a name="g-passing-a-valid-string-parameter"></a>G. Transmission d'un paramètre de chaîne valide  
 L'exemple suivant retourne la même instance `CurvePolygon` qu'indiqué précédemment, mais un paramètre de chaîne est passé à la méthode :  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves('2').ToString();
 ```  
  
### <a name="h-passing-an-invalid-string-parameter"></a>H. Transmission d'un paramètre de chaîne non valide  
 L'exemple suivant génère une erreur :  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)' 
 SELECT @g.BufferWithCurves('a').ToString();
 ```  
  
 Notez que les deux exemples précédents ont passé un littéral de chaîne à la méthode `BufferWithCurves()`. Le premier exemple fonctionne car le littéral de chaîne peut être converti en valeur numérique. Toutefois, le deuxième exemple lève un `ArgumentException`.  
  
### <a name="i-calling-bufferwithcurves-on-multipoint-instance"></a>I. Appel de BufferWithCurves() sur l'instance MultiPoint  
 L'exemple suivant retourne deux instances `GeometryCollection` et une instance `CurvePolygon` :  
  
```
 DECLARE @g geometry = 'MULTIPOINT((1 1),(1 4))'; 
 SELECT @g.BufferWithCurves(1).ToString(); 
 SELECT @g.BufferWithCurves(1.5).ToString(); 
 SELECT @g.BufferWithCurves(1.6).ToString();
 ```  
  
 Les deux premières **sélectionnez** instructions retournent un `GeometryCollection` de l’instance, car le paramètre *distance* est inférieure ou égale à 1/2 la distance entre les deux points (1 1) et (1 4). La troisième **sélectionnez** instruction retourne un `CurvePolygon` de l’instance, car les instances mises en mémoire tampon des deux points (1 1) et (1 4) se chevauchent.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances géométriques](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
 

