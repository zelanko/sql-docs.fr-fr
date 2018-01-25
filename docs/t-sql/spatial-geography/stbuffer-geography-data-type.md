---
title: "STBuffer (Type de données geography) | Documents Microsoft"
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
- STBuffer (geography Data Type)
- STBuffer_TSQL
dev_langs: TSQL
helpviewer_keywords: STBuffer (geography Data Type)
ms.assetid: cb4deab8-642b-44d9-b3d9-85114d64021e
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e6bd49bb41c8db0fa702e97e5ad8316961e7af15
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="stbuffer-geography-data-type"></a>STBuffer (type de données geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne un objet géographique qui représente l’union de tous les points dont la distance d’un **geography** instance est inférieure ou égale à une valeur spécifiée.  
  
 Ces données geography type prend en charge de la méthode **FullGlobe** instances ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STBuffer ( distance )  
```  
  
## <a name="arguments"></a>Arguments  
 *distance*  
 Est une valeur de type **float** (**double** dans le .NET Framework) qui spécifie la distance à partir de la **geography** instance autour de laquelle calculer la mémoire tampon.  
  
 La distance maximale de la mémoire tampon ne peut pas dépasser 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* circonférence du 1/2 la) ou le globe complet.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 STBuffer() calcule une mémoire tampon de la même manière que [BufferWithTolerance](../../t-sql/spatial-geography/bufferwithtolerance-geography-data-type.md), en spécifiant *la tolérance de panne* = ABS (distance) \* .001 et *relatif* = **false**.  
  
 Une mémoire tampon négative supprime tous les points dans la distance donnée de la limite de la **geography** instance.  
  
 `STBuffer()`Retourne un **FullGlobe** instance dans certains cas ; par exemple, `STBuffer()` retourne un **FullGlobe** instance lorsque la distance de tampon est supérieure à la distance à partir de l’Équateur jusqu’aux pôles. Une mémoire tampon ne peut pas dépasser le globe complet.  
  
 Cette méthode lève un **ArgumentException** dans **FullGlobe** instances où la distance de la mémoire tampon dépasse la limitation suivante :  
  
 0,999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* circonférence du 1/2 la)  
  
 La limite de distance maximale permet à la construction de la mémoire tampon d'être aussi flexible que possible.  
  
 L’erreur entre la mémoire tampon théorique et la mémoire tampon calculée est max (la tolérance de panne, les extensions * 1.E-7) où la tolérance de panne = distance \* .001. Pour plus d’informations sur les étendues, consultez [référence de méthode de Type de données geography](http://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée un `LineString``geography` instance. Il utilise ensuite `STBuffer()` pour retourner la région située à une proximité d'un mètre de l'instance.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STBuffer(1).ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [BufferWithTolerance &#40; Type de données geography &#41;](../../t-sql/spatial-geography/bufferwithtolerance-geography-data-type.md)   
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
