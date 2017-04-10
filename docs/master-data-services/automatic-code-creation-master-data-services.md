---
title: "Cr&#233;ation automatique de code (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Cr&#233;ation automatique de code (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez générer automatiquement des valeurs numériques pour l'attribut Code, ou pour toute autre attribut numérique. Lorsque vous générez les codes automatiquement, rien n'empêche de saisir d'autres valeurs pour les codes ; sinon, une valeur initiale est définie automatiquement.  
  
## Génération de valeurs de code  
 Les administrateurs peuvent configurer des valeurs générées automatiquement pour l'attribut Code en modifiant les propriétés de l'entité associée. Ils peuvent spécifier une valeur initiale, et chaque valeur suivante est augmentée d'une unité.  
  
 Lorsque vous entrez des valeurs Code dans MDS, dans l'un des outils ou à l'aide du processus de site, vous pouvez laisser la valeur Code vide pour qu'elle soit générée automatiquement. Ou vous pouvez spécifier une valeur de code de votre choix.  
  
## Génération d'autres valeurs d'attribut  
 Les administrateurs peuvent générer automatiquement des valeurs pour les attributs autres que le code en créant des règles d'entreprise. Ils peuvent spécifier une valeur initiale, puis le nombre avec lequel chaque valeur suivante est incrémentée.  
  
 Lorsque vous entrez des valeurs d'attribut dans MDS, dans l'un des outils ou à l'aide du processus de site, vous pouvez laisser les valeurs d'attribut vides. Lorsque les règles d'entreprise sont appliquées, les valeurs seront incrémentées en fonction de la valeur existante la plus élevée. Par exemple, si votre règle est « Attribut par défaut avec une valeur générée qui commence à 1 et est incrémentée par 4 » et que la valeur courante la plus élevée pour l'attribut est 700, la valeur du membre suivant ajouté sera 704.  
  
## Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Générez automatiquement les valeurs de l'attribut code.|[Générer automatiquement les valeurs de l’attribut Code &#40;Master Data Services&#41;](../master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|Générez automatiquement les valeurs des autres attributs.|[Générer automatiquement les valeurs des attributs autres que Code &#40;Master Data Services&#41;](../master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## Contenu connexe  
  
-   [Vue d’ensemble de Master Data Services &#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)  
  
-   [Règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [Entités &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  