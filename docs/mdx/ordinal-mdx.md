---
title: Ordinal (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b22cc6d5a609f8e1f585ccc1229e0e1cd67e1796
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68055641"
---
# <a name="ordinal-mdx"></a>Ordinal (MDX)


  Retourne la valeur ordinale de base zéro associée à un niveau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Level_Expression.Ordinal   
```  
  
## <a name="arguments"></a>Arguments  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
## <a name="remarks"></a>Notes  
 Le **Ordinal** fonction est souvent utilisée conjointement avec la **IIF** et **CurrentMember** fonctions pour afficher de manière conditionnelle des valeurs différentes à différents niveaux de hiérarchie, selon la position ordinale de chaque cellule spécifique dans le résultat de la requête. Par exemple, vous pouvez utiliser la **Ordinal** (fonction) pour effectuer des calculs à certains niveaux et affiche la valeur par défaut « N/a » à d’autres niveaux.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne le nombre ordinal du niveau Calendar Quarter dans la hiérarchie Calendar.  
  
```  
WITH MEMBER Measures.x AS [Date].[Calendar].[Calendar Quarter].Ordinal  
SELECT Measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
