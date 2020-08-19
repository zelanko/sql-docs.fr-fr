---
description: Opérateurs arithmétiques (DMX)
title: Opérateurs arithmétiques (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 77b9f300859b6ce1250ed9d36a33a88a3dd12fe1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88426191"
---
# <a name="operators---arithmetic"></a>Opérateurs arithmétiques
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Vous pouvez utiliser des opérateurs arithmétiques dans les extensions DMX (Data Mining Extensions) pour les calculs arithmétiques dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , y compris l’addition, la soustraction, la multiplication et la Division.  
  
 Le tableau ci-dessous identifie les opérateurs arithmétiques pris en charge par DMX.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[+ &#40;ajouter&#41; &#40;DMX&#41;](../dmx/add-dmx.md)|Additionne deux nombres.|  
|[-&#40;soustraire&#41; &#40;DMX&#41;](../dmx/subtract-dmx.md)|Soustrait un nombre d'un autre.|  
|[&#42; &#40;multiplier&#41; &#40;DMX&#41;](../dmx/multiply-dmx.md)|Multiplie un nombre par un autre.|  
|[&#40;diviser&#41; &#40;&#41;DMX ](../dmx/divide-dmx.md)|Divise un nombre par un autre nombre.|  
  
 Les règles suivantes déterminent l'ordre de priorité des opérateurs arithmétiques dans une expression DMX :  
  
-   Lorsqu'une expression contient plusieurs opérateurs arithmétiques, la multiplication et la division sont effectuées en premier, avant la soustraction et l'addition.  
  
-   Lorsque tous les opérateurs arithmétiques dans une expression ont le même niveau de priorité, l’ordre d’exécution est de gauche à droite.  
  
-   Les expressions entre parenthèses ont priorité sur toutes les autres opérations.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-reference.md)   
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Expressions &#40;DMX&#41;](../dmx/expressions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX ](../dmx/general-prediction-functions-dmx.md)   
 [Opérateurs &#40;&#41;DMX ](../dmx/operators-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
