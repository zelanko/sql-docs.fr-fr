---
title: STNumGeometries (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STNumGeometries (geometry Data Type)
- STNumGeometries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumGeometries (geometry Data Type)
ms.assetid: 9402b03d-3039-42ca-ac59-f96b7f1a48de
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 3bd050fc07c39dc33781a2c9c1ec09128540f216
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762280"
---
# <a name="stnumgeometries-geometry-data-type"></a>STNumGeometries (type de données geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Retourne le nombre de géométries qui composent une instance **geometry**.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STNumGeometries ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **int**  
  
 Type de retour CLR : **SqlInt32**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne 1 si l’instance **geometry** n’est pas une instance **MultiPoint**, **MultiLineString**, **MultiPolygon** ou **GeometryCollection**, et 0 si l’instance **geometry** est vide.  
  
> [!NOTE]  
>  Si **GeometryCollection** contient des éléments imbriqués vides, `STNumGeometries()` ne retourne pas 0. Bien que les éléments de l’instance **GeometryCollection** soient vides, l’instance elle-même n’est pas un ensemble vide.  
  
  

