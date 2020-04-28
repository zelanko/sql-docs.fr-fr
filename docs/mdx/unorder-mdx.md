---
title: Non ordonné (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 954a71c8ca2e96d905892d77ff12b7270deded5f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68097258"
---
# <a name="unorder-mdx"></a>Unorder (MDX)


  Supprime tout classement appliqué d'un jeu spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Unorder(Set_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 La fonction **Unorder** supprime tout ordonnancement imposé sur les tuples contenus dans le jeu par toute autre fonction ou instruction, telle que la fonction [Order](../mdx/order-mdx.md) . L’ordre des tuples dans le jeu retourné par la fonction **Unorder** est indéterminé.  
  
 La fonction **Unorder** est utilisée comme indicateur pour l’optimisation des requêtes pour le traitement des ensembles. Si l’ordre des tuples dans un jeu est sans importance pour un calcul ou une requête, l’utilisation de la fonction **Unorder** peut offrir un avantage en matière de performances dans de tels cas. Par exemple, la fonction non [vide (MDX)](../mdx/nonempty-mdx.md) peut être plus performante lorsque l’ensemble fourni à cette fonction n’est pas [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ordonné que si doit conserver l’ordre [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], bien que avec, le processeur de requêtes tente d’exécuter cette fonction automatiquement pour de nombreuses fonctions, telles que **Sum** et **Aggregate**. L’avantage en matière de performances de l’utilisation de la **désordonnancement** est susceptible d’être perceptible sur les jeux de très grande taille composés de millions de tuples.  
  
## <a name="example"></a>Exemple  
 Le pseudo-code suivant présente la syntaxe employée pour cette fonction.  
  
```  
NonEmpty (UnOrder (<set_expression>))  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
