---
title: "STCurveN (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- STCurveN
- STCurveN_TSQL
dev_langs: TSQL
helpviewer_keywords: STCurveN method (geography)
ms.assetid: 99ef7100-2c4b-4f07-8d66-b343da94b023
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a529bc1e3b818189f86d5e161b344291a975ec2c
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="stcurven-geography-data-type"></a>STCurveN (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la courbe spécifiée d’un **geography** instance qui est un **LineString**, **CircularString**, ou **CompoundCurve**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STCurveN( n )  
```  
  
## <a name="arguments"></a>Arguments  
 *n*  
 Est un **int** expression comprise entre 1 et le nombre de courbes dans le **geography** instance.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="exceptions"></a>Exceptions  
 Si n < 1 une **ArgumentOutOfRangeException** est levée.  
  
## <a name="remarks"></a>Notes  
 **NULL** est retourné lorsque le critère suivant se produit.  
  
-   Le **geography** instance est déclarée, mais n’est pas instanciée  
  
-   Le **geography** instance est vide  
  
-   n est supérieur au nombre de courbes dans le **geography** instance (consultez [STNumCurves &#40; Type de données geography &#41;](../../t-sql/spatial-geography/stnumcurves-geography-data-type.md)  
  
-   La dimension pour le **geography** instance n’est pas égale (consultez [STDimension &#40; Type de données geography &#41;](../../t-sql/spatial-geography/stdimension-geography-data-type.md)  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-stcurven-on-a-circularstring"></a>A. Utilisation de STCurveN() sur un CircularString  
 L’exemple suivant retourne la deuxième courbe dans un **CircularString** instance :  
  
```
 DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 L'exemple retourne.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="b-using-stcurven-on-a-compoundcurve"></a>B. Utilisation de STCurveN() sur un CompoundCurve  
 L’exemple suivant retourne la deuxième courbe dans un **CompoundCurve** instance :  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 L'exemple retourne.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="c-using-stcurven-on-a-compoundcurve-containing-three-circularstrings"></a>C. Utilisation de STCurveN() sur un CompoundCurve qui contient trois CircularStrings  
 L’exemple suivant utilise un **CompoundCurve** instance qui combine trois distinct **CircularString** instances dans la même séquence de courbes que l’exemple précédent :  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE (CIRCULARSTRING (-122.358 47.653, -122.348 47.649, -122.348 47.658), CIRCULARSTRING(-122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 L'exemple retourne.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
 `STCurveN()` retourne les mêmes résultats indépendamment du format de texte WKT utilisé.  
  
### <a name="d-testing-for-validity-before-calling-stcurve"></a>D. Test de validité avant d'appeler STCurve()  
 L’exemple suivant montre comment s’assurer que  *n*  est valide avant d’appeler la méthode STCurveN() :  
  
```
 DECLARE @g geography;  
 DECLARE @n int;  
 SET @n = 2;  
 SET @g = geography::Parse('LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 IF @n >= 1 AND @n <= @g.STNumCurves()  
 BEGIN  
 SELECT @g.STCurveN(@n).ToString();  
 END
  ```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
