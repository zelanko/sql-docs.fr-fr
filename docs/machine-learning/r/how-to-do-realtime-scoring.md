---
title: Générer des prévisions et des prédictions
description: Utilisez rxPredict (ou sp_rxPredict pour le scoring en temps réel) ou PREDICT T-SQL pour effectuer le scoring natif des prédictions et des prévisions en langages R et Python dans SQL Server Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/30/2020
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c07a5b8d3e1b34c0bb33f44a20ab5fff867db922
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "81117622"
---
# <a name="how-to-generate-forecasts-and-predictions-using-machine-learning-models-in-sql-server"></a>Générer des prévisions et des prédictions à l’aide de modèles Machine Learning dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

L’utilisation d’un modèle existant pour prévoir ou prédire les résultats des nouvelles entrées de données constitue l’une des tâches principales dans Machine Learning. Cet article énumère les approches permettant de générer des prédictions dans SQL Server. Il existe plusieurs approches, telles que les méthodologies de traitement interne qui permettent de générer des prédictions très rapidement. Leur vitesse est basée sur des réductions incrémentielles des dépendances de temps d’exécution. Une baisse des dépendances signifie des prédictions plus rapides.

Des exigences relatives aux bibliothèques s’appliquent lorsque l’infrastructure de traitement interne (scoring natif ou en temps réel) est utilisée. Les fonctions doivent provenir des bibliothèques Microsoft. Les codes R ou Python permettant d’appeler des fonctions open source ou tierces ne sont pas pris en charge sur les extensions CLR ou C++.

Le tableau suivant dresse un récapitulatif des infrastructures de scoring destinées aux prévisions et aux prédictions. 

