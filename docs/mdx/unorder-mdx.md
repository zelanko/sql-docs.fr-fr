---
title: Unorder (MDX) | Documents Microsoft
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
- UNORDER
dev_langs:
- kbMDX
helpviewer_keywords:
- Unorder function
ms.assetid: a805df2a-6320-45bc-989f-90e85faf027f
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: e731420697708432c1edd8d66aae1d3c712e579d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="unorder-mdx"></a>Unorder (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Supprime tout classement appliqué d'un jeu spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Unorder(Set_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Le **Unorder** fonction supprime tout classement appliqué aux tuples contenus dans le jeu par toute autre fonction ou instruction, telles que la [ordre](../mdx/order-mdx.md) (fonction). L’ordre des tuples dans le jeu retourné par le **Unorder** fonction est indéterminée.  
  
 Le **Unorder** fonction est utilisée comme indicateur de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour l’optimisation des requêtes pour le traitement de la série. À l’aide de l’ordre des tuples dans un jeu est sans importance pour un calcul ou une requête, le **Unorder** fonction peut améliorer les performances dans de tels cas. Par exemple, le [NonEmpty (MDX)](../mdx/nonempty-mdx.md) fonction il fonctionnera mieux lorsque le jeu fourni pour cette fonction n’est pas ordonné que lorsque [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] doit préserver l’ordre, bien qu’avec [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], le processeur de requêtes tente d’appliquer cette fonction automatiquement pour de nombreuses fonctions, telles que **somme** et **d’agrégation**. L’avantage de l’utilisation de **Unorder** n’est plus susceptible d’être notable sur les très grands jeux de comprenant des millions de tuples.  
  
## <a name="example"></a>Exemple  
 Le pseudo-code suivant présente la syntaxe employée pour cette fonction.  
  
```  
NonEmpty (UnOrder (<set_expression>))  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
