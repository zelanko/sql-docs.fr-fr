---
title: "IsNull (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IsNull (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull (geometry Data Type)
ms.assetid: f95813a5-26c0-48aa-bfb8-56d2a0980788
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9136a2caf43fea8d5cccd90d8dba85d815511afe
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="isnull-geometry-data-type"></a>IsNull (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Le type d’un **geometry** instance est null. Retourne 0 si l'instance n'est pas NULL.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.IsNull  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type : **bits**  
  
 Type CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
 `IsNull`peut être utilisé pour tester si un **geometry** instance est null. Les résultats peuvent prêter à confusion, la méthode retournant 0 si l'instance n'est pas Null, mais Null si l'instance est Null.  
  
 Cette méthode est utilisée principalement par l'infrastructure SQL Server ; il n'est pas recommandé d'utiliser `IsNull` pour tester si une instance est Null.  
  
## <a name="examples"></a>Exemples  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances géométriques](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  


