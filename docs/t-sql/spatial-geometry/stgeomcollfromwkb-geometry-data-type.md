---
title: STGeomCollFromWKB (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeomCollFromWKB (geometry Data Type)
- STGeomCollFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STGeomCollFromWKB (geometry Data Type)
ms.assetid: 6c55032c-7f5e-4181-8e67-c0265032db63
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 09e6d37f95832ed2b3e9a51ef351e6f62e464b74
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67950215"
---
# <a name="stgeomcollfromwkb-geometry-data-type"></a>STGeomCollFromWKB (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne une instance **geometrycollection** à partir d’une représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary).
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STGeomCollFromWKB ( 'WKB_geometrycollection' , SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *WKB_geometrycollection*  
 Représentation WKB de l’instance **geometrycollection** à retourner. *WKB_geometrycollection* est une expression **varbinary(max)** .  
  
 *SRID*  
 Expression **int** qui représente le SRID (ID de référence spatiale) de l’instance **geometry** à retourner.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes  
 Le type OGC de l’instance **geometry** retournée par `STGeomCollFromWKB()` a la valeur **GeomCollection**, **MultiPolygon**, **MultiLineString** ou **MultiPoint**, en fonction de l’entrée WKB correspondante.  
  
 Cette méthode lève une exception FormatException si l'entrée n'est pas correctement mise en forme.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise `STGeomCollFromWKB()` pour créer une instance **geometry**.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromWKB(0x0107000000020000000103000000010000000400000000000000000014400000000000001440000000000000244000000000000014400000000000002440000000000000244000000000000014400000000000001440010100000000000000000024400000000000002440, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes geometry statiques de l’OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
