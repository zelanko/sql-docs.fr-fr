---
title: STDistance (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 11/19/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STDistance_TSQL
- STDistance (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance method
ms.assetid: 063d8722-e019-4d3d-8fcf-dbf5325823e7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 45f0b6f9524c4877c669bfec8c5ab7bcfec198bb
ms.sourcegitcommit: 381595e990f2294dbf324ef31071e2dd2318b8dd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74200509"
---
# <a name="stdistance-geography-data-type"></a>STDistance (type de données geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne la distance la plus courte entre un point d’une instance **geography** et un point d’une autre instance **geography**.  
  
> [!NOTE]  
>  `STDistance()` retourne le **LineString** le plus court entre deux types geography. Il s'agit d'une approximation proche de la distance géodésique. L’écart de `STDistance()` sur les modèles terrestres courants par rapport à la distance géodésique exacte ne dépasse pas 0,25 %. Cela évite toute confusion quant aux subtiles différences entre longueur et distance dans les types géodésiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STDistance ( other_geography )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geography*  
 Autre instance **geography** à partir de laquelle mesurer la distance par rapport à l’instance sur laquelle STDistance() est appelé. Si *other_geography* est un ensemble vide, STDistance() retourne une valeur Null.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **float**  
  
 Type de retour CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 Le résultat est exprimé dans l’unité de mesure définie par l’[identificateur de référence spatiale &#40;SRID&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md) de données spatiales.
STDistance() retourne toujours une valeur *Null* si les SRID (ID de référence spatiale) des instances **geography** ne correspondent pas.  
  
> [!NOTE]  
>  Les méthodes du type de données **geography** qui calculent une aire ou une distance retournent des résultats distincts selon le SRID de l’instance utilisée dans la méthode. Pour plus d’informations sur les SRID, consultez [Identificateurs de référence spatiale &#40;SRID&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant trouve la distance entre deux instances **geography**.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SET @h = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
