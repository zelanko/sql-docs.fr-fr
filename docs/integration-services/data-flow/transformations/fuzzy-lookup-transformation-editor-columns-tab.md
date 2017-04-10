---
title: "&#201;diteur de transformation de recherche floue (onglet Colonnes) | Microsoft Docs"
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
  - "sql13.dts.designer.fuzzylookuptransformation.columns.f1"
helpviewer_keywords: 
  - "Éditeur de transformation de recherche floue"
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# &#201;diteur de transformation de recherche floue (onglet Colonnes)
  L'onglet **Colonnes** de la boîte de dialogue **Éditeur de transformation de recherche floue** vous permet de définir les propriétés des colonnes d'entrée et de sortie.  
  
 Pour en savoir plus sur la transformation de recherche floue, consultez [Fuzzy Lookup Transformation](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md).  
  
## Options  
 **Colonnes d'entrée disponibles**  
 Faites glisser les colonnes d'entrée sur les colonnes de recherche afin de les y connecter. Ces colonnes doivent avoir le même type de données pris en charge. Sélectionnez une ligne de mappage et cliquez avec le bouton droit de la souris pour modifier les mappages dans la boîte de dialogue [Créer des relations](../../../integration-services/data-flow/transformations/create-relationships.md).  
  
 **Nom**  
 Permet d'afficher les noms des colonnes d'entrée disponibles.  
  
 **Transfert direct**  
 Permet d'indiquer s'il convient d'inclure les colonnes d'entrée dans la sortie de la transformation.  
  
 **Colonnes de recherche disponibles**  
 Ces cases à cocher vous permettent de choisir les colonnes sur lesquelles les opérations de recherche floue doivent porter.  
  
 **colonne de recherche**  
 Permet de choisir les colonnes de recherche floue dans la liste des colonnes disponibles de la table de référence. Vos sélections se reflètent dans les sélections des cases à cocher tirées de la table **Colonnes de recherche disponibles** . En sélectionnant une colonne dans la table **Colonnes de recherche disponibles** , vous créez ainsi une colonne de sortie contenant la valeur de la colonne issue de la table de référence de chaque ligne retournée y correspondant.  
  
 **Alias de sortie**  
 Permet de saisir un alias pour la sortie de chaque colonne de recherche. La valeur par défaut correspond au nom de la colonne de recherche suivi d'une valeur d'index numérique. Vous pouvez cependant choisir tout autre nom descriptif s'il reste unique.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation de recherche floue &#40;onglet Table de référence&#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Éditeur de transformation de recherche floue &#40;onglet Avancé&#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  