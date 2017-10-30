---
title: ': (Plage) (MDX) | Documents Microsoft'
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ':'
dev_langs:
- kbMDX
helpviewer_keywords:
- ': (range operator)'
- range operator (:)
ms.assetid: f9b36aca-4efd-49b4-9e4f-12914c1b24a6
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b80f453f0553404d1d337e15e9194f7d4b97ccd7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="-range-mdx"></a>: (Plage) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Exécute une opération de jeu qui retourne un jeu naturellement ordonné, dont les extrémités sont représentées par les deux membres spécifiés, entre lesquels figurent les autres membres du jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression : Member_Expression      
```  
  
#### <a name="parameters"></a>Paramètres  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="return-value"></a>Valeur retournée  
 Jeu contenant les membres spécifiés et tous les membres situés entre eux.  
  
## <a name="remarks"></a>Notes  
 Les deux paramètres doivent spécifier des membres situés dans le même niveau et la même hiérarchie d'une dimension donnée. Si les deux paramètres spécifient le même membre, le **: (plage)** renvoie un jeu qui contient uniquement le membre spécifié. Si le premier paramètre est Null, le jeu contient tous les membres du début du niveau du membre spécifié dans le second paramètre jusqu'au dernier membre (inclus) sur le même niveau. Si le second paramètre est Null, le jeu contient tous les membres du membre spécifié dans le premier paramètre jusqu'au dernier membre (inclus) sur le même niveau.  
  
 Cet opérateur de jeu n'a aucun équivalent fonctionnel dans MDX.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
-- This query returns the freight cost per user  
-- for products, averaged by month, for the first quarter.  
With Member [Measures].[Freight Per Customer] as  
 (  
     [Measures].[Internet Freight Cost]  
     /   
     [Measures].[Customer Count]  
)  
  
SELECT   
    {[Ship Date].[Calendar].[Month].&[2004]&[1] : [Ship Date].[Calendar].[Month].&[2004]&[3]} ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Freight Per Customer])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  

