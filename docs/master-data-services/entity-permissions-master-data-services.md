---
title: "Autorisations d&#39;entit&#233; (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "entités [Master Data Services], autorisations"
  - "autorisations [Master Data Services], entités"
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Autorisations d&#39;entit&#233; (Master Data Services)
  Les autorisations d'entité s'appliquent à :  
  
-   Les attributs de l’entité, y compris **Nom** et **Code**, pour les membres feuille et les membres consolidés.  
  
-   Les collections de l'entité.  
  
-   Appartenances et relations de hiérarchie explicites.  
  
 Lorsque vous avez une autorisation sur une entité, vous pouvez ajouter et supprimer des membres de l'entité, ses hiérarchies explicites et ses collections.  
  
> [!NOTE]  
>  Ces autorisations s’appliquent à la zone fonctionnelle **Explorateur** de l’interface utilisateur uniquement.  
  
|Autorisation|Description|  
|----------------|-----------------|  
|**Lecture**|L’utilisateur peut lire des membres, des attributs, des appartenances hiérarchiques ou des appartenances aux collections.|  
|**Créer**|L’utilisateur peut créer des membres et affecter des valeurs d’attribut lors de la création.|  
|**Update**|L’utilisateur peut mettre à jour des membres, des attributs, des appartenances hiérarchiques ou des appartenances aux collections.|  
|**Supprimer**|Un utilisateur peut supprimer des membres.|  
|**Refuser**|Refusez tous les accès à l’entité.|  
  
 Vous pouvez aussi combiner les autorisations d’accès pour la lecture, la création, la mise à jour et la suppression. Lorsque les autorisations de création, de mise à jour et de suppression sont attribuées, l’autorisation d’accès en lecture est attribuée automatiquement.  
  
## Voir aussi  
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Entités &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  