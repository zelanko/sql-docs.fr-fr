---
title: Connecter des composants avec des chemins d’accès | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], connections
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 05633e4c-1370-4b05-802b-f36b07dd71c8
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 8d6cc5a5fb14fff5fd92d5120f56c06d57ddcbaf
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84921390"
---
# <a name="connect-components-with-paths"></a>Connecter des composants avec des chemins d’accès
  Le flux de données d’un package est construit sur la surface de conception de l’onglet **Flux de données** du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] . Si un flux de données contient deux composants de flux de données, vous pouvez les relier en connectant la sortie d'une source ou d'une transformation à l'entrée d'une transformation ou d'une destination. Le connecteur entre ces deux composants de flux de données porte le nom de chemin d'accès.

 Le diagramme qui suit montre un flux de données simple formé d'un composant source, de deux transformations, d'un composant de destination et des chemins d'accès les connectant.

 ![Data flow](media/mw-dts-08.gif "Flux de données") (Flux de données)

 Une fois deux composants connectés, vous pouvez afficher les métadonnées des données empruntant le chemin et les propriétés du chemin dans **l’Éditeur du chemin d’accès au flux de données**. Pour plus d’informations, consultez [Chemins d’accès d’Integration Services](data-flow/integration-services-paths.md).

 Vous pouvez également ajouter des visionneuses de données aux chemins d'accès. Une visionneuse de données permet d'afficher les données circulant entre les composants du flux de données lors de l'exécution du package.

### <a name="to-connect-components-in-a-data-flow"></a>Pour connecter des composants dans un flux de données

-   [Connecter des composants dans un flux de données](data-flow/connect-components-in-a-data-flow.md)

### <a name="to-set-path-properties"></a>Pour définir les propriétés d'un chemin d'accès

-   [Définir les propriétés d’un chemin à l’aide de l’Éditeur du chemin d’accès au flux de données](../../2014/integration-services/set-the-properties-of-a-path-by-using-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a>Pour afficher les métadonnées d'un chemin d'accès

-   [Afficher les métadonnées d'un chemin d'accès dans l'Éditeur du chemin d'accès au flux de données](../../2014/integration-services/view-path-metadata-in-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a>Pour afficher les métadonnées d'un chemin d'accès

-   [Ajouter une visionneuse de données à un flux de données](../../2014/integration-services/add-a-data-viewer-to-a-data-flow.md)

## <a name="see-also"></a>Voir aussi
 Traitement des données de la [tâche](control-flow/data-flow-task.md) [de Data](data-flow/data-flow.md) Flow [transformer des données avec des transformations](data-flow/transformations/transform-data-with-transformations.md) [gestion des erreurs dans les données](data-flow/error-handling-in-data.md)


