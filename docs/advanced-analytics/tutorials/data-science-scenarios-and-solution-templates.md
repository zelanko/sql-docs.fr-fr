---
title: Scénarios de science des données et des modèles de solution - SQL Server Machine Learning
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 83c659c3982225221c7ad262af925863c821c5ab
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962294"
---
# <a name="data-science-scenarios-and-solution-templates"></a>Scénarios de science des données et des modèles de solution
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Les modèles sont des exemples de solutions qui illustrent les bonnes pratiques et fournissent les bases qui vous aideront à implémenter une solution rapidement. Chaque modèle est conçu pour résoudre un problème spécifique, pour un vertical spécifique ou d’un secteur d’activité. Les tâches dans chaque modèle vont de la préparation des données à la formation du modèle et au calcul des scores, en passant par l’ingénierie des caractéristiques. Utilisez ces modèles pour découvrir comment [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] fonctionne. Ensuite, n’hésitez pas à personnaliser le modèle pour l’adapter à votre propre scénario et créer une solution personnalisée. 

Chaque solution inclut des exemples de données, le code R ou Python code et procédures stockées SQL le cas échéant. Le code peut être exécuté dans votre environnement de développement R ou Python par défaut, les calculs étant effectués dans SQL Server. Dans certains cas, vous pouvez exécuter le code directement à l’aide de T-SQL et n’importe quel outil client SQL, tels que SQL Server Management Studio.

> [!TIP]
> 
> La plupart des modèles sont fournis dans plusieurs versions prenant en charge à la fois en local et plateformes pour l’apprentissage de cloud computing. Par exemple, vous pouvez générer la solution à l’aide uniquement de SQL Server, ou vous pouvez générer la solution dans Microsoft R Server ou dans Azure Machine Learning.

