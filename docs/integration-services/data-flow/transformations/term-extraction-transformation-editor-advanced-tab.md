---
title: "&#201;diteur de transformation d&#39;extraction de terme (onglet Avanc&#233;) | Microsoft Docs"
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
  - "sql13.dts.designer.termextraction.advanced.f1"
helpviewer_keywords: 
  - "Éditeur de transformation d'extraction de terme"
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# &#201;diteur de transformation d&#39;extraction de terme (onglet Avanc&#233;)
  Utilisez l’onglet **Avancé** de la boîte de dialogue **Éditeur de transformation d’extraction de terme** pour définir les propriétés de l’extraction, telles que la fréquence et la longueur, et indiquer si les mots ou les phrases doivent être extraits.  
  
 Pour en savoir plus sur la transformation d'extraction de terme, consultez [Term Extraction Transformation](../../../integration-services/data-flow/transformations/term-extraction-transformation.md).  
  
## Options  
 **Nom**  
 Indique que la transformation extrait uniquement des noms individuels.  
  
 **Expression nominale**  
 Indique que la transformation extrait uniquement des expressions nominales.  
  
 **Nom et expression nominale**  
 Indique que la transformation extrait des noms et des expressions nominales.  
  
 **Fréquence**  
 Indique que le score correspond à la fréquence du terme.  
  
 **TFIDF**  
 Indique que le score correspond à la valeur TFIDF du terme. Le score TFIDF est le produit de la fréquence des termes (TF, Term Frequency) et de la fréquence inverse de documents (IDF, Inverse Document Frequency), défini comme suit : TFIDF d’un terme T = (fréquence de T) * log((#lignes en entrée) / (#lignes ayant T))  
  
 **Seuil de fréquence**  
 Définissez le nombre d'occurrences d'un mot ou d'une expression avant son extraction. La valeur par défaut est 2.  
  
 **Longueur maximale du terme**  
 Définissez la longueur maximale d'une expression en nombre de mots. Cette option affecte uniquement les expressions nominales. La valeur par défaut est 12.  
  
 **Utiliser l'extraction de terme respectant la casse**  
 Indiquez si l'extraction doit respecter la casse. La valeur par défaut est **False**.  
  
 **Configurer la sortie d'erreur**  
 Utilisez la boîte de dialogue [Configurer l’affichage des erreurs](../Topic/Configure%20Error%20Output.md) pour spécifier la gestion des erreurs dans les lignes qui provoquent des erreurs.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation d’extraction de terme &#40;onglet Extraction de terme&#41;](../../../integration-services/data-flow/transformations/term-extraction-transformation-editor-term-extraction-tab.md)   
 [Éditeur de transformation d’extraction de terme &#40;onglet Exclusion&#41;](../../../integration-services/data-flow/transformations/term-extraction-transformation-editor-exclusion-tab.md)   
 [Transformation de recherche de terme](../../../integration-services/data-flow/transformations/term-lookup-transformation.md)  
  
  