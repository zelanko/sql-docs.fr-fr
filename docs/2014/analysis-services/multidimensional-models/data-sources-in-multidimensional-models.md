---
title: Sources de données dans les modèles multidimensionnels | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [Analysis Services]
- Analysis Services objects, data sources
- storing data [Analysis Services], data sources
- data sources [Analysis Services], about data sources
- security [Analysis Services], data sources
- data sources [Analysis Services]
- storage [Analysis Services], data sources
ms.assetid: a16469d9-9d53-4e35-9982-fc06327a9d33
caps.latest.revision: 44
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 962e4cf17f53db60f3f766e1bd4432b1bd07df69
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267635"
---
# <a name="data-sources-in-multidimensional-models"></a>Sources de données dans des modèles multidimensionnels
  Toutes les données que vous importez ou chargez dans un modèle multidimensionnel proviennent d'une source de données externe. En général, les données source proviennent d’un entrepôt de données conçu pour générer des rapports, mais elles peuvent provenir de n’importe quelle base de données relationnelle, accessible directement ou indirectement via un intermédiaire, tel qu’un package [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Un objet **source de données** dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] spécifie une connexion directe à une source de données externe. En plus de l'emplacement physique, un objet de source de données spécifie la chaîne de connexion, le fournisseur de données, les informations d'identification et d'autres propriétés qui contrôlent le comportement de connexion.  
  
 Les informations fournies par l'objet source de données sont utilisées pour les opérations suivantes :  
  
-   Obtenir des informations sur le schéma et d'autres métadonnées utilisées pour générer des vues de sources de données dans un modèle.  
  
-   Interroger ou charger des données dans un modèle lors du traitement.  
  
-   Exécuter des requêtes dans des modèles multidimensionnels ou d'exploration de données qui utilisent le mode de stockage ROLAP.  
  
-   Écrire ou lire des partitions distantes.  
  
-   Établir une connexion à des objets liés et effectuer une synchronisation de la cible vers la source.  
  
-   Effectuer des opérations de réécriture qui mettent à jour les données de la table de faits stockées dans une base de données relationnelle.  
  
 Au moment de la création d’un modèle multidimensionnel, vous commencez par créer l’objet source de données, puis vous l’utilisez pour générer l’objet suivant, une **vue de source de données**. Une vue de source de données est la couche d'abstraction de données dans le modèle. Il est généralement créée après l'objet source de données, à l'aide du schéma de la base de données source comme base. Toutefois, vous pouvez choisir d'autres méthodes pour générer un modèle, y compris commencer par les cubes et les dimensions et générer le schéma qui prend le mieux en charge votre conception.  
  
 Quelle que soit la méthode de création choisie, chaque modèle requiert au moins un objet source de données qui spécifie une connexion aux données source. Vous pouvez créer plusieurs objets sources de données dans un modèle unique pour utiliser des données provenant de différentes sources ou modifier les propriétés de connexion d'objets spécifiques.  
  
 Les objets sources de données peuvent être gérés indépendamment des autres objets dans votre modèle. Après avoir créé une source de données, vous pouvez modifier ses propriétés ultérieurement, puis prétraiter le modèle pour vous assurer que les données sont récupérées correctement.  
  
## <a name="related-topics-and-tasks"></a>Tâches et rubriques connexes  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Sources de données prises en charge &#40;SSAS multidimensionnel&#41;](supported-data-sources-ssas-multidimensional.md)|Décrit les types de sources de données qui peuvent être utilisés dans un modèle multidimensionnel.|  
|[Créer une Source de données &#40;SSAS multidimensionnel&#41;](create-a-data-source-ssas-multidimensional.md)|Explique comment ajouter un objet de source de données à un modèle multidimensionnel.|  
|[Supprimer une Source de données dans l’Explorateur de solutions &#40;SSAS multidimensionnel&#41;](delete-a-data-source-in-solution-explorer-ssas-multidimensional.md)|Utilisez cette procédure pour supprimer un objet de source de données d'un modèle multidimensionnel.|  
|[Définir les propriétés de Source de données &#40;SSAS multidimensionnel&#41;](set-data-source-properties-ssas-multidimensional.md)|Décrit chaque propriété et explique comment la définir.|  
|[Définir les Options de l’emprunt d’identité &#40;SSAS - multidimensionnel&#41;](set-impersonation-options-ssas-multidimensional.md)|Explique comment configurer les options dans la boîte de dialogue Informations d'emprunt d'identité.|  
  
## <a name="see-also"></a>Voir aussi  
 [Objets de base de données &#40;Analysis Services - données multidimensionnelles&#41;](olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [Architecture logique &#40;Analysis Services - données multidimensionnelles&#41;](olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Vues de sources de données dans les modèles multidimensionnels](data-source-views-in-multidimensional-models.md)   
 [Sources de données et liaisons &#40;SSAS multidimensionnel&#41;](data-sources-and-bindings-ssas-multidimensional.md)  
  
  
