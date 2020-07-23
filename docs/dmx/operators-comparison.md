---
title: Opérateurs de comparaison (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 885285439721f017d1d6eaa5bb9eebd0a26c08a3
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86968619"
---
# <a name="operators---comparison"></a>Opérateurs de comparaison
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Vous pouvez utiliser des opérateurs de comparaison avec des données scalaires dans n’importe quelle expression DMX (Data Mining Extensions) dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Les opérateurs de comparaison sont évalués comme des booléens ; ils renvoient la valeur TRUE ou FALSE en fonction du résultat de la condition testée.  
  
 Le tableau ci-dessous identifie les opérateurs de comparaison pris en charge par DMX.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[&#60; &#40;inférieur à&#41; &#40;DMX&#41;](../dmx/less-than-dmx.md)|Pour les arguments qui donnent comme résultat une valeur Non NULL, retourne TRUE si la valeur de l'argument de gauche est inférieure à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#62; &#40;supérieur à&#41; &#40;DMX&#41;](../dmx/greater-than-dmx.md)|Pour les arguments qui donnent comme résultat une valeur Non NULL, retourne TRUE si la valeur de l'argument de gauche est supérieure à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[= &#40;égal à&#41; &#40;DMX&#41;](../dmx/equal-to-dmx.md)|Pour les arguments qui donnent comme résultat une valeur Non NULL, retourne TRUE si la valeur de l'argument de gauche est égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#60;&#62; &#40;pas égal à&#41; &#40;DMX&#41;](../dmx/not-equal-to-dmx.md)|Pour les arguments qui donnent comme résultat une valeur Non NULL, retourne TRUE si la valeur de l'argument de gauche n'est pas égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#60;= &#40;inférieure ou égale à&#41; &#40;DMX&#41;](../dmx/less-than-or-equal-to-dmx.md)|Pour les arguments qui donnent comme résultat une valeur Non NULL, retourne TRUE si la valeur de l'argument de gauche est inférieure ou égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[&#62;= &#40;supérieur ou égal à&#41; &#40;DMX&#41;](../dmx/greater-than-or-equal-to-dmx.md)|Pour les arguments qui donnent comme résultat une valeur Non NULL, retourne TRUE si la valeur de l'argument de gauche est supérieure ou égale à la valeur de l'argument de droite ; dans le cas contraire, retourne FALSE. Si l'un ou l'autre ou les deux arguments donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
  
 Vous pouvez également utiliser les opérateurs de comparaison dans les instructions et les fonctions DMX pour rechercher une condition.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-reference.md)   
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Expressions &#40;DMX&#41;](../dmx/expressions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)   
 [Opérateurs &#40;&#41;DMX](../dmx/operators-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
