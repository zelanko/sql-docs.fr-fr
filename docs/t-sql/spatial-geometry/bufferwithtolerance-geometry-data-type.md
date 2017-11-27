---
title: "BufferWithTolerance (Type de données geometry) | Documents Microsoft"
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
- BufferWithTolerance_TSQL
- BufferWithTolerance
dev_langs: TSQL
helpviewer_keywords: BufferWithTolerance (geometry Data Type)
ms.assetid: 7049d37a-3e72-4e93-87a1-c96a6f0e2b99
caps.latest.revision: "31"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a6a932ffe43e978bdc9e06f96cac300d45a035b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="bufferwithtolerance-geometry-data-type"></a>BufferWithTolerance (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un objet géométrique qui représente l’union du point de toutes les valeurs dont la distance d’un **geometry** instance est inférieure ou égale à une valeur spécifiée, permettant ainsi une tolérance spécifiée.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.BufferWithTolerance ( distance, tolerance, relative )  
```  
  
## <a name="arguments"></a>Arguments  
 *distance*  
 Est un **float** expression qui spécifie la distance à partir de la **geometry** instance autour de laquelle calculer la mémoire tampon.  
  
 *tolérance de panne*  
 Est un **float** expression qui spécifie la tolérance de la distance de tampon.  
  
 *La tolérance de panne* fait référence à la variation maximale dans la distance de tampon idéale pour l’approximation linéaire retournée.  
  
 Par exemple, la distance de mémoire tampon idéale d'un point est un cercle, mais elle doit être exprimée de façon à se rapprocher d'un polygone. Plus la tolérance est petite, plus le polygone aura de points, ce qui augmente la complexité du résultat mais décroît l'erreur.  
  
 *relatif*  
 Est un **bits** spécifiant si le *la tolérance de panne* valeur est relatif ou absolu. Si 'TRUE' ou 1, puis la tolérance est relative et est calculée comme étant le produit de la *la tolérance de panne* paramètre et du diamètre du rectangle englobant de l’instance. Si 'FALSE' ou 0, la tolérance est absolue et la *la tolérance de panne* valeur est la variation maximale absolue dans la distance de tampon idéale pour l’approximation linéaire retournée.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="exceptions"></a>Exceptions  
 Le *la tolérance de panne* paramètre doit être supérieure à zéro. Si *la tolérance de panne* < = 0, puis un `System.ArgumentOutOfRangeException` est levée.  
  
> [!NOTE]  
>  Étant donné que *la tolérance de panne* est un **float** type, un `System.Runtime.InteropServices.COMException` peut être levée si la valeur donnée pour la tolérance est très petite en raison de problèmes d’arrondi avec les types à virgule flottante.  
  
## <a name="remarks"></a>Notes  
 Lorsque *distance* > 0, puis un **polygone** ou **MultiPolygon** instance est retournée.  
  
> [!NOTE]  
>  Puisque la distance est un **float**, une valeur extrêmement petite peut être équivalente à zéro dans les calculs. Dans ce cas, une copie de l’appel **geometry** instance est retournée. Consultez [float et real &#40; Transact-SQL &#41; ](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
 Lorsque *distance* = 0, une copie de l’appel **geometry** instance est retournée.  
  
 Lorsque *distance* < 0 puis  
  
-   Vide **GeometryCollection** instance est retournée lorsque les dimensions de l’instance sont 0 ou 1.  
  
-   Une mémoire tampon négative est retournée lorsque les dimensions de l'instance sont de 2 ou plus.  
  
    > [!NOTE]  
    >  Une mémoire tampon négative peut également créer vide **GeometryCollection** instance.  
  
 Une mémoire tampon négative supprime tous les points dans la distance donnée de la limite de la **geometry** instance.  
  
 L’erreur entre la mémoire tampon théorique et la mémoire tampon calculée est max (la tolérance de panne, les extensions \* 1.E-7) où la tolérance est la valeur de la *la tolérance de panne* paramètre. Pour plus d’informations sur les étendues, consultez [référence de méthode de Type de données geometry](http://msdn.microsoft.com/library/d88e632b-6b2f-4466-a15f-9fbef1a347a7).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `Point` et utilise `BufferWithTolerance()` pour obtenir une estimation grossière de la mémoire tampon autour d'elle.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 3)', 0);  
SELECT @g.BufferWithTolerance(1, .5, 0).ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STBuffer &#40; Type de données geometry &#41;](../../t-sql/spatial-geometry/stbuffer-geometry-data-type.md)   
 [Méthodes étendues sur des instances geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