+ Pour le téléchargement et les instructions d’installation, consultez [comment utiliser les modèles](#bkmk_HowTo).

## <a name="fraud-detection"></a>Détection des fraudes

[Modèle de détection de fraude en ligne (SQL Server R Services)](https://github.com/Microsoft/r-server-fraud-detection)

**Ce que :** La capacité à détecter les transactions frauduleuses est importante pour les entreprises en ligne. Pour réduire les pertes de refacturation, les entreprises ont besoin identifier rapidement les transactions qui ont été apportées à l’aide d’instrument de paiement volé ou informations d’identification. Quand des transactions frauduleuses sont découvertes, les entreprises prennent généralement des mesures pour bloquer certains comptes dès que possible, afin d’empêcher toute perte supplémentaire. Dans ce scénario, vous allez apprendre à utiliser les données de transactions d’achat en ligne pour identifier les fraudes probables.

**Comment :**  La détection des fraudes est résolue en tant que problème de classification binaire. Vous pouvez facilement appliquer la méthodologie utilisée dans ce modèle à la détection des fraudes dans d’autres domaines.


## <a name="campaign-optimization"></a>Optimisation des campagnes

[Prédire comment et quand contacter les prospects](https://microsoft.github.io/r-server-campaign-optimization/)

**Ce que :** Cette solution utilise des données du secteur des assurances pour prédire les prospects en fonction des données démographiques, des données de réponse historiques et des détails propres au produit.  Recommandations sont également générées pour indiquer le canal et l’heure pour les utilisateurs d’approche pour influencer le comportement d’achat meilleures.

**Comment :** La solution crée et compare plusieurs modèles. La solution démontre également l’intégration de données automatisés et de préparation des données à l’aide de procédures stockées. Exemples parallèles sont fournis pour SQL Server en base de données, dans Azure et HDInsight Spark. 

## <a name="health-care-predict-length-of-stay-in-hospital"></a>Soins de santé : prédire la durée des séjours à l’hôpital 

[Prédire la durée des séjours à l’hôpital](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

**Ce que :** PRÉDICTION avec précision les patients peuvent nécessiter l’hospitalisation à long terme est une partie importante de soins et la planification. Les administrateurs doivent être en mesure de déterminer les établissements nécessitent plus de ressources et aux équipes soignantes voulez faire en sorte qu’ils peuvent répondre aux besoins des patients.

**Comment :** Cette solution utilise la Machine virtuelle de science des données et inclut une instance de SQL Server avec l’apprentissage est activé. Il inclut également un ensemble de rapports Power BI que vous pouvez utiliser pour interagir avec un modèle déployé.

## <a name="customer-churn"></a>ATTRITION

[Modèle de prédiction d’évolution du client (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/README.md)

**Ce que :** Analyse et prédiction d’ATTRITION sont importantes dans tout secteur où la perte de clients à la concurrence doit être gérée et a empêché : bancaire, télécommunications et vente au détail, pour citer que quelques-uns. L’objectif de l’analyse de l’attrition consiste à identifier les clients susceptibles de passer à la concurrence, puis d’effectuer les actions appropriées pour conserver ces clients.

**Comment :** Ce modèle formule le problème de l’ATTRITION en tant qu’un **classification binaire** problème. Il utilise des exemples de données de deux sources, données démographiques et transactions de clients, pour classer les clients comme susceptibles ou non de passer à la concurrence.
  
## <a name="predictive-maintenance"></a>Maintenance prédictive

[Modèle de maintenance prédictive (SQL Server 2016)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/PredictiveMaintenance/README.md)

**Ce que :** Maintenance prédictive vise à augmenter l’efficacité des tâches de maintenance en capturant les défaillances passées et à l’aide de ces informations pour prédire quand et où un appareil peut échouer. La capacité à prédire l’obsolescence d’appareil est particulièrement utile pour les applications qui s’appuient sur des capteurs ou des données distribuées. Cette méthode peut également être appliquée pour surveiller et de prédire l’erreur dans les appareils IoT (Internet of Things).

**Comment :** Cette solution est axée sur la réponse à la question « Quand échoue une machine en service ? » Les données d’entrée représentent des mesures de capteurs simulées pour des moteurs d’avion. Données obtenues à partir de la surveillance opération conditions actuelles du moteur, telles que le cycle de travail actuel, les paramètres et les mesures de capteurs, sont utilisées pour créer trois types de modèles prédictifs :

-   **Modèles de régression**, pour prédire dans combien de temps un moteur tombera en panne. L’exemple de modèle prédit la métrique « Vie restante » (RUL), également appelé temps à « Échec » (TTF).
  
-   **Modèles de classification**, pour prédire si un moteur est susceptible de tomber en panne.
  
    Le **modèle de classification binaire** prédit si un moteur tombera en panne dans un intervalle de temps donné.

    Le **modèle de classification multiclasse** prédit si un moteur particulier peut échouer et fournit une fenêtre de temps probable de défaillance. Par exemple, pour un jour donné, vous pouvez prédire si un appareil est susceptible de tomber en panne ce jour-là ou dans un laps de temps suivant ce jour.

## <a name="energy-demand-forecasting"></a>Prévision de la demande d’énergie

[Demande d’énergie prévision de modèle avec SQL Server R Services](https://gallery.cortanaintelligence.com/Tutorial/Energy-Demand-Forecast-Template-with-SQL-Server-R-Services-1)

**Quoi :** : Prévision de la demande est un problème important dans divers domaines, y compris l’énergie, de vente au détail et de services. Prévision de la demande exacte aide les entreprises conduite production meilleure planification, l’allocation des ressources et autres décisions métier importantes. Dans le secteur de l’énergie, la prévision de la demande est essentielle pour réduire le coût de stockage d’énergie et équilibrage offre et la demande.

**Comment :** Ce modèle utilise SQL Server R Services pour prédire la demande en électricité. Le modèle utilisé pour la prédiction est un modèle de régression de forêts aléatoires basé sur **rxDForest**, un algorithme inclus dans Microsoft R Server hautes performances d’apprentissage. La solution comprend un simulateur de demande, tout le code R et T-SQL nécessaire pour former un modèle, ainsi que les procédures stockées que vous pouvez utiliser pour générer des prédictions et créer des rapports. 


## <a name="bkmk_HowTo"></a>Comment utiliser les modèles

Pour télécharger les fichiers fournis avec chaque modèle, vous pouvez utiliser des commandes GitHub ou ouvrir le lien et cliquer sur **Download Zip** pour enregistrer tous les fichiers sur votre ordinateur.  Une fois téléchargée, la solution contient généralement ces dossiers :
  
-   **Données** : Contient les exemples de données pour chaque application.
  
-   **R**: Contient tout le code de développement R que nécessaires pour la solution. La solution nécessite les bibliothèques fournies par Microsoft R Server, mais peut être ouverte et modifiée dans n’importe quel IDE R. Le code R a été optimisé pour que les calculs soient effectués « dans la base de données », en affectant une instance de SQL Server comme contexte de calcul.
  
-   **SQLR**: Contient plusieurs fichiers .sql que vous pouvez exécuter dans un environnement SQL comme [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour créer les procédures stockées qui effectuent des tâches connexes telles que le traitement de données, ingénierie des fonctionnalités et déploiement de modèle.
  
    Ce dossier contient également un script PowerShell que vous pouvez exécuter pour appeler tous les scripts et créer l’environnement de bout en bout. N’oubliez pas de modifier le script pour l’adapter à votre environnement.

## <a name="next-steps"></a>Étapes suivantes

+ [Didacticiels de SQL Server machine learning](machine-learning-services-tutorials.md)




