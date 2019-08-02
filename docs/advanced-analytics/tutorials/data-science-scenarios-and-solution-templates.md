---
title: Scénarios de science des données et modèles de solution
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 313b00ff9c3863e8cd1c3de3b0919fc130b01d1e
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714934"
---
# <a name="data-science-scenarios-and-solution-templates"></a>Scénarios de science des données et modèles de solution
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Les modèles sont des exemples de solutions qui illustrent les bonnes pratiques et fournissent les bases qui vous aideront à implémenter une solution rapidement. Chaque modèle est conçu pour résoudre un problème spécifique, pour un secteur ou une verticale spécifique. Les tâches dans chaque modèle vont de la préparation des données à la formation du modèle et au calcul des scores, en passant par l’ingénierie des caractéristiques. Utilisez ces modèles pour découvrir comment [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] fonctionne. Ensuite, n’hésitez pas à personnaliser le modèle pour l’adapter à votre propre scénario et à créer une solution personnalisée. 

Chaque solution comprend des exemples de données, du code R ou python et des procédures stockées SQL, le cas échéant. Le code peut être exécuté dans votre environnement de développement R ou python préféré, avec des calculs effectués dans SQL Server. Dans certains cas, vous pouvez exécuter du code directement à l’aide de T-SQL et de n’importe quel outil client SQL, tel que SQL Server Management Studio.

> [!TIP]
> 
> La plupart des modèles sont fournis dans plusieurs versions prenant en charge les plateformes locales et Cloud pour Machine Learning. Par exemple, vous pouvez générer la solution en utilisant uniquement SQL Server, ou vous pouvez générer la solution dans Microsoft R Server ou dans Azure Machine Learning.

