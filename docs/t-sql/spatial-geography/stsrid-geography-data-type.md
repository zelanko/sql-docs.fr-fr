---
title: STSrid (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STSrid (geography Data Type)
- STSrid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STSrid method
ms.assetid: 6b04f5a7-2e69-4d34-901e-b61ba6ca9c14
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 96a8577d621b9cc8b22e0f3b334b1d9831fdcad7
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65939164"
---
# <a name="stsrid-geography-data-type"></a>STSrid (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **STSrid** est un entier qui représente le SRID (identificateur de référence spatiale) de l’instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STSrid  
```  
  
## <a name="return-types"></a>Types de retour  
 Type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **int**  
  
 Type CLR : **SqlInt32**  
  
## <a name="remarks"></a>Notes  
 Cette propriété peut être modifiée.  
  
## <a name="examples"></a>Exemples  
 Le premier exemple crée une instance `geography` avec la valeur de SRID 4326 (WGS84) et utilise `STSrid` pour confirmer le SRID.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STSrid;  
```  
  
 Le deuxième exemple utilise `STSrid` pour modifier la valeur de SRID de l'instance à 4267 (NAD27), puis confirme la valeur SRID modifiée.  
  
```  
SET @g.STSrid = 4267;  
SELECT @g.STSrid;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)   
 [Identificateurs de référence spatiale &#40;SRID&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
  
