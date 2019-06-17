---
title: Unorder (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3b5e360c8f15eafba2b4565ca41a557c9e1ceda9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63297915"
---
# <a name="unorder-mdx"></a>Unorder (MDX)


  Supprime tout classement appliqué d'un jeu spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Unorder(Set_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Le **Unorder** fonction supprime tout classement appliqué aux tuples contenus dans le jeu par toute autre fonction ou instruction, telles que la [ordre](../mdx/order-mdx.md) (fonction). L’ordre des tuples dans le jeu retourné par la **Unorder** fonction est indéterminée.  
  
 Le **Unorder** fonction est utilisée comme indice pour l’optimisation des requêtes pour le traitement de l’ensemble. À l’aide de l’ordre des tuples dans un jeu est sans importance pour un calcul ou une requête, le **Unorder** fonction peut améliorer les performances dans ce cas. Par exemple, le [NonEmpty (MDX)](../mdx/nonempty-mdx.md) fonction peut-être être plus efficaces lorsque le jeu fourni à cette fonction n’est pas ordonné que lorsque [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] doit préserver l’ordre, bien qu’avec [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], le processeur de requêtes tente d’effectuer Cette fonction automatiquement pour la plupart des fonctions, telles que **somme** et **agrégation**. L’amélioration des performances de l’utilisation de **Unorder** est seulement susceptible d’être notable sur de très grands ensembles comprenant des millions de tuples.  
  
## <a name="example"></a>Exemple  
 Le pseudo-code suivant présente la syntaxe employée pour cette fonction.  
  
```  
NonEmpty (UnOrder (<set_expression>))  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
