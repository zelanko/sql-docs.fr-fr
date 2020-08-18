---
description: Crossjoin-référence des opérateurs MDX
title: '* Crossjoin (MDX) | Microsoft Docs'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c957b72736fa8038f01175e3c65898a85704a56b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88413145"
---
# <a name="crossjoin----mdx-operator-reference"></a>Crossjoin-référence des opérateurs MDX


  Exécute une opération de jeu qui retourne le produit croisé de deux jeux.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set_Expression * Set_Expression  
```  
  
## <a name="parameter"></a>Paramètre  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="return-value"></a>Valeur de retour  
 Jeu contenant le produit croisé des deux paramètres spécifiés.  
  
## <a name="remarks"></a>Notes  
 L’opérateur ** \* (Crossjoin)** est fonctionnellement équivalent à la fonction [CrossJoin](../mdx/crossjoin-mdx.md) .  
  
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
 [Référence des opérateurs MDX &#40;&#41;MDX ](../mdx/mdx-operator-reference-mdx.md)  
  
  
