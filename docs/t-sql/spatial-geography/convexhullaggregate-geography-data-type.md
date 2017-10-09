---
title: "ConvexHullAggregate (Type de données geography) | Documents Microsoft"
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
- ConvexHullAggregate_TSQL
- ConvexHullAggregate
dev_langs:
- TSQL
helpviewer_keywords:
- ConvexHullAggregate method (geography)
ms.assetid: 21784c66-2725-471b-9e2d-a8c2e3695197
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5a2f112e58838c754b946bdf3870fea31125a813
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="convexhullaggregate-geography-data-type"></a>ConvexHullAggregate (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne une forme convexe pour un ensemble donné de **geography** objets.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ConvexHullAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Arguments  
 *geography_operand*  
 Est un **geography** colonne de table de type qui représente un ensemble de **geography** objets.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
## <a name="exception"></a>Exception  
 Lève un `FormatException` en présence de valeurs d'entrée qui ne sont pas valides. Consultez [STIsValid &#40; Type de données geography &#41;](../../t-sql/spatial-geography/stisvalid-geography-data-type.md)  
  
## <a name="remarks"></a>Notes  
 Méthode renvoie **null** lorsque l’entrée est vide ou l’entrée a des SRID différents. Consultez [identificateurs de référence spatiale &#40; SRID &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 Méthode ignore **null** entrées.  
  
> [!NOTE]  
>  Méthode renvoie **null** si toutes les valeurs entrées sont **null**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne une forme convexe du jeu de **geography** objets.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT geography::ConvexHullAggregate(SpatialLocation).ToString() AS SpatialLocation  
 FROM Person.Address  
 WHERE City LIKE ('Bothell')
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes géographiques statiques étendues](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  

