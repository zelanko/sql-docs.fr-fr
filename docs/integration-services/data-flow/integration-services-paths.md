---
title: "Chemins d&#39;acc&#232;s d&#39;Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.patheditor.general.f1"
  - "sql13.dts.designer.patheditor.metadata.f1"
  - "sql13.dts.designer.patheditor.visualizers.f1"
helpviewer_keywords: 
  - "chemins d’accès [Integration Services], à propos des chemins d’accès"
  - "flux de données [Integration Services], chemins d’accès"
  - "chemins d'accès [Integration Services]"
  - "destinations [Integration Services], chemins d’accès"
  - "sources [Integration Services], chemins d’accès"
ms.assetid: 6c4629a9-2ede-4011-9101-3b342249640e
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Chemins d&#39;acc&#232;s d&#39;Integration Services
  Un chemin d'accès connecte deux composants d'un flux de données en reliant la sortie d'un composant à l'entrée d'un autre composant. Un chemin d'accès comporte une source et une destination. Par exemple, si un chemin d'accès connecte une source OLE DB et une transformation de tri, la source OLE DB est la source du chemin d'accès, tandis que la transformation de tri est la destination du chemin d'accès. La source est le composant où débute le chemin d'accès et la destination, le composant où il se termine.  
  
 Si vous exécutez un package dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], vous pouvez afficher les données d'un flux de données en attachant des visionneuses de données à un chemin d'accès. Une visionneuse de données peut être configurée pour afficher des données dans une grille. Une visionneuse de données est un outil de débogage très utile. Pour plus d’informations, consultez [Débogage d’un flux de données](../../integration-services/troubleshooting/debugging-data-flow.md).  
  
## Configuration du chemin d’accès  
 Le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] contient la boîte de dialogue **Éditeur du chemin d’accès au flux de données** qui permet de définir les propriétés du chemin d’accès, d’afficher les métadonnées des colonnes de données qui empruntent le chemin d’accès et de configurer les visionneuses de données.  
  
 Le nom, la description et l'annotation du chemin d'accès sont des propriétés que vous pouvez configurer. Vous pouvez également configurer les chemins d'accès par programme. Pour plus d’informations, consultez [Connexion de composants de flux de données par programme](../../integration-services/building-packages-programmatically/connecting-data-flow-components-programmatically.md).  
  
 Une annotation de chemin d’accès affiche le nom de la source du chemin d’accès ou le nom du chemin d’accès sur l’aire de conception de l’onglet **Flux de données** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Les annotations de chemins d'accès sont similaires aux annotations ajoutées aux flux de données, aux flux de contrôles et aux gestionnaires d'événements. La seule différence est qu’une annotation de chemin d’accès est attachée à un chemin d’accès, alors que les autres annotations apparaissent sous les onglets **Flux de données**, **Flux de contrôle** et **Gestionnaires d’événements** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 Les métadonnées indiquent le nom, le type de données, la précision, l'échelle, la longueur, la page de codes et le composant source de chaque colonne dans la sortie du composant précédent. Le composant source est le composant du flux de données ayant créé la colonne. Il peut ou non s'agir du premier composant du flux de données. Par exemple, les transformations d'union totale et de tri créent leurs propres colonnes et sont les sources de leurs colonnes de sortie. À l'inverse, une transformation de copie de colonne peut transmettre des colonnes sans les modifier ou créer des colonnes en copiant les colonnes d'entrée. La transformation de copie de colonne est le composant source des nouvelles colonnes uniquement.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur du chemin d’accès au flux de données**, cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur du chemin d’accès au flux de données &#40;Page Général&#41;](../Topic/Data%20Flow%20Path%20Editor%20\(General%20Page\).md)  
  
-   [Éditeur du chemin d’accès au flux de données &#40;Page Métadonnées&#41;](../Topic/Data%20Flow%20Path%20Editor%20\(Metadata%20Page\).md)  
  
-   [Éditeur du chemin d’accès au flux de données &#40;Page Visionneuses de données&#41;](../Topic/Data%20Flow%20Path%20Editor%20\(Data%20Viewers%20Page\).md)  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir par programmation, consultez [Propriétés du chemin d’accès](../Topic/Path%20Properties.md).  
  
## Tâches associées  
  
-   [Afficher les métadonnées d'un chemin d'accès dans l'Éditeur du chemin d'accès au flux de données](../Topic/View%20Path%20Metadata%20in%20the%20Data%20Flow%20Path%20Editor.md)  
  
-   [Connecter des composants dans un flux de données](../../integration-services/data-flow/connect-components-in-a-data-flow.md)  
  
## Voir aussi  
 [Flux de données](../../integration-services/data-flow/data-flow.md)  
  
  