---
title: "RingN (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- RingN
- RingN_TSQL
dev_langs: TSQL
helpviewer_keywords: RingN method
ms.assetid: 30f47275-2727-4d22-bbec-c0c54bcb3ac2
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dec2dcb3ee06eddc71d0063d6e1de3fd1626858f
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ringn-geography-data-type"></a>RingN (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne l’anneau spécifié de la **geography** instance : `1 ≤ n ≤ NumRings()`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.RingN (expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Est un **int** expression comprise entre 1 et le nombre d’anneaux dans une **polygone** instance.  
  
## <a name="return-value"></a>Valeur retournée  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Si la valeur de l’index d’anneau  **n**  est inférieur à 1, cette méthode lève un **l’exception ArgumentOutOfRangeException.** La valeur d’index en anneau doit être supérieur ou égal à 1 et doit être inférieur ou égal au nombre retourné par `NumRings()`.  
  
## <a name="examples"></a>Exemples  
 Cet exemple crée une instance `Polygon` avec deux anneaux et retourne le deuxième anneau.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.RingN(2).ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [NumRings &#40;type de données geography&#41;](../../t-sql/spatial-geography/numrings-geography-data-type.md)  
  
  
