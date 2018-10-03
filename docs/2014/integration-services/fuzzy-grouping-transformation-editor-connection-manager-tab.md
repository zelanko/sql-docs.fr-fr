---
title: Éditeur de Transformation de regroupement probable (onglet Gestionnaire de connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.connection.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a2d55c713fa1286177d5cb12d39d0f05a1834432
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139931"
---
# <a name="fuzzy-grouping-transformation-editor-connection-manager-tab"></a>Éditeur de transformation de regroupement probable (onglet Gestionnaire de connexions)
  Utilisez l'onglet **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de transformation de regroupement probable** pour sélectionner une connexion existante ou en créer une.  
  
> [!NOTE]  
>  Le serveur défini par la connexion doit exécuter [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La transformation de regroupement probable crée des objets de données temporaires dans tempdb qui peuvent être aussi volumineux que l’ensemble de l’entrée de la transformation. Au cours de son exécution, la transformation envoie des requêtes serveur par rapport aux objets temporaires, ce qui peut affecter les performances générales du serveur.  
  
 Pour en savoir plus sur la transformation de regroupement approximatif, consultez [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## <a name="options"></a>Options  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez une connexion OLE DB existante en utilisant la zone de liste, ou créez une connexion en utilisant le bouton **Nouvelle** .  
  
 **Nouveau**  
 Crée une connexion en utilisant la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB** .  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Identifier des lignes de données semblables à l'aide de la transformation de regroupement probable](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
