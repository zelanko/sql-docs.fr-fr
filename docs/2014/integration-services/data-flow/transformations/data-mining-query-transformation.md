---
title: Requête d’exploration de données, transformation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquerytrans.f1
helpviewer_keywords:
- Data Mining Query transformation
- prediction queries [Integration Services]
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d9ab528b290fdbba841a1a8acf56f1f4f01c8fec
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62770692"
---
# <a name="data-mining-query-transformation"></a>transformation de requête d'exploration de données
  La transformation de requête d'exploration de données effectue des requêtes de prédiction par rapport aux modèles d'exploration de données. Cette transformation contient un générateur de requêtes qui permet de créer des requêtes DMX (Data Mining Extensions). Le générateur de requêtes vous permet de créer des instructions personnalisées afin d'évaluer les données d'entrée de la transformation par rapport à un modèle d'exploration de données existant à l'aide du langage DMX. Pour plus d’informations, consultez [Guide de référence du langage DMX & #40;Data Mining Extensions&#41;](/sql/dmx/data-mining-extensions-dmx-reference).  
  
 Une transformation peut exécuter plusieurs requêtes de prédiction si les modèles sont basés sur la même structure d'exploration de données. Pour plus d’informations, consultez [Interfaces de requête d’exploration de données](../../../analysis-services/data-mining/data-mining-query-tools.md).  
  
## <a name="configuration-of-the-data-mining-query-transformation"></a>Configuration de la transformation de requête d’exploration de données  
 La transformation de requête d’exploration de données utilise un gestionnaire de connexions [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour se connecter au projet [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ou à l’instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] qui contient la structure et les modèles d’exploration de données. Pour plus d'informations, consultez [Analysis Services Connection Manager](../../connection-manager/analysis-services-connection-manager.md).  
  
 Cette transformation a une entrée et une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue **Éditeur de transformation de requête d’exploration de données**, cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de transformation de requête d’exploration de données &#40;onglet Modèle d'exploration de données&#41;](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
-   [Éditeur de transformation de requête d’exploration de données &#40;onglet Modèle d’exploration de données&#41;](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md).  
  
  
