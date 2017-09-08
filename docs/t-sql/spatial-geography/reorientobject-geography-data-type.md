---
title: "ReorientObject (Type de données geography) | Documents Microsoft"
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
- ReorientObject
- ReorientObject_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ReorientObject method (geography)
ms.assetid: e2a1a4f1-211b-4e82-abed-03fc7140a83c
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3a32dc43776511881697b972c9279d143af917c2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="reorientobject-geography-data-type"></a>ReorientObject (type de données geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne un **geography** instance avec l’échange des régions intérieures et des régions.  
  
 Cela **geography** prend en charge de la méthode de type de données **FullGlobe** instances ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.ReorientObject (geography)  
```  
  
## <a name="arguments"></a>Arguments  
 *geography*  
 Une autre **geography** instance sur laquelle `ReorientObject()` est appelé.  
  
## <a name="return-value"></a>Valeur retournée  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Cette méthode modifie l’orientation d’anneau de tous les **polygones** dans un **GeometryCollection** mais ne supprime ne pas ni ne modifie aucun **Points** ou **Linestrings** dans la collection donnée.  
  
 Si un **GeometryCollection** est passé à cette méthode, chaque instance de la collection est réorientée, mais la collection dans son ensemble n’est pas réorientée dans son intégralitée.  
  
## <a name="examples"></a>Exemples  
  
```  
DECLARE @R GEOGRAPHY = GEOGRAPHY::Parse('Polygon((-10 -10, -10 10, 10 10, 10 -10, -10 -10))');  
SELECT @R.ReorientObject().STAsText();  
--Result: POLYGON ((10 10, -10 10, -10 -10, 10 -10, 10 10))  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
