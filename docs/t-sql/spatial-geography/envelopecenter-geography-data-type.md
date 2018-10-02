---
title: EnvelopeCenter (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- EnvelopeCenter
- EnvelopeCenter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeCenter method
ms.assetid: dee9d807-faad-45b8-b3f3-7e8aa7d07147
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d2f53f6efd0e4c1dbcbbeaccc78fd25fdad0c093
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685367"
---
# <a name="envelopecenter-geography-data-type-"></a>EnvelopeCenter (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne un point qui peut être utilisé comme centre d’un cercle englobant pour l’instance **geography**.  
  
 Pour déterminer le cercle englobant, chaque point dans l'instance est décrit comme un vecteur du centre de la Terre au point sur la surface de la Terre. Le point central du cercle englobant est calculé en faisant la moyenne de tous les vecteurs. Pour les boucles fermées, que ce soit dans une instance **polygon** ou une instance **linestring**, le premier et dernier point est utilisé une seule fois.  
  
 Cette méthode de type de données **geography** prend en charge les instances **FullGlobe** ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EnvelopeCenter( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes   
 Cette méthode retourne un **point**. En cas d’utilisation avec `EnvelopeAngle()`, `EnvelopeCenter()` retourne un cercle englobant d’une instance **geography**.  
  
> [!NOTE]  
>  `EnvelopeCenter()` retourne un cercle englobant pour une instance **geography**, mais il n’est pas garanti que les résultats produisent le cercle englobant minimal. En revanche, la méthode de type de données **geometry** `STEnvelope()` retourne de manière certaine le rectangle englobant minimal quand elle est appliquée à une instance **geometry**.  
  
 Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et les versions ultérieures, retourne le centre du cercle qui représente l’enveloppe de cette instance en tant que **point**. Pour tous les objets volumineux, tels qu'ils sont définis par `EnvelopeAngle()` = 180, `EnvelopeCenter()` retourne (90,0).  
  
 Cette méthode n'est pas précise.  
  
## <a name="examples"></a>Exemples  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';  
SELECT @g.EnvelopeCenter().ToString();  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes étendues sur des instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeAngle &#40;type de données geography&#41;](../../t-sql/spatial-geography/envelopeangle-geography-data-type.md)  
  
  
