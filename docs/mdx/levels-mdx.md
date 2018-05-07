---
title: Niveaux (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Levels
dev_langs:
- kbMDX
helpviewer_keywords:
- Levels function
ms.assetid: 1a989cc9-8aa8-4ec3-b5e9-795d6fa84983
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 3e50783a6d59315441f76549f32607d17a2100c0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="levels-mdx"></a>Levels (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
### <a name="string"></a>Chaîne  
 L'exemple ci-dessous retourne le niveau Country :  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
