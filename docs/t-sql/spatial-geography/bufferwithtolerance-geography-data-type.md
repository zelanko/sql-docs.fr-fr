---
title: "BufferWithTolerance (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- BufferWithTolerance_TSQL
- BufferWithTolerance
dev_langs:
- TSQL
helpviewer_keywords:
- BefferWithTolerance method
ms.assetid: f1783e6b-0f17-464f-b1c7-1c3f7d8aa042
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: feaa401cfd6e2077035d164412941392412011ae
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="bufferwithtolerance-geography-data-type"></a>BufferWithTolerance (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne un objet géométrique qui représente l’union du point de toutes les valeurs dont la distance d’un **geography** instance est inférieure ou égale à une valeur spécifiée, permettant ainsi une tolérance spécifiée.  
  
 Ces données geography type prend en charge de la méthode **FullGlobe** instances ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.BufferWithTolerance ( distance, tolerance, relative )  
```  
  
## <a name="arguments"></a>Arguments  
 *distance*  
 Est un **float** expression qui spécifie la distance à partir de la **geography** instance autour de laquelle calculer la mémoire tampon.  
  
 La distance maximale de la mémoire tampon ne peut pas dépasser 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* circonférence du 1/2 la) ou le globe complet.  
  
 *tolérance de panne*  
 Est un **float** expression qui spécifie la tolérance de la distance de tampon.  
  
 Le *la tolérance de panne* valeur fait référence à la variation maximale dans la distance de tampon idéale pour l’approximation linéaire retournée.  
  
 Par exemple, la distance de mémoire tampon idéale d'un point est un cercle, mais elle doit être exprimée de façon à se rapprocher d'un polygone. Plus la tolérance est petite, plus le polygone aura de points, ce qui augmente la complexité du résultat mais décroît l'erreur.  
  
 La limite minimum est de 0,1 pour cent de la distance, plus toute tolérance inférieure à la valeur qui sera arrondie à la limite minimale.  
  
 *relatif*  
 Est un **bits** spécifiant si le *la tolérance de panne* valeur est relatif ou absolu. Si 'TRUE' ou 1, la tolérance est relative et est calculée comme étant le produit de la *la tolérance de panne* paramètre et l’étendue angulaire \* rayon équatorial de l’ellipsoïde. Si 'FALSE' ou 0, la tolérance est absolue et la *la tolérance de panne* valeur est la variation maximale absolue dans la distance de tampon idéale pour l’approximation linéaire retournée.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Cette méthode lève un **ArgumentException** si le *distance* n’est pas un nombre (NAN), ou si *distance* est l’infini positif ou négatif.  Cette méthode lève également une **ArgumentException** si *la tolérance de panne* est zéro (0), pas un nombre (NaN), un infini négative ou positive ou négative.  
  
 `STBuffer()`Retourne un **FullGlobe** instance dans certains cas ; par exemple, `STBuffer()` retourne un **FullGlobe** instance sur deux pôles lorsque la distance de tampon est supérieure à la distance à partir de l’Équateur jusqu’aux pôles.  
  
 Cette méthode lève un **ArgumentException** dans **FullGlobe** instances où la distance de la mémoire tampon dépasse la limitation suivante :  
  
 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* circonférence du 1/2 la)  
  
 L’erreur entre la mémoire tampon théorique et la mémoire tampon calculée est max (la tolérance de panne, les extensions \* 1.E-7) où la tolérance est la valeur de la *la tolérance de panne* paramètre. Pour plus d’informations sur les étendues, consultez [référence de méthode de Type de données geography](http://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e).  
  
 Cette méthode n'est pas précise.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `Point` et utilise `BufferWithTolerance()` pour obtenir une estimation grossière de la mémoire tampon autour d'elle.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.BufferWithTolerance(1, .5, 0).ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STBuffer &#40; Type de données geography &#41;](../../t-sql/spatial-geography/stbuffer-geography-data-type.md)   
 [Méthodes étendues sur les Instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  

