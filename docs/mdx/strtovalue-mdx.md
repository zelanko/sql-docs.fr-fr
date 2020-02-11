---
title: StrToValue (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cad8fec605a56a60cfcc7024739225e474fd42f8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036687"
---
# <a name="strtovalue-mdx"></a>StrToValue (MDX)


  Retourne la valeur numérique spécifiée par une chaîne au format MDX (Multidimensional Expressions).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
StrToValue(MDX_Expression [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Arguments  
 *MDX_Expression*  
 Expression de chaîne valide résolue, directement ou indirectement, à une cellule unique.  
  
## <a name="remarks"></a>Notes  
 La fonction **StrToValue** retourne la valeur numérique spécifiée par l’expression MDX. La fonction **StrToValue** est généralement utilisée avec des fonctions définies par l’utilisateur pour retourner une expression MDX d’une fonction externe à une instruction MDX qui peut être résolue en une cellule unique.  
  
-   En cas d'utilisation de l'indicateur CONSTRAINED, l'expression MDX doit contenir uniquement une valeur scalaire. L'indicateur CONSTRAINED est employé pour réduire les risques d'attaques par injection au travers de la chaîne spécifiée. Si une expression MDX qui ne peut être directement résolue à une valeur scalaire est fournie, l'erreur suivante s'affiche : « Les restrictions imposées par l'indicateur CONSTRAINED dans la fonction STRTOVALUE n'ont pas été respectées ».  
  
-   Si l'indicateur CONSTRAINED n'est pas utilisé, l'expression MDX (Multidimensional Expressions) peut être aussi complexe que vous le souhaitez tant qu'elle est résolue à une expression MDX qui retourne une cellule unique.  
  
> [!NOTE]  
>  Le retour du résultat d'une expression MDX sous forme de valeur numérique peut s'avérer utile si la valeur est stockée sous forme de texte et si vous souhaitez appliquer des opérations arithmétiques aux valeurs retournées.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la fonction **StrToValue** pour retourner le poids de chaque bicyclette sous la forme d’une valeur.  
  
```  
WITH MEMBER Measures.x AS   
StrToValue   
   ([Product].[Product].CurrentMember.Properties ('Weight')  
   ,CONSTRAINED  
   )  
SELECT Measures.x ON 0  
,[Product].[Product].[Product].Members ON 1  
FROM [Adventure Works]  
WHERE [Product].[Product Categories].[Bikes]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
