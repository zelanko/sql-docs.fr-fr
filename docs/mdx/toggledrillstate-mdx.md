---
title: ToggleDrillState (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8d027a76a82de3fd82b6c0c81c54ace08167039b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036611"
---
# <a name="toggledrillstate-mdx"></a>ToggleDrillState (MDX)


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
 Le **ToggleDrillState** fonction active ou désactive l’état d’extraction de chaque membre du deuxième jeu est présent dans le premier jeu. Le premier jeu peut contenir des tuples de n'importe quelle dimensionnalité mais le deuxième jeu doit contenir les membres d'une dimension unique. Le **ToggleDrillState** (fonction) est une combinaison de la **DrillupMember** et **DrilldownMember** fonctions. Si le membre, *m*, du deuxième jeu est présent dans le premier jeu, et que ce membre est extrait vers le bas (autrement dit, suivi d’un descendant immédiatement il), puis `DrillupMember(Set_Expression1, {m})` est appliqué au membre ou tuple dans le premier jeu. Si le problème *m* membre est extrait vers le haut (autrement dit, il n’existe aucun descendant de *m* qui suit immédiatement *m*), `DrilldownMember(Set_Expression1, {m}[, RECURSIVE])` est appliqué au premier jeu.  
  
 Si le paramètre facultatif **récursive** indicateur est utilisé, monter et Descendre dans la hiérarchie sont appliquées de manière récursive. Pour plus d’informations sur l’indicateur récursif, consultez le [DrillupMember](../mdx/drillupmember-mdx.md) et [DrilldownMember](../mdx/drilldownmember-mdx.md) fonctions.  
  
 Interrogez la propriété XMLA MdpropMdxDrillFunctions vous permet de vérifier le niveau de prise en charge fournis par le serveur pour les fonctions d’extraction ; consultez [propriétés XMLA prises en charge &#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) pour plus d’informations.  
  
 Consultez [Journal de base de données : Fonctions de jeu MDX : The ToggleDrillState() Function](https://go.microsoft.com/fwlink/?LinkId=517759) pour les scénarios et exemples impliquant cette fonction.  
  
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
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
