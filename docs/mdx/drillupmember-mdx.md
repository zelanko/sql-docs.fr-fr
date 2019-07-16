---
title: DrillupMember (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5dfdec16d20173639cc92a80b1ca546f44b70334
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68049189"
---
# <a name="drillupmember-mdx"></a>DrillupMember (MDX)


  Retourne les membres figurant dans un jeu spécifié qui ne sont pas les descendants des membres figurant dans un second jeu spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DrillupMember(Set_Expression1, Set_Expression2)   
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Le **DrillupMember** fonction retourne un jeu de membres en fonction des membres spécifiés dans le premier jeu qui sont des descendants des membres dans le deuxième jeu. Le premier jeu peut avoir n'importe quelle dimensionnalité mais le deuxième jeu doit contenir un jeu unidimensionnel. L'ordre des membres d'origine dans le premier jeu est conservé. La fonction construit le jeu en incluant uniquement les membres du premier jeu qui sont des descendants immédiats des membres du deuxième jeu. Si l'ancêtre immédiat d'un membre du premier jeu n'est pas présent dans le deuxième jeu, le membre du premier jeu est inclus dans le jeu retourné par cette fonction. Les descendants dans le premier jeu qui précèdent un membre ancêtre du deuxième jeu sont également inclus.  
  
 Le premier jeu peut contenir des tuples au lieu de membres. Descente de tuple est une extension de OLE DB et retourne un jeu de tuples au lieu de membres.  
  
> [!IMPORTANT]  
>  Un membre fait l'objet d'une exploration vers le haut uniquement s'il est aussitôt suivi d'un enfant ou d'un descendant. L’ordre des membres dans le jeu est important pour les deux la fonction d’exploration\* et Drillup\* familles de fonctions. Envisagez d’utiliser le **Hierarchize** (fonction) pour ordonner les membres du premier jeu de manière appropriée.  
  
## <a name="example"></a>Exemple  
 Les trois exemples suivants sont identiques, à l'exception du deuxième jeu. Dans le premier exemple, le deuxième jeu contient le membre United States. Par conséquent, le membre Colorado est exclu du jeu de résultats. C'est un descendant du membre United States.  
  
```  
SELECT DrillUpMember (   
  { [Geography].[Geography].[Country].[Canada]   
   ,[Geography].[Geography].[Country].[United States]   
   ,[Geography].[Geography].[State-Province].[Colorado]   
   ,[Geography].[Geography].[State-Province].[Alberta]   
   ,[Geography].[Geography].[State-Province].[Brunswick]    
 }   
 , {[Geography].[Geography].[Country].[United States]}   
 ) ON 0   
FROM [Adventure Works]  
```  
  
 Le deuxième exemple illustre l'importance de l'ordre dans lequel les membres sont placés. Dans la mesure où **DrillupMember** vers le haut uniquement pour les membres qui sont suivis immédiatement des descendants dans le premier jeu, il effectue une extraction sur le membre Canada. Le membre Canada est séparé de ses descendants par les membres United States et Colorado. Si vous réorganisez les membres afin que le membre Canada soit situé juste au-dessus du membre Alberta, les membres Alberta et Brunswick sont exclus de l'ensemble de lignes.  
  
```  
SELECT DrillUpMember (   
 {  [Geography].[Geography].[Country].[Canada]   
   ,[Geography].[Geography].[Country].[United States]   
   ,[Geography].[Geography].[State-Province].[Colorado]   
   ,[Geography].[Geography].[State-Province].[Alberta]   
   ,[Geography].[Geography].[State-Province].[Brunswick]    
 }   
 , {[Geography].[Geography].[Country].[Canada]}   
 )   
ON 0   
FROM [Adventure Works]  
```  
  
 Troisième exemple montre comment l’utilisation de **Hierarchize** peut atténuer les effets de classement des membres et remonte le membre Canada.  
  
```  
SELECT DrillUpMember (   
 Hierarchize   
  (   
   { [Geography].[Geography].[Country].[Canada]   
    ,[Geography].[Geography].[Country].[United States]   
    ,[Geography].[Geography].[State-Province].[Colorado]   
    ,[Geography].[Geography].[State-Province].[Alberta]   
    ,[Geography].[Geography].[State-Province].[Brunswick]    
   }   
  ), {[Geography].[Geography].[Country].[Canada]}   
 )   
ON 0   
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
