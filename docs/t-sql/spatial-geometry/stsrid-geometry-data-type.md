---
description: STSrid (type de données geometry)
title: STSrid (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STSrid (geometry Data Type)
- STSrid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STSrid (geometry Data Type)
ms.assetid: 5e0de983-a0fe-48b7-9e08-30588d7271e2
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: e7f66e25e09d02e506da762909ec80ff7a98114e
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "88454229"
---
# <a name="stsrid-geometry-data-type"></a>STSrid (type de données geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  **STSrid** est un entier qui représente l’identificateur de référence spatiale de l’instance.  
  
Cette propriété peut être modifiée.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STSrid  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Types de retour
 Type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **int**  
  
 Type CLR : **SqlInt32**  
  
## <a name="examples"></a>Exemples  
 Le premier exemple crée une instance **geometry** avec la valeur de SRID 13 et utilise `STSrid` pour confirmer le SRID.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0))', 13);  
SELECT @g.STSrid;  
```  
  
 Le deuxième exemple utilise `STSrid` pour modifier la valeur de SRID de l'instance à 23, puis confirme la valeur SRID modifiée.  
  
```  
SET @g.STSrid = 23;  
SELECT @g.STSrid;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STX &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stx-geometry-data-type.md)   
 [STY &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/sty-geometry-data-type.md)   
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

