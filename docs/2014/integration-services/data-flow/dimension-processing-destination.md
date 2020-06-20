---
title: Destination de traitement de dimension | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimensionprocessingdest.f1
helpviewer_keywords:
- Dimension Processing destination
- loading dimensions
- destinations [Integration Services], Dimension Processing
- dimensions [Analysis Services], processing
ms.assetid: 4c49bb95-7259-42f4-a785-bb6aaf5f8566
author: janinezhang
ms.author: janinez
ms.openlocfilehash: fadfc8b700ab575582a61388a9b641aa9a01f010
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84915999"
---
# <a name="dimension-processing-destination"></a>Destination de traitement de dimension
  La destination de traitement de dimension charge et traite une dimension [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour plus d’informations sur les dimensions, consultez [Dimensions &#40;Analysis Services - Données multidimensionnelles&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data).  
  
 La destination de traitement de dimension regroupe les fonctionnalités suivantes :  
  
-   options permettant de choisir entre un traitement incrémentiel, un traitement complet ou un traitement de mise à jour ;  
  
-   configuration d'erreur, permettant de spécifier si le traitement de dimension ignore les erreurs ou s'arrête après un nombre spécifique d'erreurs ;  
  
-   mappage des colonnes d'entrée aux colonnes des tables de dimension.  
  
 Pour plus d’informations sur le traitement des objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez [Options et paramètres de traitement &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services).  
  
## <a name="configuration-of-the-dimension-processing-destination"></a>Configuration de la destination de traitement de dimension  
 La destination de traitement de dimension utilise un gestionnaire de connexions [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour se connecter au projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou à l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient les dimensions traitées par la destination. Pour plus d'informations, consultez [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).  
  
 Cette destination comporte une entrée. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de destination de traitement de dimension** , cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de destination de traitement de dimension &#40;page Gestionnaire de connexions&#41;](../dimension-processing-destination-editor-connection-manager-page.md)  
  
-   [Éditeur de destination de traitement de dimension &#40;page Mappages&#41;](../dimension-processing-destination-editor-mappings-page.md)  
  
-   [Éditeur de destination de traitement de dimension &#40;page Avancé&#41;](../dimension-processing-destination-editor-advanced-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l’une des rubriques suivantes :  
  
-   [Propriétés communes](../common-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Transmission de données](data-flow.md)   
 [Transformations Integration Services](transformations/integration-services-transformations.md)  
  
  
