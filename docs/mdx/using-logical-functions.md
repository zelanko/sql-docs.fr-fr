---
title: À l’aide de fonctions logiques | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a63d8cb22a8533cf352acb690f87916e2e9d568d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743518"
---
# <a name="using-logical-functions"></a>Utilisation de fonctions logiques


  Une fonction logique exécute une opération ou une comparaison logique sur des objets et des expressions et retourne une valeur booléenne. Les fonctions logiques sont essentielles dans la syntaxe MDX (Multidimensional Expressions) pour déterminer la position d'un membre.  
  
 La fonction logique couramment utilisée est le **IsEmpty** (fonction). Pour plus d’informations sur l’utilisation de la **IsEmpty** , consultez [fonctionne avec des valeurs vides](../mdx/working-with-empty-values.md).  
  
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
  
  
