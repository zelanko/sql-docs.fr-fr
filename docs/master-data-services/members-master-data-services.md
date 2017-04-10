---
title: "Membres (services de donn&#233;es de r&#233;f&#233;rence) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "membres feuille [Master Data Services]"
  - "membres consolidés [Master Data Services]"
  - "membres consolidés [Master Data Services], à propos des membres consolidés"
  - "membres [Master Data Services], à propos des membres"
  - "membres feuille [Master Data Services], à propos des membres feuille"
  - "membres [Master Data Services]"
ms.assetid: 0fda32b9-677d-4ba2-bb28-f76f2383a30f
caps.latest.revision: 16
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 14
---
# Membres (services de donn&#233;es de r&#233;f&#233;rence)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], les membres sont les données de référence physiques. Par exemple, un membre peut être un vélo Road-150 spécifique dans une entité Product ou un client spécifique dans une entité Customer.  
  
## Relations entre les membres et les autres objets de modèle  
 Vous pouvez considérer les membres comme les lignes d'une table. Les membres associés sont contenus dans une entité et chaque membre est défini par des valeurs d'attribut.  
  
 Dans cet exemple, la table représente une entité, les lignes de la table des membres et les colonnes de la table des attributs. Chaque cellule représente une valeur d'attribut pour un membre spécifique.  
  
 ![Entité Master Data Services représentée en tant que table](../master-data-services/media/mds-conc-entity-table.gif "Entité Master Data Services représentée en tant que table")  
  
## Types de membres  
 Il existe trois types de membres : les membres feuille, les membres consolidés et les membres de collection.  
  
 Les membres feuille sont les membres par défaut d'une entité.  
  
-   Dans les hiérarchies dérivées, les membres feuille sont le seul type de membre. Les membres feuille d'une entité sont utilisés comme parents des membres feuille d'une autre entité.  
  
-   Dans les hiérarchies explicites, les membres feuille représentent le niveau le plus bas et ils ne peuvent pas avoir d'enfants.  
  
 Les membres consolidés existent uniquement quand les hiérarchies explicites et les collections sont activées pour une entité.  
  
-   Les hiérarchies dérivées ne contiennent pas de membres consolidés.  
  
-   Dans les hiérarchies explicites, les membres consolidés peuvent être les parents d'autres membres de la hiérarchie, ou être les enfants.  
  
## Utiliser des hiérarchies et des collections pour organiser des membres  
 Les hiérarchies et les collections permettent de regrouper des membres pour la création de rapports ou l'analyse. Pour plus d’informations, consultez [Hiérarchies &#40;Master Data Services&#41;](../master-data-services/hierarchies-master-data-services.md) et [Collections &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md).  
  
## Exemple de membre  
 Dans l'exemple suivant, chaque membre est constitué d'une valeur d'attribut : Name, Code, Subcategory, StandardCost, ListPrice et FilePhoto.  
  
 ![Table de l'entité Bike Product](../master-data-services/media/mds-conc-entity-table-w-data.gif "Table de l'entité Bike Product")  
  
## Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créez un membre feuille.|[Créer un membre feuille &#40;Master Data Services&#41;](../master-data-services/create-a-leaf-member-master-data-services.md)|  
|Créez un membre consolidé.|[Créer un membre consolidé &#40;Master Data Services&#41;](../master-data-services/create-a-consolidated-member-master-data-services.md)|  
|Supprimez une collection ou un membre existant.|[Supprimer un membre ou une collection &#40;Master Data Services&#41;](../master-data-services/delete-a-member-or-collection-master-data-services.md)|  
|Réactivez une collection ou un membre supprimé.|[Réactiver un membre ou une collection &#40;Master Data Services&#41;](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)|  
|Mettez à jour les valeurs d'attribut d'un membre.|[Modifier le type d’attribut &#40;Complément MDS pour Excel&#41;](../master-data-services/microsoft-excel-add-in/change-the-attribute-type-mds-add-in-for-excel.md)|  
|Déplacez des membres au sein d'une hiérarchie.|[Déplacer des membres au sein d’une hiérarchie &#40;Master Data Services&#41;](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)|  
|Corrigez les conflits de fusion.|[Fusionner les conflits &#40;Master Data Services&#41;](../master-data-services/merge-conflicts-master-data-services.md)|  
  
## Contenu connexe  
  
-   [Vue d’ensemble de Master Data Services &#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)  
  
-   [Entités &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
-   [Attributs &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
-   [Hiérarchies &#40;Master Data Services&#41;](../master-data-services/hierarchies-master-data-services.md)  
  
-   [Collections &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)  
  
-   [Autorisations de feuille &#40;Master Data Services&#41;](../master-data-services/leaf-permissions-master-data-services.md)  
  
-   [Autorisations consolidées &#40;Master Data Services&#41;](../Topic/Consolidated%20Permissions%20\(Master%20Data%20Services\).md)  
  
-   [Opérateurs de filtre &#40;Master Data Services&#41;](../master-data-services/filter-operators-master-data-services.md)  
  
  