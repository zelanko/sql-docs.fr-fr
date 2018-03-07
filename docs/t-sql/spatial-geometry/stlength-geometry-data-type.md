---
title: "STLength (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
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
- STLength_TSQL
- STLength (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STLength (geometry Data Type)
ms.assetid: e34dc620-2a65-4248-b099-fff91830ab98
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4611b911e765135235f06fa656751e6cebd9ea18
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="stlength-geometry-data-type"></a>STLength (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne la longueur totale des éléments dans un **geometry** instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STLength ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **float**  
  
 Type de retour CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 Si un **geometry** instance est fermée, sa longueur est calculée comme la longueur totale autour de l’instance ; la longueur de tout polygone est son périmètre et la longueur d’un point est 0. La longueur d’une **geometrycollection** type est la somme des longueurs de ses **geometry** instances.  
  
 STLength () fonctionne sur LineStrings valide et non valide. Généralement, un LineString n'est pas valide à cause du chevauchement des segments, qui peut être provoqué par des anomalies telles que des traces de longitude GPS inexactes. STLength () ne supprime pas les segments chevauchés ou non valides. Il les inclut dans la valeur de longueur retournée. La méthode MakeValid () peut supprimer les segments chevauchés d'un LineString.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `LineString` et utilise `STLength()` pour déterminer la longueur de l'instance.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

