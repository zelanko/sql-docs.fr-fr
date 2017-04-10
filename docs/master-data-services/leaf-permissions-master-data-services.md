---
title: "Autorisations de feuille (services de donn&#233;es de r&#233;f&#233;rence) | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "groupes d’attributs [Master Data Services], autorisations"
  - "membres [Master Data Services], autorisations de membre feuille"
  - "autorisations [Master Data Services], membres feuille"
  - "membres feuille [Master Data Services], autorisations d’attribut"
  - "attributs [Master Data Services], autorisations d’attribut de membre feuille"
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Autorisations de feuille (services de donn&#233;es de r&#233;f&#233;rence)
  Les autorisations de feuille s'appliquent aux valeurs d'attribut pour tous les membres feuille d'une entité.  
  
 Pour les entités sans hiérarchies explicites activées, l'affectation d'une autorisation **Feuille** revient à affecter l'autorisation à l'entité.  
  
 **Remarques :**  
  
-   Les autorisations de feuille s'appliquent à la zone fonctionnelle **Explorateur** de l'interface utilisateur uniquement.  
  
-   Les autorisations attribuées à **Nom** et **Code** ne sont pas appliquées.  
  
|Autorisation|Description|  
|----------------|-----------------|  
|**Lecture**|L’utilisateur peut lire les membres feuille et les attributs.|  
|**Créer**|L’utilisateur peut créer des membres feuille et affecter des valeurs d’attribut lors de la création.|  
|**Update**|L’utilisateur peut mettre à jour les membres feuille et les attributs.|  
|**Delete**|L’utilisateur peut supprimer des membres feuille.|  
|**Refuser**|Refusez tout accès aux membres feuille.|  
  
 Vous pouvez aussi combiner les autorisations Read, Create, Update et Delete. Lorsque les autorisations Create, Update et Delete sont attribuées, l’autorisation Read est attribuée automatiquement.  
  
## Autorisations d'attribut  
 Les autorisations d'attribut s'appliquent aux valeurs de l'attribut pour l'entité spécifique. Les utilisateurs avec des autorisations d'attribut uniquement ne peuvent pas ajouter ni supprimer des membres.  
  
|Autorisation|Description|  
|----------------|-----------------|  
|**Lecture**|L’utilisateur peut lire des attributs.|  
|**Créer**|L’utilisateur peut attribuer des valeurs lorsqu’il crée des membres.|  
|**Update**|L’utilisateur peut mettre à jour des attributs.|  
|**Delete**|Aucun effet.|  
|**Refuser**|L'attribut n'est pas affiché.<br /><br /> Remarque : vous ne pouvez pas refuser explicitement l’accès aux attributs Name et Code.|  
  
### Exemple  
 Pour l'entité Product, affectez l'autorisation **Mise à jour** à l'attribut Subcategory. Autorisation refuser à tous les autres attributs.  
  
|Nom|Code|Subcategory (Mise à jour)|  
|----------|----------|----------------------------|  
|Mountain-100|BK-M101|\{5\} Mountain Bikes|  
|Mountain-100|BK-M201|\{5\} Mountain Bikes|  
  
 Dans l' **Explorateur**, vous pouvez mettre à jour toute valeur d'attribut de la colonne Subcategory. Si vous n'avez pas d'autorisation sur un attribut, l'attribut n'est pas affiché.  
  
> [!NOTE]  
>  Dans cet exemple, Subcategory est un attribut basé sur un domaine, basé sur l'entité SubcategoryList. Vous pouvez sélectionner une sous-catégorie différente pour Mountain-100, mais vous ne pouvez pas ajouter ni supprimer des membres dans l'entité SubcategoryList.  
  
## Voir aussi  
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Autorisations consolidées &#40;Master Data Services&#41;](../Topic/Consolidated%20Permissions%20\(Master%20Data%20Services\).md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Membres &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)   
 [Attributs &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
  