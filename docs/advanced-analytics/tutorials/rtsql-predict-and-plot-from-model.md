---
title: Guide de démarrage rapide pour prédire et tracer à partir du modèle à l’aide de R dans SQL Server Machine Learning | Microsoft Docs
description: Dans ce démarrage rapide, obtenir des informations sur la notation à l’aide d’un modèle prédéfini dans les données R et SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 60e152948945f4e86cc1114ae7b20c0e48b403bf
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086651"
---
# <a name="quickstart-predict-and-plot-from-model-using-r-in-sql-server"></a>Démarrage rapide : Prédire et tracer à partir du modèle à l’aide de R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans ce démarrage rapide, utilisez le modèle que vous avez créé dans le Guide de démarrage rapide précédent pour noter des prédictions sur les données actualisées. Pour effectuer _notation_ à l’aide de nouvelles données, obtenir un des modèles formés à partir de la table, puis appeler un nouveau jeu de données sur lequel baser vos prévisions. Notation terme est parfois utilisé dans la science des données pour désigner la génération des prédictions, de probabilités ou d’autres valeurs selon de nouvelles données sont chargées dans un modèle formé.

## <a name="prerequisites"></a>Prérequis

Ce démarrage rapide est une extension de [créer un modèle prédictif](rtsql-create-a-predictive-model-r.md).

## <a name="create-the-table-of-new-speeds"></a>Créer la table des nouvelles vitesses

Avez-vous remarqué que les données d’apprentissage d’origine ne vont pas au-delà de la vitesse de 25 km/h ? Cela s’explique par le fait que ces données découlent d’une expérience réalisée en 1920 !

Vous voulez savoir quelle aurait été la distance d’arrêt d’une voiture des années 20 qui aurait pu rouler à 60 km/h voire à 100 km/h ? Pour répondre à cette question, vous devez fournir certaines nouvelles valeurs de vitesse.

```sql
CREATE TABLE [dbo].[NewCarSpeed]([speed] [int] NOT NULL,
    [distance] [int]  NULL) ON [PRIMARY]
GO
INSERT [dbo].[NewCarSpeed] (speed)
VALUES (40),  (50),  (60), (70), (80), (90), (100)
```

## <a name="predict-stopping-distance"></a>Prédire la distance d’arrêt

Vous utilisez peut-être une table qui contient plusieurs modèles R, créés avec des paramètres ou algorithmes différents, ou formés à partir de plusieurs sous-ensembles de données.

![rsql_basictut_listofmodels](media/rsql-basictut-listofmodels.png)

Pour obtenir des prédictions basées sur un modèle spécifique, vous devez écrire un script SQL qui effectue les opérations suivantes :

1. Obtenir le modèle voulu
2. Obtenir les nouvelles données d’entrée
3. Appeler une fonction de prédiction R compatible avec ce modèle

Dans cet exemple, étant donné que votre modèle est basé sur le **rxLinMod** algorithme fourni dans le cadre de la **RevoScaleR** package, vous appelez le [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) (fonction), plutôt que la R générique `predict` (fonction).

```sql
DECLARE @speedmodel varbinary(max) = (SELECT model FROM [dbo].[stopping_distance_models] WHERE model_name = 'latest model');
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(speedmodel));
            new <- data.frame(NewCarData);
            predicted.distance <- rxPredict(current_model, new);
            str(predicted.distance);
            OutputDataSet <- cbind(new, ceiling(predicted.distance));
            '
    , @input_data_1 = N'SELECT speed FROM [dbo].[NewCarSpeed]'
    , @input_data_1_name = N'NewCarData'
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ Utilisez une instruction SELECT pour obtenir un seul modèle de la table à passer comme paramètre d’entrée.
+ Après avoir récupéré le modèle de la table, appelez la fonction `unserialize` sur ce modèle.

    > [!TIP] 
    > Consultez également la nouvelle [fonctions de sérialisation](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) fournie par RevoScaleR, qui prennent en charge [notation en temps réel](../real-time-scoring.md).
+  Appliquez la fonction `rxPredict` avec les arguments appropriés au modèle et fournissez les nouvelles données d’entrée.
+  Dans l’exemple, le `str` fonction est ajoutée au cours de la phase de test, de vérifier le schéma de données est retournés à partir de R. Vous pouvez supprimer l’instruction ultérieurement.
+ Les noms de colonne utilisés dans le script R ne sont pas nécessairement transmises à la sortie de la procédure stockée. Ici, nous avons utilisé la clause WITH RESULTS pour définir des nouveaux noms de colonnes.

**Résultats**

![rsql_basictut_scoringresults_smalldata](media/rsql-basictut-scoringresults-smalldata.PNG)

## <a name="perform-scoring-in-parallel"></a>Effectuer un calcul de score en parallèle

Les prédictions ont été retournées rapidement en raison de la petite taille du jeu de données de cet exemple. Mais cela aurait-il été aussi rapide avec un très grand nombre de prédictions ? Il existe de nombreuses façons d’accélérer les opérations exécutées dans SQL Server, plus par conséquent, si les opérations peuvent être traitées en parallèle. Pour calculer les scores en particulier, une méthode simple consiste à ajouter le *@parallel* paramètre dans sp_execute_external_script et définissez la valeur sur **1**.

Supposez que vous ayez obtenu une table de vitesses de voiture possibles beaucoup plus volumineuse, contenant des centaines de milliers de valeurs. La communauté propose de nombreux exemples de scripts T-SQL pour vous aider à générer des tables de nombres. Nous n’allons donc pas les reproduire ici. Imaginez simplement que vous avez une colonne contenant beaucoup d’entiers et que vous voulez utiliser ces nombres comme entrée pour `speed` dans le modèle.

Pour ce faire, il suffit exécuter la même requête de prédiction, mais remplacer le jeu de données plus volumineux et ajouter la `@parallel = 1` argument.

```sql
DECLARE @speedmodel varbinary(max) = (select model from [dbo].[stopping_distance_models] where model_name = 'default model');
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(speedmodel));
            new <- data.frame(NewCarData);
            predicted.distance <- rxPredict(current_model, new);
            OutputDataSet <- cbind(new, ceiling(predicted.distance));
            '
    , @input_data_1 = N' SELECT [speed] FROM [dbo].[HugeTableofCarSpeeds] '
    , @input_data_1_name = N'NewCarData'
    , @parallel = 1
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ L’exécution parallèle offre généralement des avantages uniquement lorsque vous travaillez avec des données très volumineuses. Le moteur de base de données SQL peut décider que l’exécution parallèle n’est pas nécessaire. De plus, la requête SQL qui récupère vos données doit être capable de générer un plan de requêtes en parallèle.

