---
title: STGeomFromWKB (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeomFromWKB (geometry Data Type)
- STGeomFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STGeomFromWKB (geometry Data Type)
ms.assetid: 6546ddb0-4a5f-46e5-ba04-8007486c95ec
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 769b48c99e59c8bfcf38fa96cd60d6ef11cd3237
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67950144"
---
# <a name="stgeomfromwkb-geometry-data-type"></a>STGeomFromWKB (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne une instance **geometry** à partir d’une représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary).
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STGeomFromWKB ( 'WKB_geometry' , SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *WKB_geometry*  
 Représentation WKB de l’instance **geometry** à retourner. *WKB_geometry* est une expression **varbinary(max)** .  
  
 *SRID*  
 Expression **int** qui représente le SRID (ID de référence spatiale) de l’instance **geometry** à retourner.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes  
 Le type OGC de l’instance **geometry** retournée par `STGeomFromText()` a comme valeur l’entrée WKB correspondante.  
  
 Cette méthode lève **FormatException** si l’entrée n’est pas au format approprié.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise `STGeomFromWKB()` pour créer une instance **geometry**.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STGeomFromWKB(0x010200000003000000000000000000594000000000000059400000000000003440000000000080664000000000008066400000000000806640, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes geometry statiques de l’OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

