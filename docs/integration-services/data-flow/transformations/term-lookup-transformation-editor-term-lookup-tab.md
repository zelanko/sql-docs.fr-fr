---
title: "&#201;diteur de transformation de recherche de terme (onglet Recherche de terme) | Microsoft Docs"
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
  - "sql13.dts.designer.termlookup.termlookup.f1"
helpviewer_keywords: 
  - "Éditeur de transformation de recherche de terme"
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# &#201;diteur de transformation de recherche de terme (onglet Recherche de terme)
  L'onglet **Recherche de terme** de la boîte de dialogue **Éditeur de transformation de recherche de terme** permet de mapper une colonne d'entrée à une colonne de recherche dans une table de référence et de fournir un alias pour chaque colonne de sortie.  
  
 Pour en savoir plus sur la transformation de recherche de terme, consultez [Term Lookup Transformation](../../../integration-services/data-flow/transformations/term-lookup-transformation.md).  
  
## Options  
 **Colonnes d'entrée disponibles**  
 À l'aide des cases à cocher, sélectionnez les colonnes d'entrées à transmettre telles quelles à la sortie. Faites glisser une colonne d'entrée vers la liste **Colonnes de référence disponibles** pour la mapper sur une colonne de recherche dans la table de référence. Les types de données prises en charge par les colonnes d'entrée et de recherche doivent correspondre et avoir pour valeur  DT_NTEXT ou DT_WSTR. Sélectionnez une ligne de mappage et cliquez avec le bouton droit pour modifier les mappages dans la boîte de dialogue [Créer des relations](../../../integration-services/data-flow/transformations/create-relationships.md).  
  
 **Colonnes de référence disponibles**  
 Affiche les colonnes disponibles dans la table de référence. Choisissez la colonne qui contient la liste de termes correspondants.  
  
 **Colonne SQL directe**  
 Permet de sélectionner des colonnes dans la liste des colonnes d'entrée disponibles. Vos sélections se reflètent dans les sélections des cases à cocher de la table **Colonnes d'entrée disponibles** .  
  
 **Alias de colonne de sortie**  
 Permet de saisir un alias pour chaque colonne de sortie. La valeur par défaut correspond au nom de la colonne. Cependant, vous pouvez choisir un nom unique descriptif.  
  
 **Configurer la sortie d'erreur**  
 Utilisez la boîte de dialogue [Configurer l’affichage des erreurs](../Topic/Configure%20Error%20Output.md) pour spécifier les options de gestion des erreurs dans les lignes qui provoquent des erreurs.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation de recherche de terme &#40;onglet Table de référence&#41;](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-reference-table-tab.md)   
 [Éditeur de transformation de recherche de terme &#40;onglet Avancé&#41;](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-advanced-tab.md)   
 [Transformation d'extraction de terme](../../../integration-services/data-flow/transformations/term-extraction-transformation.md)  
  
  