+ Si vous utilisez l’option d’exécution parallèle, vous **devez** spécifier le schéma de résultats de sortie au préalable, à l’aide de la clause WITH RESULT SETS. Cela permet à SQL Server d’agréger les résultats de plusieurs jeux de données parallèles, en leur évitant d’avoir des schémas inconnus.

+ Si vous êtes *formation* un modèle au lieu de *notation*, ce paramètre a souvent pas d’effet. Selon le type de modèle, le processus de création de modèle peut avoir besoin de lire toutes les lignes pour générer les résumés.

+ Pour obtenir les avantages du traitement parallèle quand vous former votre modèle, nous vous recommandons d’utiliser une de la **RevoScaleR** algorithmes. Ces algorithmes sont conçus pour distribuer le traitement automatiquement, même si vous ne spécifiez pas <code>@parallel =1</code> dans l’appel à `sp_execute_external_script`. Pour obtenir des conseils sur la façon d’obtenir les meilleures performances avec des algorithmes RevoScaleR, consultez [distribuées et les calculs parallèles avec ScaleR dans Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).

## <a name="create-an-r-plot-of-the-model"></a>Créer un tracé R du modèle

Beaucoup de clients, y compris SQL Server Management Studio, ne peuvent pas afficher directement les tracés créés avec [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Au lieu de cela, le processus général pour générer des tracés R consiste à créer le tracé dans le cadre de votre code R, puis écrivez l’image dans un fichier.

Vous pouvez également retourner l’objet de tracé binaire sérialisé à n’importe quelle application qui peut afficher des images.

L’exemple suivant montre comment créer un graphique simple à l’aide d’une fonction de traçage fournie par défaut avec R. L’image de sortie est retournée dans le fichier spécifié, mais également dans une variable SQL par la procédure stockée.

```sql
 EXECUTE sp_execute_external_script
 @language = N'R'
 , @script = N'
     imageDir <- ''C:\\temp\\plots'';
     image_filename = tempfile(pattern = "plot_", tmpdir = imageDir, fileext = ".jpg")
     print(image_filename);
     jpeg(filename=image_filename,  width=600, height = 800);
     print(plot(distance~speed, data=InputDataSet, xlab="Speed", ylab="Stopping distance", main = "1920 Car Safety"));
     abline(lm(distance~speed, data = InputDataSet));
     dev.off();
     OutputDataSet <- data.frame(data=readBin(file(image_filename, "rb"), what=raw(), n=1e6));
     '
  , @input_data_1 = N'SELECT speed, distance from [dbo].[CarSpeed]'
  WITH RESULT SETS ((plot varbinary(max)));
```

+ Le `tempfile` fonction retourne une chaîne qui peut être utilisée comme nom de fichier, mais le fichier n’a pas encore été généré.
+ Pour les arguments à `tempfile`, vous pouvez spécifier un préfixe et extension de fichier, ainsi que le répertoire. Pour vérifier le nom complet du fichier et le chemin d’accès, imprimer un message à l’aide `str()`.
+ La fonction `jpeg` crée un périphérique R avec les paramètres spécifiés.
+ Après avoir créé le tracé, vous pouvez ajouter davantage de fonctionnalités visual à celui-ci. Dans ce cas, une ligne de régression est ajoutée à l’aide de `abline`.
+ Quand vous avez terminé d’ajouter les fonctions de traçage, fermez le périphérique graphique à l’aide de la fonction `dev.off()`.
+ La fonction `readBin` prend un fichier à lire, une spécification de format et le nombre d’enregistrements. Le `rb`**' mot clé indique que le fichier est binaire au lieu de texte.

**Résultats**

![rsql_basictut_plotresult_small](media/rsql-basictut-plotresult-small.png)

Si vous souhaitez effectuer des tracés plus élaborés, à l’aide de certains packages graphiques avancés de R, nous vous recommandons de lire ces articles. Les deux articles nécessitent le package **ggplot2**.

+ [Loan Classification using SQL Server 2016 R Services](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/09/27/loan-classification-using-sql-server-2016-r-services/) : scénario complet basé sur des données d’assurance. Nécessite le **remodeler** package.
+ [Créer des graphiques et des tracés à l’aide de R](walkthrough-create-graphs-and-plots-using-r.md)

## <a name="next-steps"></a>Étapes suivantes

L’intégration de R avec SQL Server facilite le déploiement de solutions R à grande échelle, en exploitant les fonctionnalités les plus performantes de R et des bases de données relationnelles pour optimiser la gestion des données et accélérer le traitement analytique de R. 

Continuer à découvrir des solutions à l’aide de R avec SQL Server dans des scénarios de bout en bout créés par les équipes de développement Microsoft Data Science et R Services.

> [!div class="nextstepaction"]
> [Didacticiels de SQL Server R](sql-server-r-tutorials.md)
