---
title: Modèles de solution de science des données
description: Cet article présente les modèles spécifiques au secteur qui illustrent les meilleures pratiques et fournissent les bases qui vous aideront à implémenter une solution de Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6d87fbbb60f70292075d4f24080798d017ee5288
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "74947277"
---
# <a name="data-science-scenarios-and-solution-templates"></a>Scénarios de science des données et modèles de solutions
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit un certain nombre de modèles de solution de Machine Learning SQL Server. Ces modèles illustrent les bonnes pratiques et fournissent les bases qui vous aideront à implémenter une solution de Machine Learning rapidement. Chaque modèle est conçu pour résoudre un problème de science des données spécifique, pour un secteur vertical donné.
Les tâches dans chaque modèle vont de la préparation des données à la formation du modèle et au calcul des scores, en passant par l’ingénierie des caractéristiques. 

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Utilisez ces modèles pour en savoir plus sur le fonctionnement de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Ensuite, n’hésitez pas à adapter le modèle en fonction de votre propre scénario pour créer votre solution personnalisée.
::: moniker-end

::: moniker range=">=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Utilisez ces modèles pour découvrir comment fonctionnent les services de Machine Learning SQL Server. Ensuite, n’hésitez pas à adapter le modèle en fonction de votre propre scénario pour créer votre solution personnalisée.
::: moniker-end

Chaque solution comprend des exemples de données, du code R ou Python et des procédures stockées SQL, selon les besoins. Le code peut être exécuté dans votre environnement de développement R ou Python préféré, tout en effectuant les calculs dans SQL Server. Dans certains cas, vous pouvez exécuter du code directement à l’aide de T-SQL et d’un outil client SQL, tel que SQL Server Management Studio.

> [!TIP]
> 
> La plupart des modèles sont fournis dans plusieurs versions prenant en charge les plateformes locales et Cloud pour le Machine Learning. Par exemple, vous pouvez créer la solution en utilisant uniquement SQL Server, dans Microsoft R Server ou dans Azure Machine Learning.

