---
title: STNumCurves (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STNumCurves method (geometry)
ms.assetid: 20c2fa0b-656b-4519-b34c-cc8f094290d4
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 1eb57ac476d430d5bc79c71ce5c6a12087155366
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68089000"
---
# <a name="stnumcurves-geometry-data-type"></a>STNumCurves (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Cette méthode retourne le nombre de courbes d’une instance **geometry** quand l’instance est d’un type de données spatiales unidimensionnel. Les types de données spatiales unidimensionnels incluent **LineString**, **CircularString** et **CompoundCurve**. `STNumCurves`() fonctionne uniquement sur les types simples. Il ne fonctionne pas avec les collections **geometry** telles que **MultiLineString**.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STNumCurves()  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes  
 Une instance **geometry** unidimensionnelle vide retourne 0. **NULL** est retourné quand l’instance **geometry** n’est pas une instance unidimensionnelle ou une instance initialisée.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-stnumcurves-on-a-circularstring-instance"></a>R. Utilisation de STNumCurves() sur une instance CircularString  
 L'exemple suivant indique comment obtenir le nombre de courbes dans une instance `CircularString` :  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0)');  
 SELECT @g.STNumCurves();
 ```  
  
### <a name="b-using-stnumcurves-on-a-compoundcurve-instance"></a>B. Utilisation de STNumCurves() sur une instance CompoundCurve  
 L'exemple suivant utilise `STNumCurves()` pour retourner le nombre de courbes dans une instance `CompoundCurve`.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0))');  
 SELECT @g.STNumCurves();
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des types de données spatiales](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

