---
title: "Options des attributs fixes et variables (Assistant Dimension &#224; variation lente) | Microsoft Docs"
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
  - "sql13.dts.loaddimwizard.attriboption.f1"
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# Options des attributs fixes et variables (Assistant Dimension &#224; variation lente)
  Utilisez la boîte de dialogue **Options des attributs fixes et variables** pour spécifier comment répondre aux modifications apportées aux attributs fixes et variables.  
  
 Pour en savoir plus sur cet Assistant, consultez [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## Options  
 **Attributs fixes**  
 Pour les attributs fixes, indiquez si la tâche doit échouer lorsqu'un changement est détecté dans un attribut fixe.  
  
 **Modification des attributs**  
 Pour les attributs variables, spécifiez si la tâche doit modifier les enregistrements obsolètes ou expirés, en plus des enregistrements actuels, lorsqu'un changement est détecté dans un attribut variable. Un enregistrement expiré est un enregistrement qui a été remplacé par un enregistrement plus récent par une modification d'un attribut d'historique (modification de Type 2). La sélection de cette option peut imposer des exigences de traitement supplémentaires sur un objet multidimensionnel construit sur l'entrepôt de données relationnelles.  
  
## Voir aussi  
 [Configurer les sorties à l'aide de l'Assistant Dimension à variation lente](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  