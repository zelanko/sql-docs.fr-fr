---
title: ': (Plage) (MDX) | Documents Microsoft'
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: e9ca2a16a74ce772ce7737c6c30581522d6d30f1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="-range-mdx"></a>: (Plage) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
  