+ Pour obtenir des instructions de téléchargement et d’installation, consultez [Comment utiliser les modèles](#bkmk_HowTo).

## <a name="fraud-detection"></a>Détection des fraudes

[Modèle de détection de fraude en ligne (SQL Server R Services)](https://github.com/Microsoft/r-server-fraud-detection)

**Quoi :** La possibilité de détecter les transactions frauduleuses est une importante pour les entreprises en ligne. Pour réduire les pertes financières, les entreprises doivent rapidement identifier les transactions qui ont été effectuées à l’aide de moyens de paiement ou d’informations d’identification dérobés. Quand des transactions frauduleuses sont découvertes, les entreprises prennent généralement des mesures pour bloquer certains comptes dès que possible, afin d’empêcher toute perte supplémentaire. Dans ce scénario, vous découvrirez comment utiliser des données de transactions d’achat en ligne pour identifier les fraudes probables.

**Comment :**  La détection des fraudes est résolue en tant que problème de classification binaire. Vous pouvez facilement appliquer la méthodologie utilisée dans ce modèle à la détection des fraudes dans d’autres domaines.


## <a name="campaign-optimization"></a>Optimisation de la campagne

[Prédire comment et quand contacter les prospects](https://microsoft.github.io/r-server-campaign-optimization/)

**Quoi :** Cette solution utilise les données du secteur des assurances pour prédire les prospects en fonction des données démographiques et de réponse historiques, ainsi que les détails spécifiques du produit.  Des suggestions sont également générées pour indiquer le meilleur canal et le moment idéal pour contacter les utilisateurs afin d’influencer le comportement d’achat.

**Comment :** La solution crée et compare plusieurs modèles. La solution dispose également de l’intégration et de la préparation automatisées des données à l’aide de procédures stockées. Des exemples parallèles sont fournis pour SQL Server dans la base de données, Azure et HDInsight Spark. 

## <a name="health-care-predict-length-of-stay-in-hospital"></a>Soins de santé : prédire la durée de séjour à l’hôpital 

[Prédiction de la durée de séjour dans les hôpitaux](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

**Quoi :** En ce qui concerne les soins et la planification, il est essentiel de pouvoir prédire de manière exacte si un patient doit être hospitalisé à long terme. Les administrateurs doivent être en mesure de déterminer les installations exigeant davantage de ressources, tandis que le personnel soignant souhaite être sûr de pouvoir répondre aux besoins des patients.

**Comment :** Cette solution utilise la Data Science Virtual Machine et comprend une instance de SQL Server dotée de fonctions de Machine Learning. Il comprend également un ensemble de rapports Power BI que vous pouvez utiliser pour interagir avec un modèle déployé.

## <a name="customer-churn"></a>Attrition clients

[Modèle de prédiction de l’attrition clients (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/README.md)

**Quoi :** L’analyse et la prédiction de l’attrition clients sont importantes dans tout secteur où la perte de clients à la concurrence doit être gérée et prévenue : secteur bancaire, télécommunications et vente au détail, pour n’en citer que quelques-uns. L’objectif de l’analyse de l’attrition consiste à identifier les clients susceptibles de passer à la concurrence, puis d’effectuer les actions appropriées pour conserver ces clients.

**Comment :** Ce modèle considère l’attrition comme un problème de **classification binaire**. Il utilise des exemples de données de deux sources, données démographiques et transactions de clients, pour classer les clients comme susceptibles ou non de passer à la concurrence.
  
## <a name="predictive-maintenance"></a>Maintenance prédictive

[Modèle de maintenance prédictive (SQL Server 2016)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/PredictiveMaintenance/README.md)

**Quoi :** L’objectif de la maintenance prédictive consiste à augmenter l’efficacité des tâches de maintenance en capturant les défaillances passées et en utilisant ces informations pour prédire quand et où un appareil est susceptible de tomber en panne. La possibilité de prévoir l’obsolescence des appareils est particulièrement importante pour les applications qui dépendent de capteurs ou de données distribuées. Cette méthode peut également être appliquée pour analyser ou prédire une erreur au niveau des appareils IoT (Internet des objets).

**Comment :** Cette solution s’attache à répondre à la question « Quand un ordinateur en service va-t-il tomber en panne ? » Les données d’entrée représentent des mesures de capteurs simulées pour des moteurs d’avion. Les données obtenues à partir de la surveillance des conditions d’exploitation actuelles du moteur, telles que le cycle de travail, les paramètres et les mesures de capteurs, sont utilisées pour créer trois types de modèles prédictifs :

-   **Modèles de régression**, pour prédire dans combien de temps un moteur tombera en panne. L’exemple de modèle prédit la métrique « Durée de vie restante » (RUL), également appelée « Temps de fonctionnement avant panne » (TTF).
  
-   **Modèles de classification**, pour prédire si un moteur est susceptible de tomber en panne.
  
    Le **modèle de classification binaire** prédit si un moteur tombera en panne dans un délai donné.

    Le **modèle de classification multiclasse** prédit si un moteur particulier tombera en panne et fournit une fenêtre de temps de défaillance probable. Par exemple, pour un jour donné, vous pouvez prédire si un appareil est susceptible de tomber en panne ce jour-là ou dans un laps de temps suivant ce jour.

## <a name="energy-demand-forecasting"></a>Prévisions de demande d’énergie

[Modèle de prévision de demande d’énergie avec SQL Server R Services](https://gallery.cortanaintelligence.com/Tutorial/Energy-Demand-Forecast-Template-with-SQL-Server-R-Services-1)

**Quoi :** La prévision de la demande est un problème important dans différents domaines, notamment l’énergie, la vente au détail et les services. Prévoir la demande de façon précise aide les entreprises à améliorer la planification de la production ainsi que l’allocation des ressources, tout en facilitant la prise d’autres décisions importantes pour l’entreprise. Dans le secteur de l’énergie, la prévision de la demande est essentielle pour réduire le coût de stockage énergétique tout en équilibrant l’offre et la demande.

**Comment :** Ce modèle utilise SQL Server R Services pour prédire la demande en électricité. Le modèle utilisé pour la prédiction est un modèle de régression de forêt aléatoire basé sur **rxDForest**, un algorithme de Machine Learning hautes performances inclus dans Microsoft R Server. La solution comprend un simulateur de demande, tout le code R et T-SQL nécessaire pour former un modèle, ainsi que les procédures stockées que vous pouvez utiliser pour générer des prédictions et créer des rapports. 


## <a name="how-to-use-the-templates"></a><a name="bkmk_HowTo"></a>Comment utiliser les modèles

Pour télécharger les fichiers fournis avec chaque modèle, vous pouvez utiliser des commandes GitHub ou ouvrir le lien et cliquer sur **Download Zip** pour enregistrer tous les fichiers sur votre ordinateur.  Une fois téléchargée, la solution contient généralement ces dossiers :
  
-   **Données** : contient les exemples de données pour chaque application.
  
-   **R** : contient tout le code de développement R dont vous avez besoin pour la solution. La solution nécessite les bibliothèques fournies par Microsoft R Server, mais peut être ouverte et modifiée dans n’importe quel IDE R. Le code R a été optimisé pour que les calculs soient effectués « dans la base de données », en affectant une instance de SQL Server comme contexte de calcul.
  
-   **SQLR** : contient plusieurs fichiers .sql que vous pouvez exécuter dans un environnement SQL comme [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour créer les procédures stockées qui effectuent des tâches associées, telles que le traitement des données, l’ingénierie des caractéristiques et le déploiement de modèle.
  
    Ce dossier contient également un script PowerShell que vous pouvez exécuter pour appeler tous les scripts et créer l’environnement de bout en bout. N’oubliez pas de modifier le script pour l’adapter à votre environnement.

## <a name="next-steps"></a>Étapes suivantes

+ [Didacticiels sur SQL Server Machine Learning](machine-learning-services-tutorials.md)




