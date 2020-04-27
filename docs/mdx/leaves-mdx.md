---
title: Feuilles (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d29c77250c23900d74d1969a6c37bc719c89cdd7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905736"
---
# <a name="leaves-mdx"></a>Leaves (MDX)


  Retourne un jeu composé de l'ensemble des attributs (éventuellement limités aux attributs appartenant à une dimension spécifique). Pour chaque attribut x dans le jeu retourné, si x correspond à l'attribut de granularité ou est directement ou indirectement lié à ce dernier, la granularité est définie à l'attribut x sans affecter la tranche. La fonction **sorts** est conçue pour être utilisée dans une instruction Scope ou sur le côté gauche d’une assignation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Leaves( [ Dimension_expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Dimension_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une dimension.  
  
## <a name="remarks"></a>Notes  
 Les membres feuilles sont des tuples formés par la jointure croisée du niveau le plus bas de toutes les hiérarchies d'attribut. Les membres calculés sont exclus.  
  
-   Si un nom de dimension est spécifié, la fonction **sorts** retourne un jeu qui contient les membres feuille de l’attribut de clé pour la dimension spécifiée.  
  
-   Si la dimension est associée à plusieurs groupes de mesures, c'est celle de la mesure dans la portée actuelle qui est utilisée.  
  
-   Si aucun nom de dimension n'est spécifié, la fonction retourne un jeu qui contient les membres feuilles du cube tout entier.  
  
    > [!NOTE]  
    >  Si l'expression de dimension se résout à une hiérarchie et si le nom unique de la hiérarchie est identique au nom unique de la dimension (propriété de dimension de cube HierarchyUniqueNameStyle=ExcludeDimensionName et hierarchyname=dimension name), la dimension est alors utilisée.  
  
    > [!IMPORTANT]  
    >  Une erreur est générée si tous les attributs ne présentent pas la même granularité dans les groupes de mesures de l'étendue actuelle.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
