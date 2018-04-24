---
title: STPointFromWKB (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STPointFromWKB (geometry Data Type)
- STPointFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STPointFromWKB (geometry Data Type)
ms.assetid: 1157c172-2dc7-4393-bae6-b85406171a34
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ec9b2e6e8306627dfca0613e32bb3c4196e7a78
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="stpointfromwkb-geometry-data-type"></a>STPointFromWKB (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne une instance **geometryPoint** à partir d’une représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary).
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STPointFromWKB ( 'WKB_point' , SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *WKB_point*  
 Représentation WKB de l’instance **geometryPoint** à retourner. *WKB_point* est une expression **varbinary(max)**.  
  
 *SRID*  
 Expression **int** qui représente le SRID (ID de référence spatiale) de l’instance **geometryPoint** à retourner.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
 Type OGC : **Point**  
  
## <a name="remarks"></a>Notes   
 Cette méthode lève **FormatException** si l’entrée n’est pas au format approprié.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `STPointFromWKB()` pour créer une instance `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STPointFromWKB(0x010100000000000000000059400000000000005940, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes geometry statiques de l’OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

