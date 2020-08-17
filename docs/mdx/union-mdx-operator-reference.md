---
description: Référence des opérateurs Union-MDX
title: + UE (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 84e6bc2b6b8460b90013ade5f0981af7f0ed8432
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341188"
---
# <a name="union---mdx-operator-reference"></a>Référence des opérateurs Union-MDX


  Exécute une opération de jeu qui retourne une union de deux jeux en supprimant les membres dupliqués.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set_Expression + Set_Expression      
```  
  
#### <a name="parameters"></a>Paramètres  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="return-value"></a>Valeur de retour  
 Jeu contenant les membres des deux jeux spécifiés.  
  
## <a name="remarks"></a>Notes  
 L’opérateur **+ (Union)** est fonctionnellement équivalent à l' [Union &#40;fonction MDX&#41;](../mdx/union-mdx.md) .  
  
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
 [Référence des opérateurs MDX &#40;&#41;MDX ](../mdx/mdx-operator-reference-mdx.md)  
  
  
