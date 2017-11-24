---
title: '* (Crossjoin) (MDX) | Documents Microsoft'
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '*'
dev_langs: kbMDX
helpviewer_keywords:
- '* (crossjoin operator)'
- crossjoin operator (*)
ms.assetid: e00cb260-0189-4c4e-b3d2-088f4421337b
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e9b5310618070d999d66c83114b6d8a9ae9c1299
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="crossjoin----mdx-operator-reference"></a>Crossjoin - référence des opérateurs MDX
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Exécute une opération de jeu qui retourne le produit croisé de deux jeux.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set_Expression * Set_Expression  
```  
  
## <a name="parameter"></a>Paramètre  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="return-value"></a>Valeur retournée  
 Jeu contenant le produit croisé des deux paramètres spécifiés.  
  
## <a name="remarks"></a>Notes  
 Le  **\* (Crossjoin)** opérateur est fonctionnellement équivalente à la [Crossjoin](../mdx/crossjoin-mdx.md) (fonction).  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
-- This query returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
    [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Gross Profit Margin])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
