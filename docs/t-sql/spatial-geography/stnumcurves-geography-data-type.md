---
title: STNumCurves (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STNumCurves
- STNumCurves_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumCurves method (geography)
ms.assetid: e98a56c2-8496-4dfd-9b37-7f3c4ca9b2b5
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 0c4e8a1e2a277d5888603a84a1dcb9f582380e3a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85702499"
---
# <a name="stnumcurves-geography-data-type"></a>STNumCurves (type de données geography)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Retourne le nombre de courbes d’une instance **geography** unidimensionnelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STNumCurves()  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Les types de données spatiales unidimensionnels incluent **LineString**, **CircularString** et **CompoundCurve**. Une instance **geography** unidimensionnelle vide retourne 0.  
  
 `STNumCurves`() fonctionne uniquement sur les types simples. Il ne fonctionne pas avec les collections **geography** telles que **MultiLineString**. **NULL** est retourné quand l’instance **geography** ne correspond pas à un type de données unidimensionnel.  
  
 **Null** est retourné pour les instances **geography** non initialisées.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-stnumcurves-on-a-circularstring-instance"></a>R. Utilisation de STNumCurves() sur une instance CircularString  
 L'exemple suivant indique comment obtenir le nombre de courbes dans une instance `CircularString` :  
  
```
 DECLARE @g geography; 
 SET @g = geography::Parse('CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 SELECT @g.STNumCurves();
 ```  
  
### <a name="b-using-stnumcurves-on-a-compoundcurve-instance"></a>B. Utilisation de STNumCurves() sur une instance CompoundCurve  
 L'exemple suivant utilise `STNumCurves()` pour retourner le nombre de courbes dans une instance `CompoundCurve`.  
  
```
 DECLARE @g geography;  
 SET @g = geography::Parse('COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))');  
 SELECT @g.STNumCurves();
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des types de données spatiales](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
