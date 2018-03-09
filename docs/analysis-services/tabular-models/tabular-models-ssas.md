---
title: "Les modèles tabulaires | Documents Microsoft"
ms.custom: 
ms.date: 02/21/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: 2df607b47e4bb2a5a770e27d1bceb5a6d7e6ebbc
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="tabular-models"></a>Modèles tabulaires
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Les modèles tabulaires sont des bases de données Analysis Services qui s’exécutent en mémoire ou en mode DirectQuery, en accédant aux données directement à partir de sources de données relationnelles principales. À l’aide des algorithmes de compression de pointe et processeur de requêtes multithread, le moteur analytique permet un accès rapide aux données et objets de modèle tabulaire par le rapport d’applications clientes telles que Power BI et Excel.  
  
 Alors que les modèles en mémoire sont la valeur par défaut :, DirectQuery est un mode de requête alternatif pour les modèles qui sont trop volumineux pour tenir en mémoire, ou lorsque la volatilité des données empêche une stratégie de traitement raisonnable. DirectQuery permet d’obtenir la parité avec les modèles en mémoire prise en charge pour un large éventail de sources de données, permet de gérer les tables calculées et les colonnes dans un modèle DirectQuery, la sécurité de niveau ligne via des expressions DAX qui atteignent la base de données et de requête optimisations qui entraînent un débit plus rapide.
  
 Les modèles tabulaires sont créés dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] à l’aide du modèle de projet de modèle tabulaire qui fournit un espace de conception pour la création d’un modèle, de tables, de relations et d’expressions DAX. Vous pouvez importer des données depuis plusieurs sources, puis enrichir le modèle en ajoutant des relations, des colonnes et des tables calculées, des mesures, des indicateurs de performance clés, des hiérarchies et des traductions.  
  
 Les modèles peuvent ensuite être déployés sur Azure Analysis Services ou une instance de SQL Server Analysis Services est configuré pour le mode serveur tabulaire. Les modèles tabulaires déployés peuvent être gérés dans SQL Server Management Studio. À mesure que vos modèles augmentent, ils peuvent partitionnés pour un traitement optimisé et sécurisés au niveau de la ligne en utilisant la sécurité basée sur les rôles.  
  
## <a name="in-this-section"></a>Contenu de cette section  
 [Solutions de modèles tabulaires](../../analysis-services/tabular-models/tabular-model-solutions-ssas-tabular.md) -Articles de cette section décrivent la création et le déploiement des solutions de modèle tabulaire.
  
 [Bases de données model tabulaire](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md) -Articles de cette section décrivent la gestion des solutions de modèle tabulaire déployé.
  
 [Accès aux données de modèle tabulaire](../../analysis-services/tabular-models/tabular-model-data-access.md) -Articles de cette section décrivent la connexion au déploiement des solutions de modèle tabulaire.
  
## <a name="see-also"></a>Voir aussi  
 [Quelles sont les nouveautés dans Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Comparaison des solutions tabulaires et multidimensionnelles](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Outils et applications utilisés dans Analysis Services](../../analysis-services/tools-and-applications-used-in-analysis-services.md)   
 [Mode DirectQuery](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Niveau de compatibilité](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
