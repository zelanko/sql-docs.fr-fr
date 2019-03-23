---
title: Éditeur de Transformation (onglet Avancé) d’agrégation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.advanced.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: 186a9736-2554-40a0-9cb2-877a8db5fde8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 605a92e00b21d64679076fabcb41068b94921779
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58386147"
---
# <a name="aggregate-transformation-editor-advanced-tab"></a>Éditeur de transformation d'agrégation (onglet Avancé)
  L’onglet **Avancé** de la boîte de dialogue **Éditeur de transformation d’agrégation** permet de définir les propriétés des composants, de spécifier des agrégations et de définir les propriétés des colonnes d’entrée et de sortie.  
  
> [!NOTE]  
>  Les options concernant le nombre et l’échelle de clés d’une part, et le nombre et l’échelle de clés distinctes d’autre part, s’appliquent au niveau du composant quand ces options sont indiquées sous l’onglet **Avancé** , au niveau de la sortie quand elles sont précisées dans l’affichage avancé de l’onglet **Agrégations** , ou encore au niveau des colonnes quand elles sont spécifiées dans la liste de colonnes se trouvant dans la partie inférieure de l’onglet **Agrégations** .  
>   
>  Dans la transformation d’agrégation, **Clés** et **Échelle de clé** font référence au nombre de groupes attendus d’une opération **Regrouper par** . **Nombre de clés distinctes** et **Échelle de nombre des valeurs distinctes** font référence au nombre de valeurs distinctes attendues d’une opération **Comptage de valeurs** .  
  
 Pour en savoir plus sur la transformation d’agrégation, consultez [Transformation d’agrégation](data-flow/transformations/aggregate-transformation.md).  
  
## <a name="options"></a>Options  
 **Échelle de clé**  
 Permet de spécifier le nombre approximatif de clés attendu par l'agrégation (facultatif). La transformation utilise ces informations afin d'optimiser la taille initiale de son cache. Par défaut, la valeur de cette option est **Non spécifié**. Si les deux options **Échelle de clé** et **Nombre de clés** sont spécifiées, **Nombre de clés** est prioritaire.  
  
|Value|Description|  
|-----------|-----------------|  
|Non spécifié|La propriété **KeyScale** n’est pas utilisée.|  
|Faible|L’agrégation peut écrire environ 500 000 clés.|  
|Moyenne|L'agrégation peut écrire environ 5 000 000 clés.|  
|Élevée|L'agrégation peut écrire plus de 25 000 000 clés.|  
  
 **Nombre de clés**  
 Permet de spécifier le nombre exact de clés attendu par l'agrégation (facultatif). La transformation utilise ces informations afin d'optimiser la taille initiale de son cache. Si les deux options **Échelle de clé** et **Nombre de clés** sont spécifiées, **Nombre de clés** est prioritaire.  
  
 **Échelle de nombre des valeurs distinctes**  
 Permet éventuellement de spécifier le nombre approximatif de valeurs distinctes que l'agrégation peut écrire. Par défaut, la valeur de cette option est **Non spécifié**. Si les deux options **Échelle de nombre des valeurs distinctes** et **Nombre de clés distinctes** sont spécifiées, **Nombre de clés distinctes** est prioritaire.  
  
|Value|Description|  
|-----------|-----------------|  
|Non spécifié|La propriété CountDistinctScale n'est pas utilisée.|  
|Faible|L'agrégation peut écrire environ 500 000 valeurs distinctes.|  
|Moyenne|L’agrégation peut écrire environ 5 000 000 de valeurs distinctes.|  
|Élevée|L'agrégation peut écrire plus de 25 000 000 valeurs distinctes.|  
  
 **Nombre de clés distinctes**  
 Permet de spécifier éventuellement le nombre exact de valeurs distinctes que l'agrégation peut écrire. Si les deux options **Échelle de nombre des valeurs distinctes** et **Nombre de clés distinctes** sont spécifiées, **Nombre de clés distinctes** est prioritaire.  
  
 **Facteur d'extension automatique**  
 Utilisez une valeur comprise entre 1 et 100 afin de spécifier le pourcentage selon lequel la mémoire peut être étendue pendant l'agrégation. Par défaut, la valeur de cette option est **25 %**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation d’agrégation &#40;onglet Agrégations&#41;](../../2014/integration-services/aggregate-transformation-editor-aggregations-tab.md)   
 [Agréger les valeurs dans un dataset à l'aide de la transformation d'agrégation](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
