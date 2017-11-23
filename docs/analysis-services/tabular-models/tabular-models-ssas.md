---
title: "Les modèles tabulaires (SSAS) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: 1d770b114a708301f884de76d7c6a4cc39227195
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="tabular-modeling-ssas"></a>Modélisation tabulaire (SSAS)
  Les modèles tabulaires sont des bases de données Analysis Services qui s’exécutent en mémoire ou en mode DirectQuery, en accédant aux données directement à partir de sources de données relationnelles principales.  
  
 Par défaut, l’exécution s’effectue en mémoire. À l’aide d’algorithmes de compression de pointe et du processeur de requêtes multithread, le moteur analytique en mémoire permet un accès rapide aux objets de modèles tabulaires et aux données par les applications clientes de création de rapports telles que Microsoft Excel et Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].  
  
 DirectQuery est un mode de requête alternatif pour les modèles qui sont trop volumineux pour tenir dans la mémoire, ou lorsque la volatilité des données empêche la mise en place d’une stratégie de traitement raisonnable. Dans cette version, DirectQuery garantit une meilleure parité avec les modèles en mémoire via la prise en charge des sources de données supplémentaires, la possibilité de gérer les tables et les colonnes calculées dans un modèle DirectQuery, la sécurité de niveau ligne via les expressions DAX qui atteignent la base de données principale et les optimisations de requêtes qui assurent un débit plus rapide que dans les versions précédentes.
  
 Les modèles tabulaires sont créés dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] à l’aide du modèle de projet de modèle tabulaire qui fournit un espace de conception pour la création d’un modèle, de tables, de relations et d’expressions DAX. Vous pouvez importer des données depuis plusieurs sources, puis enrichir le modèle en ajoutant des relations, des colonnes et des tables calculées, des mesures, des indicateurs de performance clés, des hiérarchies et des traductions.  
  
 Des modèles peuvent ensuite être déployés sur une instance d’Analysis Services configurée pour le mode de serveur Tabulaire, à laquelle les applications clientes de création de rapports peuvent se connecter. Les modèles déployés peuvent être gérés dans SQL Server Management Studio comme tous les modèles multidimensionnels. Ils peuvent également être partitionnés pour un traitement optimisé et être sécurisés au niveau de la ligne à l'aide de la sécurité basée sur le rôle.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Solutions de modèles tabulaires &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/tabular-model-solutions-ssas-tabular.md) - Les rubriques de cette section décrivent la création et le déploiement de solutions de modèles tabulaires.
  
 [Bases de données de modèles tabulaires &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md) - Les rubriques de cette section décrivent la gestion des solutions de modèles tabulaires déployées.
  
 [Accès aux données de modèle tabulaire](../../analysis-services/tabular-models/tabular-model-data-access.md) - Les rubriques de cette section décrivent la connexion aux solutions de modèles tabulaires déployées.
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés d’Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Comparaison des solutions tabulaires et multidimensionnelles &#40;SSAS&#41;](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Outils et applications utilisés dans Analysis Services](../../analysis-services/tools-and-applications-used-in-analysis-services.md)   
 [Mode DirectQuery &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Niveau de compatibilité pour les modèles tabulaires dans Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
