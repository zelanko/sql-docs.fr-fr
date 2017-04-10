---
title: "&#201;diteur de transformation de recherche floue (onglet Avanc&#233;) | Microsoft Docs"
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
  - "sql13.dts.designer.fuzzylookuptransformation.advanced.f1"
helpviewer_keywords: 
  - "Éditeur de transformation de recherche floue"
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# &#201;diteur de transformation de recherche floue (onglet Avanc&#233;)
  Utilisez l’onglet **Avancé** de la boîte de dialogue **Éditeur de transformation de recherche floue** pour définir les paramètres relatifs à une recherche floue.  
  
 Pour en savoir plus sur la transformation de recherche floue, consultez [Fuzzy Lookup Transformation](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md).  
  
## Options  
 **Correspondances maximales à afficher par recherche**  
 Indiquez le nombre maximal de correspondances que la transformation peut retourner pour chaque ligne d'entrée. La valeur par défaut est **1**.  
  
 **Seuil de similarité**  
 Définissez le seuil de similarité au niveau du composant à l'aide du curseur. Plus la valeur est proche de 1, plus la valeur de recherche doit être proche de la valeur source pour constituer une correspondance. Si vous augmentez le seuil, vous pouvez améliorer la vitesse de correspondance étant donné qu'un plus petit nombre d'enregistrements candidats doit être pris en compte.  
  
 **Séparateurs de jetons**  
 Indiquez les séparateurs utilisés par la transformation pour marquer les valeurs de colonne.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation de recherche floue &#40;onglet Table de référence&#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Éditeur de transformation de recherche floue &#40;onglet Colonnes&#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-columns-tab.md)  
  
  