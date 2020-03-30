---
title: STMPointFromWKB (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STMPointFromWKB (geography Data Type)
- STMPointFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STPointFromWKB method
ms.assetid: eeb7d806-3cbb-405d-8199-8b82282c53df
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 2e13735c1782c4b2ced2751cbc59d53859516fcb
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68117393"
---
# <a name="stmpointfromwkb-geography-data-type"></a>STMPointFromWKB (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne une instance **geographyMultiPoint** à partir d’une représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary).
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STMPointFromWKB ( 'WKB_multipoint' , SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *WKB_multipoint*  
 Représentation WKB de l’instance **geographyMultiPoint** à retourner. *WKB_multipoint* est une expression **varbinary(max)** .  
  
 *SRID*  
 Expression **int** qui représente le SRID (ID de référence spatiale) de l’instance **geographyMultiPoint** à retourner.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
 Type OGC : **MultiPoint**  
  
## <a name="remarks"></a>Notes  
 Cette méthode lève **FormatException** si l’entrée n’est pas au format approprié.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `STMPointFromWKB()` pour créer une instance `geography`.  
  
```  
DECLARE @g geography;   
SET @g = geography::STMPointFromWKB(0x0104000000020000000101000000D7A3703D0A975EC08716D9CEF7D347400101000000CBA145B6F3955EC08716D9CEF7D34740, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes geography statiques de l’OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
