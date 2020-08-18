---
description: Guide de référence des opérateurs DMX (Data Mining Extensions)
title: Informations de référence sur les opérateurs DMX (Data Mining Extensions) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ba8f03b86a93122b2dcd9b825adc656feae80cd2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88414295"
---
# <a name="data-mining-extensions-dmx-operator-reference"></a>Guide de référence des opérateurs DMX (Data Mining Extensions)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Le langage DMX (Data Mining Extensions) dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prend en charge les opérateurs arithmétiques, d’assignation, de comparaison, logiques et unaires. Le tableau ci-dessous affiche la liste des opérateurs pris en charge par DMX.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[+ &#40;ajouter&#41; &#40;DMX&#41;](../dmx/add-dmx.md)|Opérateur arithmétique qui ajoute deux nombres ensemble.|  
|[-&#40;soustraire&#41; &#40;DMX&#41;](../dmx/subtract-dmx.md)|Opérateur arithmétique qui soustrait un nombre d'un autre.|  
|[&#42; &#40;multiplier&#41; &#40;DMX&#41;](../dmx/multiply-dmx.md)|Opérateur arithmétique qui multiplie un nombre par un autre.|  
|[&#40;diviser&#41; &#40;&#41;DMX ](../dmx/divide-dmx.md)|Opérateur arithmétique qui divise un nombre par un autre.|  
|[&#60; &#40;inférieur à&#41; &#40;DMX&#41;](../dmx/less-than-dmx.md)|Opérateur de comparaison. Pour les arguments qui donnent comme résultat des valeurs Non NULL, retourne TRUE si la valeur de l'argument de gauche est inférieure à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#62; &#40;supérieur à&#41; &#40;DMX&#41;](../dmx/greater-than-dmx.md)|Opérateur de comparaison. Pour les arguments qui donnent comme résultat des valeurs Non NULL, retourne TRUE si la valeur de l'argument de gauche est supérieure à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[= &#40;égal à&#41; &#40;DMX&#41;](../dmx/equal-to-dmx.md)|Opérateur de comparaison. Pour les arguments qui donnent comme résultat des valeurs Non NULL, retourne TRUE si la valeur de l'argument de gauche est égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#60;&#62; &#40;pas égal à&#41; &#40;DMX&#41;](../dmx/not-equal-to-dmx.md)|Opérateur de comparaison. Pour les arguments qui donnent comme résultat des valeurs Non NULL, retourne TRUE si la valeur de l'argument de gauche n'est pas égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#60;= &#40;inférieure ou égale à&#41; &#40;DMX&#41;](../dmx/less-than-or-equal-to-dmx.md)|Opérateur de comparaison. Pour les arguments qui donnent comme résultat des valeurs Non NULL, retourne TRUE si la valeur de l'argument de gauche est inférieure ou égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#62;= &#40;supérieur ou égal à&#41; &#40;DMX&#41;](../dmx/greater-than-or-equal-to-dmx.md)|Opérateur de comparaison. Pour les arguments qui donnent comme résultat des valeurs Non NULL, retourne TRUE si la valeur de l'argument de gauche est supérieure ou égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[ET &#40;DMX&#41;](../dmx/and-dmx.md)|Opérateur logique qui effectue une conjonction logique sur deux expressions numériques.|  
|[NON &#40;&#41;DMX ](../dmx/not-dmx.md)|Opérateur logique qui effectue une négation sur une expression numérique.|  
|[OU &#40;&#41;DMX ](../dmx/or-dmx.md)|Opérateur logique qui effectue une disjonction logique sur deux expressions numériques.|  
|[+ &#40;&#41;&#41; &#40;DMX positif ](../dmx/positive-dmx.md)|Opérateur unaire qui retourne la valeur positive d'une expression numérique.|  
|[-&#40;&#41;&#41; &#40;DMX négatif ](../dmx/negative-dmx.md)|Opérateur unaire qui retourne la valeur négative d'une expression numérique.|  
|[Double barre oblique &#40;commentaire&#41; &#40;&#41;DMX ](../dmx/double-slash-comment-dmx.md)|Indique une chaîne de texte que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne doit pas exécuter. Vous pouvez imbriquer les commentaires dans une instruction DMX, les ajouter à la fin d'une ligne de code ou les insérer sur une ligne séparée.|  
|[--&#40;commentaire&#41; &#40;synthèse&#41; DMX](../dmx/comment-dmx-summary.md)|Indique une chaîne de texte que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne doit pas exécuter. Vous pouvez imbriquer les commentaires dans une instruction DMX, les ajouter à la fin d'une ligne de code ou les insérer sur une ligne séparée.|  
|[Barre oblique &#40;commentaire&#41; &#40;&#41;DMX ](../dmx/slash-star-comment-dmx.md)|Indique une chaîne de texte que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne doit pas exécuter. Vous pouvez imbriquer les commentaires dans une instruction DMX, les ajouter à la fin d'une ligne de code ou les insérer sur une ligne séparée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Informations de référence sur la&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Opérateurs &#40;&#41;DMX ](../dmx/operators-dmx.md)  
  
  
