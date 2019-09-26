---
title: Générer des prévisions et des prédictions à l’aide de modèles de Machine Learning
description: Utilisez rxPredict ou sp_rxPredict pour la notation en temps réel, ou prédire T-SQL pour la notation native pour les prédictions et les prévisions dans R et Python dans SQL Server Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/30/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 14ccd4beb2186213cb3d94b10031ac732224f4d9
ms.sourcegitcommit: 2f56848ec422845ee81fb84ed321a716c677aa0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71271901"
---
# <a name="how-to-generate-forecasts-and-predictions-using-machine-learning-models-in-sql-server"></a>Comment générer des prévisions et des prédictions à l’aide de modèles de Machine Learning dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

L’utilisation d’un modèle existant pour prévoir ou prédire les résultats des nouvelles entrées de données est une tâche principale dans Machine Learning. Cet article énumère les approches permettant de générer des prédictions dans SQL Server. Parmi les approches, citons les méthodologies de traitement interne pour les prédictions à haut débit, où la vitesse est basée sur des réductions incrémentielles des dépendances au moment de l’exécution. Moins de dépendances signifient des prédictions plus rapides.

L’utilisation de l’infrastructure de traitement interne (notation native ou en temps réel) est fournie avec les exigences de bibliothèque. Les fonctions doivent provenir des bibliothèques Microsoft. Le code R ou python appelant des fonctions Open source ou tierces n’est pas pris en charge C++ dans le CLR ou les extensions.

Le tableau suivant récapitule les frameworks de notation pour les prévisions et les prédictions. 

