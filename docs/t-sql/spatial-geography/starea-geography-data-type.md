---
title: STArea (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STArea (geography Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea method
ms.assetid: cfc0b0e0-7fde-431a-863f-d13f3b1b1bef
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: acbc28abde35089acbb76af886b1e9a8c27ed9a0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85705264"
---
# <a name="starea-geography-data-type"></a>STArea (type de données geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Retourne la surface d’exposition totale d’une instance **geography**. Les résultats de STArea() sont l’unité de mesure au carré utilisée par l’identificateur de référence spatiale de l’instance **geography**. Par exemple, si le SRID de l’instance est 4326, STArea() retourne les résultats en mètres carrés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>Types de retour  
Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **float**  
  
Type de retour CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
STArea() retourne 0 si l’instance **geography** est vide ou contient uniquement des figures à zéro et une dimension.  
  
> [!NOTE]  
>  Les méthodes du type de données **geography** qui produisent une valeur de retour métrique ont des résultats distincts selon le SRID de l’instance utilisée dans la méthode. Pour plus d’informations sur les SRID, consultez [Identificateurs de référence spatiale &#40;SRID&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Exemples  
L’exemple suivant utilise `STArea()` pour créer une instance `Polygon geography` et calcule la surface du polygone.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STArea();  
```  
  
## <a name="see-also"></a>Voir aussi  
[Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
