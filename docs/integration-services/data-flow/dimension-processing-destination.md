---
title: "Destination de traitement de dimension | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.dimensionprocessingdest.f1"
helpviewer_keywords: 
  - "Destination de traitement de dimension"
  - "chargement de dimensions"
  - "destinations [Integration Services], traitement de dimension"
  - "dimensions [Analysis Services], traitement"
ms.assetid: 4c49bb95-7259-42f4-a785-bb6aaf5f8566
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Destination de traitement de dimension
  La destination de traitement de dimension charge et traite une dimension [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour plus d’informations sur les dimensions, consultez [Dimensions &#40;Analysis Services - Données multidimensionnelles&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md).  
  
 La destination de traitement de dimension regroupe les fonctionnalités suivantes :  
  
-   options permettant de choisir entre un traitement incrémentiel, un traitement complet ou un traitement de mise à jour ;  
  
-   configuration d'erreur, permettant de spécifier si le traitement de dimension ignore les erreurs ou s'arrête après un nombre spécifique d'erreurs ;  
  
-   mappage des colonnes d'entrée aux colonnes des tables de dimension.  
  
 Pour plus d’informations sur le traitement des objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez [Options et paramètres de traitement &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
## Configuration de la destination de traitement de dimension  
 La destination de traitement de dimension utilise un gestionnaire de connexions [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour se connecter au projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou à l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient les dimensions traitées par la destination. Pour plus d'informations, consultez [Analysis Services Connection Manager](../../integration-services/connection-manager/analysis-services-connection-manager.md).  
  
 Cette destination comporte une entrée. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de destination de traitement de dimension**, cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de destination de traitement de dimension &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/dimension-processing-destination-editor-connection-manager-page.md)  
  
-   [Éditeur de destination de traitement de dimension &#40;page Mappages&#41;](../../integration-services/data-flow/dimension-processing-destination-editor-mappings-page.md)  
  
-   [Éditeur de destination de traitement de dimension &#40;page Avancé&#41;](../../integration-services/data-flow/dimension-processing-destination-editor-advanced-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l’une des rubriques suivantes :  
  
-   [Propriétés communes](../Topic/Common%20Properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## Voir aussi  
 [Flux de données](../../integration-services/data-flow/data-flow.md)   
 [Transformations Integration Services](../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  