| Méthodologie           | Interface         | Exigences relatives aux bibliothèques | Vitesses de traitement |
|-----------------------|-------------------|----------------------|----------------------|
| Framework d’extensibilité | [rxPredict (R)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) <br/>[rx_predict (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Aucun. Les modèles peuvent être basés sur n’importe quelle fonction R ou Python | Centaines de millisecondes. <br/>Le chargement d’un environnement d’exécution implique un coût fixe, avec un délai moyen compris entre 300 et 600 millisecondes avant qu’un score ne soit attribué aux nouvelles données. |
| [Extension CLR de scoring en temps réel](../real-time-scoring.md) | [sp_rxPredict](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) sur un modèle sérialisé | R : RevoScaleR, MicrosoftML <br/>Python : revoscalepy, microsoftml | Dizaines de millisecondes, en moyenne. |
| [Extension C++ de scoring natif](../sql-native-scoring.md) | [Fonction PREDICT T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) sur un modèle sérialisé | R : RevoScaleR <br/>Python : revoscalepy | Moins de 20 millisecondes, en moyenne. | 

L’utilisation de la vitesse de traitement au lieu de la substance de la sortie constitue une caractéristique notable. Si les mêmes fonctions et entrées sont utilisées, la sortie avec un score ne doit pas varier en fonction de l’approche choisie.

Le modèle doit être créé à l’aide d’une fonction prise en charge, puis sérialisé sous la forme d’un flux d’octets bruts enregistré sur le disque ou stocké au format binaire dans une base de données. À l’aide d’une procédure stockée ou de T-SQL, vous pouvez charger et utiliser un modèle binaire sans la surcharge de temps d’exécution d’un langage R ou Python. Cela permet de réduire le délai d’exécution lors de la génération de scores de prédiction sur les nouvelles entrées.

La proximité avec le moteur de base de données en question constitue un aspect important des extensions CLR et C++. Le moteur de base de données utilise C++ comme langage natif. Les extensions écrites en C++ fonctionnent donc avec moins de dépendances. En revanche, les extensions CLR dépendent de .NET Core. 

Comme vous pouvez vous y attendre, la prise en charge de la plateforme est affectée par ces environnements d’exécution. Les extensions du moteur de base de données native peuvent être exécutées partout où la base de données relationnelle est prise en charge : Windows, Linux, Azure. Les extensions CLR avec des exigences .NET Core fonctionnent actuellement sous Windows uniquement.

## <a name="scoring-overview"></a>Vue d’ensemble du scoring

Le _scoring_ est un processus en deux étapes. Tout d’abord, vous spécifiez un modèle déjà entraîné à charger à partir d’une table. Ensuite, vous transmettez les nouvelles données d’entrée à la fonction afin de générer des valeurs de prédiction (ou des _scores_). L’entrée est souvent une requête T-SQL retournant des lignes tabulaires ou uniques. Vous pouvez choisir de générer une valeur de colonne unique, qui représente une probabilité, ou plusieurs valeurs, comme un intervalle de confiance, une erreur ou un autre complément utile pour la prédiction.

En ce qui concerne les étapes précédentes, nous pouvons résumer le processus global de préparation du modèle et de génération des scores de la façon suivante :

1. Créez un modèle à l’aide d’un algorithme pris en charge. La prise en charge varie selon la méthodologie de scoring choisie.
2. Effectuez l’apprentissage du modèle.
3. Sérialisez le modèle à l’aide d’un format binaire spécial.
3. Enregistrez le modèle sur SQL Server. En général, cela signifie que le modèle sérialisé est stocké dans une table SQL Server.
4. Appelez la fonction ou la procédure stockée en spécifiant les entrées de modèle et de données comme paramètres.

Lorsque l’entrée comprend de plusieurs lignes de données, il est généralement plus rapide d’insérer les valeurs de prédiction dans une table dans le cadre du processus de scoring. Un score unique est plus souvent généré lorsque les valeurs d’entrée proviennent d’une demande de formulaire ou d’utilisateur et que le score est retourné à une application cliente. Pour améliorer les performances lors de la génération de scores consécutifs, SQL Server peut mettre en cache le modèle afin qu’il puisse être rechargé dans la mémoire.

## <a name="compare-methods"></a>Comparer les méthodes

Pour préserver l’intégrité des principaux processus du moteur de base de données, la prise en charge de R et Python est activée dans une architecture double qui isole le traitement du langage de celui du SGBDR. À partir de SQL Server 2016, Microsoft a ajouté une infrastructure d’extensibilité qui permet d’exécuter des scripts R à partir de T-SQL. Dans SQL Server 2017, l’intégration de Python a été ajoutée. 

L’infrastructure d’extensibilité prend en charge toutes les opérations que vous pouvez effectuer en langage R ou Python (fonctions simples, entraînement de modèles Machine Learning complexes, etc.). Toutefois, l’architecture à double processus nécessite d’appeler un processus R ou Python externe à chaque appel, quelle que soit la complexité de l’opération. Lorsque la charge de travail nécessite de charger un modèle pré-entraîné à partir d’une table et de lui attribuer un score en comparant avec les données déjà présentes dans SQL Server, la surcharge liée à l’appel des processus externes ajoute alors une latence pouvant être inacceptable dans certaines circonstances. Par exemple, la détection des fraudes exige un scoring rapide pour être pertinente.

Pour augmenter la vitesse de scoring dans le cadre de scénarios tels que la détection des fraudes, SQL Server a ajouté des bibliothèques de scores intégrées ainsi que des extensions C++ et CLR destinées à éliminer la surcharge lors des processus de démarrage R et Python.

Le [**scoring en temps réel**](../real-time-scoring.md) représentait la première solution de scoring hautes performances. Introduit dans les premières versions de SQL Server 2017 et dans les mises à jour ultérieures de SQL Server 2016, le scoring en temps réel s’appuie sur des bibliothèques CLR qui viennent remplacer le traitement R et Python dans les fonctions contrôlées par Microsoft dans RevoScaleR, MicrosoftML (R), revoscalepy et microsoftml (Python). Les bibliothèques CLR sont appelées à l’aide de la procédure stockée **sp_rxPredict** pour générer des scores à partir de n’importe quel type de modèle pris en charge, sans devoir appeler le runtime R ou Python.

Le [**scoring natif**](../sql-native-scoring.md) est une fonctionnalité SQL Server 2017 implémentée en tant que bibliothèque C++ native, mais uniquement pour les modèles RevoScaleR et revoscalepy. Il s’agit de l’approche la plus rapide et la plus sécurisée, mais elle prend en charge moins de fonctions que les autres méthodologies.

## <a name="choose-a-scoring-method"></a>Choisir une méthode de scoring

Les exigences en matière de plateforme imposent souvent la méthodologie de scoring à utiliser.

| Plateforme et version du produit | Méthodologie |
|------------------------------|-------------|
| SQL Server 2017 sur Windows, SQL Server 2017 Linux et Azure SQL Database | **Scoring natif** avec T-SQL PREDICT |
| SQL Server 2017 (Windows uniquement), SQL Server 2016 R Services avec SP1 ou une version ultérieure | **Scoring en temps réel** avec la procédure stockée sp\_rxPredict |

Nous recommandons le scoring natif avec la fonction PREDICT. Utiliser sp\_rxPredict nécessite d’activer l’intégration SQLCLR. Tenez compte des implications en matière de sécurité avant d’activer cette option.

## <a name="serialization-and-storage"></a>Sérialisation et stockage

Afin d’utiliser un modèle avec l’une des options de scoring rapide, enregistrez le modèle sous un format sérialisé spécial qui a été optimisé en termes de taille et d’efficacité du scoring.

+ Appelez [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) pour écrire un modèle pris en charge au format **brut**.
+ Appelez [rxUnserializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) pour reconstituer le modèle afin de l’utiliser dans un autre code R ou d’afficher le modèle.

**Avec SQL**

Avec un code SQL, vous pouvez effectuer l’apprentissage du modèle à l’aide de [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), puis insérer directement les modèles entraînés dans une table, à l’intérieur d’une colonne de type **varbinary(max)** . Pour obtenir un exemple simple, consultez [Create a preditive model in R](../tutorials/quickstart-r-train-score-model.md) (Créer un modèle prédictif en langage R)

**Avec R**

Avec un code R, appelez la fonction [rxWriteObject](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxwriteobject) du package RevoScaleR pour écrire le modèle directement dans la base de données. La fonction **rxWriteObject()** peut récupérer des objets R à partir d’une source de données ODBC comme SQL Server ou y écrire des objets. L’API est modélisée à partir d’un magasin de paires clé-valeur simple.
  
Si vous utilisez cette fonction, assurez-vous de sérialiser le modèle à l’aide de [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) au préalable. Ensuite, définissez l’argument *serialize* dans **rxWriteObject** sur FALSE pour éviter de répéter l’étape de sérialisation.

La sérialisation d’un modèle dans un format binaire est utile, mais elle n’est pas obligatoire si vous générez un score pour les prédictions à l’aide des environnements d’exécution R et Python dans l’infrastructure d’extensibilité. Vous pouvez enregistrer un modèle au format d’octet brut en tant que fichier, puis le lire dans SQL Server. Cette option peut être utile si vous déplacez ou copiez des modèles entre des environnements.

## <a name="scoring-in-related-products"></a>Scoring dans les produits associés

Si vous utilisez le [serveur autonome](r-server-standalone.md) ou un serveur [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), les procédures stockées et les fonctions T-SQL ne sont pas les seules options dont vous disposez pour générer des prédictions rapidement. Le serveur autonome et Machine Learning Server prennent tous les deux en charge le concept d’un *service Web* pour le déploiement de code. Vous pouvez regrouper un modèle R ou Python pré-entraîné en tant que service web qui sera appelé au moment de l’exécution pour évaluer de nouvelles entrées de données. Pour plus d’informations, voir les articles suivants :

+ [What are web services in Machine Learning Server?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services) (Qu’est-ce qu’un service web dans Machine Learning Server ?)
+ [What is operationalization?](https://docs.microsoft.com/machine-learning-server/what-is-operationalization) (Qu’est-ce que l’opérationnalisation ?)
+ [Deploy a Python model as a web service with azureml-model-management-sdk](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service) (Déployer un modèle Python en tant que service web avec azureml-model-management-sdk)
+ [Publish an R code block or a real-time model as a new web service](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice) (Publier un bloc de code R ou un modèle en temps réel en tant que nouveau service web)
+ [mrsdeploy package for R](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package) (Package mrsdeploy pour R)


## <a name="see-also"></a>Voir aussi

+ [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)  
+ [rxRealTimeScoring](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxrealtimescoring)
+ [sp-rxPredict](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql)
+ [PREDICT T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)