---
description: Ancestor (MDX)
title: Ancêtre (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9e08a0f281a9e48c3416bb00f6ee47322d554d9c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461661"
---
# <a name="ancestor-mdx"></a>Ancestor (MDX)


  Cette fonction retourne l'ancêtre d'un membre spécifié à un niveau ou une distance spécifique du membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Level syntax  
Ancestor(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestor(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
 *Distance*  
 Expression numérique valide qui spécifie la distance depuis le membre spécifié.  
  
## <a name="remarks"></a>Notes  
 Avec la fonction **Ancestor** , vous fournissez la fonction avec une expression de membre MDX, puis vous fournissez soit une expression MDX d’un niveau qui est un ancêtre du membre, soit une expression numérique qui représente le nombre de niveaux au-dessus de ce membre. Avec ces informations, la fonction **ancêtres** retourne le membre ancêtre à ce niveau.  
  
> [!NOTE]  
>  Pour retourner un jeu contenant le membre ancêtre, au lieu du membre ancêtre uniquement, utilisez la fonction [ancêtres &#40;&#41;MDX ](../mdx/ancestors-mdx.md) .  
  
 Si une expression de niveau est spécifiée, la fonction **Ancestor** retourne l’ancêtre du membre spécifié au niveau spécifié. Si le membre spécifié n'apparaît pas dans la même hiérarchie en tant que niveau spécifié, la fonction retourne une erreur.  
  
 Si une distance est spécifiée, la fonction **Ancestor** retourne l’ancêtre du membre spécifié qui est le nombre d’étapes spécifiées dans la hiérarchie spécifiée par l’expression de membre. Vous pouvez spécifier un membre en tant que membre d'une hiérarchie d'attribut, d'une hiérarchie définie par l'utilisateur ou, dans certains cas, d'une hiérarchie parent-enfant. Un nombre 1 retourne le parent d'un membre ; un nombre 2 retourne le grand-parent d'un membre (le cas échéant). Un nombre 0 retourne le membre lui-même.  
  
> [!NOTE]  
>  Utilisez cette forme de la fonction **Ancestor** pour les cas où le niveau du parent est inconnu ou ne peut pas être nommé.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise une expression de niveau et retourne la mesure Internet Sales Amount (volume de vente Internet) pour chaque State-Province (état-Province) en Australie ; il dévoile également le pourcentage de volume de vente Internet total pour l'Australie.  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   (  
   [Measures].[Internet Sales Amount],    
      Ancestor   
         (  
         [Customer].[Customer Geography].CurrentMember,  
            [Customer].[Customer Geography].[Country]  
         )  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{  
   Descendants   
      (  
        [Customer].[Customer Geography].[Country].&[Australia],  
           [Customer].[Customer Geography].[State-Province], SELF   
      )  
} ON 1  
FROM [Adventure Works]  
```  
  
 L'exemple suivant utilise une expression numérique et retourne la mesure Internet Sales Amount (volume de vente Internet) pour chaque State-Province (état-Province) en Australie ; il dévoile également le pourcentage de volume de vente Internet total pour tous les pays.  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   (  
      [Measures].[Internet Sales Amount],  
         Ancestor   
            ([Customer].[Customer Geography].CurrentMember, 2)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{  
   Descendants   
      (  
         [Customer].[Customer Geography].[Country].&[Australia],  
            [Customer].[Customer Geography].[State-Province], SELF   
      )  
} ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
