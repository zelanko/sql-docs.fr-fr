---
title: Opérateurs de comparaison (DMX) | Documents Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8049f2bad6e78ff301b460b1375a0a73807ccd8d
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842462"
---
# <a name="operators---comparison"></a>Opérateurs de comparaison-
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Vous pouvez utiliser des opérateurs de comparaison avec des données scalaires dans n’importe quelle expression Extensions DMX (Data Mining) dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Les opérateurs de comparaison sont évalués comme des booléens ; ils renvoient la valeur TRUE ou FALSE en fonction du résultat de la condition testée.  
  
 Le tableau ci-dessous identifie les opérateurs de comparaison pris en charge par DMX.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[&#60;&#40;Moins&#41; &#40;DMX&#41;](../dmx/less-than-dmx.md)|Pour les arguments qui donnent comme résultat une valeur Non NULL, retourne TRUE si la valeur de l'argument de gauche est inférieure à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#62;&#40;Supérieur&#41; &#40;DMX&#41;](../dmx/greater-than-dmx.md)|Pour les arguments qui donnent comme résultat une valeur Non NULL, retourne TRUE si la valeur de l'argument de gauche est supérieure à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[= &#40;Égal à&#41; &#40;DMX&#41;](../dmx/equal-to-dmx.md)|Pour les arguments qui donnent comme résultat une valeur Non NULL, retourne TRUE si la valeur de l'argument de gauche est égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#60;&#62;&#40;Différent de&#41; &#40;DMX&#41;](../dmx/not-equal-to-dmx.md)|Pour les arguments qui donnent comme résultat une valeur Non NULL, retourne TRUE si la valeur de l'argument de gauche n'est pas égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#60;= &#40;Inférieure ou égale à&#41; &#40;DMX&#41;](../dmx/less-than-or-equal-to-dmx.md)|Pour les arguments qui donnent comme résultat une valeur Non NULL, retourne TRUE si la valeur de l'argument de gauche est inférieure ou égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#62;= &#40;Supérieur ou égal à&#41; &#40;DMX&#41;](../dmx/greater-than-or-equal-to-dmx.md)|Pour les arguments qui donnent comme résultat une valeur Non NULL, retourne TRUE si la valeur de l'argument de gauche est supérieure ou égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
  
 Vous pouvez également utiliser les opérateurs de comparaison dans les instructions et les fonctions DMX pour rechercher une condition.  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; référence](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40;DMX&#41; Conventions de syntaxe](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;DMX&#41; éléments de syntaxe](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Expressions &#40;DMX&#41;](../dmx/expressions-dmx.md)   
 [Fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Opérateurs &#40;DMX&#41;](../dmx/operators-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
