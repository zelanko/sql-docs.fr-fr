---
title: Opérateurs arithmétiques (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e78241252733e8298c0bc727f9c45dd6df2768ac
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68008216"
---
# <a name="operators---arithmetic"></a>Opérateurs arithmétiques
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Vous pouvez utiliser des opérateurs arithmétiques dans les extensions DMX (Data Mining Extensions) pour [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]les calculs arithmétiques dans, y compris l’addition, la soustraction, la multiplication et la Division.  
  
 Le tableau ci-dessous identifie les opérateurs arithmétiques pris en charge par DMX.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[+ &#40;ajouter&#41; &#40;DMX&#41;](../dmx/add-dmx.md)|Additionne deux nombres.|  
|[-&#40;soustraire&#41; &#40;DMX&#41;](../dmx/subtract-dmx.md)|Soustrait un nombre d'un autre.|  
|[&#42; &#40;multiplier&#41; &#40;DMX&#41;](../dmx/multiply-dmx.md)|Multiplie un nombre par un autre.|  
|[&#40;diviser&#41; &#40;&#41;DMX](../dmx/divide-dmx.md)|Divise un nombre par un autre nombre.|  
  
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
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)   
 [Opérateurs &#40;&#41;DMX](../dmx/operators-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
