---
title: Membres (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- leaf members [Master Data Services]
- consolidated members [Master Data Services]
- consolidated members [Master Data Services], about consolidated members
- members [Master Data Services], about members
- leaf members [Master Data Services], about leaf members
- members [Master Data Services]
ms.assetid: 0fda32b9-677d-4ba2-bb28-f76f2383a30f
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 8125a27eed225a137a5665d87c923271cb592859
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923992"
---
# <a name="members-master-data-services"></a>Membres (services de données de référence)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], les membres sont les données de référence physiques. Par exemple, un membre peut être un vélo Road-150 spécifique dans une entité Product ou un client spécifique dans une entité Customer.  
  
## <a name="how-members-relate-to-other-model-objects"></a>Relations entre les membres et les autres objets de modèle  
 Vous pouvez considérer les membres comme les lignes d'une table. Les membres associés sont contenus dans une entité et chaque membre est défini par des valeurs d'attribut.  
  
 Dans cet exemple, la table représente une entité, les lignes de la table des membres et les colonnes de la table des attributs. Chaque cellule représente une valeur d'attribut pour un membre spécifique.  
  
 ![Entité Master Data Services représentée en tant que table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Entité Master Data Services représentée en tant que table")  
  
## <a name="member-types"></a>Types de membres  
 Il existe trois types de membres : les membres feuille, les membres consolidés et les membres de collection.  
  
 Les membres feuille sont les membres par défaut d'une entité.  
  
-   Dans les hiérarchies dérivées, les membres feuille sont le seul type de membre. Les membres feuille d'une entité sont utilisés comme parents des membres feuille d'une autre entité.  
  
-   Dans les hiérarchies explicites, les membres feuille représentent le niveau le plus bas et ils ne peuvent pas avoir d'enfants.  
  
 Les membres consolidés existent uniquement quand les hiérarchies explicites et les collections sont activées pour une entité.  
  
-   Les hiérarchies dérivées ne contiennent pas de membres consolidés.  
  
-   Dans les hiérarchies explicites, les membres consolidés peuvent être les parents d'autres membres de la hiérarchie, ou être les enfants.  
  
## <a name="use-hierarchies-and-collections-to-organize-members"></a>Utiliser des hiérarchies et des collections pour organiser des membres  
 Les hiérarchies et les collections permettent de regrouper des membres pour la création de rapports ou l'analyse. Pour plus d’informations, consultez [Hierarchies &#40;Master Data Services&#41;](hierarchies-master-data-services.md) et [Collections &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md).  
  
## <a name="member-example"></a>Exemple de membre  
 Dans l'exemple suivant, chaque membre est constitué d'une valeur d'attribut : Name, Code, Subcategory, StandardCost, ListPrice et FilePhoto.  
  
 ![Table de l’entité Bike Product](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Table de l’entité Bike Product")  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créez un membre feuille.|[Créer un membre feuille &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)|  
|Créez un membre consolidé.|[Créer un membre consolidé &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)|  
|Supprimez une collection ou un membre existant.|[Supprimer un membre ou une collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md)|  
|Réactivez une collection ou un membre supprimé.|[Réactiver un membre ou une collection &#40;Master Data Services&#41;](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)|  
|Mettez à jour les valeurs d'attribut d'un membre.|[Modifier le type d’attribut &#40;Complément MDS pour Excel&#41;](microsoft-excel-add-in/change-the-attribute-type-mds-add-in-for-excel.md)|  
|Déplacez des membres au sein d'une hiérarchie.|[Déplacer des membres dans une hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Vue d’ensemble de Master Data Services](master-data-services-overview-mds.md)  
  
-   [Entités &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md)  
  
-   [Attributs &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
-   [Hiérarchies &#40;Master Data Services&#41;](hierarchies-master-data-services.md)  
  
-   [Collections &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md)  
  
-   [Autorisations de feuille &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)  
  
-   [Consolidés autorisations &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
-   [Opérateurs de filtre &#40;Master Data Services&#41;](../../2014/master-data-services/filter-operators-master-data-services.md)  
  
  
