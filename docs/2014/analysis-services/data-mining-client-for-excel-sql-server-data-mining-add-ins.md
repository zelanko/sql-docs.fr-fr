---
title: Client d’exploration de données pour Excel (compléments d’exploration de données SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Data Mining Client
- wizards
- getting started
ms.assetid: e075e2de-11cc-4f71-9603-0b161bca8a24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9c2f11ecbdf90aeeb5e0e5a3ef097152898042d6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66086429"
---
# <a name="data-mining-client-for-excel-sql-server-data-mining-add-ins"></a>Client d'exploration de données pour Excel (Compléments d'exploration de données SQL Server)
  Le client d'exploration de données pour Excel est un ensemble d'outils qui vous permettent d'effectuer des tâches courantes d'exploration de données, allant du nettoyage des données à la génération de modèle et de requêtes de prédiction. Utilisez les données dans des tableaux ou des plages Excel, ou accédez à des sources de données externes.  
  
 ![DM](media/dm-tabletools.gif "DM")  
  
-   [Utiliser des données](#bkmk_Data)  
  
     Chargez vos données dans Excel, nettoyez les données, vérifiez les valeurs hors norme et créez des résumés statistiques. Exécutez également différents genres d'échantillonnage, profil de données et modèles de test en utilisant des données externes. Le client d'exploration de données constitue la meilleure façon de préparer des données à analyser sans scripts complexes ou processus ETL.  
  
-   [Générer des modèles et les analyser](#bkmk_Model)  
  
     Ces outils fournissent des interfaces de l'Assistant aux algorithmes d'exploration de données connus et testés de manière empirique, y compris le clustering (K-means et EM), l'analyse des associations, l'analyse de séries chronologiques et les arbres de décisions. Les options avancées de modélisation de chaque Assistant vous donnent le choix entre différents algorithmes, tels que Naïve Bayes ou de réseaux neuronaux, et personnaliser le comportement, par exemple la valeur de départ de cluster ou la taille d'échantillonnage initiale.  
  
     Tous les algorithmes d'exploration de données sont hébergés dans une instance d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], ce qui vous donne davantage de puissance pour générer des modèles complexes.  
  
-   [Tester, interroger et valider les modèles](#bkmk_Validate)  
  
     Le client d'exploration de données fournit des outils standard de test des modèles, notamment les graphiques de courbes d'élévation et la validation croisée. Les Assistants disponibles facilitent le test de la validité du jeu de données et sa de précision. L'Assistant Requête crée des requêtes pour utiliser les modèles de prédiction et score.  
  
-   [Afficher les modèles](#bkmk_ViewModels)  
  
     Les graphiques générés par la plupart des outils peuvent être enregistrés directement dans Excel. Utilisez les [modèles de navigation dans Excel &#40;SQL Server les compléments d’exploration de données&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) outil pour explorer les modèles.  
  
-   [Gérer, documenter et déployer](#bkmk_UsageMgmt)  
  
     Le client d'exploration de données pour Excel gère une connexion active au serveur, ce qui vous permet d'enregistrer votre modèle d'exploration de données sur le serveur afin de l'utiliser pour d'autres tests ou pour le déploiement sur un serveur de production pour une meilleure extensibilité.  
  
##  <a name="work-with-data"></a><a name="bkmk_Data"></a>Utiliser des données  
 Le groupe **préparation des données** contient les assistants suivants qui vous permettent d’examiner et de nettoyer les données en préparation des tâches d’exploration de données. La plupart des Assistants vous permettent de fractionner les données dans des jeux d'apprentissage et de test.  
  
 [Explorez les &#40;de données SQL Server les compléments d’exploration de données&#41;](explore-data-sql-server-data-mining-add-ins.md)  
 Pour générer et stocker les modèles, les compléments prennent en charge ces connexions de données :  
  
-   Connexion à un serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], pour le stockage et le traitement des modèles.  
  
-   Connexions facultatives à des sources de données externes. Créez votre modèle à l'aide de tout type de données qui peuvent être définies comme source de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], ou utilisez uniquement les données qui se trouvent déjà dans Excel.  
  
 [Explorez les &#40;de données SQL Server les compléments d’exploration de données&#41;](explore-data-sql-server-data-mining-add-ins.md)  
 L’Assistant **exploration des données** vous aide à comprendre le type et la quantité de données de votre table de données en graphiques la distribution et les valeurs des colonnes sélectionnées, une à la fois.  
  
 [Exemples de données &#40;SQL Server des compléments d’exploration de données&#41;](sample-data-sql-server-data-mining-add-ins.md)  
 La création du type de données correct pour l'apprentissage et le test de vos modèles constitue une part importante de l'exploration de données, mais cette tâche peut être fastidieuse si vous ne disposez pas des outils adéquats. L’Assistant **exemples de données** permet de diviser facilement les données utilisées pour un modèle en deux groupes, l’un pour la génération du modèle et l’autre pour le tester. Utilisez l'échantillonnage aléatoire ou le suréchantillonnage.  
  
 [Calcul de prédiction &#40;les outils d’analyse de table pour Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 L’Assistant **suppression** des valeurs hors norme vous propose plusieurs outils permettant d’identifier et de gérer de manière appropriée les valeurs hors norme. Il montre la distribution des valeurs et la relation des valeurs hors norme avec d'autres données, et vous permet de décider s'il faut supprimer ou modifier des valeurs hors norme.  
  
 [Calcul de prédiction &#40;les outils d’analyse de table pour Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 L’Assistant **réétiqueter** vous permet de créer de nouvelles étiquettes pour les données afin de faciliter la compréhension des résultats de l’analyse. Par exemple, vous pouvez renommer une plage de données avec un nom plus descriptif ou vous pouvez choisir une valeur représentative dans la liste.  
  
##  <a name="build-models-and-analyze"></a><a name="bkmk_Model"></a>Créer des modèles et analyser  
 Les options de la section **modélisation des données** de la barre d’outils vous permettent de dériver des modèles à partir de données. Regroupez les lignes de données en fonction des attributs ou explorez les associations. Les Assistants de ce ruban reposent sur les algorithmes d'exploration de données performants qui sont disponibles dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Contrairement aux outils similaires proposés par les Outils d'analyse de table pour Excel, ces Assistants vous permettent de personnaliser le comportement de l'algorithme et d'utiliser diverses sources de données.  
  
 [Assistant classification &#40;compléments d’exploration de données pour Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
 L’Assistant **classification** vous aide à créer un modèle de classification basé sur des données existantes dans une table Excel, une plage Excel ou une source de données externe. Un modèle de classification extrait des séquences de vos données qui indiquent des similarités et vous aide à faire des prédictions basées sur des groupements de valeurs. Par exemple, un modèle de classification peut être utilisé pour prédire un risque en fonction des caractéristiques des revenus ou des dépenses.  
  
 L’Assistant **classification** prend en charge l’utilisation des algorithmes d’exploration de données Microsoft suivants : algorithme MDT (Decision Trees), régression logistique, Naïve Bayes, réseaux neuronaux.  
  
 [Assistant estimation &#40;des compléments d’exploration de données pour Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
 L’Assistant **estimation** vous aide à créer un modèle d’estimation. Un modèle d'estimation extrait les séquences de données remarquables et les utilise pour prédire des valeurs de type numérique, telles que devise, montant des ventes, date ou heure.  
  
 L’Assistant **estimation** utilise les algorithmes d’exploration de données Microsoft suivants : arbres de décision, régression linéaire, régression logistique et réseaux neuronaux.  
  
 [Analyser les influenceurs clés &#40;les outils d’analyse de table pour Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 L'Assistant Cluster vous permet de créer un modèle de clustering. Un modèle de clustering détecte les groupes de lignes qui partagent des caractéristiques communes. Cet Assistant permet d'explorer des séquences dans tous les types de données.  
  
 L’Assistant **cluster** utilise l’algorithme de gestion de clusters Microsoft, qui comprend K-signifiant et em.  
  
 [Assistant Association &#40;client d’exploration de données pour Excel&#41;](associate-wizard-data-mining-client-for-excel.md)  
 L’Assistant **Association** vous aide à créer un modèle d’exploration de données à l’aide de l’algorithme Microsoft Association Rules, qui détecte les événements ou les événements qui se produisent fréquemment. Ces modèles d'association sont particulièrement utiles pour établir des recommandations.  
  
 L’Assistant **Association** utilise l’algorithme Microsoft Association Rules.  
  
 [Assistant Prévision &#40;des compléments d’exploration de données pour Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
 L’Assistant **prévision** vous aide à prédire des valeurs dans une série chronologique. En général, les données que vous utilisez dans les prédictions contiennent un certain type de série chronologique, un cachet de date ou un ID de séquence, et vous l'utilisez pour dériver des séquences afin de prévoir des valeurs.  
  
 L’Assistant **prévision** utilise l’algorithme MTS (Microsoft Time Series).  
  
 [Modèles avancés &#40;des compléments d’exploration de données pour Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md)  
 Vous êtes déjà familiarisé avec l'exploration de données ? Vous pouvez utiliser les options de modélisation **avancée** des données pour créer des structures de données personnalisées et générer des modèles à l’aide de personnalisations qui ne sont pas incluses dans les autres outils et assistants.  
  
##  <a name="test-query-and-validate-models"></a><a name="bkmk_Validate"></a>Tester, interroger et valider des modèles  
 Utilisez les assistants de la barre d’outils **précision et validation** pour utiliser des tests standard pour valider la précision de vos modèles, et pour évaluer la viabilité du jeu de données pour la création de modèles.  
  
 [Analyser les influenceurs clés &#40;les outils d’analyse de table pour Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 Permet d'évaluer les performances d'un modèle d'exploration de données en générant un graphique de courbes d'élévation ou un graphique en nuage de points.  
  
 [&#40;de matrices de classification SQL Server des compléments d’exploration de données&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
 Permet d'évaluer les performances d'un modèle de classification en créant un graphique qui synthétise les prédictions précises et imprécises faites par le modèle.  
  
 [Graphique des bénéfices &#40;les compléments d’exploration de données SQL Server&#41;](profit-chart-sql-server-data-mining-add-ins.md)  
 Vous permet de comprendre l'impact d'un modèle d'exploration de données en établissant un graphique de l'exactitude des prédictions contenant les coûts et les avantages des actions entreprises basées sur la prédiction.  
  
 [Validation croisée &#40;SQL Server des compléments d’exploration de données&#41;](cross-validation-sql-server-data-mining-add-ins.md)  
 Crée un rapport qui résume la précision du modèle par rapport à de nombreux sous-ensemble du jeu de données, afin que vous puissiez déterminer la stabilité du modèle.  
  
 Vous pouvez également utiliser les données d'un tableau Excel comme entrée d'une requête de prédiction sur un modèle d'exploration de données stocké sur le serveur.  
  
 [&#40;de requêtes SQL Server des compléments d’exploration de données&#41;](query-sql-server-data-mining-add-ins.md)  
 L’Assistant **requête** vous aide à créer des prédictions sur un modèle d’exploration de données existant.  
  
 [Éditeur de requêtes d’exploration de données avancée](advanced-data-mining-query-editor.md)  
 Pour les utilisateurs expérimentés, cet outil fournit une interface de type glisser-déplacer dans DMX. Créez facilement des requêtes de prédiction ou de nouveaux modèles sans vous préoccuper de la syntaxe.  
  
##  <a name="view-models"></a><a name="bkmk_ViewModels"></a>Afficher les modèles  
 Les modèles créés automatiquement sont ouverts pour l'exploration. Toutefois, vous pouvez également parcourir les modèles sur le serveur et générer de nouvelles visualisations. Utilisez les [formes Visio](viewing-data-mining-models-in-visio-data-mining-add-ins.md) pour exporter des diagrammes de modèle vers une zone de dessin personnalisable.  
  
 [Exploration des modèles dans Excel &#40;SQL Server les compléments d’exploration de données&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
 Affichez les modèles créés à l'aide de graphiques interactifs personnalisés pour chaque type de modèle.  
  
 [Documentation des modèles d’exploration de données &#40;les compléments d’exploration de données pour Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)  
 Cet Assistant crée des rapports qui fournissent un résumé statistique du jeu de données et des métadonnées relatives au modèle, pour vous aider à effectuer les tâches d'analyse et d'interprétation.  
  
##  <a name="manage-document-and-deploy"></a><a name="bkmk_UsageMgmt"></a>Gérer, documenter et déployer  
 Ces outils vous aident à établir la connexion à un serveur d'exploration de données, ainsi qu'à gérer et exporter des modèles, et surveiller l'activité d'exploration de données.  
  
 [Gérer les modèles &#40;SQL Server des compléments d’exploration de données&#41;](manage-models-sql-server-data-mining-add-ins.md)  
 Si vous bénéficiez des autorisations nécessaires, vous pouvez supprimer, modifier, renommer ou traiter les structures et modèles d'exploration de données existants sans quitter Excel.  
  
 [Trace &#40;client d’exploration de données pour Excel&#41;](trace-data-mining-client-for-excel.md)  
 Cliquez sur **trace** pour afficher une capture en continu de l’interaction entre le client Excel [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et le serveur. Toutes les activités sont stockées sous forme d'instructions DMX ou XMLA ; vous pouvez donc résoudre les problèmes de votre session d'exploration de données ou enregistrer les informations en vue de les utiliser ultérieurement.  
  
 [Connexion à un serveur d'exploration de données](connect-to-a-data-mining-server.md)  
 Pour pouvoir utiliser Excel comme client pour l'exploration de données, vous devez établir une connexion à une instance d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. La connexion vous permet d'accéder au moteur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Si vous disposez des autorisations nécessaires, la connexion vous permet également de stocker les séquences que vous avez découvertes et de modifier des objets d'exploration de données existants.  
  
 La barre d’outils **connexions** fournit des assistants pour gérer les connexions [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]à une instance de. Pour pouvoir utiliser les algorithmes et les outils d'exploration de données, vous devez définir une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Vous pouvez créer la connexion lorsque vous installez le complément, ou vous pouvez ajouter une connexion par la suite.  
  
 **Prise en main**  
 Cliquez sur le bouton **prise en main** pour démarrer un assistant de configuration qui vous guide tout au long du processus de création d’une [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]connexion à une instance de et d’obtention des autorisations nécessaires pour effectuer l’exploration de données.  
  
 **Aide**  
 Le menu déroulant **aide** fournit des liens vers l’aide en ligne, les sites Web et un Assistant Configuration pour vous aider à terminer l’installation et à démarrer l’exploration de données.  
  
 La page d'aide fournit également des liens vers des ressources en ligne, notamment l'aide du complément, et des vidéos, des démonstrations et des exemples supplémentaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d’analyse de table pour Excel](table-analysis-tools-for-excel.md)   
 [Dépannage des diagrammes d’exploration de données Visio &#40;SQL Server des compléments d’exploration de données&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
