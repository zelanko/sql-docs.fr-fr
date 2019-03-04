---
title: STArea (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STArea (geography Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea method
ms.assetid: cfc0b0e0-7fde-431a-863f-d13f3b1b1bef
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 299ccb67b03a654a348492f81ea62f086229efab
ms.sourcegitcommit: 01e17c5f1710e7058bad8227c8011985a9888d36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265276"
---
# <a name="starea-geography-data-type"></a>STArea (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne la surface d’exposition totale d’une instance **geography**. Les résultats de STArea() sont l’unité de mesure au carré utilisée par l’identificateur de référence spatiale de l’instance **geography**. Par exemple, si le SRID de l’instance est 4326, STArea() retourne les résultats en mètres carrés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>Types de retour  
Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **float**  
  
Type de retour CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes   
STArea() retourne 0 si l’instance **geography** est vide ou contient uniquement des figures à zéro et une dimension.  
  
> [!NOTE]  
>  Les méthodes du type de données **geography** qui produisent une valeur de retour métrique ont des résultats distincts selon le SRID de l’instance utilisée dans la méthode. Pour plus d’informations sur les SRID, consultez [Identificateurs de référence spatiale &#40;SRID&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Exemples  
L’exemple suivant utilise `STArea()` pour créer une instance `Polygon geography` et calcule la surface du polygone.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STArea();  
```  
  
## <a name="see-also"></a> Voir aussi  
[Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
