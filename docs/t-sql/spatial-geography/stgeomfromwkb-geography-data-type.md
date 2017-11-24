---
title: "STGeomFromWKB (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STGeomFromWKB_TSQL
- STGeomFromWKB (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: STGeomFromWKB method
ms.assetid: 79d39d88-5440-49a7-9247-190eafce3f4f
caps.latest.revision: "18"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 984271f301a641c72eb8a0eef5f5153ba7bfd5f1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="stgeomfromwkb-geography-data-type"></a>STGeomFromWKB (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un **geography** instance à partir d’une représentation de l’Open Geospatial Consortium (OGC) WKB Well-Known Binary ().
  
Cela **geography** prend en charge de la méthode de type de données **FullGlobe** instances ou les instances spatiales qui sont plus grandes qu’un hémisphère.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STGeomFromWKB ( 'WKB_geography' , SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *WKB_geography*  
 Est la représentation WKB de le **geography** instance à retourner. *WKB_geography* est un **varbinary (max)** expression.  
  
 *SRID*  
 Est un **int** expression représentant les données spatiales ID de référence (SRID) de la **geography** instance à retourner.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Le type OGC de le **geography** instance retournée par `STGeomFromText()` est définie sur l’entrée WKB correspondante.  
  
 Cette méthode lève un **FormatException** si l’entrée n’est pas correctement mise en forme.  
  
 Cette méthode lève **ArgumentException** si l’entrée contient un contour antipode.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `STGeomFromWKB()` pour créer une instance `geography`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromWKB(0x010200000002000000D7A3703D0A975EC08716D9CEF7D34740CBA145B6F3955EC08716D9CEF7D34740, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes geography statiques de l’OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
