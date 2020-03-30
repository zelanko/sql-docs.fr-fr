---
title: STInteriorRingN (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STInteriorRingN_TSQL
- STInteriorRingN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STInteriorRingN (geometry Data Type)
ms.assetid: 47310f9f-2cdb-41e0-a6da-7c3cfbf139ac
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 328e77c0a5be561f795d1892512e7a72fd21340a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67950159"
---
# <a name="stinteriorringn-geometry-data-type"></a>STInteriorRingN (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne l’anneau intérieur spécifié d’une instance **Polygongeometry**.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STInteriorRingN ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Expression **int** comprise entre 1 et le nombre d’anneaux intérieurs de l’instance **geometry**.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
 Type OGC (Open Geospatial Consortium) : **LineString**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne **null** si l’instance **geometry** n’est pas un polygone. Cette méthode lève également **ArgumentOutOfRangeException** si l’expression est plus grande que le nombre d’anneaux. Le nombre d’anneaux peut être retourné à l’aide de `STNumInteriorRing``()`.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée une instance `Polygon` et utilise `STInteriorRingN()` pour retourner l’anneau intérieur du polygone en tant que **LineString**.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STInteriorRingN(1).ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

