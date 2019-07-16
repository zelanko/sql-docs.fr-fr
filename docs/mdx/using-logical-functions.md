---
title: Utilisation de fonctions logiques | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 723d481bc858d7d1db4a63cbb32ab5614eddbb55
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097168"
---
# <a name="using-logical-functions"></a>Utilisation de fonctions logiques


  Une fonction logique exécute une opération ou une comparaison logique sur des objets et des expressions et retourne une valeur booléenne. Les fonctions logiques sont essentielles dans la syntaxe MDX (Multidimensional Expressions) pour déterminer la position d'un membre.  
  
 La fonction logique la plus couramment utilisée est la **IsEmpty** (fonction). Pour plus d’informations sur l’utilisation de la **IsEmpty** de fonction, consultez [fonctionne avec des valeurs vides](../mdx/working-with-empty-values.md).  
  
 La requête suivante montre comment utiliser le **IsLeaf** et **IsAncestor** fonctions :  
  
 `WITH`  
  
 `//Returns true if the CurrentMember on Calendar is a leaf member, ie it has no children`  
  
 `MEMBER MEASURES.[IsLeafDemo] AS IsLeaf([Date].[Calendar].CurrentMember)`  
  
 `//Returns true if the CurrentMember on Calendar is an Ancestor of July 1st 2001`  
  
 `MEMBER MEASURES.[IsAncestorDemo] AS IsAncestor([Date].[Calendar].CurrentMember, [Date].[Calendar].[Date].&[1])`  
  
 `SELECT{MEASURES.[IsLeafDemo],MEASURES.[IsAncestorDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;syntaxe MDX&#41;](../mdx/functions-mdx-syntax.md)  
  
  
