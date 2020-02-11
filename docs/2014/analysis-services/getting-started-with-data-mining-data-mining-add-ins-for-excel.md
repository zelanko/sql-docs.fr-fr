---
title: Prise en main avec l’exploration de données (compléments d’exploration de données pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: cbe10a19-e194-408e-a65b-5fdf3fb1e880
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3e5a24a158681c3f596355b1b9abca6ada990531
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66080935"
---
# <a name="getting-started-with-data-mining-data-mining-add-ins-for-excel"></a>Mise en route avec l'exploration de données (compléments d'exploration de données pour Excel)
  L'exploration de données est le processus de découverte des tendances au travers de données. L'exploration de données est un complément naturel du processus d'exploration et d'analyse de vos données via la BI traditionnelle. Les algorithmes d'ordinateur peuvent traiter de grandes quantités de données et dégager des tendances et des séquences qui resteraient autrement masquées.  
  
 Pour effectuer l’exploration de données, vous collectez des données pertinentes pour une question spécifique, par exemple « qui sont mes clients ? ». ou « quels produits ont été achetés ? » puis appliquez un algorithme pour rechercher des corrélations statistiques dans les données. Les schémas et les tendances identifiés par l'analyse sont stockés en tant que modèle d'exploration de données. Appliquez ensuite le modèle d'exploration de données aux nouvelles données, dans des scénarios d'entreprise comme :  
  
-   Utilisation des tendances passées pour prévoir les ventes du trimestre suivant, les besoins du stock, ou la satisfaction des clients.  
  
-   Application des connaissances aux clients actuels pour profiler de nouveaux clients et recommander de nouveaux produits ou saisir des occasions.  
  
-   Recherche de corrélations entre des événements passés pour prévenir les erreurs ou le temps mort du serveur.  
  
-   Analyse des produits achetés simultanément par les clients et utilisation des informations pour recommander des offres groupées ou planifier un placement de produit.  
  
 La méthode d'analyse que vous choisissez dépend de vos besoins. Les compléments d'exploration de données prennent en charge ces types d'analyse :  
  
-   Apprentissage supervisé et non supervisé  
  
-   Clustering (segmentation)  
  
-   Analyse factorielle, en utilisant réseaux bayésiens et neuronaux  
  
-   Analyse des séries chronologiques  
  
-   Analyse d'association, recommandations, puis analyse du panier d'achat  
  
-   Calcul de score des résultats binaires  
  
-   Régression linéaire  
  
 En outre, les compléments aident lors de la phase de préparation des données : sélection, exploration, et nettoyage.  
  
## <a name="define-your-goal"></a>Définir votre objectif  
 Avant de démarrer, prenez une minute pour penser à la question à laquelle vous voulez vraiment répondre. L'exploration est par elle même très éclairante, mais si vous souhaitez appliquer vos résultats aux nouvelles données, vous devez définir clairement ce vous attendez du modèle, et comment vous mesurerez son adéquation à vos objectifs.  
  
 Par exemple, plutôt qu’un objectif de « recherche de nouveaux clients », Clarifiez votre objectif en matière de plus concrète, par exemple « identifier les données démographiques des clients susceptibles d’acheter notre produit, avec une probabilité d’au moins 65% ».  
  
-   Votre jeu de données doit contenir au moins un attribut « result » que vous pouvez utiliser pour l’apprentissage et la prédiction. Si vous n'avez pas cet attribut, vous pouvez étiqueter manuellement des données d'apprentissage, ou utiliser d'autres colonnes pour créer un proxy pour les résultats.  
  
     Par exemple, si vous souhaitez prédire « les meilleurs prospects », vous devez appliquer une règle d’entreprise au préalable pour étiqueter les clients existants, afin que l’exploration de données puisse tirer parti des exemples que vous fournissez.  
  
-   Si vous utilisez une valeur qui change au fil du temps et que vous souhaitez prédire des tendances futures, décidez de la granularité des résultats dont vous avez besoin. Souhaitez-vous des prédictions pour un mois, un jour ou un an ? Vos données doivent être analysées en utilisant les mêmes unités que vous voulez prédire.  
  
     Avec les modèles cycliques, si vous n’obtenez pas de bons résultats avec des données quotidiennes, essayez différentes tranches de temps ou essayez d’utiliser des jours de semaine, des mois, voire des jours fériés.  
  
-   Avant de lancer un assistant pour trouver de nouvelles corrélations, jetez encore un coup d'œil à vos données et déterminez quelles sortes de relations existantes peuvent être présentes dans le dataset. Existe-t-il des variables parasites ? Existe-t-il des doublons ou des proxys ?  
  
-   Quelles sont les mesures selon lesquelles la réussite du modèle sera évaluée ? Comment saurez-vous que le modèle est « suffisant » ?  
  
-   Souhaitez-vous effectuer des prédictions à partir du modèle d'exploration de données ou seulement rechercher des tendances et associations intéressantes ?  
  
## <a name="explore-your-data-and-explore-the-model"></a>Explorer vos données et explorer le modèle  
 Peut-être comprenez-vous déjà parfaitement les données et le domaine. Même si tel est le cas, vous devriez consacrer un peu de temps à profiler vos données pour la modélisation que vous avez à l'esprit.  
  
 Prenez quelques minutes pour observer la distribution des valeurs, et identifier les problèmes éventuels tels que des valeurs manquantes ou des espaces réservés.  
  
 Si vous envisagez d’effectuer l’exploration de données sur un jeu de données tellement grand ou complexe que vous ne pouviez pas l’analyser avec d’autres méthodes, envisagez d’échantillonner ou de réduire les données.  
  
-   Comment sont distribuées les données ?  
  
-   Comment sont associées les colonnes ou, s'il y a plusieurs tables, comment sont associées les tables ?  
  
-   Manque-t-il des valeurs ? Certaines valeurs ont-elles besoin d'une conversion ou d'un prétraitement ?  
  
-   Les données sont-elles composées principalement de texte, de nombres ou un mélange des deux ?  
  
-   Disposez-vous de suffisamment de données pour prendre en charge l'analyse du résultat désiré ? Si vous analysez des associations entre les produits, vous aurez peut-être besoin de beaucoup plus de données. Si vous prédisez un résultat binaire, vous pouvez obtenir des résultats avec beaucoup moins de données, en supposant que le dataset soit équilibré.  
  
 Une fois votre modèle terminé, attachez-vous à revoir les résultats et à identifier comment modifier les données ou obtenir de meilleurs scores. Il est rare qu'un modèle initial apporte toutes les réponses. L'exploration de données est généralement un processus itératif.  
  
 À mesure que vous essayez compartimentage vos données différemment ou en ajoutant de nouvelles colonnes, n’oubliez pas d’utiliser l’Assistant **modèle de document** pour capturer un instantané des métadonnées et des résultats de chaque modèle. Avec un enregistrement, vous suivrez plus facilement le progression de votre exploration.  
  
 [Exploration et nettoyage des données](exploring-and-cleaning-data.md)  
  
## <a name="validate-your-model"></a>Valider votre modèle  
 Lorsque vous exécutez un Assistant ou un outil, l'algorithme analyse le contenu des données et détermine si un modèle valide d'un point de vue statistique existe. Si l’algorithme ne trouve pas de modèles valides, vous obtiendrez un message d’erreur. Toutefois, même si un modèle a été créé avec succès, vous voudrez tester le modèle pour voir s’il valide vos hypothèses. Vous pouvez utiliser des outils tels que le graphique d’analyse de [précision &#40;SQL Server des compléments d’exploration de données&#41;](accuracy-chart-sql-server-data-mining-add-ins.md) ou la [Validation croisée &#40;SQL Server des compléments d’exploration de données&#41;](cross-validation-sql-server-data-mining-add-ins.md) pour produire des mesures statistiques sur la qualité du modèle.  
  
 Lorsque vous évaluez les résultats de votre premier modèle, posez-vous des questions telles que :  
  
-   Quels types de modèles ont été trouvés ? Quelles sont les probabilités et les valeurs de prise en charge ?  
  
-   Nos estimations des tendances sont-elles correctes ou révèlent-elles des corrélations inattendues ?  
  
-   Avons-nous collecté suffisamment de données ? La liaison des données produira-t-elle des modèles plus clairs ?  
  
-   Le jeu de données est-il équilibré ? La validation croisée peut tester la représentativité de vos données.  
  
 [Outils d'analyse de table pour Excel](table-analysis-tools-for-excel.md)  
  
 [Client d’exploration de données pour Excel &#40;SQL Server des compléments d’exploration de données&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
 [Choix d'un modèle](choosing-a-model.md)  
  
## <a name="explore-and-refine"></a>Explorer et affiner  
 Si le modèle semble être valide, vous pouvez l'utiliser pour la prédiction et la recommandation, pour apporter un éclairage ou pour planifier des stratégies commerciales.  
  
-   Utilisez le navigateur pour l'exploration de données du Client d'exploration de données pour Excel pour explorer et interagir avec le modèle.  
  
-   Utilisez Excel pour réarranger et filtrer les résultats.  
  
-   Utilisez Visio pour créer des présentations et pour mettre en avant les relations trouvées dans les données.  
  
 Souvent, le premier résultat de l'analyse vous permet de mettre à jour des façons d'améliorer l'analyse ou de vous rendre compte que vous devez obtenir de nouvelles données de meilleure qualité. Étant donné que les modèles que vous créez à l'aide des compléments d'exploration de données pour Excel peuvent être enregistrés dans une instance d'Analysis services, il est relativement facile de mettre à jour le modèle avec de nouvelles données, puis de continuer à affiner et réutiliser les modèles pertinents.  
  
 Parmi les utilisations importantes des modèles d'exploration de données, l'une consiste à créer des prédictions et des recommandations. Les compléments d'exploration de données pour Excel incluent des outils qui simplifient la génération de requêtes de prédiction même complexes, afin de convertir des analyses en résultats utilisables. Tous ces outils sont totalement intégrés à Excel.  
  
 [Affichage des modèles &#40;compléments d’exploration de données pour Office&#41;](viewing-models-data-mining-add-ins-for-office.md)  
  
 [Validation des modèles et utilisation de modèles pour la prédiction &#40;compléments d’exploration de données pour Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ce qui est inclus dans les compléments d’exploration de données pour Office](what-s-included-in-the-data-mining-add-ins-for-office.md)   
 [Référence technique &#40;compléments d’exploration de données pour Excel&#41;](technical-reference-data-mining-add-ins-for-excel.md)  
  
  
