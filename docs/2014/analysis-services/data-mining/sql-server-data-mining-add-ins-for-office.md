---
title: SQL Server Data Mining Add-Ins for Office | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: c9021a19-2c19-4f0a-a293-5f7e0ac2524c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1f27a9834fb8a33ab98f9a8e7c6d309d10056484
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50099880"
---
# <a name="sql-server-data-mining-add-ins-for-office"></a>Compléments d'exploration de données SQL Server pour Office
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Compléments d'exploration de données est un ensemble d'outils légers pour l'analyse prédictive qui vous permet d'utiliser les données dans Excel pour générer des modèles d'analyse pour la prédiction, les recommandations ou l'exploration.  
  
 Les Assistants et les outils de gestion de données des compléments fournissent des instructions pas à pas pour les tâches d'exploration de données communes suivantes :  
  
-   **Organiser et nettoyer vos données avant la modélisation.** Utiliser des données stockées dans Excel ou dans une source de données Excel. Créez et enregistrez les connexions de façon à réutiliser les sources de données, répéter les expériences ou réapprendre les modèles.  
  
-   **Profiler, échantillonner et préparer.** Nombre de mineurs d'exploration de données expérimentés déclarent que 70 à 90 % du temps d'un projet d'exploration de données est consacré à la préparation des données. Les compléments permettent d'accélérer cette tâche. De fait, ils fournissent des visualisations dans Excel et des Assistants qui vous aident à exécuter les tâches courantes suivantes :  
  
    -   Profiler les données et comprendre leurs distribution et caractéristiques.  
  
    -   Créer des jeux d'apprentissage et de test via un échantillonnage aléatoire ou un suréchantillonnage.  
  
    -   Rechercher et supprimer ou remplacer les valeurs hors norme.  
  
    -   Réétiqueter les données pour améliorer la qualité d'analyse.  
  
-   **Analyser des modèles au moyen d'un apprentissage supervisé ou non.** Cliquez dans les Assistants conviviaux pour effectuer certaines tâches les plus fréquentes d'exploration de données, y compris l'analyse de clustering, l'analyse du panier d'achat et des prédictions.  
  
     Parmi les algorithmes d'apprentissage automatique connus inclus dans les compléments figurent Naïve Bayes, régression logistique, clustering, série chronologique et réseaux neuronaux.  
  
     Si vous découvrez l'exploration de données, obtenez de l'aide pour créer des requêtes de prédiction dans l'Assistant **Requête** .  
  
     Les utilisateurs expérimentés peuvent créer des requêtes personnalisées DMX à l’aide de l’ **Éditeur de requêtes avancé**par glisser-déplacer, ou automatiser les prédictions à l’aide d’Excel VBA.  
  
-   **Documenter et gérer.** Après avoir créé un jeu de données et généré des modèles, documentez votre travail et vos analyses en générant un résumé statistique des paramètres de données et du modèle.  
  
-   **Explorer et visualiser.** L'exploration de données n'est pas une activité qui peut être entièrement automatisée. Vous devez explorer et comprendre les résultats pour prendre des mesures explicites. Les compléments facilitent l'exploration en fournissant des visionneuses interactives dans Excel, des modèles Visio qui vous laissent personnaliser les diagrammes de modèle, et la possibilité d'exporter des graphiques et des tables pour Excel à des fins de filtrage ou de modification supplémentaire.  
  
-   **Déployer et intégrer.** Lorsque vous avez créé un modèle utile, mettez votre modèle en production, en utilisant les outils de gestion pour exporter le modèle de votre serveur expérimental vers une autre instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     Vous pouvez également laisser le modèle sur le serveur où vous l'avez créé, mais actualisez les données d'apprentissage et exécutez des prédictions à l'aide d'Integration Services ou de scripts DMX.  
  
     Les utilisateurs avancés apprécieront la fonctionnalité de **trace** , qui permet d'afficher les instructions XMLA et DMX envoyées au serveur.  
  
## <a name="getting-started"></a>Mise en route  
 Consultez les rubriques suivantes pour en savoir plus sur les outils et sur l'installation :  
  
-   [Client d’exploration de données pour Excel &#40;compléments d’exploration de données SQL Server&#41;](../data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
-   [Outils d’analyse de table pour Excel](../table-analysis-tools-for-excel.md)  
  
-   [Formes d’exploration de données pour Visio](../data-mining-shapes-for-visio.md)  
  
-   [Connexion à un serveur d’exploration de données](../connect-to-a-data-mining-server.md)  
  
## <a name="support-and-requirements"></a>Prise en charge et configuration requise  
 Les compléments d'exploration de données SQL Server pour Office peuvent être téléchargés gratuitement. Vous devez disposer de l'une des versions suivantes d'Office déjà installée pour utiliser ces outils :  
  
-   Office 2010, version 32 bits ou 64 bits  
  
-   Office 2013, 32 bits ou 64 bits  
  
> [!WARNING]  
>  Veillez à installer la version des compléments qui correspond à votre version d'Excel.  
  
 Les compléments d'exploration de données nécessitent une connexion à l'une des versions suivantes de SQL Server Analysis Services :  
  
-   Enterprise  
  
-   Business Intelligence  
  
-   Standard  
  
 Selon l'édition de SQL Server Analysis Services à laquelle vous vous connectez, certains algorithmes avancés peuvent ne pas être disponibles. Pour plus d'informations, consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2014](https://msdn.microsoft.com/library/cc645993.aspx).  
  
 Pour plus d’informations avec l’installation, consultez cette page sur le centre de téléchargement : [http://www.microsoft.com/download/details.aspx?id=29061](http://www.microsoft.com/download/details.aspx?id=29061)  
  
  
