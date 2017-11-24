---
title: "Hiérarchies dérivées avec des niveaux supérieurs d’une hiérarchie dérivée (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies [Master Data Services], derived hierarchies with explicit caps
- explicit hierarchies, derived hierarchies with explicit caps
- derived hierarchies, derived hierarchies with explicit caps
ms.assetid: 6a82ff66-c137-4757-99bb-787d189b4295
caps.latest.revision: "7"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 67b1d04dfc8e5e220b3b911db0af7f434da1a51a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="derived-hierarchies-with-explicit-caps-master-data-services"></a>Hiérarchies dérivées avec un niveau supérieur composé d'une hiérarchie explicite (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], si une hiérarchie dérivée inclut une hiérarchie explicite, les niveaux de la hiérarchie explicite sont utilisés comme niveaux supérieurs de la hiérarchie dérivée.  
  
 La hiérarchie explicite doit être basée sur la même entité que celle située au sommet de la hiérarchie dérivée.  
  
 Dans l’interface utilisateur de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , vous créez ce type de hiérarchie en faisant glisser une hiérarchie explicite au sommet d’une hiérarchie dérivée.  
  
 ![mds_conc_explicit_cap_UI_structure](../master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")  
  
## <a name="derived-hierarchy-with-explicit-cap-example"></a>Exemple de hiérarchie dérivée avec niveau supérieur  
 Dans cet exemple, les membres de la hiérarchie explicite proviennent de l'entité Subcategory. Dans la hiérarchie dérivée, les membres de niveau supérieur proviennent également de l'entité Subcategory.  
  
 ![mds_conc_explicit_cap_UI_example](../master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")  
  
 En utilisant la hiérarchie explicite au sommet d'une hiérarchie dérivée, la hiérarchie dérivée devient déséquilibrée.  
  
## <a name="rules"></a>Règles  
  
-   Une hiérarchie dérivée avec un niveau supérieur ne peut inclure qu'une seule hiérarchie explicite.  
  
-   Vous pouvez utiliser la même hiérarchie explicite comme niveau supérieur dans plusieurs hiérarchies dérivées.  
  
-   Vous ne pouvez pas affecter d'autorisations de membre de hiérarchie à des hiérarchies dérivées avec un niveau supérieur d'une hiérarchie dérivée. Si vous affectez des autorisations individuellement à la hiérarchie explicite ou à la hiérarchie dérivée, les autorisations s'appliquent aux deux hiérarchies.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créer une hiérarchie dérivée.|[Créer une hiérarchie dérivée &#40;Master Data Services&#41;](../master-data-services/create-a-derived-hierarchy-master-data-services.md)|  
|Créer une hiérarchie explicite.|[Créer une hiérarchie explicite &#40;Master Data Services&#41;](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)|  
|Supprimer une hiérarchie dérivée existante.|[Supprimer une hiérarchie dérivée &#40;Master Data Services&#41;](../master-data-services/delete-a-derived-hierarchy-master-data-services.md)|  
|||  
  
## <a name="related-content"></a>Contenu connexe  
  
-   [Hiérarchies dérivées &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
-   [Hiérarchies explicites &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
