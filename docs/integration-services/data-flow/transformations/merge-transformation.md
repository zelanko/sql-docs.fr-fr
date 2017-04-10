---
title: "Transformation de fusion | Microsoft Docs"
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
  - "sql13.dts.designer.mergetrans.f1"
helpviewer_keywords: 
  - "fusion de datasets [Integration Services]"
  - "fusion de données [Integration Services]"
  - "transformation de fusion"
  - "combinaison de datasets"
  - "jeux de données [Integration Services], fusion"
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# Transformation de fusion
  La transformation de fusion combine deux datasets triés en un seul datasets. Les lignes de chaque ensemble de données sont insérées dans la sortie en fonction des valeurs de leurs colonnes clés.  
  
 L'intégration de la transformation de fusion dans un flux de données permet de réaliser les tâches suivantes :  
  
-   Fusionner des données de deux sources de données, telles que des tables et des fichiers.  
  
-   Créer des ensembles de données complexes en imbriquant des transformations de fusion.  
  
-   Fusionner des lignes à nouveau après avoir corrigé les erreurs affectant les données.  
  
 La transformation de fusion est similaire aux transformations d'union totale. Utilisez la transformation d'union totale au lieu de la transformation de fusion dans les situations suivantes :  
  
-   Les entrées de transformation ne sont pas triées.  
  
-   La sortie combinée n'a pas besoin d'être triée.  
  
-   La transformation a au moins trois entrées.  
  
## Spécifications relatives aux entrées  
 La transformation de fusion requiert des données triées pour ses entrées. Pour plus d’informations sur cette spécification importante, consultez [Trier des données pour les transformations de fusion et de jointure de fusion](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 La transformation de fusion requiert également que les colonnes fusionnées dans ses entrées aient des métadonnées correspondantes. Par exemple, vous ne pouvez pas fusionner une colonne de type de données numérique avec une colonne de type de données caractère. Si les données sont du type de données chaîne, la colonne de la deuxième entrée doit avoir une longueur inférieure ou égale à celle de la colonne de la première entrée avec laquelle elle est fusionnée.  
  
 Dans le Concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)], l’interface utilisateur de la transformation de fusion mappe automatiquement les colonnes qui ont les mêmes métadonnées. Vous pouvez ensuite mapper manuellement les colonnes ayant des types de données compatibles.  
  
 Cette transformation a deux entrées et une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
## Configuration de la transformation de fusion  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue **Éditeur de transformation de fusion**, consultez [Éditeur de transformation de fusion](../../../integration-services/data-flow/transformations/merge-transformation-editor.md).  
  
 Pour plus d'informations sur les propriétés définissables par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../Topic/Common%20Properties.md)  
  
-   [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## Tâches associées  
 Pour plus d'informations sur la définition des propriétés, consultez les rubriques suivantes :  
  
-   [Définir les propriétés d'un composant de flux de données](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
-   [Trier des données pour les transformations de fusion et de jointure de fusion](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## Voir aussi  
 [Transformation de jointure de fusion](../../../integration-services/data-flow/transformations/merge-join-transformation.md)   
 [Transformation d'union totale](../../../integration-services/data-flow/transformations/union-all-transformation.md)   
 [Flux de données](../../../integration-services/data-flow/data-flow.md)   
 [Transformations Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  