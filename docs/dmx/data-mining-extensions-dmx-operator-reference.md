---
title: Data Mining Extensions (DMX) référence des opérateurs | Documents Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7a85644328591f037ee342866ca7dfb5e887ed17
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842762"
---
# <a name="data-mining-extensions-dmx-operator-reference"></a>Guide de référence des opérateurs DMX (Data Mining Extensions)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Le langage d’Extensions DMX (Data Mining) dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prend en charge les opérateurs arithmétiques, d’affectation, de comparaison, logiques et d’unaire. Le tableau ci-dessous affiche la liste des opérateurs pris en charge par DMX.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[+ &#40;Ajouter&#41; &#40;DMX&#41;](../dmx/add-dmx.md)|Opérateur arithmétique qui ajoute deux nombres ensemble.|  
|[- &#40;Soustraire&#41; &#40;DMX&#41;](../dmx/subtract-dmx.md)|Opérateur arithmétique qui soustrait un nombre d'un autre.|  
|[&#42;&#40;Multiplier&#41; &#40;DMX&#41;](../dmx/multiply-dmx.md)|Opérateur arithmétique qui multiplie un nombre par un autre.|  
|[&#40;Diviser&#41; &#40;DMX&#41;](../dmx/divide-dmx.md)|Opérateur arithmétique qui divise un nombre par un autre.|  
|[&#60;&#40;Moins&#41; &#40;DMX&#41;](../dmx/less-than-dmx.md)|Opérateur de comparaison. Pour les arguments qui donnent comme résultat des valeurs Non NULL, retourne TRUE si la valeur de l'argument de gauche est inférieure à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#62;&#40;Supérieur&#41; &#40;DMX&#41;](../dmx/greater-than-dmx.md)|Opérateur de comparaison. Pour les arguments qui donnent comme résultat des valeurs Non NULL, retourne TRUE si la valeur de l'argument de gauche est supérieure à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[= &#40;Égal à&#41; &#40;DMX&#41;](../dmx/equal-to-dmx.md)|Opérateur de comparaison. Pour les arguments qui donnent comme résultat des valeurs Non NULL, retourne TRUE si la valeur de l'argument de gauche est égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#60;&#62;&#40;Différent de&#41; &#40;DMX&#41;](../dmx/not-equal-to-dmx.md)|Opérateur de comparaison. Pour les arguments qui donnent comme résultat des valeurs Non NULL, retourne TRUE si la valeur de l'argument de gauche n'est pas égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#60;= &#40;Inférieure ou égale à&#41; &#40;DMX&#41;](../dmx/less-than-or-equal-to-dmx.md)|Opérateur de comparaison. Pour les arguments qui donnent comme résultat des valeurs Non NULL, retourne TRUE si la valeur de l'argument de gauche est inférieure ou égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#62;= &#40;Supérieur ou égal à&#41; &#40;DMX&#41;](../dmx/greater-than-or-equal-to-dmx.md)|Opérateur de comparaison. Pour les arguments qui donnent comme résultat des valeurs Non NULL, retourne TRUE si la valeur de l'argument de gauche est supérieure ou égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[ET &AMP;#40;DMX&AMP;#41;](../dmx/and-dmx.md)|Opérateur logique qui effectue une conjonction logique sur deux expressions numériques.|  
|[PAS &AMP;#40;DMX&AMP;#41;](../dmx/not-dmx.md)|Opérateur logique qui effectue une négation sur une expression numérique.|  
|[OU &AMP;#40;DMX&AMP;#41;](../dmx/or-dmx.md)|Opérateur logique qui effectue une disjonction logique sur deux expressions numériques.|  
|[+ &#40;Positif&#41; &#40;DMX&#41;](../dmx/positive-dmx.md)|Opérateur unaire qui retourne la valeur positive d'une expression numérique.|  
|[- &#40;Négatif&#41; &#40;DMX&#41;](../dmx/negative-dmx.md)|Opérateur unaire qui retourne la valeur négative d'une expression numérique.|  
|[Double barre oblique &#40;commentaire&#41; &#40;DMX&#41;](../dmx/double-slash-comment-dmx.md)|Indique une chaîne de texte que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne doit pas exécuter. Vous pouvez imbriquer les commentaires dans une instruction DMX, les ajouter à la fin d'une ligne de code ou les insérer sur une ligne séparée.|  
|[-- &#40;Commentaire&#41; &#40;DMX&#41; résumé](../dmx/comment-dmx-summary.md)|Indique une chaîne de texte que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne doit pas exécuter. Vous pouvez imbriquer les commentaires dans une instruction DMX, les ajouter à la fin d'une ligne de code ou les insérer sur une ligne séparée.|  
|[Barre oblique étoile &#40;commentaire&#41; &#40;DMX&#41;](../dmx/slash-star-comment-dmx.md)|Indique une chaîne de texte que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne doit pas exécuter. Vous pouvez imbriquer les commentaires dans une instruction DMX, les ajouter à la fin d'une ligne de code ou les insérer sur une ligne séparée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40;DMX&#41; Conventions de syntaxe](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;DMX&#41; éléments de syntaxe](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Opérateurs &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
