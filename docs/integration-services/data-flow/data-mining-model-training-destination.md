---
title: "Destination d’apprentissage du modèle d’exploration de données | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.dataminingmodeltrainingdest.f1
helpviewer_keywords:
- destinations [Integration Services], Data Mining Model Training
- Data Mining Model Training destination
- mining models [Analysis Services], training
- training mining models
ms.assetid: 6bc8cbe2-46af-4f7b-93d6-86779313c9d7
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cdb0903098dee37d88e89519cf6bc375b0fb90f0
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="data-mining-model-training-destination"></a>Destination d’apprentissage du modèle d’exploration de données
  La destination d'apprentissage du modèle d'exploration de données exerce les modèles d'exploration de données en transmettant les données que la destination reçoit par le biais des algorithmes de modèles d'exploration de données. Plusieurs modèles d'exploration de données peuvent faire l'objet d'un apprentissage par une même destination si les modèles sont construits sur la même structure d'exploration des données. Pour plus d’informations, consultez [Colonnes de structure d’exploration de données](../../analysis-services/data-mining/mining-structure-columns.md) et [Colonnes d’un modèle d’exploration de données](../../analysis-services/data-mining/mining-model-columns.md).  
  
## <a name="configuration-of-the-data-mining-model-training-destination"></a>Configuration de la destination d'apprentissage du modèle d'exploration de données  
 Si une colonne de niveau de cas de la structure cible et les modèles créés sur cette structure ont un contenu de type KEY TIME ou KEY SEQUENCE, les données d'entrée doivent être triées sur cette colonne. Par exemple, les modèles créés à l'aide de l'algorithme Microsoft Time Series utilisent le type de contenu KEY TIME. Si les données d'entrée ne sont pas triées, le traitement du modèle risque d'échouer. Si les données doivent être triées, vous pouvez utiliser une transformation de tri plus haut dans le flux de données afin de trier les données. Ceci ne s'applique pas aux colonnes dont le type de contenu est KEY. Pour plus d’informations, consultez [Types de contenu &#40;exploration de données&#41;](../../analysis-services/data-mining/content-types-data-mining.md) et [Transformation de tri](../../integration-services/data-flow/transformations/sort-transformation.md).  
  
> [!NOTE]  
>  L'entrée de la destination d'apprentissage du modèle d'exploration de données doit être triée. Pour trier les données, vous pouvez inclure une destination de tri en amont de la destination d'apprentissage du modèle d'exploration de données dans le flux de données. Pour plus d’informations, voir [Sort Transformation](../../integration-services/data-flow/transformations/sort-transformation.md).  
  
 La destination comporte une entrée et aucune sortie.  
  
 La destination d’apprentissage du modèle d’exploration de données utilise un gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour se connecter au projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou à l’instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient la structure et les modèles d’exploration de données dont la destination assure l’apprentissage. Pour plus d'informations, consultez [Analysis Services Connection Manager](../../integration-services/connection-manager/analysis-services-connection-manager.md).  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur d’apprentissage du modèle d’exploration de données** , cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur d’apprentissage du modèle d’exploration de données &#40;onglet Connexion&#41;](../../integration-services/data-flow/data-mining-model-training-editor-connection-tab.md)  
  
-   [Éditeur d’apprentissage du modèle d’exploration de données &#40;onglet Colonnes&#41;](../../integration-services/data-flow/data-mining-model-training-editor-columns-tab.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programme, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Propriétés personnalisées de la destination d'apprentissage du modèle d'exploration de données](../../integration-services/data-flow/data-mining-model-training-destination-custom-properties.md)  
  
 Pour plus d’informations sur la définition des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  
