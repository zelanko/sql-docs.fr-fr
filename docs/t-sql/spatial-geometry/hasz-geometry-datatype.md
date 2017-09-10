---
title: "HasZ (type de données de géométrie) | Documents Microsoft"
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- HasZ geometry
ms.assetid: aa378943-252a-4079-848b-6c59344fcfce
caps.latest.revision: 6
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5b62dabf472e72accc34e3c554720dba77113528
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="hasz-geometry-datatype"></a>HasZ (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne 1 (true) si un objet spatial contient au moins une valeur Z ; sinon retourne 0 (false).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.HasZ  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **bits**  
  
 Type de retour CLR : **booléenne**  
  
## <a name="remarks"></a>Notes  
  
## <a name="examples"></a>Exemples  
  
```tsql  
DECLARE @p GEOMETRY = 'Point(1 1 1 1)'  
SELECT @p.HasZ   
--Returns: 1 (true)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances géométriques](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [Z &#40; Type de données geometry &#41;](../../t-sql/spatial-geometry/z-geometry-data-type.md)  
  
  

