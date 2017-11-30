---
title: "Référence des opérateurs MDX (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], operators
- operators [MDX]
- MDX [Analysis Services], operators
ms.assetid: 1cdb8c31-a5f6-4430-b509-f81344f4622a
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: ddbddfefdaf6b51cbd9cc60eb9111a6c07cfaac8
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="mdx-operator-reference-mdx"></a>Référence des opérateurs MDX (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Le langage MDX (Multidimensional Expressions) prend en charge des opérateurs arithmétiques, logiques, de comparaison, de jeu, de chaîne et unaires. Le tableau ci-dessous répertorie et décrit les opérateurs pris en charge.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[--&#40; Commentaire &#41; &#40; MDX &#41;](../mdx/comment-mdx-operator-reference.md)|Signale un texte de commentaire inséré par l'utilisateur.|  
|[-&#40; À l’exception de &#41; &#40; MDX &#41;](../mdx/except-mdx-operator.md)|Exécute une opération de jeu qui retourne la différence entre deux jeux, en supprimant les doublons.|  
|[-&#40; Négatif &#41; &#40; MDX &#41;](../mdx/negative-mdx.md)|Exécute une opération unaire qui retourne la valeur négative d'une expression numérique.|  
|[-&#40; Soustraire &#41; &#40; MDX &#41;](../mdx/subtract-mdx.md)|Exécute une opération arithmétique qui soustrait un nombre d'un autre.|  
|[&#42; &#40; Jointure croisée &#41; &#40; MDX &#41;](../mdx/crossjoin-mdx-operator-reference.md)|Exécute une opération de jeu qui retourne le produit croisé de deux jeux.|  
|[&#42; &#40; Multiplier &#41; &#40; MDX &#41;](../mdx/multiply-mdx.md)|Exécute une opération arithmétique qui multiplie deux nombres.|  
|[&#40; division &#41; &#40; MDX &#41;](../mdx/divide-mdx-operator-reference.md)|Exécute une opération arithmétique qui divise un nombre par un autre.|  
|[^ &#40; Alimentation &#41; &#40; MDX &#41;](../mdx/power-mdx.md)|Exécute une opération arithmétique qui élève un nombre à la puissance indiquée par un autre nombre.|  
|[Commentaire &#40; MDX &#41;](../mdx/comment-mdx.md)|Signale un texte de commentaire inséré par l'utilisateur.|  
|[&#40; Commentaire &#41; &#40; MDX &#41;](../mdx/comment-mdx-double-slash.md)|Indique un texte défini par l'utilisateur.|  
|[: &#40; Plage &#41; &#40; MDX &#41;](../mdx/range-mdx.md)|Exécute une opération de jeu qui retourne un jeu naturellement ordonné, dont les extrémités sont représentées par les deux membres spécifiés, entre lesquels figurent les autres membres du jeu.|  
|[+ &#40; Ajouter &#41; &#40; MDX &#41;](../mdx/add-mdx.md)|Exécute une opération arithmétique qui additionne deux nombres.|  
|[+ &#40; Positif &#41; &#40; MDX &#41;](../mdx/positive-mdx.md)|Exécute une opération unaire qui retourne la valeur positive d'une expression numérique.|  
|[+ &#40; Concaténation de chaînes &#41; &#40; MDX &#41;](../mdx/string-concatenation-mdx.md)|Exécute une opération de chaîne qui concatène deux ou plusieurs chaînes de caractères, tuples, ou une combinaison de chaînes et de tuples.|  
|[+ &#40; Union &#41; &#40; MDX &#41;](../mdx/union-mdx-operator-reference.md)|Exécute une opération de jeu qui retourne une union de deux jeux en supprimant les doublons.|  
|[&#60; &#40; Inférieur à &#41; &#40; MDX &#41;](../mdx/less-than-mdx.md)|Exécute une opération de comparaison qui détermine si la valeur d'une expression MDX est inférieure à celle d'une autre expression MDX.|  
|[&#60; = &#40; Inférieur ou égal à &#41; &#40; MDX &#41;](../mdx/less-than-or-equal-to-mdx.md)|Exécute une opération de comparaison qui détermine si la valeur d'une expression MDX est inférieure ou égale à celle d'une autre expression MDX.|  
|[&#60; &#62; &#40; Non égal à &#41; &#40; MDX &#41;](../mdx/not-equal-to-mdx.md)|Exécute une opération de comparaison qui détermine si la valeur d'une expression MDX est différente de celle d'une autre expression MDX.|  
|[= &#40; Égal à &#41; &#40; MDX &#41;](../mdx/equal-to-mdx.md)|Effectue une opération de comparaison qui détermine si la valeur d’une expression MDX est égale à la valeur d’une autre expression MDX.|  
|[&#62; &#40; Supérieur à &#41; &#40; MDX &#41;](../mdx/greater-than-mdx.md)|Effectue une opération de comparaison qui détermine si la valeur d’une expression MDX est supérieure à la valeur d’une autre expression MDX.|  
|[&#62; = &#40; Supérieur ou égal à &#41; &#40; MDX &#41;](../mdx/greater-than-or-equal-to-mdx.md)|Exécute une opération de comparaison qui détermine si la valeur d'une expression MDX est supérieure ou égale à celle d'une autre expression MDX.|  
|[ET &#40; MDX &#41;](../mdx/and-mdx.md)|Effectue une conjonction logique sur deux expressions numériques.|  
|[EST &#40; MDX &#41;](../mdx/is-mdx.md)|Effectue une comparaison logique sur deux expressions d'objet.|  
|[PAS &#40; MDX &#41;](../mdx/not-mdx.md)|Effectue une négation logique sur une expression numérique.|  
|[OU &#40; MDX &#41;](../mdx/or-mdx.md)|Effectue une disjonction logique sur deux expressions numériques.|  
|[XOR &#40; MDX &#41;](../mdx/xor-mdx.md)|Effectue une exclusion logique sur deux expressions numériques.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du langage MDX &#40; MDX &#41;](../mdx/mdx-language-reference-mdx.md)  
  
  
