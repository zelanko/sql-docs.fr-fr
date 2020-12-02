---
description: STDistance (type de données geometry)
title: STDistance (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STDistance_TSQL
- STDistance (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance (geometry Data Type)
ms.assetid: ac815bc7-5342-4cc4-af40-c80a1c4c8b68
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 48ae04bdc272bcb7513fe4c2ac1d474406b4ba04
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "88467364"
---
# <a name="stdistance-geometry-data-type"></a>STDistance (type de données geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Retourne la distance la plus courte entre un point d’une instance **geometry** et un point d’une autre instance **geometry**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STDistance ( other_geometry )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
 *other_geometry*  
 Autre instance **geometry** à partir de laquelle mesurer la distance par rapport à l’instance sur laquelle `STDistance()` est appelé. Si *other_geometry* est un ensemble vide, `STDistance()` retourne une valeur Null.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **float**  
  
 Type de retour CLR : **SqlDouble**  
  
## <a name="remarks"></a>Remarques  
 `STDistance()` retourne toujours une valeur Null si les SRID (ID de référence spatiale) des instances **geometry** ne correspondent pas.  
  
## <a name="examples"></a>Exemples  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 2 0, 2 2, 0 2, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POINT(10 10)', 0);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des index spatiaux](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
