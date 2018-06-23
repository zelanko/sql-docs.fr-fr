---
title: Client d’exploration de données pour Excel (SQL Server Data Mining Add-ins) | Documents Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Mining Client
- wizards
- getting started
ms.assetid: e075e2de-11cc-4f71-9603-0b161bca8a24
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fac95740fbf00c6623f8a8eeb44f1711319615d4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144409"
---
# <a name="data-mining-client-for-excel-sql-server-data-mining-add-ins"></a>Client d'exploration de données pour Excel (Compléments d'exploration de données SQL Server)
  Le client d'exploration de données pour Excel est un ensemble d'outils qui vous permettent d'effectuer des tâches courantes d'exploration de données, allant du nettoyage des données à la génération de modèle et de requêtes de prédiction. Utilisez les données dans des tableaux ou des plages Excel, ou accédez à des sources de données externes.  
  
 ![DM](media/dm-tabletools.gif "DM")  
  
-   [Utiliser des données](#bkmk_Data)  
  
     Chargez vos données dans Excel, nettoyez les données, vérifiez les valeurs hors norme et créez des résumés statistiques. Exécutez également différents genres d'échantillonnage, profil de données et modèles de test en utilisant des données externes. Le client d'exploration de données constitue la meilleure façon de préparer des données à analyser sans scripts complexes ou processus ETL.  
  
-   [Générer des modèles et analyser](#bkmk_Model)  
  
     Ces outils fournissent des interfaces de l'Assistant aux algorithmes d'exploration de données connus et testés de manière empirique, y compris le clustering (K-means et EM), l'analyse des associations, l'analyse de séries chronologiques et les arbres de décisions. Les options avancées de modélisation de chaque Assistant vous donnent le choix entre différents algorithmes, tels que Naïve Bayes ou de réseaux neuronaux, et personnaliser le comportement, par exemple la valeur de départ de cluster ou la taille d'échantillonnage initiale.  
  
     Tous les algorithmes d'exploration de données sont hébergés dans une instance d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], ce qui vous donne davantage de puissance pour générer des modèles complexes.  
  
-   [Tester, interroger et valider les modèles](#bkmk_Validate)  
  
     Le client d'exploration de données fournit des outils standard de test des modèles, notamment les graphiques de courbes d'élévation et la validation croisée. Les Assistants disponibles facilitent le test de la validité du jeu de données et sa de précision. L'Assistant Requête crée des requêtes pour utiliser les modèles de prédiction et score.  
  
-   [Afficher les modèles](#bkmk_ViewModels)  
  
     Les graphiques générés par la plupart des outils peuvent être enregistrés directement dans Excel. Utilisez le [exploration des modèles dans Excel &#40;des compléments d’exploration de données SQL Server&#41; ](browsing-models-in-excel-sql-server-data-mining-add-ins.md) outil pour Explorer les modèles.  
  
-   [Gérer, documenter et déployer](#bkmk_UsageMgmt)  
  
     Le client d'exploration de données pour Excel gère une connexion active au serveur, ce qui vous permet d'enregistrer votre modèle d'exploration de données sur le serveur afin de l'utiliser pour d'autres tests ou pour le déploiement sur un serveur de production pour une meilleure extensibilité.  
  
##  <a name="bkmk_Data"></a> Utiliser des données  
 Le **la préparation des données** groupe contient les Assistants suivants qui vous aident à vérifier et nettoyer les données en vue de tâches d’exploration de données. La plupart des Assistants vous permettent de fractionner les données dans des jeux d'apprentissage et de test.  
  
 [Explorer les données &#40;compléments d’exploration de données SQL Server&#41;](explore-data-sql-server-data-mining-add-ins.md)  
 Pour générer et stocker les modèles, les compléments prennent en charge ces connexions de données :  
  
-   Connexion à un serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], pour le stockage et le traitement des modèles.  
  
-   Connexions facultatives à des sources de données externes. Créez votre modèle à l'aide de tout type de données qui peuvent être définies comme source de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], ou utilisez uniquement les données qui se trouvent déjà dans Excel.  
  
 [Explorer les données &#40;compléments d’exploration de données SQL Server&#41;](explore-data-sql-server-data-mining-add-ins.md)  
 Le **Explorer les données** Assistant vous aide à comprendre le type et la quantité de données dans votre table de données en traçant la distribution et les valeurs des colonnes sélectionnées, une à la fois.  
  
 [Les exemples de données &#40;compléments d’exploration de données SQL Server&#41;](sample-data-sql-server-data-mining-add-ins.md)  
 La création du type de données correct pour l'apprentissage et le test de vos modèles constitue une part importante de l'exploration de données, mais cette tâche peut être fastidieuse si vous ne disposez pas des outils adéquats. Le **Sample Data** Assistant vous permet de diviser les données utilisées pour un modèle en deux groupes, un pour la création de modèle et un pour le tester. Utilisez l'échantillonnage aléatoire ou le suréchantillonnage.  
  
 [Calcul de prédiction &#40;outils d’analyse de Table pour Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 Le **suppression des observations aberrantes** Assistant vous propose plusieurs outils pour identifier et gérer les valeurs hors norme. Il montre la distribution des valeurs et la relation des valeurs hors norme avec d'autres données, et vous permet de décider s'il faut supprimer ou modifier des valeurs hors norme.  
  
 [Calcul de prédiction &#40;outils d’analyse de Table pour Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 Le **Réétiqueter** Assistant vous aide à créer de nouvelles étiquettes pour les données pour le rendre plus facile à comprendre les résultats d’analyse. Par exemple, vous pouvez renommer une plage de données avec un nom plus descriptif ou vous pouvez choisir une valeur représentative dans la liste.  
  
##  <a name="bkmk_Model"></a> Générer des modèles et analyser  
 Les options de la **modélisation des données** section de la barre d’outils vous permettre de dériver des modèles à partir des données ; regrouper des lignes de données en fonction des attributs ou d’Explorer des associations. Les Assistants de ce ruban reposent sur les algorithmes d'exploration de données performants qui sont disponibles dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Contrairement aux outils similaires proposés par les Outils d'analyse de table pour Excel, ces Assistants vous permettent de personnaliser le comportement de l'algorithme et d'utiliser diverses sources de données.  
  
 [Assistant classification &#40;les données des compléments d’exploration de données pour Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
 Le **classifier** Assistant vous aide à créer un modèle de classification basé sur des données existantes dans une table Excel, une plage Excel ou une source de données externe. Un modèle de classification extrait des séquences de vos données qui indiquent des similarités et vous aide à faire des prédictions basées sur des groupements de valeurs. Par exemple, un modèle de classification peut être utilisé pour prédire un risque en fonction des caractéristiques des revenus ou des dépenses.  
  
 Le **classifier** Assistant prend en charge l’utilisation de ces algorithmes d’exploration de données Microsoft : algorithme des arbres de décision, régression logistique, Naïve Bayes, réseaux neuronaux.  
  
 [Assistant estimation &#40;les données des compléments d’exploration de données pour Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
 Le **estimation** Assistant vous permet de créer un modèle d’estimation. Un modèle d'estimation extrait les séquences de données remarquables et les utilise pour prédire des valeurs de type numérique, telles que devise, montant des ventes, date ou heure.  
  
 Le **estimation** Assistant utilise ces algorithmes d’exploration de données Microsoft : arbres de décision, régression linéaire, régression logistique et réseaux neuronaux.  
  
 [Analyser les facteurs d’influence clés &#40;outils d’analyse de Table pour Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 L'Assistant Cluster vous permet de créer un modèle de clustering. Un modèle de clustering détecte les groupes de lignes qui partagent des caractéristiques communes. Cet Assistant permet d'explorer des séquences dans tous les types de données.  
  
 Le **Cluster** Assistant utilise l’algorithme Microsoft Clustering, qui comprend K-means et EM.  
  
 [Assistant association &#40;Client d’exploration de données pour Excel&#41;](associate-wizard-data-mining-client-for-excel.md)  
 Le **associer** Assistant vous permet de créer un modèle d’exploration de données à l’aide de l’algorithme Microsoft Association Rules, qui détecte les éléments fréquents de créer ou événements. Ces modèles d'association sont particulièrement utiles pour établir des recommandations.  
  
 Le **associer** Assistant utilise l’algorithme Microsoft Association Rules.  
  
 [Assistant prévisions &#40;les données des compléments d’exploration de données pour Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
 Le **prévision** Assistant vous permet de prévoir des valeurs dans une série chronologique. En général, les données que vous utilisez dans les prédictions contiennent un certain type de série chronologique, un cachet de date ou un ID de séquence, et vous l'utilisez pour dériver des séquences afin de prévoir des valeurs.  
  
 Le **prévision** Assistant utilise l’algorithme MTS.  
  
 [Avancées de modélisation &#40;les données des compléments d’exploration de données pour Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md)  
 Vous êtes déjà familiarisé avec l'exploration de données ? Vous pouvez utiliser la **avancé** options pour créer des structures de données personnalisées et générer des modèles à l’aide de personnalisations non incluses dans les autres outils et Assistants de modélisation de données.  
  
##  <a name="bkmk_Validate"></a> Tester, interroger et valider les modèles  
 Utilisez les Assistants sur le **précision et Validation** barre d’outils pour utiliser les tests standard pour la validation de la précision de vos modèles et pour évaluer la viabilité du jeu de données de création de modèles.  
  
 [Analyser les facteurs d’influence clés &#40;outils d’analyse de Table pour Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 Permet d'évaluer les performances d'un modèle d'exploration de données en générant un graphique de courbes d'élévation ou un graphique en nuage de points.  
  
 [Matrice de classification &#40;compléments d’exploration de données SQL Server&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
 Permet d'évaluer les performances d'un modèle de classification en créant un graphique qui synthétise les prédictions précises et imprécises faites par le modèle.  
  
 [Graphique des bénéfices &#40;compléments d’exploration de données SQL Server&#41;](profit-chart-sql-server-data-mining-add-ins.md)  
 Vous permet de comprendre l'impact d'un modèle d'exploration de données en établissant un graphique de l'exactitude des prédictions contenant les coûts et les avantages des actions entreprises basées sur la prédiction.  
  
 [La Validation croisée &#40;compléments d’exploration de données SQL Server&#41;](cross-validation-sql-server-data-mining-add-ins.md)  
 Crée un rapport qui résume la précision du modèle par rapport à de nombreux sous-ensemble du jeu de données, afin que vous puissiez déterminer la stabilité du modèle.  
  
 Vous pouvez également utiliser les données d'un tableau Excel comme entrée d'une requête de prédiction sur un modèle d'exploration de données stocké sur le serveur.  
  
 [Requête &#40;compléments d’exploration de données SQL Server&#41;](query-sql-server-data-mining-add-ins.md)  
 Le **requête** Assistant vous aide à créer des prédictions sur un modèle d’exploration de données existant.  
  
 [Éditeur de requête d’exploration de données données avancé](advanced-data-mining-query-editor.md)  
 Pour les utilisateurs expérimentés, cet outil fournit une interface de type glisser-déplacer dans DMX. Créez facilement des requêtes de prédiction ou de nouveaux modèles sans vous préoccuper de la syntaxe.  
  
##  <a name="bkmk_ViewModels"></a> Afficher les modèles  
 Les modèles créés automatiquement sont ouverts pour l'exploration. Toutefois, vous pouvez également parcourir les modèles sur le serveur et générer de nouvelles visualisations. Utilisez le [formes Visio](viewing-data-mining-models-in-visio-data-mining-add-ins.md) pour exporter des diagrammes de modèle dans une zone personnalisable.  
  
 [Exploration des modèles dans Excel &#40;compléments d’exploration de données SQL Server&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
 Affichez les modèles créés à l'aide de graphiques interactifs personnalisés pour chaque type de modèle.  
  
 [Les modèles d’exploration de données de documentation &#40;les données des compléments d’exploration de données pour Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)  
 Cet Assistant crée des rapports qui fournissent un résumé statistique du jeu de données et des métadonnées relatives au modèle, pour vous aider à effectuer les tâches d'analyse et d'interprétation.  
  
##  <a name="bkmk_UsageMgmt"></a> Gérer, documenter et déployer  
 Ces outils vous aident à établir la connexion à un serveur d'exploration de données, ainsi qu'à gérer et exporter des modèles, et surveiller l'activité d'exploration de données.  
  
 [Gérer les modèles &#40;compléments d’exploration de données SQL Server&#41;](manage-models-sql-server-data-mining-add-ins.md)  
 Si vous bénéficiez des autorisations nécessaires, vous pouvez supprimer, modifier, renommer ou traiter les structures et modèles d'exploration de données existants sans quitter Excel.  
  
 [Trace &#40;Client d’exploration de données pour Excel&#41;](trace-data-mining-client-for-excel.md)  
 Cliquez sur **Trace** pour afficher une capture de l’interaction entre le client Excel et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] server. Toutes les activités sont stockées sous forme d'instructions DMX ou XMLA ; vous pouvez donc résoudre les problèmes de votre session d'exploration de données ou enregistrer les informations en vue de les utiliser ultérieurement.  
  
 [Se connecter à un serveur d’exploration de données](connect-to-a-data-mining-server.md)  
 Pour pouvoir utiliser Excel comme client pour l'exploration de données, vous devez établir une connexion à une instance d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. La connexion vous permet d'accéder au moteur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Si vous disposez des autorisations nécessaires, la connexion vous permet également de stocker les séquences que vous avez découvertes et de modifier des objets d'exploration de données existants.  
  
 Le **connexions** barre d’outils fournit des Assistants pour gérer les connexions à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Pour pouvoir utiliser les algorithmes et les outils d'exploration de données, vous devez définir une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Vous pouvez créer la connexion lorsque vous installez le complément, ou vous pouvez ajouter une connexion par la suite.  
  
 **Bien démarrer**  
 Cliquez sur le **mise en route** bouton pour démarrer un Assistant de configuration qui vous guide tout au long du processus de création d’une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]et l’obtention des autorisations nécessaires pour effectuer l’exploration de données.  
  
 **Aide**  
 Le **aide** menu déroulant fournit des liens vers l’aide en ligne, les sites Web et un Assistant de configuration pour vous aider à terminer l’installation et démarrer l’exploration de données.  
  
 La page d'aide fournit également des liens vers des ressources en ligne, notamment l'aide du complément, et des vidéos, des démonstrations et des exemples supplémentaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d’analyse de table pour Excel](table-analysis-tools-for-excel.md)   
 [Dépannage des diagrammes d’exploration de données Visio &#40;compléments d’exploration de données SQL Server&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  