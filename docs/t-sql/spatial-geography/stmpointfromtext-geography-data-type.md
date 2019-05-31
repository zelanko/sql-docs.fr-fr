---
title: STMPointFromText (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STMPointFromText (geography Data Type)
- STMPointFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STMPointFromText method
ms.assetid: fe91a9f5-8de6-464e-88db-00650eae79b0
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: cbb07f0854f775d1f4a64bc561b49fb9654dc140
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65936629"
---
# <a name="stmpointfromtext-geography-data-type"></a>STMPointFromText (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne une instance **geography** à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text), à laquelle s’ajoutent les valeurs Z (élévation) et M (mesure) apportées par l’instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STMPointFromText ( 'multipoint_tagged_text', SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *multipoint_tagged_text*  
 Représentation WKT de l’instance **geographyMultiPoint** à retourner. *multipoint_tagged_text* est une expression **nvarchar(max)** .  
  
 *SRID*  
 Expression **int** qui représente le SRID (ID de référence spatiale) de l’instance **geographyMultiPoint** à retourner.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
 Type OGC : **MultiPoint**  
  
## <a name="remarks"></a>Notes  
 Cette méthode lève **FormatException** si l’entrée n’est pas au format approprié.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `STMPointFromText()` pour créer une instance `geography`.  
  
```  
DECLARE @g geography;   
SET @g = geography::STMPointFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes geography statiques de l’OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
