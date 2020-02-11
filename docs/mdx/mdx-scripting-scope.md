---
title: SCOPE, instruction (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2f355842999b505a97c3387ab9e51d3b651c3b7c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138281"
---
# <a name="mdx-scripting---scope"></a>Écriture de scripts MDX - SCOPE


  Limite l'étendue des instructions MDX (Multidimensional Expressions) spécifiées à un sous-cube spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SCOPE(Subcube_Expression)   
   [ MDX_Statement ]  
END SCOPE  
  
Subcube_Expression ::=(Auxiliary_Subcube [, Auxiliary_Subcube,...n])  
  
Auxiliary_Subcube ::=   
        Limited_Set   
    | Root([dimension_name])   
    | Leaves([dimension_name])  
  
Limited_Set ::=   
        single_tuple   
    | member   
    | Common_Grain_Members   
    | hierarchy.members   
    | level.members   
    | {}   
    | Descendants  
            (  
                  Member  
         , [level  
         [  
            , SELF   
             | AFTER   
                          | BEFORE   
                          | SELF_AND_AFTER   
                          | SELF_AND_BEFORE   
                          | SELF_BEFORE_AFTER   
                          | LEAVES  
                  ]  
            )   
[* <limited set>]  
```  
  
## <a name="arguments"></a>Arguments  
 *Subcube_Expression*  
 Expression de sous-cube MDX valide.  
  
 *MDX_Statement*  
 Instruction MDX valide.  
  
 *Common_Grain_Members*  
 Instruction MDX valide qui évalue les membres qui ont la même granularité.  
  
 *single_tuple*  
 Tuple unique.  
  
## <a name="remarks"></a>Notes  
 L'instruction SCOPE détermine le sous-cube qui sera affecté par l'exécution d'une ou plusieurs instructions MDX. Sauf si une instruction MDX est insérée dans une instruction SCOPE, l'étendue implicite d'une instruction MDX est le cube tout entier.  
  
> [!NOTE]  
>  Les membres cachés sont exposés dans les instructions SCOPE.  
  
 Les instructions SCOPE vont créer des sous-cubes qui exposent les « trous », quel que soit le paramètre de **compatibilité MDX** . Par exemple, l'instruction `Scope( Customer.State.members )` peut inclure les états de pays ou de régions qui n'ont pas d'états, mais dans lesquels des membres d'espace réservés autrement invisibles ont été insérés.  
  
 Les membres calculés et les jeux nommés créés dans le cadre d'une instruction SCOPE ne sont pas affectés par l'instruction SCOPE.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant, extrait du script de calcul MDX de l’exemple de solution Adventure Works, définit l’étendue actuelle en tant que trimestre fiscal de l’année fiscale 2005 et la mesure Sales Amount quota, puis affecte une valeur aux cellules de l’étendue actuelle à l’aide de la fonction **ParallelPeriod** . L’exemple modifie ensuite la portée à l’aide d’une autre instruction SCOPE, puis effectue une autre assignation à l’aide de la fonction [This (MDX)](../mdx/this-mdx.md) .  
  
```  
Scope   
 (   
    [Date].[Fiscal Year].&[2005],  
    [Date].[Fiscal].[Fiscal Quarter].Members,  
    [Measures].[Sales Amount Quota]  
 ) ;     
  
   This = ParallelPeriod                               
          (   
             [Date].[Fiscal].[Fiscal Year], 1,  
             [Date].[Fiscal].CurrentMember   
          ) * 1.35 ;  
  
/*-- Allocate equally to months in FY 2002 -----------------------------*/  
  
  Scope   
  (   
     [Date].[Fiscal Year].&[2002],  
     [Date].[Fiscal].[Month].Members   
  ) ;     
  
    This = [Date].[Fiscal].CurrentMember.Parent / 3 ;     
  
  End Scope ;     
End Scope ;     
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de script MDX &#40;&#41;MDX](../mdx/mdx-scripting-statements-mdx.md)  
  
  
