---
description: STIsSimple (type de données geometry)
title: STIsSimple (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsSimple_TSQL
- STIsSimple (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsSimple (geometry Data Type)
ms.assetid: da8f45d4-4f9c-405d-b883-760eb5344a71
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 51e9f38a40b26ab4ff50c371519ed50e85ae984d
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "88472451"
---
# <a name="stissimple-geometry-data-type"></a>STIsSimple (type de données geometry)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

Retourne 1 si une instance **geometry** est simple, tel que le définit l’OGC (Open Geospatial Consortium). Retourne 0 si une instance **geometry** n’est pas simple.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STIsSimple ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Types de retour
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **bit**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Remarques  
 Pour être simple, une instance **geometry** doit répondre à toutes les exigences suivantes :  
  
-   Chaque graphique de l'instance ne doit pas se croiser lui-même, sauf à ses points de terminaison.  
  
-   Deux graphiques de l'instance ne peuvent se croiser l'un l'autre à un point qui n'est pas dans leurs limites.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `LineString` non simple qui se croise elle-même et utilise `STIsSimple()` pour tester si le `LineString` est simple.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, 2 0)', 0);  
SELECT @g.STIsSimple();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

