---
title: "EnvelopeCenter (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EnvelopeCenter
- EnvelopeCenter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeCenter method
ms.assetid: dee9d807-faad-45b8-b3f3-7e8aa7d07147
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0638e8793c75ad78aafa12bec1d1f8a3061022c2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="envelopecenter-geography-data-type-"></a>EnvelopeCenter (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne un point qui peut être utilisé comme centre d’un cercle englobant pour le **geography** instance.  
  
 Pour déterminer le cercle englobant, chaque point dans l'instance est décrit comme un vecteur du centre de la Terre au point sur la surface de la Terre. Le point central du cercle englobant est calculé en faisant la moyenne de tous les vecteurs. Pour les boucles fermées, soit dans un **polygone** instance ou un **linestring** de l’instance, le premier et dernier point est utilisé qu’une seule fois.  
  
 Cela **geography** prend en charge de la méthode de type de données **FullGlobe** instances ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EnvelopeCenter( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne un **point**. Lorsqu’il est utilisé avec `EnvelopeAngle()`, `EnvelopeCenter()` retourne un cercle englobant d’un **geography** instance.  
  
> [!NOTE]  
>  `EnvelopeCenter()`Retourne un cercle englobant pour un **geography** instance, mais les résultats ne sont pas garanti pour produire le cercle englobant minimal. En revanche, le **geometry** méthode de type de données `STEnvelope()` est garantie pour retourner le rectangle englobant minimum lorsqu’il est appliqué à un **geometry** instance.  
  
 Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures, retourne le centre du cercle qui représente l’enveloppe de cette instance comme un **point**. Pour tous les objets volumineux, tels qu'ils sont définis par `EnvelopeAngle()` = 180, `EnvelopeCenter()` retourne (90,0).  
  
 Cette méthode n'est pas précise.  
  
## <a name="examples"></a>Exemples  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';  
SELECT @g.EnvelopeCenter().ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeAngle &#40; Type de données geography &#41;](../../t-sql/spatial-geography/envelopeangle-geography-data-type.md)  
  
  

