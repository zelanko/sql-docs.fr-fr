---
title: STGeometryN (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeometryN (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryN method
ms.assetid: 53755f69-cd50-475b-b3b8-a1a9157cf03a
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 0955e653c2181cb8004780a8695c06c5c99a593f
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65936866"
---
# <a name="stgeometryn-geography-data-type"></a>STGeometryN (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne l’élément **geography** spécifié dans un **GeometryCollection** ou l’un de ses sous-types. Quand STGeometryN() est utilisé sur un sous-type de **GeometryCollection**, par exemple **MultiPoint** ou **MultiLineString**, cette méthode retourne l’instance **geography** si elle est appelée avec N=1.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STGeometryN ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Expression **int** comprise entre 1 et le nombre d’instances **geography** dans **GeometryCollection**.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne une valeur Null si le paramètre est supérieur au résultat de [STNumGeometries()](../../t-sql/spatial-geography/stnumgeometries-geography-data-type.md), et lève **ArgumentOutOfRangeException** si le paramètre *expression* est inférieur à 1.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée une instance `MultiPoint``geography` et utilise `STGeometryN()` pour rechercher la deuxième instance `geography` de **GeometryCollection**.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STGeometryN(2).ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
