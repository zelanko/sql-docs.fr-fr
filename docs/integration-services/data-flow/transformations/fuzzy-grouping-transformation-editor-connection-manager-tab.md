---
title: "&#201;diteur de transformation de regroupement probable (onglet Gestionnaire de connexions) | Microsoft Docs"
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
  - "sql13.dts.designer.fuzzygroupingtransformation.connection.f1"
helpviewer_keywords: 
  - "Éditeur de transformation de regroupement probable"
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# &#201;diteur de transformation de regroupement probable (onglet Gestionnaire de connexions)
  Utilisez l'onglet **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de transformation de regroupement probable** pour sélectionner une connexion existante ou en créer une.  
  
> [!NOTE]  
>  Le serveur défini par la connexion doit exécuter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La transformation de regroupement probable crée des objets de données temporaires dans tempdb qui peuvent être aussi volumineux que l’ensemble de l’entrée de la transformation. Au cours de son exécution, la transformation envoie des requêtes serveur par rapport aux objets temporaires, ce qui peut affecter les performances générales du serveur.  
  
 Pour en savoir plus sur la transformation de regroupement approximatif, consultez [Fuzzy Grouping Transformation](../../../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## Options  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez une connexion OLE DB existante en utilisant la zone de liste, ou créez une connexion en utilisant le bouton **Nouvelle**.  
  
 **Nouveau**  
 Crée une connexion en utilisant la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB**.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Identifier des lignes de données semblables à l'aide de la transformation de regroupement probable](../../../integration-services/data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  