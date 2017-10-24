---
title: "STMLineFromText (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STMLineFromText (geography Data Type)
- STMLineFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STLineFromText method
ms.assetid: 66dfd722-a9bd-45d3-9788-f1946dd23e17
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 42915255ad24454fe8824a73d3080b850b668e12
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stmlinefromtext-geography-data-type"></a>STMLineFromText (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un **geography** instance à partir d’une représentation sous forme de réplication continue en cluster (WKT, Open Geospatial Consortium (OGC) Well-Known Text) augmentée des Z (élévation) et les valeurs M (mesure) apportées par l’instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STMLineFromText ( 'multilinestring_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *multilinestring_tagged_text*  
 Est la représentation WKT de le **geographyMultiLineString** instance à retourner. *multilinestring_tagged_text* est un **nvarchar (max)** expression.  
  
 *SRID*  
 Est un **int** expression représentant les données spatiales ID de référence (SRID) de la **geographyMultiLineString** instance à retourner.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
 Type OGC : **MultiLineString**  
  
## <a name="remarks"></a>Notes  
 Cette méthode lève un **FormatException** si l’entrée n’est pas correctement mise en forme.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `STMLineFromText()` pour créer une instance `geography`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STMLineFromText('MULTILINESTRING ((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes géographiques statiques OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  

