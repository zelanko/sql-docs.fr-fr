---
title: Exploration de données (SSAS) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], about data mining
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b118f03580aeb0053203cd2535bafecd1649ccb4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142381"
---
# <a name="data-mining-ssas"></a>Data Mining (SSAS)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit une plateforme intégrée pour les solutions qui intègrent l'exploration de données. Vous pouvez utiliser des données de cube ou relationnelles pour créer des solutions décisionnelles avec des analyses prévisionnelles.  
  
## <a name="benefits-of-data-mining"></a>Avantages de l’exploration de données  
 L'exploration de données utilise les principes statistiques bien connus pour découvrir des modèles dans vos données, afin de prendre des décisions réfléchies concernant des problèmes complexes. En appliquant les algorithmes d'exploration de données dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à vos données, vous pouvez prévoir des tendances, identifier des modèles, créer des règles et des recommandations, analyser la séquence d'événements dans des jeux de données complexes et bénéficier de nouvelles analyses.  
  
 Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], l’exploration des données est une fonctionnalité puissante et accessible, qui est intégrée aux principaux outils utilisés pour effectuer des analyses et créer des rapports. Consultez les liens de cette section pour connaître la structure générale de l'exploration de données dont vous avez besoin pour commencer.  
  
## <a name="key-data-mining-features"></a>Fonctionnalités d'exploration de données clés  
 SQL Server fournit les fonctionnalités suivantes pour la prise en charge des solutions d'exploration de données intégrées :  
  
-   Plusieurs sources de données : vous n'avez pas à créer d'entrepôt de données ni de cube OLAP pour effectuer l'exploration de données. Vous pouvez utiliser des données tabulaires, des feuilles de calcul et même des fichiers texte provenant de fournisseurs externes. Vous pouvez aussi facilement exploiter les cubes OLAP créés dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Toutefois, vous ne pouvez pas utiliser les données d'une base de données en mémoire.  
  
-   Nettoyage de données intégré, gestion des données et ETL (extraction, transformation et chargement) : Data Quality Services fournit des outils avancés pour le profilage et le nettoyage des données. Integration Services peut être utilisé pour générer des processus ETL pour nettoyer les données, ainsi que pour créer, traiter, effectuer l'apprentissage et mettre à jour des modèles.  
  
-   Plusieurs algorithmes personnalisables : outre la mise à disposition d'algorithmes comme le clustering, les réseaux neuronaux et les arbres de décision, la plateforme prend en charge le développement de vos propres algorithmes de plug-in personnalisés.  
  
-   Infrastructure de test de modèle : testez vos modèles et jeux de données à l'aide d'outils statistiques importants comme la validation croisée, les matrices de classification, les graphiques de courbes d'élévation et les nuages de points. Créez et gérez facilement des jeux d'apprentissage et de test.  
  
-   Interrogation et extraction : créez des requêtes de prédiction, récupérer les schémas et statistiques de modèles et explorez des données de cas.  
  
-   Outils clients : outre les studios de développement et de conception fournis par SQL Server, vous pouvez utiliser les compléments d'exploration de données pour Excel afin de créer, interroger et parcourir des modèles. Vous pouvez également créer des clients personnalisés, notamment des services Web.  
  
-   Prise en charge du langage de script et des API managées : tous les objets d'exploration de données sont entièrement programmables. La création de scripts est possible grâce à MDX, XMLA ou aux extensions PowerShell pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Utilisez le langage DMX (Data Mining Extensions) pour la création rapide de requêtes et de scripts.  
  
-   Sécurité et déploiement : fournit la sécurité basée sur les rôles via [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], notamment les autorisations distinctes pour l’extraction des données de structure et de modèle. Déploiement simple des modèles vers d'autres serveurs, afin que les utilisateurs puissent accéder aux modèles ou effectuer des prédictions  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques de cette section présentent les principales fonctionnalités de l'exploration de données et des tâches associées de SQL Server.  
  
-   [Concepts d’exploration de données](data-mining-concepts.md)  
  
-   [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md)  
  
-   [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-structures-analysis-services-data-mining.md)  
  
-   [Les modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-models-analysis-services-data-mining.md)  
  
-   [Test et Validation &#40;d’exploration de données&#41;](testing-and-validation-data-mining.md)  
  
-   [Requêtes d’exploration de données](data-mining-queries.md)  
  
-   [Solutions d’exploration de données](data-mining-solutions.md)  
  
-   [Outils d’exploration de données](data-mining-tools.md)  
  
-   [Architecture d’exploration de données](data-mining-architecture.md)  
  
-   [Vue d’ensemble de la sécurité &#40;d’exploration de données&#41;](security-overview-data-mining.md)  
  
  