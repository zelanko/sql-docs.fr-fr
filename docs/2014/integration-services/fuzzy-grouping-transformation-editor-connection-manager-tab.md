---
title: Éditeur de transformation de regroupement probable (onglet Gestionnaire de connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.connection.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7cfee2c2a79410d73eb6ca4da47f0fd361a24fb2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058338"
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
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Identifier des lignes de données semblables à l'aide de la transformation de regroupement probable](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
