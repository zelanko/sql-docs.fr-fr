---
title: ToggleDrillState (MDX) | Documents Microsoft
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
- TOGGLEDRILLSTATE
dev_langs:
- kbMDX
helpviewer_keywords:
- ToggleDrillState function
ms.assetid: 26fa1a0d-3ed1-45dc-955d-0591d49e4db9
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 63b5fb01cac2fe886bce15ded807b8e655d98056
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="toggledrillstate-mdx"></a>ToggleDrillState (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Active ou désactive l'état d'extraction des membres entre les modes d'extraction vers le bas et vers le haut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ToggleDrillState(Set_Expression1,Set_Expression2 [, [RECURSIVE] [,INCLUDE_CALC_MEMBERS] ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Récursive*  
 (Facultatif). Mot clé qui indique une comparaison récursive de jeux. Le **ToggleDrillState** (fonction) est une combinaison de la **DrillupMember** et **DrilldownMember** fonctions. La récursivité s’applique uniquement lorsque le membre est dans le **DrilldownMember** état.  
  
 *Include_calc_members*  
 (Facultatif). Un indicateur spécifiant s'il faut inclure les membres calculés (s'ils existent) au niveau d'exploration.  
  
## <a name="remarks"></a>Notes  
 Le **ToggleDrillState** fonction active ou désactive l’état d’extraction de chaque membre du deuxième jeu est présent dans le premier jeu. Le premier jeu peut contenir des tuples de n'importe quelle dimensionnalité mais le deuxième jeu doit contenir les membres d'une dimension unique. Le **ToggleDrillState** (fonction) est une combinaison de la **DrillupMember** et **DrilldownMember** fonctions. Si le membre, *m*, du deuxième jeu est présent dans le premier jeu, et que ce membre est extrait vers le bas (, qui est un descendant immédiatement), puis `DrillupMember(Set_Expression1, {m})` est appliqué au membre ou tuple dans le premier jeu. Si ce *m* jeu des membres (autrement dit, il n’existe aucun descendant de *m* qui suit immédiatement *m*), `DrilldownMember(Set_Expression1, {m}[, RECURSIVE])` est appliqué au premier jeu.  
  
 Si le paramètre facultatif **récursive** indicateur est utilisé, monter et Descendre sont appliquées de manière récursive. Pour plus d’informations sur l’indicateur récursif, consultez le [DrillupMember](../mdx/drillupmember-mdx.md) et [DrilldownMember](../mdx/drilldownmember-mdx.md) fonctions.  
  
 Interrogez la propriété XMLA MdpropMdxDrillFunctions vous permet de vérifier le niveau de prise en charge par le serveur pour les fonctions d’extraction ; consultez [pris en charge les propriétés XMLA &#40;XMLA&#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) pour plus d’informations.  
  
 Consultez [Journal de base de données : les fonctions MDX définie : The ToggleDrillState() Function](http://go.microsoft.com/fwlink/?LinkId=517759) pour les scénarios et exemples utilisant cette fonction.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous procède à une extraction vers le bas du membre Australia du premier jeu, puis à une extraction vers le haut du membre United States de ce même jeu.  
  
```  
SELECT ToggleDrillState  
   ({[Geography].[Geography].[Country].Members, [Geography].[Geography].[Country].&[United States].Children},  
      {[Geography].[Geography].[Country].[Australia]  
      , [Geography].[Geography].[Country].&[United States]}  
      --, recursive  
      --, include_calc_members  
   ) ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
