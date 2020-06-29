---
title: Chemins Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- paths [Integration Services], about paths
- data flow [Integration Services], paths
- paths [Integration Services]
- destinations [Integration Services], paths
- sources [Integration Services], paths
ms.assetid: 6c4629a9-2ede-4011-9101-3b342249640e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c225d2fe52fcb12a5abc22df5008b6cbc9b861a0
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85432106"
---
# <a name="integration-services-paths"></a>Chemins d'accès d'Integration Services
  Un chemin d'accès connecte deux composants d'un flux de données en reliant la sortie d'un composant à l'entrée d'un autre composant. Un chemin d'accès comporte une source et une destination. Par exemple, si un chemin d'accès connecte une source OLE DB et une transformation de tri, la source OLE DB est la source du chemin d'accès, tandis que la transformation de tri est la destination du chemin d'accès. La source est le composant où débute le chemin d'accès et la destination, le composant où il se termine.  
  
 Si vous exécutez un package dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vous pouvez afficher les données d'un flux de données en attachant des visionneuses de données à un chemin d'accès. Une visionneuse de données peut être configurée pour afficher des données dans une grille. Une visionneuse de données est un outil de débogage très utile. Pour plus d’informations, consultez [Débogage d’un flux de données](../troubleshooting/debugging-data-flow.md).  
  
## <a name="configuration-of-the-path"></a>Configuration du chemin d’accès  
 Le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] contient la boîte de dialogue **Éditeur du chemin d’accès au flux de données** qui permet de définir les propriétés du chemin d’accès, d’afficher les métadonnées des colonnes de données qui empruntent le chemin d’accès et de configurer les visionneuses de données.  
  
 Le nom, la description et l'annotation du chemin d'accès sont des propriétés que vous pouvez configurer. Vous pouvez également configurer les chemins d'accès par programme. Pour plus d’informations, consultez [Connexion de composants de flux de données par programme](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).  
  
 Une annotation de chemin d’accès affiche le nom de la source du chemin d’accès ou le nom du chemin d’accès sur l’aire de conception de l’onglet **Flux de données** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Les annotations de chemins d'accès sont similaires aux annotations ajoutées aux flux de données, aux flux de contrôles et aux gestionnaires d'événements. La seule différence est qu’une annotation de chemin d’accès est attachée à un chemin d’accès, alors que les autres annotations apparaissent sous les onglets **Flux de données**, **Flux de contrôle**et **Gestionnaires d’événements**du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Les métadonnées indiquent le nom, le type de données, la précision, l'échelle, la longueur, la page de codes et le composant source de chaque colonne dans la sortie du composant précédent. Le composant source est le composant du flux de données ayant créé la colonne. Il peut ou non s'agir du premier composant du flux de données. Par exemple, les transformations d'union totale et de tri créent leurs propres colonnes et sont les sources de leurs colonnes de sortie. À l'inverse, une transformation de copie de colonne peut transmettre des colonnes sans les modifier ou créer des colonnes en copiant les colonnes d'entrée. La transformation de copie de colonne est le composant source des nouvelles colonnes uniquement.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur du chemin d’accès au flux de données**, cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur du chemin d’accès au Data Flow &#40;&#41;de page général](../general-page-of-integration-services-designers-options.md)  
  
-   [Éditeur du chemin d’accès de données &#40;page de métadonnées&#41;](../data-flow-path-editor-metadata-page.md)  
  
-   [Éditeur du chemin d’accès au workflow &#40;page des visionneuses de données&#41;](../data-flow-path-editor-data-viewers-page.md)  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir par programmation, consultez [Propriétés du chemin d’accès](../path-properties.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Afficher les métadonnées d'un chemin d'accès dans l'Éditeur du chemin d'accès au flux de données](../view-path-metadata-in-the-data-flow-path-editor.md)  
  
-   [Connecter des composants dans un flux de données](connect-components-in-a-data-flow.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de données](data-flow.md)  
  
  
