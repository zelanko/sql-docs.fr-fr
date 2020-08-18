---
description: ToggleDrillState (MDX)
title: ToggleDrillState (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e10c62742e28b69545efac51f70bf9628b43e08d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412903"
---
# <a name="toggledrillstate-mdx"></a>ToggleDrillState (MDX)


  Active ou désactive l'état d'extraction des membres entre les modes d'extraction vers le bas et vers le haut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ToggleDrillState(Set_Expression1,Set_Expression2 [, [RECURSIVE] [,INCLUDE_CALC_MEMBERS] ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Récursive*  
 (Facultatif). Mot clé qui indique une comparaison récursive de jeux. La fonction **ToggleDrillState** est une combinaison des fonctions **DrillupMember** et **DrilldownMember** . La récursivité s’applique uniquement lorsque le membre est dans l’état **DrilldownMember** .  
  
 *Include_calc_members*  
 (Facultatif). Un indicateur spécifiant s'il faut inclure les membres calculés (s'ils existent) au niveau d'exploration.  
  
## <a name="remarks"></a>Notes  
 La fonction **ToggleDrillState** bascule l’état d’exploration de chaque membre du deuxième jeu qui est présent dans le premier jeu. Le premier jeu peut contenir des tuples de n'importe quelle dimensionnalité mais le deuxième jeu doit contenir les membres d'une dimension unique. La fonction **ToggleDrillState** est une combinaison des fonctions **DrillupMember** et **DrilldownMember** . Si le membre, *m*, du deuxième jeu est présent dans le premier jeu et que ce membre est extrait vers le dessous (c’est-à-dire qu’il a un descendant immédiatement après), `DrillupMember(Set_Expression1, {m})` est appliqué au membre ou au tuple dans le premier jeu. Si ce membre *m* est remonté vers le haut (autrement dit, il n’y a aucun descendant de *m* qui suit immédiatement *m*), `DrilldownMember(Set_Expression1, {m}[, RECURSIVE])` est appliqué au premier jeu.  
  
 Si l’indicateur **récursif** facultatif est utilisé, l’exploration vers le haut et l’exploration sont appliquées de manière récursive. Pour plus d’informations sur l’indicateur récursif, consultez les fonctions [DrillupMember](../mdx/drillupmember-mdx.md) et [DrilldownMember](../mdx/drilldownmember-mdx.md) .  
  
 L’interrogation de la propriété XMLA MdpropMdxDrillFunctions vous permet de vérifier le niveau de prise en charge fourni par le serveur pour les fonctions de perçage. Pour plus d’informations, consultez [Propriétés XMLA prises en charge &#40;&#41;XMLA ](https://docs.microsoft.com/analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) .  
  
 Consultez [Journal de base de données : fonctions de jeu MDX : la fonction ToggleDrillState ()](https://go.microsoft.com/fwlink/?LinkId=517759) pour les scénarios et des exemples impliquant cette fonction.  
  
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
  
  
