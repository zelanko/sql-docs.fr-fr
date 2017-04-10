---
title: "Transformation Unpivot | Microsoft Docs"
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
  - "sql13.dts.designer.unpivottrans.f1"
helpviewer_keywords: 
  - "Transformation Unpivot"
  - "ensemble de données plus normalisées [Integration Services]"
  - "données normalisées [Integration Services]"
  - "ensemble de données [Integration Services], données normalisées"
ms.assetid: f635c64b-a9c5-4f11-9c40-9cd9d5298c5d
caps.latest.revision: 45
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 45
---
# Transformation Unpivot
  La transformation Unpivot convertit un dataset non normalisé en version plus normalisée en étendant les valeurs de plusieurs colonnes d'un enregistrement dans plusieurs enregistrements avec les mêmes valeurs dans une colonne unique. Par exemple, un dataset qui répertorie des noms de clients possède une ligne pour chaque client, avec les produits et la quantité achetée mentionnés dans les colonnes sur la ligne. Après que la transformation Unpivot a normalisé le dataset, celui-ci contient une ligne différente pour chaque produit que le client a acheté.  
  
 Le schéma suivant illustre un dataset avant que les données n'aient été transformées dans la colonne Product.  
  
 ![Dataset après la suppression du tableau croisé dynamique](../../../integration-services/data-flow/transformations/media/mw-dts-18.gif "Dataset après la suppression du tableau croisé dynamique")  
  
 Le schéma suivant illustre un dataset après transformation de la colonne Product.  
  
 ![Dataset avant la suppression du tableau croisé dynamique](../../../integration-services/data-flow/transformations/media/mw-dts-17.gif "Dataset avant la suppression du tableau croisé dynamique")  
  
 Dans certaines circonstances, les résultats de la suppression du tableau croisé dynamique peuvent contenir des lignes aux valeurs inattendues. Par exemple, si les exemples de données du diagramme qui doivent être supprimées du tableau croisé dynamique possèdent des valeurs Null dans toutes les colonnes Qty pour Fred, la sortie ne comprend qu'une ligne pour Fred, au lieu de cinq. La colonne Qty contient Null ou zéro, suivant le type de données de la colonne.  
  
## Configuration de la transformation Unpivot  
 La transformation Unpivot inclut la propriété personnalisée **PivotKeyValue**. La propriété peut être mise à jour par une expression de propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41; ](../../../integration-services/expressions/integration-services-ssis-expressions.md), [Expressions de propriété dans des packages](../../../integration-services/expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 Cette transformation a une entrée et une sortie. Elle ne possède aucune sortie d'erreur.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation UnPivot**, cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de transformation UnPivot](../../../integration-services/data-flow/transformations/unpivot-transformation-editor.md)  
  
 Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../Topic/Common%20Properties.md)  
  
-   [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  