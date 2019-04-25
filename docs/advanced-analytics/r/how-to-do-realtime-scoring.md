---
title: Générer des prévisions et des prédictions à l’aide de modèles d’apprentissage automatique - SQL Server Machine Learning Services
description: Destiné à rxPredict ou sp_rxPredict pour calculer les scores en temps réel, ou prédire le T-SQL natif pour les prédictions de notation et de prévision dans R et Pythin dans SQL Server Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/30/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 001b90eafd26c90f730e5647f0dc62d756ca9d1b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62503771"
---
# <a name="how-to-generate-forecasts-and-predictions-using-machine-learning-models-in-sql-server"></a>Comment générer des prévisions et des prédictions à l’aide de modèles d’apprentissage automatique dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

À l’aide d’un modèle existant pour prévoir ou prédire les résultats de nouvelles entrées de données est une tâche essentielle dans l’apprentissage. Cet article énumère les approches permettant de générer des prédictions dans SQL Server. Parmi les approches méthodologies de traitement interne pour les prédictions à haut débit, où la vitesse est basée sur des réductions incrémentielles de sont exécutés les dépendances de temps. Moins de dépendances signifient des prédictions plus rapides.

À l’aide de l’infrastructure de traitement interne (notation en temps réel ou natif) est fourni avec les exigences de la bibliothèque. Fonctions doivent être des bibliothèques Microsoft. Extensions CLR ou C++ ne prend pas en charge R ou Python code appelant les fonctions de tiers ou open source.

Le tableau suivant récapitule les infrastructures de calcul de score pour les prévisions et des prédictions. 