| Méthodologie           | Interface         | Configuration requise pour la bibliothèque | Vitesses de traitement |
|-----------------------|-------------------|----------------------|----------------------|
| Framework d’extensibilité | [rxPredict (R)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) <br/>[rx_predict (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Aucun. Les modèles peuvent être basés sur n’importe quelle fonction R ou python | Centaines de millisecondes. <br/>Le chargement d’un environnement d’exécution a un coût fixe, avec une moyenne de trois à 600 millisecondes, avant que les nouvelles données ne soient notées. |
| [Extension CLR de notation en temps réel](../real-time-scoring.md) | [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) sur un modèle sérialisé | R RevoScaleR, MicrosoftML <br/>Python: revoscalepy, microsoftml | Dizaines de millisecondes, en moyenne. |
| [Extension de C++ notation Native](../sql-native-scoring.md) | [Prédire la fonction T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) sur un modèle sérialisé | R RevoScaleR <br/>Python: revoscalepy | Moins de 20 millisecondes, en moyenne. | 

La vitesse de traitement et non la substance de la sortie est la fonctionnalité de différenciation. En supposant que les mêmes fonctions et entrées, la sortie notée ne doit pas varier en fonction de l’approche que vous utilisez.

Le modèle doit être créé à l’aide d’une fonction prise en charge, puis sérialisé en un flux d’octets bruts enregistré sur le disque ou stocké au format binaire dans une base de données. À l’aide d’une procédure stockée ou de T-SQL, vous pouvez charger et utiliser un modèle binaire sans la surcharge du runtime de langage R ou python, ce qui réduit le délai d’exécution lors de la génération de scores de prédiction sur les nouvelles entrées.

L’importance du CLR et C++ des extensions est proche du moteur de base de données lui-même. Le langage natif du moteur de base de C++données est, ce qui signifie C++ que les extensions écrites dans s’exécutent avec moins de dépendances. En revanche, les extensions CLR dépendent de .NET Core. 

Comme vous pouvez vous y attendre, la prise en charge de la plateforme est affectée par ces environnements d’exécution. Les extensions du moteur de base de données native s’exécutent partout où la base de données relationnelle est prise en charge Windows, Linux, Azure. Les extensions CLR avec l’exigence .NET Core sont actuellement Windows uniquement.

## <a name="scoring-overview"></a>Vue d’ensemble du score

Le _score_ est un processus en deux étapes. Tout d’abord, vous spécifiez un modèle déjà formé à charger à partir d’une table. Ensuite, transmettez les nouvelles données d’entrée à la fonction afin de générer des valeursde prédiction (ou des scores). L’entrée est souvent une requête T-SQL, en retournant des lignes tabulaires ou uniques. Vous pouvez choisir de générer une valeur de colonne unique représentant une probabilité, ou vous pouvez générer plusieurs valeurs, telles qu’un intervalle de confiance, une erreur ou un autre complément utile à la prédiction.

En effectuant un pas à pas principal, le processus global de préparation du modèle, puis de génération des scores, peut être résumé de cette façon:

1. Créez un modèle à l’aide d’un algorithme pris en charge. La prise en charge varie selon la méthodologie de notation que vous choisissez.
2. Former le modèle.
3. Sérialisez le modèle à l’aide d’un format binaire spécial.
3. Enregistrez le modèle dans SQL Server. En général, cela signifie que le modèle sérialisé est stocké dans une table SQL Server.
4. Appelez la fonction ou la procédure stockée, en spécifiant les entrées de modèle et de données comme paramètres.

Lorsque l’entrée comprend de nombreuses lignes de données, il est généralement plus rapide d’insérer les valeurs de prédiction dans une table dans le cadre du processus de notation. La génération d’un score unique est plus courante dans un scénario où vous obtenez des valeurs d’entrée à partir d’une demande de formulaire ou d’utilisateur, et renvoie le score à une application cliente. Pour améliorer les performances lors de la génération de scores successifs, SQL Server peut mettre en cache le modèle afin qu’il puisse être rechargé en mémoire.

## <a name="compare-methods"></a>Comparer des méthodes

Pour préserver l’intégrité des principaux processus du moteur de base de données, la prise en charge de R et Python est activée dans une architecture double qui isole le traitement de la langue du traitement du SGBDR. À compter de SQL Server 2016, Microsoft a ajouté une infrastructure d’extensibilité qui permet d’exécuter des scripts R à partir de T-SQL. Dans SQL Server 2017, l’intégration Python a été ajoutée. 

L’infrastructure d’extensibilité prend en charge toutes les opérations que vous pouvez effectuer dans R ou python, allant des fonctions simples à la formation des modèles Machine Learning complexes. Toutefois, l’architecture à double processus nécessite l’appel d’un processus R ou python externe pour chaque appel, quelle que soit la complexité de l’opération. Lorsque la charge de travail implique le chargement d’un modèle pré-formé à partir d’une table et son évaluation sur les données déjà présentes dans SQL Server, la surcharge liée à l’appel des processus externes ajoute de la latence qui peut être inacceptable dans certaines circonstances. Par exemple, la détection des fraudes requiert une notation rapide pour être pertinente.

Pour augmenter les vitesses de notation pour les scénarios tels que la détection des fraudes, SQL Server C++ ajouté des bibliothèques de score intégrées et des extensions CLR qui éliminent la surcharge des processus de démarrage R et Python.

La [**notation en temps réel**](../real-time-scoring.md) était la première solution pour une notation hautes performances. Introduite dans les premières versions de SQL Server 2017 et des mises à jour ultérieures de SQL Server 2016, la notation en temps réel s’appuie sur les bibliothèques CLR qui se trouvent dans le traitement R et Python sur les fonctions contrôlées par Microsoft dans RevoScaleR, MicrosoftML (R), revoscalepy et microsoftml (Python). Les bibliothèques CLR sont appelées à l’aide de la procédure stockée **sp_rxPredict** pour générer des scores à partir de n’importe quel type de modèle pris en charge, sans appeler le runtime R ou python.

La [notation Native](../sql-native-scoring.md) est une fonctionnalité SQL Server 2017, implémentée en C++ tant que bibliothèque native, mais uniquement pour les modèles RevoScaleR et revoscalepy. Il s’agit de l’approche la plus rapide et la plus sécurisée, mais elle prend en charge un plus petit ensemble de fonctions par rapport à d’autres méthodologies.

## <a name="choose-a-scoring-method"></a>Choisir une méthode de calcul de score

Les exigences en matière de plateforme dictent souvent la méthodologie de notation à utiliser.

| Version et plateforme du produit | Méthodologie |
|------------------------------|-------------|
| SQL Server 2017 sur Windows, SQL Server 2017 Linux et Azure SQL Database | **Notation Native** avec prédiction T-SQL |
| SQL Server 2017 (Windows uniquement), SQL Server 2016 R services à SP1 ou version ultérieure | **Notation en temps réel** avec procédure\_stockée SP rxPredict |

Nous recommandons la notation native avec la fonction PREDICT. L’utilisation\_de SP rxPredict requiert l’activation de l’intégration SQLCLR. Tenez compte des implications en matière de sécurité avant d’activer cette option.

## <a name="serialization-and-storage"></a>Sérialisation et stockage

Pour utiliser un modèle avec l’une des options de notation rapide, enregistrez le modèle à l’aide d’un format sérialisé spécial, qui a été optimisé pour l’efficacité de la taille et de la notation.

+ Appelez [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) pour écrire un modèle pris en charge dans le format **RAW** .
+ Appelez [rxUnserializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel)pour reconstituer le modèle pour une utilisation dans un autre code R ou pour afficher le modèle.

**Utilisation de SQL**

À partir du code SQL, vous pouvez former le modèle à l’aide de [sp_execute_external_script](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)et insérer directement les modèles formés dans une table, dans une colonne de type **varbinary (max)** . Pour obtenir un exemple simple, consultez [créer un modèle preditive dans R](../tutorials/quickstart-r-train-score-model.md)

**Utilisation de R**

À partir du code R, appelez la fonction [rxWriteObject](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxwriteobject) à partir du package RevoScaleR pour écrire le modèle directement dans la base de données. La fonction **rxWriteObject ()** peut récupérer des objets R à partir d’une source de données ODBC comme SQL Server ou écrire des objets dans SQL Server. L’API est modélisée à partir d’un magasin clé-valeur simple.
  
Si vous utilisez cette fonction, veillez à sérialiser le modèle à l’aide de [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) en premier. Ensuite, définissez l’argument *Serialize* dans **rxWriteObject** sur false pour éviter de répéter l’étape de sérialisation.

La sérialisation d’un modèle dans un format binaire est utile, mais elle n’est pas obligatoire si vous évaluez des prédictions à l’aide de l’environnement d’exécution R et Python dans l’infrastructure d’extensibilité. Vous pouvez enregistrer un modèle au format d’octet brut dans un fichier, puis le lire dans SQL Server. Cette option peut être utile si vous déplacez ou copiez des modèles entre des environnements.

## <a name="scoring-in-related-products"></a>Score dans les produits associés

Si vous utilisez le [serveur autonome](r-server-standalone.md) ou un [Microsoft machine learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), vous avez d’autres options, outre des procédures stockées et des fonctions T-SQL pour générer des prédictions rapidement. Le serveur autonome et Machine Learning Server prennent en charge le concept de *service Web* pour le déploiement de code. Vous pouvez regrouper un modèle pré-formé R ou python en tant que service Web, appelé au moment de l’exécution pour évaluer de nouvelles entrées de données. Pour plus d’informations, consultez ces articles :

+ [Qu’est-ce que les services Web dans Machine Learning Server?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services)
+ [Qu’est-ce que la fonction de fonctionnement?](https://docs.microsoft.com/machine-learning-server/what-is-operationalization)
+ [Déployer un modèle Python en tant que service Web avec azureml-Model-Management-SDK](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service)
+ [Publier un bloc de code R ou un modèle en temps réel en tant que nouveau service Web](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)
+ [package mrsdeploy pour R](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)


## <a name="see-also"></a>Voir aussi

+ [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)  
+ [rxRealTimeScoring](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxrealtimescoring)
+ [sp-rxPredict](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql)
+ [PRÉDIRE T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)