---
title: "STPointN (type de données geometry) | Microsoft Docs"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STPointN_TSQL
- STPointN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPointN (geometry Data Type)
ms.assetid: 8f0bb3b7-5cd9-42c2-b9f8-f04628653bd0
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 123ce8f5775bff59ff917bf0916f8e37108b9245
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="stpointn-geometry-data-type"></a>STPointN (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un point spécifique dans une instance **geometry**.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STPointN ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Expression **int** comprise entre 1 et le nombre de points de l’instance **geometry**.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
 Type OGC (Open Geospatial Consortium) : **Point**  
  
## <a name="remarks"></a>Notes   
 Si une instance **geometry** est créée par l’utilisateur, `STPointN()` retourne le point spécifié par *expression* en classant les points dans l’ordre dans lequel ils ont été entrés à l’origine.  
  
 Si une instance **geometry** est construite par le système, `STPointN()` retourne le point spécifié par *expression* en classant tous les points dans le même ordre que celui de leur sortie : d’abord par instance geometry, puis par anneau dans l’instance geometry (le cas échéant), puis par point dans l’anneau. Cet ordre est déterministe.  
  
 Si cette méthode est appelée avec une valeur inférieure à 1, elle lève **ArgumentOutOfRangeException**.  
  
 Si cette méthode est appelée avec une valeur supérieure au nombre de points dans l'instance, elle retourne Null.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `LineString` et utilise `STPointN()` pour extraire le deuxième point dans la description de l'instance.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STPointN(2).ToString();  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