| Méthodologie           | Interface         | Exigences de la bibliothèque | Vitesse de traitement |
|-----------------------|-------------------|----------------------|----------------------|
| Framework d’extensibilité | [rxPredict (R)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) <br/>[rx_predict (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Aucun. Les modèles peuvent être basées sur n’importe quelle fonction R ou Python | Centaines de millisecondes. <br/>Le chargement d’un environnement d’exécution présente un coût fixe, en moyenne trois à six cents millisecondes, avant toute nouvelle donnée est transformée en score. |
| [Extension CLR de notation en temps réel](../real-time-scoring.md) | [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) sur un modèle sérialisé | R : RevoScaleR, MicrosoftML <br/>Python : revoscalepy, microsoftml | Dizaines de millisecondes, en moyenne. |
| [Notation d’extension C++ native](../sql-native-scoring.md) | [Fonction T-SQL prédire](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) sur un modèle sérialisé | R : RevoScaleR <br/>Python : revoscalepy | Inférieur à 20 millisecondes, en moyenne. | 

Vitesse de traitement et non la substance de la sortie sont la fonctionnalité de différenciation. En supposant que les mêmes fonctions et les entrées, le résultat évalué ne doit pas varier selon l’approche que vous utilisez.

Le modèle doit être créé à l’aide d’une fonction prise en charge, puis sérialisé en un flux d’octets bruts enregistrés sur disque, ou stockés au format binaire dans une base de données. À l’aide d’une procédure stockée ou T-SQL, vous pouvez charger et utiliser un modèle binaire sans la surcharge d’une durée d’exécution de langage R ou Python, et accélérer jusqu'à la fin lors de la génération de scores de prédiction sur les nouvelles entrées.

La signification des extensions C++ et le CLR est proximité au moteur de base de données elle-même. La langue native du moteur de base de données est en C++, ce qui signifie que les extensions écrites en C++ à exécuter avec moins de dépendances. En revanche, les extensions CLR dépendent de .NET Core. 

Comme vous pouvez l’imaginer, prise en charge de la plateforme est affectée par ces environnements d’exécution. Extensions du moteur de base de données native exécuter n’importe quel endroit de que la base de données relationnelle est pris en charge : Windows, Linux, Azure. Extensions CLR à l’exigence de .NET Core est actuellement Windows uniquement.

## <a name="scoring-overview"></a>Vue d’ensemble de notation

_Calcul de score_ est un processus en deux étapes. Tout d’abord, vous spécifiez un modèle déjà formé pour charger à partir d’une table. En second lieu, passez de nouveau les données à la fonction, pour générer des valeurs de prédiction d’entrée (ou _scores_). L’entrée est souvent une requête T-SQL, renvoyant des lignes tabulaires ou uniques. Vous pouvez choisir de générer une valeur de colonne unique qui représente une probabilité ou vous pouvez générer plusieurs valeurs, comme un intervalle de confiance, erreur ou autres complément utile à la prédiction.

Une étape sauvegarder, le processus de préparation du modèle et générer des scores peut se résumer ainsi :

1. Créer un modèle à l’aide d’un algorithme pris en charge. Prise en charge varie selon la méthodologie de notation que vous choisissez.
2. Apprentissage du modèle.
3. Sérialisation du modèle à l’aide d’un format binaire spécial.
3. Enregistrer le modèle dans SQL Server. En général, cela signifie stocker le modèle sérialisé dans une table SQL Server.
4. Appelez la fonction ou procédure stockée, en spécifiant les entrées de modèle et les données en tant que paramètres.

Lorsque l’entrée inclut plusieurs lignes de données, il est généralement plus rapide pour insérer les valeurs de prédiction dans une table en tant que partie du processus de calcul de score. Génération d’une seule note est plus courant dans un scénario où obtenir les valeurs d’entrée à partir d’une demande de formulaire ou d’utilisateur et retourner le score à une application cliente. Pour améliorer les performances lors de la génération de scores successives, SQL Server peut mettre en cache le modèle afin qu’il peut être rechargé en mémoire.

## <a name="compare-methods"></a>Comparaison des méthodes

Pour préserver l’intégrité du processus de moteur de base de données de base, prise en charge de R et Python est activée dans une architecture double qui isole le traitement en langage de traitement de SGBDR. À compter de SQL Server 2016, Microsoft a ajouté une infrastructure d’extensibilité qui permet aux scripts R doit être exécuté à partir de T-SQL. Dans SQL Server 2017, l’intégration de Python a été ajoutée. 

L’infrastructure d’extensibilité prend en charge toute opération que vous pouvez effectuer dans R ou Python, allant de fonctions simples de formation complexe modèles d’apprentissage. Toutefois, l’architecture du processus de double requiert appeler un processus externe de R ou Python pour chaque appel, quel que soit la complexité de l’opération. Lorsque la charge de travail implique le chargement d’un modèle préentraîné à partir d’une table et la notation dont elle fait sur les données déjà présentes dans SQL Server, la surcharge de l’appel du processus externes ajoute une latence pouvant être inacceptable dans certaines circonstances. Par exemple, la détection des fraudes nécessite une notation rapide pour être pertinentes.

Pour augmenter les vitesses de notation pour les scénarios tels que la détection des fraudes, SQL Server ajouté des bibliothèques de calcul de score intégrées en tant qu’extensions C++ et CLR qui éliminent la surcharge des processus de démarrage de R et Python.

[**Calcul de score en temps réel** ](../real-time-scoring.md) a été la première solution pour calculer les scores hautes performances. Introduits dans les premières versions de SQL Server 2017 et les mises à jour ultérieures à SQL Server 2016, notation en temps réel s’appuie sur les bibliothèques CLR l’acronyme R et Python de traitement sur les fonctions de contrôlés par Microsoft dans RevoScaleR, MicrosoftML (R), revoscalepy, et microsoftml (Python). Bibliothèques CLR sont appelées à l’aide de la **sp_rxPredict** procédure stockée génère des scores à partir de n’importe quel type de modèle pris en charge, sans appeler le runtime R ou Python.

[**Notation native** ](../sql-native-scoring.md) est une fonctionnalité de SQL Server 2017, implémentée comme une bibliothèque C++ native, mais uniquement pour les modèles de RevoScaleR et revoscalepy. Il est l’approche plus rapide et plus sûre, mais prend en charge un plus petit jeu de fonctions par rapport à d’autres méthodologies.

## <a name="choose-a-scoring-method"></a>Choisissez une méthode de notation

Exigences de plates-formes imposent souvent notation méthodologie à utiliser.

| Plateforme et version du produit | Méthodologie |
|------------------------------|-------------|
| SQL Server 2017 sur Windows, SQL Server 2017 Linux et de la base de données SQL Azure | **Notation native** avec prédire de T-SQL |
| SQL Server 2017 (Windows uniquement), SQL Server 2016 R Services doté de SP1 ou version ultérieure | **Calcul de score en temps réel** avec sp\_rxPredict de procédure stockée |

Nous vous recommandons de notation native avec la fonction PREDICT. À l’aide de sp\_rxPredict nécessite que vous activez l’intégration de SQLCLR. Prendre en compte les implications de sécurité avant d’activer cette option.

## <a name="serialization-and-storage"></a>Sérialisation et stockage

Pour utiliser un modèle avec des options de calcul de score rapides, enregistrez le modèle à l’aide d’un format sérialisé spéciaux, il a été optimisé pour la taille et l’efficacité de la notation.

+ Appelez [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) pour écrire un modèle pris en charge pour le **brutes** format.
+ Appelez [rxUnserializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel)' pour reconstituer le modèle pour une utilisation dans un autre code R, ou pour afficher le modèle.

**À l’aide de SQL**

À partir de code SQL, vous pouvez former le modèle à l’aide [sp_execute_external_script](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)et insérer directement les modèles formés dans une table, dans une colonne de type **varbinary (max)**. Pour obtenir un exemple simple, consultez [créer un modèle preditive dans R](../tutorials/rtsql-create-a-predictive-model-r.md)

**À l’aide de R**

À partir du code R, appelez le [rxWriteObject](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxwriteobject) (fonction) à partir du package RevoScaleR pour écrire le modèle directement à la base de données. Le **rxWriteObject()** fonction peut récupérer des objets R à partir d’une source de données ODBC comme SQL Server, ou écrire des objets dans SQL Server. L’API est modélisée d’après un magasin clé-valeur simple.
  
Si vous utilisez cette fonction, veillez à sérialiser le modèle à l’aide [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) premier. Ensuite, définissez le *sérialiser* argument dans **rxWriteObject** sur FALSE, pour éviter de répéter l’étape de sérialisation.

Sérialisation d’un modèle dans un format binaire est utile, mais pas obligatoire si vous calculez le score des prédictions à l’aide de R et Python exécute environnement au moment de l’infrastructure d’extensibilité. Vous pouvez enregistrer un modèle au format brut dans un fichier et ensuite lire à partir du fichier dans SQL Server. Cette option peut être utile si vous déplacez ou copiez les modèles entre les environnements.

## <a name="scoring-in-related-products"></a>Notation dans les produits connexes

Si vous utilisez le [serveur autonome](r-server-standalone.md) ou un [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), vous disposez d’autres options en plus des procédures stockées et fonctions T-SQL pour générer des prédictions rapidement. Le serveur autonome et le Machine Learning Server prennent en charge le concept d’un *service web* pour le déploiement de code. Vous pouvez les regrouper R ou Python préformés de modèle comme un service web, appelé au moment de l’exécution pour évaluer les nouvelles entrées de données. Pour plus d’informations, consultez ces articles :

+ [Quels sont les services web dans Machine Learning Server ?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services)
+ [Nouveautés d’Opérationnalisation ?](https://docs.microsoft.com/machine-learning-server/what-is-operationalization)
+ [Déployer un modèle Python comme un service web avec le Kit de développement logiciel modèle azureml gestion](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service)
+ [Publier un bloc de code R ou d’un modèle en temps réel comme un nouveau service web](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)
+ [package mrsdeploy pour R](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)


## <a name="see-also"></a>Voir aussi

+ [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)  
+ [rxRealTimeScoring](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxrealtimescoring)
+ [sp-rxPredict](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql)
+ [PRÉDIRE T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)