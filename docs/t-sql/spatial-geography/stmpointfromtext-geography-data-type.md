---
title: "STMPointFromText (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 07/30/2017
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
- STMPointFromText (geography Data Type)
- STMPointFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STMPointFromText method
ms.assetid: fe91a9f5-8de6-464e-88db-00650eae79b0
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f1ec274b6dcf0fdea1fa86920248d937b241a938
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stmpointfromtext-geography-data-type"></a>STMPointFromText (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un **geography** instance à partir d’une représentation sous forme de réplication continue en cluster (WKT, Open Geospatial Consortium (OGC) Well-Known Text) augmentée des Z (élévation) et les valeurs M (mesure) apportées par l’instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STMPointFromText ( 'multipoint_tagged_text', SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *multipoint_tagged_text*  
 Est la représentation WKT de le **geographyMultiPoint** instance à retourner. *multipoint_tagged_text* est un **nvarchar (max)** expression.  
  
 *SRID*  
 Est un **int** expression représentant les données spatiales ID de référence (SRID) de la **geographyMultiPoint** instance à retourner.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
 Type OGC : **MultiPoint**  
  
## <a name="remarks"></a>Notes  
 Cette méthode lève un **FormatException** si l’entrée n’est pas correctement mise en forme.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `STMPointFromText()` pour créer une instance `geography`.  
  
```  
DECLARE @g geography;   
SET @g = geography::STMPointFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes géographiques statiques OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  

