---
title: "GeomFromGML (type de données geography) | Microsoft Docs"
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
- GeomFromGML_TSQL
- GeomFromGML
dev_langs:
- TSQL
helpviewer_keywords:
- GeomFromGML (geography Data Type)
- GeomFromGML method
ms.assetid: 470d0997-3cb0-4d34-9a45-b332fe432b14
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b71e3d10dd2e6aaaca091a7f37eed48392261f5a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="geomfromgml-geography-data-type"></a>GeomFromGML (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Construit une instance **geography** en fonction d’une représentation du sous-ensemble [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du langage GML (Geography Markup Language).
  
Pour plus d’informations sur le langage GML, consultez les spécifications OGC (Open Geospatial Consortium) suivantes : [OGC Specifications, Geography Markup Language](http://go.microsoft.com/fwlink/?LinkId=93629)
  
Cette méthode de type de données **geography** prend en charge les instances **FullGlobe** ou les instances spatiales qui sont plus grandes qu’un hémisphère.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GeomFromGml ( GML_input, SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *GML_input*  
 Entrée XML à partir de laquelle le GML renverra une valeur.  
  
 *SRID*  
 Expression **int** qui représente le SRID (ID de référence spatiale) de l’instance **geography** à retourner.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes   
 Cette méthode lève **FormatException** si l’entrée n’est pas au format approprié.  
  
 Cette méthode lève **ArgumentException** si l’entrée contient une arête antipodale.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `GeomFromGml()` pour créer une instance `geography`.  
  
```  
DECLARE @g geography;  
DECLARE @x xml;  
SET @x = '<LineString xmlns="http://www.opengis.net/gml"><posList>47.656 -122.36 47.656 -122.343</posList></LineString>';  
SET @g = geography::GeomFromGml(@x, 4326);  
SELECT @g.ToString();  
```  
  
 L'exemple suivant utilise la méthode `GeomFromGml()` pour créer une instance `FullGlobe``geography`.  
  
```  
DECLARE @g geography;  
DECLARE @x xml;  
SET @x = '<FullGlobe xmlns="http://schemas.microsoft.com/sqlserver/2011/geography" />';  
SET @g = geography::GeomFromGml(@x, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes geography statiques étendues](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
