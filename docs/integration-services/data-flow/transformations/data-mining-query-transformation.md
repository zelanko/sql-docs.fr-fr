---
title: "Transformation de requête d’exploration de données | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.dataminingquerytrans.f1
helpviewer_keywords:
- Data Mining Query transformation
- prediction queries [Integration Services]
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 544f0aaf11e83b9ba2fc0ae5150b85e537998c25
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="data-mining-query-transformation"></a>transformation de requête d'exploration de données
  La transformation de requête d'exploration de données effectue des requêtes de prédiction par rapport aux modèles d'exploration de données. Cette transformation contient un générateur de requêtes qui permet de créer des requêtes DMX (Data Mining Extensions). Le générateur de requêtes vous permet de créer des instructions personnalisées afin d'évaluer les données d'entrée de la transformation par rapport à un modèle d'exploration de données existant à l'aide du langage DMX. Pour plus d’informations, consultez [Guide de référence du langage DMX &#40;Data Mining Extensions&#41;](../../../dmx/data-mining-extensions-dmx-reference.md).  
  
 Une transformation peut exécuter plusieurs requêtes de prédiction si les modèles sont basés sur la même structure d'exploration de données. Pour plus d’informations, consultez [Outils de requête d’exploration de données](../../../analysis-services/data-mining/data-mining-query-tools.md).  
  
## <a name="configuration-of-the-data-mining-query-transformation"></a>Configuration de la transformation de requête d’exploration de données  
 La transformation de requête d’exploration de données utilise un gestionnaire de connexions [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour se connecter au projet [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ou à l’instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] qui contient la structure et les modèles d’exploration de données. Pour plus d'informations, consultez [Analysis Services Connection Manager](../../../integration-services/connection-manager/analysis-services-connection-manager.md).  
  
 Cette transformation a une entrée et une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue **Éditeur de transformation de requête d’exploration de données** , cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de transformation de requête d’exploration de données &#40;onglet Modèle d'exploration de données&#41;](../../../integration-services/data-flow/transformations/data-mining-query-transformation-editor-mining-model-tab.md)  
  
-   [Éditeur de transformation de requête d’exploration de données &#40;onglet Modèle d'exploration de données&#41;](../../../integration-services/data-flow/transformations/data-mining-query-transformation-editor-mining-model-tab.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programme, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  
