---
title: "Exploration de données (SSAS) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], about data mining
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 23048ed60a625a573d4820435f4ba87c0375e013
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="data-mining-ssas"></a>Data Mining (SSAS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est la première solution d’analyse prédictive depuis la version 2000, qui a introduit l’exploration de données dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. La combinaison d’ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]et de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Mining fournit une plateforme intégrée pour l’analyse prédictive qui englobe la préparation et le nettoyage des données, l’apprentissage automatique et la création de rapports. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Mining inclut de nombreux algorithmes standard, y compris les modèles de clustering EM et K-means, les réseaux neuronaux, les régressions logistique et linéaire, les arbres de décision et les classifieurs Naive Bayes. Tous les modèles proposent des visualisations destinées à vous aider à concevoir, ajuster et évaluer vos modèles.  L’intégration de l’exploration des données dans une solution d’aide à la décision vous permet de prendre des décisions plus avisées concernant des problèmes complexes.  
  
## <a name="benefits-of-data-mining"></a>Avantages de l’exploration de données  
 L’exploration des données (également appelée analyse prédictive ou apprentissage automatique) utilise les principes statistiques bien connus pour découvrir des modèles dans vos données. En appliquant les algorithmes d'exploration de données dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à vos données, vous pouvez prévoir des tendances, identifier des modèles, créer des règles et des recommandations, analyser la séquence d'événements dans des jeux de données complexes et bénéficier de nouvelles analyses.  
  
 Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], l’exploration des données est une fonctionnalité puissante et accessible, qui est intégrée aux principaux outils utilisés pour effectuer des analyses et créer des rapports.  
  
## <a name="key-data-mining-features"></a>Fonctionnalités d'exploration de données clés  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Mining fournit les fonctionnalités suivantes pour la prise en charge des solutions d’exploration de données intégrées :  
  
-   Sources de données multiples : vous pouvez utiliser n’importe quelle source de données tabulaires pour l’exploration des données, y compris des fichiers texte et des feuilles de calcul. Vous pouvez aussi facilement exploiter les cubes OLAP créés dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Toutefois, vous ne pouvez pas utiliser les données d'une base de données en mémoire.  
  
-   Intégration du nettoyage des données, de la gestion des données et de la création de rapports : [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fournit des outils de profilage et de nettoyage des données. Vous pouvez créer des processus ETL pour nettoyer les données préalablement à la modélisation. De plus, ssISnoversion facilite la conservation et la mise à jour des modèles.  
  
-   Plusieurs algorithmes personnalisables : outre la mise à disposition d’algorithmes comme le clustering, les réseaux neuronaux et les arbres de décision, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Mining prend en charge le développement de vos propres algorithmes de plug-in personnalisés.  
  
-   Infrastructure de test de modèle : testez vos modèles et jeux de données à l'aide d'outils statistiques importants comme la validation croisée, les matrices de classification, les graphiques de courbes d'élévation et les nuages de points. Créez et gérez facilement des jeux d'apprentissage et de test.  
  
-   Interrogation et extraction : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Mining fournit le langage DMX permettant d’intégrer des requêtes de prédiction dans des applications. Vous pouvez également récupérer des statistiques détaillées et des schémas à partir des modèles, et effectuer une extraction de données de cas.  
  
-   Outils clients : outre les studios de développement et de conception fournis par SQL Server, vous pouvez utiliser les compléments d'exploration de données pour Excel afin de créer, interroger et parcourir des modèles. Vous pouvez également créer des clients personnalisés, notamment des services Web.  
  
-   Prise en charge du langage de script et des API managées : tous les objets d'exploration de données sont entièrement programmables. La création de scripts est possible grâce à MDX, XMLA ou aux extensions PowerShell pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Utilisez le langage DMX (Data Mining Extensions) pour la création rapide de requêtes et de scripts.  
  
-   Sécurité et déploiement : fournit la sécurité basée sur les rôles via [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], notamment les autorisations distinctes pour l’extraction des données de structure et de modèle. Déploiement simple des modèles vers d'autres serveurs, afin que les utilisateurs puissent accéder aux modèles ou effectuer des prédictions  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques de cette section présentent les principales fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Mining et les tâches associées.  
  
-   [Concepts d'exploration de données](../../analysis-services/data-mining/data-mining-concepts.md)  
  
-   [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)  
  
-   [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
-   [Modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
-   [Test et validation &#40;exploration de données&#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)  
  
-   [Requêtes d'exploration de données](../../analysis-services/data-mining/data-mining-queries.md)  
  
-   [Solutions d'exploration de données](../../analysis-services/data-mining/data-mining-solutions.md)  
  
-   [Outils d'exploration de données](../../analysis-services/data-mining/data-mining-tools.md)  
  
-   [Architecture d'exploration de données](../../analysis-services/data-mining/data-mining-architecture.md)  
  
-   [Vue d’ensemble de la sécurité &#40;exploration de données&#41;](../../analysis-services/data-mining/security-overview-data-mining.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  

