---
title: + (Union) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: be12a1af53957ab0d8f3347a0464dd987152bca0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63129821"
---
# <a name="union---mdx-operator-reference"></a>Union - référence des opérateurs MDX


  Exécute une opération de jeu qui retourne une union de deux jeux en supprimant les membres dupliqués.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set_Expression + Set_Expression      
```  
  
#### <a name="parameters"></a>Paramètres  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="return-value"></a>Valeur de retour  
 Jeu contenant les membres des deux jeux spécifiés.  
  
## <a name="remarks"></a>Notes  
 Le **+ (Union)** opérateur est fonctionnellement équivalent à la [Union &#40;MDX&#41; ](../mdx/union-mdx.md) (fonction).  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
-- This member returns the gross profit margin for each year for North American countries.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members ON 0,  
    {[Sales Territory].[Sales Territory].[Country].[United States]} +  
     {[Sales Territory].[Sales Territory].[Country].[Canada]} ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Gross Profit Margin])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
