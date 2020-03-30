---
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
ms.openlocfilehash: 0b91fdde3c6940ffa0a7f2e77591e05578e005c4
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67894916"
---
# <a name="stissimple-geometry-data-type"></a>STIsSimple (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Retourne 1 si une instance **geometry** est simple, tel que le définit l’OGC (Open Geospatial Consortium). Retourne 0 si une instance **geometry** n’est pas simple.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STIsSimple ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **bit**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
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
  
  

