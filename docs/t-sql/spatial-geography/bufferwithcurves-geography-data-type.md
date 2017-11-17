---
title: "BufferWithCurves (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 08/11/2017
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
- BufferWithCurves
- BufferWithCurves_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- BufferWithCurves method (geography)
ms.assetid: abf0a11c-c99c-4faa-bf80-3ae8e04d7bfb
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 80f16777999a029e1063305a0d1b8501af7e05d7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="bufferwithcurves-geography-data-type"></a>BufferWithCurves (type de données geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne un **geography** instance qui représente le jeu de tous les points dont la distance à partir de l’appel **geography** instance est inférieure ou égale à la *distance* paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.BufferWithCurves ( distance )  
```  
  
## <a name="arguments"></a>Arguments  
 *distance*  
 Est un **float** indiquant la distance maximale qui pointe forment la mémoire tampon peut être de l’instance géographique.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="exceptions"></a>Exceptions  
 Les critères suivants lèveront un **ArgumentException**.  
  
-   Aucun paramètre n'est passé à la méthode, telle que `@g.BufferWithCurves()`  
  
-   Un paramètre non numérique est passé à la méthode, telle que `@g.BufferWithCurves('a')`  
  
-   **NULL** est passé à la méthode, telles que`@g.BufferWithCurves(NULL)`  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant affiche les résultats retournés pour différentes valeurs de distance.  
  
|Valeur de distance|Dimensions de type|Type spatial retourné|  
|--------------------|---------------------|---------------------------|  
|distance < 0|Zéro ou un|Vide **GeometryCollection** instance|  
|distance \< 0|Deux ou plus|A **CurvePolygon** ou **GeometryCollection** instance avec une mémoire tampon négative.<br /><br /> Remarque : Une mémoire tampon négative peut créer vide **GeometryCollection**|
|distance = 0|Toutes les dimensions|Copie de l’appel de **geography** instance|  
|distance > 0|Toutes les dimensions|**CurvePolygon** ou **GeometryCollection** instance|  
  
> [!NOTE]  
>  Étant donné que *distance* est un **float**, une valeur très petite peut être équivalente à zéro dans les calculs.  Lorsque cela se produit, puis une copie de l’appel **geography** instance est retournée.  
  
 Si un **chaîne** paramètre est passé à la méthode, puis elle sera convertie en un **float** ou il lèvera un `ArgumentException`.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-calling-bufferwithcurves-with-a-parameter-value--0-on-one-dimensional-geography-instance"></a>A. Appel de BufferWithCurves() avec une valeur de paramètre < 0 sur instance géographique unidimensionnelle  
 L'exemple suivant retourne une instance `GeometryCollection` vide :  
  
 ```sql
 DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves(-1).ToString();
``` 
  
### <a name="b-calling-bufferwithcurves-with-a-parameter-value--0-on-a-two-dimensional-geography-instance"></a>B. Appel de BufferWithCurves() avec une valeur de paramètre < 0 sur une instance géographique bidimensionnelle  
 L'exemple suivant retourne une instance `CurvePolygon` avec une mémoire tampon négative :  
  
 ```sql
 DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.BufferWithCurves(-1).ToString()
 ```  
  
### <a name="c-calling-bufferwithcurves-with-a-parameter-value--0-that-returns-an-empty-geometrycollection"></a>C. Appel de BufferWithCurves() avec une valeur de paramètre < 0 qui retourne un GeometryCollection vide  
 L’exemple suivant montre ce qui se produit lorsque le *distance* paramètre est égal à -2 :  
  
 ```sql
 DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.BufferWithCurves(-2).ToString();
 ```  
  
 Cela **sélectionnez** retourne d’instruction`GEOMETRYCOLLECTION EMPTY`  
  
### <a name="d-calling-bufferwithcurves-with-a-parameter-value--0"></a>D. Appel de BufferWithCurves() avec une valeur de paramètre = 0  
 L’exemple suivant retourne une copie de l’appel **geography** instance :  

 ```sql
 DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves(0).ToString();
 ```  
  
### <a name="e-calling-bufferwithcurves-with-a-non-zero-parameter-value-that-is-extremely-small"></a>E. Appel de BufferWithCurves() avec une valeur de paramètre non nulle extrêmement petite  
 L’exemple suivant retourne également une copie de l’appel **geography** instance :  

 ```sql
 DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @distance float = 1e-20;  
 SELECT @g.BufferWithCurves(@distance).ToString();
 ```  
  
### <a name="f-calling-bufferwithcurves-with-a-parameter-value--0"></a>F. Appel de BufferWithCurves() avec une valeur de paramètre > 0  
 L'exemple suivant retourne une instance `CurvePolygon` :  

 ```sql
 DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves(2).ToString();
 ```  
### <a name="g-passing-a-valid-string-parameter"></a>G. Transmission d'un paramètre de chaîne valide  
 L'exemple suivant retourne la même instance `CurvePolygon` qu'indiqué précédemment, mais un paramètre de chaîne est passé à la méthode :  

 ```sql
 DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves('2').ToString();
```  
  
### <a name="h-passing-an-invalid-string-parameter"></a>H. Transmission d'un paramètre de chaîne non valide  
 L'exemple suivant génère une erreur :  

 ```sql
 DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)'  
 SELECT @g.BufferWithCurves('a').ToString();
 ```  
  
 Notez que les deux exemples précédents ont passé un littéral de chaîne à la méthode `BufferWithCurves()`. Le premier exemple fonctionne car le littéral de chaîne peut être converti en valeur numérique. Toutefois, le deuxième exemple lève un `ArgumentException`.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [BufferWithCurves &#40; Type de données geometry &#41;](../../t-sql/spatial-geometry/bufferwithcurves-geometry-data-type.md)  
  
  

