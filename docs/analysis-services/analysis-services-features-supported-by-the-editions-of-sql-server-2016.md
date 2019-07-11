---
title: Fonctionnalités Analysis Services prises en charge par les éditions de SQL Server | Microsoft Docs
ms.date: 07/10/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6d4f0cc16638963dbbbb091bc19cade36e45fe3b
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792551"
---
# <a name="analysis-services-features-supported-by-sql-server-edition"></a>Fonctionnalités Analysis Services prises en charge par l’édition de SQL Server

[!INCLUDE[ssas-appliesto-sql2016-later](../includes/ssas-appliesto-sql2016-later.md)]

Cet article décrit les fonctionnalités prises en charge par les différentes éditions de SQL Server 2016, 2017, 2019 Analysis Services. Version d’évaluation prend en charge les fonctionnalités de l’édition Enterprise.

## <a name="analysis-services-servers"></a>Analysis Services (serveurs)
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Développeur|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Bases de données partagées évolutives|Oui||||||Oui|  
|Sauvegarder/Restaurer et Attacher/Détacher des bases de données|Oui|Oui|||||Oui|  
|Synchroniser des bases de données|Oui||||||Oui|  
|Instances de cluster de basculement Always On|Oui<br /><br /> Le nombre de nœuds correspond au maximum du système d’exploitation|Oui<br /><br /> Prise en charge de 2 nœuds|||||Oui<br /><br /> Le nombre de nœuds correspond au maximum du système d’exploitation|  
|Programmabilité (AMO, ADOMD.Net, OLEDB, XML/A, ASSL, TMSL)|Oui|Oui|||||Oui|  
  
## <a name="tabular-models"></a>Modèles tabulaires 
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Développeur|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Hierarchies|Oui|Oui|||||Oui|  
|Indicateurs de performance clés|Oui|Oui|||||Oui|  
|Perspectives|Oui||||||Oui|  
|Translations|Oui|Oui|||||Oui|  
|Calculs DAX, requêtes DAX, requêtes MDX|Oui|Oui|||||Oui|  
|Sécurité au niveau des lignes|Oui|Oui|||||Oui|  
|Partitions multiples|Oui||||||Oui|  
|Groupes de calcul|Oui (à partir de SQL Server 2019)|Oui (à partir de SQL Server 2019)|||||Oui (à partir de SQL Server 2019)|  
|Mode de stockage en mémoire|Oui|Oui|||||Oui|  
|Mode DirectQuery|Oui|Oui (à partir de SQL Server 2019)|||||Oui|  

## <a name="multidimensional-models"></a>Modèles multidimensionnels 
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Développeur|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Mesures semi-additives|Oui|Ne <sup> [1](#sameas)</sup>|||||Oui|  
|Hierarchies|Oui|Oui|||||Oui|  
|Indicateurs de performance clés|Oui|Oui|||||Oui|  
|Perspectives|Oui||||||Oui|  
|Actions|Oui|Oui|||||Oui|  
|Intelligence comptable|Oui|Oui|||||Oui|  
|Time Intelligence|Oui|Oui|||||Oui|  
|Cumuls personnalisés|Oui|Oui|||||Oui|  
|Cube d'écriture différée|Oui|Oui|||||Oui|  
|Dimensions d'écriture différée|Oui <sup>[2](#wb)</sup>||||||Oui <sup>[2](#wb)</sup>|  
|Cellules d'écriture différée|Oui|Oui|||||Oui|  
|Extraction|Oui|Oui|||||Oui|  
|Types de hiérarchies avancés (parent-enfant et irrégulières)|Oui|Oui|||||Oui|  
|Dimensions avancées (dimensions de référence, plusieurs-à-plusieurs)|Oui|Oui|||||Oui|  
|Dimensions et mesures liées|Oui|Oui <sup> [3](#linkmd)</sup> |||||Oui|  
|Translations|Oui|Oui|||||Oui|  
|Aggregations|Oui|Oui|||||Oui|  
|Partitions multiples|Oui|Oui, jusqu'à 3|||||Oui|  
|Mise en cache proactive|Oui||||||Oui|  
|Assemblys personnalisés (procédures stockées)|Oui|Oui|||||Oui|  
|Requêtes et scripts MDX|Oui|Oui|||||Oui|  
|Requêtes DAX|Oui|Oui|||||Oui|  
|Modèle de sécurité basé sur les rôles|Oui|Oui|||||Oui|  
|Sécurité au niveau de la dimension et de la cellule|Oui|Oui|||||Oui|  
|Stockage évolutif de chaîne|Oui|Oui|||||Oui|  
|Modèles de stockage MOLAP, ROLAP et HOLAP|Oui|Oui|||||Oui|  
|Transport XML binaire et compressé|Oui|Oui|||||Oui|  
|Traitement de type envoi de données (push)|Oui||||||Oui|  
|Expressions de mesure|Oui||||||Oui|  
  
<a name="sameas">[1] </a> The semi-additive LastChild est prise en charge dans l’Édition Standard, mais d’autres mesures semi-additives, telles que None, FirstChild, FirstNonEmpty, LastNonEmpty, AverageOfChildren et ByAccount, ne sont pas. Les mesures additives, telles que Sum, Count, Min, Max, et les mesures non additives (DistinctCount) sont prises en charge dans toutes les éditions. 

<a name="wb">[2] </a> L’écriture différée des dimensions sont supprimées dans SQL Server Analysis Services 2019 et versions ultérieures.
 
<a name="linkmd">[3] </a> Standard edition prend en charge la liaison des mesures et dimensions dans la même base de données, mais pas à partir de bases de données ou des autres instances.
  
  
## <a name="power-pivot-for-sharepoint"></a>Power Pivot pour SharePoint  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Développeur|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Intégration de batterie de serveurs SharePoint selon l'architecture de service partagé|Oui||||||Oui|  
|Création de rapports d'utilisation|Oui||||||Oui|  
|Règles de contrôle d'intégrité|Oui||||||Oui|  
|Galerie Power Pivot|Oui||||||Oui|  
|Actualisation des données Power Pivot|Oui||||||Oui|  
|Flux de données Power Pivot|Oui||||||Oui|  
  
## <a name="data-mining"></a>Exploration de données  

> [!NOTE]
> Exploration de données est [déconseillée](analysis-services-backward-compatibility-sql2017.md#deprecated-features) dans SQL Server Analysis Services 2017.
  
|Nom de la fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Développeur|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Algorithmes standard|Oui|Oui|||||Oui|  
|Outils d’exploration de données (Assistants, éditeurs, générateurs de requêtes)|Oui|Oui|||||Oui|  
|Validation croisée|Oui||||||Oui|  
|Modèles sur les sous-ensembles filtrés de données de structure d'exploration de données|Oui||||||Oui|  
|Série chronologique : Fusion personnalisée entre les méthodes ARTXP et ARIMA|Oui||||||Oui|  
|Série chronologique : PRÉDICTION avec de nouvelles données|Oui||||||Oui|  
|Requêtes d’exploration de données simultanées illimitées|Oui||||||Oui|  
|Configuration avancée et options de paramétrage pour les algorithmes d’exploration de données|Oui||||||Oui|  
|Prise en charge des algorithmes de plug-in|Oui||||||Oui|  
|Traitement de modèle parallèle|Oui||||||Oui|  
|Série chronologique : prédiction inter-série|Oui||||||Oui|  
|Attributs illimités pour les règles d'association|Oui||||||Oui|  
|Prédiction de séquence|Oui||||||Oui|  
|Plusieurs cibles de prédiction pour naïve Bayes, réseau neuronal et régression logistique|Oui||||||Oui|  
  


