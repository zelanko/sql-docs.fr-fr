---
title: Destination de traitement de partition | Documents Microsoft
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
- sql13.dts.designer.partitionprocessingdest.f1
helpviewer_keywords:
- partitions [Analysis Services], processing
- Partition Processing destination [Integration Services]
- destinations [Integration Services], Partition Processing
ms.assetid: 36c592ff-3f78-4a58-b496-31c1c8eee131
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 036b792f9895c6b5d56438ce52455aeb5622e0ba
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="partition-processing-destination"></a>Destination de traitement de partition
  La destination de traitement de partition charge et traite une partition [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour plus d’informations sur les partitions, consultez [Partitions &#40;Analysis Services - Données multidimensionnelles&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md).  
  
 La destination de traitement de partition regroupe les fonctionnalités suivantes :  
  
-   options permettant de choisir entre un traitement incrémentiel, un traitement complet ou un traitement de mise à jour ;  
  
-   configuration d'erreur permettant de spécifier si le traitement ignore les erreurs ou s'arrête après un nombre spécifique d'erreurs ;  
  
-   mappage des colonnes d'entrée aux colonnes de partition.  
  
 Pour plus d’informations sur le traitement des objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez [Options et paramètres de traitement &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
> [!NOTE]  
>  Les tâches décrites ici ne s’appliquent pas aux modèles tabulaires Analysis Services.  Vous ne pouvez pas mapper des colonnes d’entrée aux colonnes de partition pour les modèles tabulaires. Vous pouvez en revanche utiliser la tâche DDL d'exécution [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) d'Analysis Services pour traiter la partition.  
  
## <a name="configuration-of-the-partition-processing-destination"></a>Configuration de la destination de traitement de partition  
 La destination de traitement de partition utilise un gestionnaire de connexions [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour se connecter au projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou à l’instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient les cubes et partitions traités par la destination. Pour plus d'informations, consultez [Analysis Services Connection Manager](../../integration-services/connection-manager/analysis-services-connection-manager.md).  
  
 Cette destination comporte une entrée. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés pouvant être définies dans la boîte de dialogue **Éditeur de destination de traitement de partition** , cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de destination de traitement de partition &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/partition-processing-destination-editor-connection-manager-page.md)  
  
-   [Éditeur de destination de traitement de partition &#40;page Mappages&#41;](../../integration-services/data-flow/partition-processing-destination-editor-mappings-page.md)  
  
-   [Éditeur de destination de traitement de partition &#40;page Avancé&#41;](../../integration-services/data-flow/partition-processing-destination-editor-advanced-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programme, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Propriétés personnalisées de la destination de traitement de partition](../../integration-services/data-flow/partition-processing-destination-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  
