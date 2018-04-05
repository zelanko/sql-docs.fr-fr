---
title: StrToValue (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STRTOVALUE
dev_langs:
- kbMDX
helpviewer_keywords:
- StrToValue function
ms.assetid: 118a9c4f-74a3-48d5-a4f4-318664bc51bc
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 37424120aee0b38303b086019e2fb74a823cdc1b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="strtovalue-mdx"></a>StrToValue (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne la valeur numérique spécifiée par une chaîne au format MDX (Multidimensional Expressions).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
StrToValue(MDX_Expression [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Arguments  
 *MDX_Expression*  
 Expression de chaîne valide résolue, directement ou indirectement, à une cellule unique.  
  
## <a name="remarks"></a>Notes   
 Le **StrToValue** fonction retourne la valeur numérique spécifiée par l’expression MDX. Le **StrToValue** fonction est généralement utilisée avec les fonctions définies par l’utilisateur pour retourner une expression MDX à partir d’une fonction externe vers une instruction MDX qui peut être résolue en une seule cellule.  
  
-   En cas d'utilisation de l'indicateur CONSTRAINED, l'expression MDX doit contenir uniquement une valeur scalaire. L'indicateur CONSTRAINED est employé pour réduire les risques d'attaques par injection au travers de la chaîne spécifiée. Si une expression MDX qui ne peut être directement résolue à une valeur scalaire est fournie, l'erreur suivante s'affiche : « Les restrictions imposées par l'indicateur CONSTRAINED dans la fonction STRTOVALUE n'ont pas été respectées ».  
  
-   Si l'indicateur CONSTRAINED n'est pas utilisé, l'expression MDX (Multidimensional Expressions) peut être aussi complexe que vous le souhaitez tant qu'elle est résolue à une expression MDX qui retourne une cellule unique.  
  
> [!NOTE]  
>  Le retour du résultat d'une expression MDX sous forme de valeur numérique peut s'avérer utile si la valeur est stockée sous forme de texte et si vous souhaitez appliquer des opérations arithmétiques aux valeurs retournées.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant utilise le **StrToValue** fonction pour retourner le poids de chaque bicyclette en tant que valeur.  
  
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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