+ Pour obtenir des instructions de téléchargement et d’installation, consultez [comment utiliser les modèles](#bkmk_HowTo).

## <a name="fraud-detection"></a>Détection des fraudes

[Modèle de détection des fraudes en ligne (SQL Server R Services)](https://github.com/Microsoft/r-server-fraud-detection)

**Données** La possibilité de détecter les transactions frauduleuses est importante pour les entreprises en ligne. Pour réduire les pertes de frais, les entreprises doivent rapidement identifier les transactions qui ont été effectuées à l’aide de moyens de paiement ou d’informations d’identification volés. Quand des transactions frauduleuses sont découvertes, les entreprises prennent généralement des mesures pour bloquer certains comptes dès que possible, afin d’empêcher toute perte supplémentaire. Dans ce scénario, vous allez apprendre à utiliser les données de transactions d’achat en ligne pour identifier les fraudes probables.

**Utilisation**  La détection des fraudes est résolue en tant que problème de classification binaire. Vous pouvez facilement appliquer la méthodologie utilisée dans ce modèle à la détection des fraudes dans d’autres domaines.


## <a name="campaign-optimization"></a>Optimisation de la campagne

[Prédire comment et quand contacter les responsables](https://microsoft.github.io/r-server-campaign-optimization/)

**Données** Cette solution utilise les données de l’industrie de l’assurance pour prédire les clients en fonction des données démographiques, des données de réponse historiques et des détails spécifiques au produit.  Des recommandations sont également générées pour indiquer le meilleur canal et le plus de temps pour aborder les utilisateurs afin d’influencer le comportement d’achat.

**Utilisation** La solution crée et compare plusieurs modèles. La solution illustre également l’intégration de données automatisée et la préparation des données à l’aide de procédures stockées. Des exemples parallèles sont fournis pour SQL Server dans la base de données, dans Azure et HDInsight Spark. 

## <a name="health-care-predict-length-of-stay-in-hospital"></a>Soins de santé: prédire la durée de séjour dans l’hôpital 

[Prédiction de la durée de séjour dans les hôpitaux](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

**Données** La prédiction précise des patients qui peuvent nécessiter une hospitalisation à long terme est une partie importante des soins et de la planification. Les administrateurs doivent être en mesure de déterminer les installations qui nécessitent davantage de ressources, et les soignants souhaitent garantir qu’ils peuvent répondre aux besoins des patients.

**Utilisation** Cette solution utilise la Data Science Virtual Machine et comprend une instance de SQL Server avec Machine Learning activée. Il comprend également un ensemble de rapports de Power BI que vous pouvez utiliser pour interagir avec un modèle déployé.

## <a name="customer-churn"></a>Évolution du client

[Modèle de prédiction de l’évolution du client (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/README.md)

**Données** L’analyse et la prédiction de l’évolution du client sont importantes dans tous les secteurs où la perte de clients aux concurrents doit être gérée et empêchée: Banque, télécommunications et vente au détail, pour n’en nommer que quelques-uns. L’objectif de l’analyse de l’attrition consiste à identifier les clients susceptibles de passer à la concurrence, puis d’effectuer les actions appropriées pour conserver ces clients.

**Utilisation** Ce modèle formule le problème d’évolution comme un problème de **classification binaire** . Il utilise des exemples de données de deux sources, données démographiques et transactions de clients, pour classer les clients comme susceptibles ou non de passer à la concurrence.
  
## <a name="predictive-maintenance"></a>Maintenance prédictive

[Modèle de maintenance prédictive (SQL Server 2016)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/PredictiveMaintenance/README.md)

**Données** La maintenance prédictive vise à augmenter l’efficacité des tâches de maintenance en capturant les défaillances passées et en utilisant ces informations pour prédire à quel moment ou à quel endroit un appareil peut échouer. La possibilité de prévoir l’obsolescence des appareils est particulièrement utile pour les applications qui reposent sur des données distribuées ou des capteurs. Cette méthode peut également être appliquée pour analyser ou prédire une erreur dans les appareils IoT (Internet des objets).

**Utilisation** Cette solution se concentre sur la réponse à la question «quand un ordinateur en service échoue-t-il?» Les données d’entrée représentent des mesures de capteurs simulées pour des moteurs d’avion. Les données obtenues à partir de la surveillance des conditions d’exploitation actuelles du moteur, telles que le cycle de travail actuel, les paramètres et les mesures de capteur, sont utilisées pour créer trois types de modèles prédictifs:

-   **Modèles de régression**, pour prédire dans combien de temps un moteur tombera en panne. L’exemple de modèle prédit la mesure «durée de vie utile restante» (vie utile restante), également appelée «temps d’échec» (TTF).
  
-   **Modèles de classification**, pour prédire si un moteur est susceptible de tomber en panne.
  
    Le **modèle de classification binaire** prédit si un moteur échoue dans un intervalle de temps donné.

    Le **modèle de classification multiclasse** prédit si un moteur particulier peut échouer et fournit une fenêtre de temps probable de défaillance. Par exemple, pour un jour donné, vous pouvez prédire si un appareil est susceptible de tomber en panne ce jour-là ou dans un laps de temps suivant ce jour.

## <a name="energy-demand-forecasting"></a>Prévision de la demande d’énergie

[Modèle de prévision de la demande d’énergie avec SQL Server R Services](https://gallery.cortanaintelligence.com/Tutorial/Energy-Demand-Forecast-Template-with-SQL-Server-R-Services-1)

**Éléments suivants:** La prévision de la demande est un problème important dans différents domaines, y compris l’énergie, la vente au détail et les services. La prévision de la demande précise aide les entreprises à améliorer la planification de la production, l’allocation des ressources et à prendre d’autres décisions importantes pour l’entreprise. Dans le secteur de l’énergie, la prévision de la demande est essentielle pour réduire le coût du stockage énergétique et l’approvisionnement et la demande d’équilibrage.

**Utilisation** Ce modèle utilise SQL Server R Services pour prédire la demande d’électricité. Le modèle utilisé pour la prédiction est un modèle de régression de forêt aléatoire basé sur **rxDForest**, un algorithme de machine learning hautes performances inclus dans Microsoft R Server. La solution comprend un simulateur de demande, tout le code R et T-SQL nécessaire pour former un modèle, ainsi que les procédures stockées que vous pouvez utiliser pour générer des prédictions et créer des rapports. 


## <a name="bkmk_HowTo"></a>Comment utiliser les modèles

Pour télécharger les fichiers fournis avec chaque modèle, vous pouvez utiliser des commandes GitHub ou ouvrir le lien et cliquer sur **Download Zip** pour enregistrer tous les fichiers sur votre ordinateur.  Une fois téléchargée, la solution contient généralement ces dossiers :
  
-   **Données** : Contient les exemples de données pour chaque application.
  
-   **R**: Contient tout le code de développement R dont vous avez besoin pour la solution. La solution nécessite les bibliothèques fournies par Microsoft R Server, mais peut être ouverte et modifiée dans n’importe quel IDE R. Le code R a été optimisé pour que les calculs soient effectués « dans la base de données », en affectant une instance de SQL Server comme contexte de calcul.
  
-   **SQLR**: Contient plusieurs fichiers. SQL que vous pouvez exécuter dans un environnement SQL, par [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] exemple pour créer les procédures stockées qui effectuent des tâches associées, telles que le traitement des données, l’ingénierie des fonctionnalités et le déploiement de modèle.
  
    Ce dossier contient également un script PowerShell que vous pouvez exécuter pour appeler tous les scripts et créer l’environnement de bout en bout. N’oubliez pas de modifier le script pour l’adapter à votre environnement.

## <a name="next-steps"></a>Étapes suivantes

+ [Didacticiels de Machine Learning SQL Server](machine-learning-services-tutorials.md)




