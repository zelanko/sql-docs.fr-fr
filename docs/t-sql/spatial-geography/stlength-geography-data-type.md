---
title: "STLength (Type de données geography) | Documents Microsoft"
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
- STLength (geography Data Type)
- STLength_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STLength method
ms.assetid: 774560ab-4a4a-4058-b043-1e67cf6fb9eb
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2f5b7a075d562731f986c0f85db505c81315acbd
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="stlength-geography-data-type"></a>STLength (type de données geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne la longueur totale des éléments dans un **geography** instance ou la **geography** instances au sein d’un **GeometryCollection**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STLength ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **float**  
  
 Type de retour CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 Si un **geography** instance est fermée, sa longueur est calculée comme la longueur totale autour de l’instance ; la longueur de tout polygone est son périmètre et la longueur d’un point est 0. La longueur d’un **GeometryCollection** est déterminée en calculant la somme des longueurs de toutes les **geography** instances contenues dans la collection.  
  
 STLength () fonctionne sur LineStrings valide et non valide. Généralement, un LineString n'est pas valide à cause du chevauchement des segments, qui peut être provoqué par des anomalies telles que des traces de longitude GPS inexactes. STLength () ne supprime pas les segments chevauchés ou non valides. Il les inclut dans la valeur de longueur retournée. La méthode MakeValid () peut supprimer les segments chevauchés d'un LineString.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `LineString` et utilise `STLength()` pour déterminer la longueur de l'instance.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
