---
title: "Éditeur de Transformation de regroupement probable (onglet Gestionnaire de connexions) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.fuzzygroupingtransformation.connection.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5bcb24248af5cc666ee45f53d60785fff679aca3
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="fuzzy-grouping-transformation-editor-connection-manager-tab"></a>Éditeur de transformation de regroupement probable (onglet Gestionnaire de connexions)
  Utilisez l'onglet **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de transformation de regroupement probable** pour sélectionner une connexion existante ou en créer une.  
  
> [!NOTE]  
>  Le serveur défini par la connexion doit exécuter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La transformation de regroupement probable crée des objets de données temporaires dans tempdb qui peuvent être aussi volumineux que l’ensemble de l’entrée de la transformation. Au cours de son exécution, la transformation envoie des requêtes serveur par rapport aux objets temporaires, ce qui peut affecter les performances générales du serveur.  
  
 Pour en savoir plus sur la transformation de regroupement approximatif, consultez [Fuzzy Grouping Transformation](../../../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## <a name="options"></a>Options  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez une connexion OLE DB existante en utilisant la zone de liste, ou créez une connexion en utilisant le bouton **Nouvelle** .  
  
 **Nouvelle**  
 Crée une connexion en utilisant la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB** .  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Identifier les lignes de données semblables à l’aide de la Transformation de regroupement probable](../../../integration-services/data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
