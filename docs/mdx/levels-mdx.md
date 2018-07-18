---
title: Niveaux (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6e8edfdc3c6888c34dd789c521bc42c6b919e1a4
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741188"
---
# <a name="levels-mdx"></a>Levels (MDX)


  Retourne le niveau dont la position dans une dimension ou une hiérarchie est spécifiée par une expression numérique ou dont le nom est spécifié par une expression de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Numeric expression syntax  
Hierarchy_Expression.Levels( Level_Number )  
  
String expression syntax  
Hierarchy_Expression.Levels( Level_Name )  
```  
  
## <a name="arguments"></a>Arguments  
 *Hierarchy_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
 *Level_Number*  
 Expression numérique valide qui spécifie un numéro de niveau.  
  
 *Nom_niveau*  
 Expression de chaîne valide qui spécifie un nom de niveau.  
  
## <a name="remarks"></a>Notes  
 Si un numéro de niveau est spécifié, la **niveaux** fonction retourne le niveau associé à la position de base zéro spécifiée.  
  
 Si un nom de niveau est spécifié, la **niveaux** fonction retourne le niveau spécifié.  
  
> [!NOTE]  
>  Utilisez la syntaxe d'une expression de chaîne pour des fonctions définies par l'utilisateur.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants illustrent chacun de la **niveaux** syntaxes de fonction.  
  
### <a name="numeric"></a>Numérique  
 L'exemple ci-dessous retourne le niveau Country :  
  
```  
SELECT [Geography].[Geography].Levels(1) ON 0  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>String  
 L'exemple ci-dessous retourne le niveau Country :  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
