---
title: "Transformation de multidiffusion | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.multicasttrans.f1"
helpviewer_keywords: 
  - "sorties multiples"
  - "transformation de multidiffusion"
  - "jeux de données [Integration Services], sorties multiples"
  - "transformations multiples"
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
caps.latest.revision: 45
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 45
---
# Transformation de multidiffusion
  La transformation de multidiffusion distribue son entrée vers une ou plusieurs sorties. Cette transformation est similaire à la transformation de fractionnement conditionnel. Les deux transformations dirigent une entrée vers plusieurs sorties. Leur différence réside dans le fait que la transformation de multidiffusion dirige chaque ligne vers chaque sortie, tandis que la transformation de fractionnement conditionnel dirige une ligne vers une seule sortie. Pour plus d’informations, voir [Conditional Split Transformation](../../../integration-services/data-flow/transformations/conditional-split-transformation.md).  
  
 Vous configurez la transformation de multidiffusion en ajoutant des sorties.  
  
 À l'aide de la transformation de multidiffusion, un package peut créer des copies logiques des données. Cette fonctionnalité est utile lorsque le package doit appliquer plusieurs ensembles de transformations aux mêmes données. Par exemple, une copie des données est agrégée et seules les informations de résumé sont chargées à leur emplacement de destination, tandis qu'une autre copie des données est enrichie de valeurs recherchées et de colonnes dérivées avant d'être chargée à son emplacement de destination.  
  
 Cette transformation a une entrée et plusieurs sorties. Elle ne prend pas en charge de sortie d'erreur.  
  
## Configuration de la transformation de multidiffusion  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue **Éditeur de transformation de multidiffusion**, consultez [Éditeur de transformation de multidiffusion](../../../integration-services/data-flow/transformations/multicast-transformation-editor.md).  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir par programmation, consultez [Propriétés communes](../Topic/Common%20Properties.md).  
  
## Tâches associées  
 Pour plus d’informations sur la définition des propriétés de ce composant, consultez [Définir les propriétés d’un composant de flux de données](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## Voir aussi  
 [Flux de données](../../../integration-services/data-flow/data-flow.md)   
 [Transformations Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  