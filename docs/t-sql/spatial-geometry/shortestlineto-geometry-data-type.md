---
title: "ShortestLineTo (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: ShortestLineTo method (geometry)
ms.assetid: 39a2d0e4-4f93-4e94-a27e-6ad9537cfe74
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 53d9b061c8007db287f7738349e21f74d3bbbced
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="shortestlineto-geometry-data-type"></a>ShortestLineTo (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Retourne un **LineString** instance avec deux points qui représentent la distance la plus courte entre les deux **geometry** instances. La longueur de la **LineString** instance retournée est la distance entre les deux **geometry** instances.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.ShortestLineTo ( geometry_other )  
```  
  
## <a name="arguments"></a>Arguments  
 *geometry_other*  
 La seconde **geometry** de l’instance qui l’appelle **geometry** instance essaie de déterminer la distance la plus courte.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes  
 La méthode retourne un **LineString** instance avec les points de terminaison sur les bordures des deux planifications **geometry** instances comparées. La longueur de la **LineString** retournée est égale à la distance la plus courte entre les deux **geometry** instances. Vide **LineString** instance est retournée lorsque les deux **geometry** instances croisent.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-calling-shortestlineto-on-non-intersecting-instances"></a>A. Appel de ShortestLineTo() sur des instances qui ne se croisent pas  
 Cet exemple recherche la distance la plus courte entre une instance `CircularString` et une instance `LineString` et retourne l'instance `LineString` qui connecte les deux points :  
  
```
 DECLARE @g1 geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 DECLARE @g2 geometry = 'LINESTRING(-4 7, 7 10, 3 7)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
### <a name="b-calling-shortestlineto-on-intersecting-instances"></a>B. Appel de ShortestLineTo() sur des instances qui se croisent  
 Cet exemple retourne une instance `LineString` vide du fait que l'instance `LineString` croise l'instance `CircularString` :  
  
```
 DECLARE @g1 geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 DECLARE @g2 geometry = 'LINESTRING(0 5, 7 10, 3 7)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [ShortestLineTo &#40; Type de données geography &#41;](../../t-sql/spatial-geography/shortestlineto-geography-data-type.md)  
  
  

