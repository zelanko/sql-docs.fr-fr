---
title: "CurveToLineWithTolerance (Type de données geography) | Documents Microsoft"
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
- CurveToLineWithTolerance_TSQL
- CurveToLineWithTolerance
dev_langs: TSQL
helpviewer_keywords: CurveToLineWithTolerance method (geography)
ms.assetid: 74369c76-2cf6-42ae-b9cc-e7a051db2767
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 208878805dcf7c812caa1e6fb4f06120431ad803
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="curvetolinewithtolerance-geography-data-type"></a>CurveToLineWithTolerance (type de données geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne une approximation polygonale d’une **geography** instance qui contient les segments d’arc de cercle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.CurveToLineWithTolerance( tolerance, relative )  
```  
  
## <a name="arguments"></a>Arguments  
 *tolerance*  
 Est un **double** expression qui définit l’erreur maximale entre le segment d’arc de cercle d’origine et son approximation linéaire.  
  
 *relative*  
 Est un **bool** expression indiquant s’il faut utiliser une valeur maximale relative pour l’écart. Lorsque la valeur relative est définie sur False (0), une valeur maximale absolue est définie pour l'écart d'une approximation linéaire.  Si la valeur relative est True (1), la tolérance est calculée sous la forme d'un produit du paramètre de tolérance et du diamètre du rectangle englobant pour l'objet spatial.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="exceptions"></a>Exceptions  
 Définition d’une tolérance < = 0 lève une **ArgumentOutOfRange** exception.  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet une valeur de tolérance d’erreur être spécifié pour la résultante **LineString**.  
  
 **CurveToLineWithTolerance** méthode retournera un **LineString** d’instance pour un **CircularString** ou **CompoundCurve** instance et **polygone** d’instance pour un **CurvePolygon** instance.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-different-tolerance-values-on-a-circularstring-instance"></a>A. Utilisation de valeurs de tolérance différentes sur une instance CircularString  
 L’exemple suivant montre comment la définition de la tolérance affecte le `LineString`instance retournée par un `CircularString` instance :  
  
 ```
 DECLARE @g geography;  
 SET @g = geography::Parse('CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 SELECT @g.CurveToLineWithTolerance(0.1,0).STNumPoints(), @g.CurveToLineWithTolerance(0.01, 0).STNumPoints();
```  
  
### <a name="b-using-the-method-on-a-multilinestring-instance-containing-one-linestring"></a>B. Utilisation de la méthode sur une instance MultiLineString qui contient un LineString  
 L'exemple suivant montre ce qui est retourné d'une instance `MultiLineString` qui contient uniquement une instance `LineString` :  
  
 ```
 DECLARE @g geography;  
 SET @g = geography::Parse('MULTILINESTRING((-122.358 47.653, -122.348 47.649))');  
 SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();
 ```  
  
### <a name="c-using-the-method-on-a-multilinestring-instance-containing-multiple-linestrings"></a>C. Utilisation de la méthode sur une instance MultiLineString qui contient plusieurs LineStrings  
 L'exemple suivant montre ce qui est retourné d'une instance `MultiLineString` qui contient plusieurs instances `LineString` :  
  
 ```
 DECLARE @g geography;  
 SET @g = geography::Parse('MULTILINESTRING((-122.358 47.653, -122.348 47.649),(-123.358 47.653, -123.348 47.649))');  
 SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();
 ```  
  
### <a name="d-setting-relative-to-true-for-an-invoking-curvepolygon-instance"></a>D. Définition d'une valeur relative sur True pour appeler une instance CurvePolygon  
 L’exemple suivant utilise un `CurvePolygon` instance pour appeler `CurveToLineWithTolerance()` avec *relatif* défini sur true :  
  
 ```
 DECLARE @g geography = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658), (-122.348 47.658, -122.358 47.658, -122.358 47.653)))';  
 SELECT @g.CurveToLineWithTolerance(.5,1).ToString();
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
