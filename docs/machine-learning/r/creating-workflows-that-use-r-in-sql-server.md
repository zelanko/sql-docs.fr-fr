---
title: Créer des workflows SSIS et SSRS avec R
description: Scénarios d’intégration combinant SQL Server Machine Learning Services et R Services, Reporting Services (SSRS) et SQL Server Integration Services (SSIS).
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/17/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2b8d55e95991437e4d76911fd26afb5b1bc9c550
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "81117742"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>Créer des workflows SSIS et SSRS avec R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment utiliser le script R et Python incorporé à l’aide du langage et des fonctionnalités de science des données de SQL Server Machine Learning Services avec deux fonctionnalités importantes de SQL Server : SQL Server Integration Services (SSIS) et SQL Server Reporting Services (SSRS). Les bibliothèques R et Python dans SQL Server fournissent des fonctions statistiques et prédictives. SSIS et SSRS fournissent respectivement une transformation ETL et des visualisations coordonnées. Cet article explique comment rassembler toutes ces fonctionnalités dans ce modèle de workflow :

> [!div class="checklist"]
> * Créer une procédure stockée contenant un exécutable R ou Python
> * Exécuter la procédure stockée à partir de SSIS ou SSRS

Les exemples de cet article concernent essentiellement R et SSIS, mais les concepts et les étapes s’appliquent également à Python. La deuxième section fournit des conseils et des liens pour les visualisations SSRS.

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-automation"></a>Utiliser SSIS pour l’automatisation

Les workflows de science des données sont hautement itératifs et impliquent beaucoup de transformations de données, notamment la mise à l'échelle, les agrégations, le calcul des probabilités, le renommage et la fusion des attributs. Les scientifiques des données sont habitués à effectuer une grande partie de ces tâches dans R, Python ou un autre langage, mais l’exécution de ces flux de travail sur des données d’entreprise nécessite une intégration transparente avec les outils et processus ETL.

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] vous permet d’effectuer des opérations complexes dans R avec Transact-SQL et les procédures stockées. Vous pouvez donc intégrer des tâches de science des données avec des processus ETL existants. Plutôt que d’effectuer une série de tâches utilisant beaucoup de mémoire, vous pouvez mieux préparer les données à l’aide de plusieurs outils très performants, tels que [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et [!INCLUDE[tsql](../../includes/tsql-md.md)]. 

Voici quelques propositions de méthodes d’automatisation de vos pipelines de traitement et de modélisation des données à l’aide de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] :

+ Extraire des données à partir de sources locales ou cloud pour créer des données d’apprentissage 
+ Générer et exécuter des modèles R ou Python dans le cadre d’un workflow d’intégration de données
+ Reformer les modèles sur une base régulière (planifiée)
+ Charger les résultats du script R ou Python dans d’autres destinations, notamment Excel, Power BI, Oracle et Teradata
+ Utiliser des tâches SSIS pour créer des fonctionnalités de données dans la base de données SQL
+ Utiliser le branchement conditionnel afin de changer de contexte de calcul pour les travaux R et Python

## <a name="ssis-example"></a>Exemple SSIS

L’exemple suivant provient d’un billet de blog MSDN désormais supprimé, créé par Jimmy Wong à l’adresse suivante : `https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`

Cet exemple vous montre comment automatiser des tâches à l’aide de SSIS. Vous créez des procédures stockées avec R incorporé à l’aide de SQL Server Management Studio, avant de les exécuter à l’aide de [tâches d’exécution T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) dans un package SSIS.

Pour suivre cet exemple, vous devez connaître Management Studio, SSIS, SSIS Designer, la conception de package et T-SQL. Le package SSIS utilise trois [tâches d’exécution T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) qui insèrent des données d’apprentissage dans une table, modélisent les données et notent les données pour obtenir une sortie de prédiction.

### <a name="load-training-data"></a>Charger des données d’apprentissage

Exécutez le script suivant dans SQL Server Management Studio pour créer une table qui servira à stocker les données. Pour cet exercice, vous devez créer et utiliser une base de données de test. 

```T-SQL
Use test-db
GO

Create table ssis_iris (
    id int not null identity primary key
    , "Sepal.Length" float not null, "Sepal.Width" float not null
    , "Petal.Length" float not null, "Petal.Width" float not null
    , "Species" varchar(100) null
);
GO
```

Créez une procédure stockée qui charge les données d’apprentissage dans une trame de données. Cet exemple utilise le jeu de données Iris intégré. 

```T-SQL
Create procedure load_iris
as
begin
    execute sp_execute_external_script
        @language = N'R'
        , @script = N'iris_df <- iris;'
        , @input_data_1 = N''
        , @output_data_1_name = N'iris_df'
    with result sets (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100)));
end;
```

Dans SSIS Designer, créez une [tâche d’exécution SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) qui exécute la procédure stockée que vous venez de définir. Le script pour **SQLStatement** supprime les données existantes, spécifie les données à insérer, puis appelle la procédure stockée pour fournir les données.

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

![Insérer des données](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "Insertion des données")

### <a name="generate-a-model"></a>Générer un modèle

Exécutez le script suivant dans SQL Server Management Studio pour créer une table qui stocke un modèle. 

```T-SQL
Use test-db
GO

Create table ssis_iris_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
GO
```

Créez une procédure stockée qui génère un modèle linéaire à l’aide de [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod). Les bibliothèques RevoScaleR et revoscalepy sont automatiquement disponibles dans les sessions R et Python sur SQL Server. Il n’est donc pas nécessaire d’importer la bibliothèque.

```T-SQL
Create procedure generate_iris_rx_model
as
begin
    execute sp_execute_external_script
        @language = N'R'
        , @script = N'
          irisLinMod <- rxLinMod(Sepal.Length ~ Sepal.Width + Petal.Length + Petal.Width + Species, data = ssis_iris);
          trained_model <- data.frame(payload = as.raw(serialize(irisLinMod, connection=NULL)));'
        , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from ssis_iris'
        , @input_data_1_name = N'ssis_iris'
        , @output_data_1_name = N'trained_model'
    with result sets ((model varbinary(max)));
end;
GO
```

Dans SSIS Designer, créez une [tâche d’exécution SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) pour exécuter la procédure stockée **generate_iris_rx_model**. Le modèle est sérialisé et enregistré dans la table ssis_iris_models. Le script pour **SQLStatement** se présente comme suit :

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

![Génère un modèle linéaire](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "Génère un modèle linéaire")

En tant que point de contrôle, une fois cette tâche terminée, vous pouvez interroger la table ssis_iris_models pour vérifier qu’elle contient un modèle binaire.

### <a name="predict-score-outcomes-using-the-trained-model"></a>Résultats de prédiction (score) à l’aide du modèle « formé »

Maintenant que vous disposez d’un code qui charge les données d’apprentissage et génère un modèle, il ne vous reste plus qu’à utiliser le modèle pour générer des prédictions. 

Pour ce faire, placez le script R dans la requête SQL pour déclencher la fonction R intégrée [rxPredict](https://docs.microsoft.com//machine-learning-server/r-reference/revoscaler/rxpredict) sur la table ssis_iris_model. Une procédure stockée appelée **predict_species_length** effectue cette tâche.

```T-SQL
Create procedure predict_species_length (@model varchar(100))
as
begin
    declare @rx_model varbinary(max) = (select model from ssis_iris_models where model_name = @model);
    -- Predict based on the specified model:
    exec sp_execute_external_script
        @language = N'R'
        , @script = N'
irismodel <-unserialize(rx_model);
irispred <- rxPredict(irismodel, ssis_iris[,2:6]);
OutputDataSet <- cbind(ssis_iris[1], irispred$Sepal.Length_Pred, ssis_iris[2]);
colnames(OutputDataSet) <- c("id", "Sepal.Length.Actual", "Sepal.Length.Expected");
#OutputDataSet <- subset(OutputDataSet, Species.Length.Actual != Species.Expected);
'
    , @input_data_1 = N'
    select id, "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from ssis_iris
    '
    , @input_data_1_name = N'ssis_iris'
    , @params = N'@rx_model varbinary(max)'
    , @rx_model = @rx_model
    with result sets ( ("id" int, "Species.Length.Actual" float, "Species.Length.Expected" float)
        );
end;
```

Dans SSIS Designer, créez une [tâche d’exécution SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) qui exécute la procédure stockée **predict_species_length** afin de générer une longueur de pétale prédite.

```T-SQL
exec predict_species_length 'rxLinMod';
```

![Générer des prédictions](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "Générer des prédictions")

### <a name="run-the-solution"></a>Exécuter la solution

Dans SSIS Designer, appuyez sur F5 pour exécuter le package. Vous devez obtenir un résultat similaire à la capture d’écran suivante.

![F5 pour l’exécution en mode débogage](../media/create-workflows-using-r-in-sql-server/ssis-exec-F5-run.png "F5 pour l’exécution en mode débogage")

<a name="bkmk_ssrs"></a> 

## <a name="use-ssrs-for-visualizations"></a>Utiliser SSRS pour les visualisations

Si R permet de créer des graphiques et offre des visualisations intéressantes, il n’est pas bien intégré avec des sources de données externes, ce qui signifie que chaque diagramme ou graphique doit être produit individuellement. Le partage peut également être difficile.

En utilisant [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], vous pouvez effectuer des opérations complexes dans R avec des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)], qui peuvent facilement être utilisées par divers outils de rapports d’entreprise, y compris [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et Power BI.

### <a name="ssrs-example"></a>Exemple SSRS

[Périphérique graphique de R pour Microsoft Reporting Services (SSRS)](https://rgraphicsdevice.codeplex.com/)

Ce projet CodePlex fournit du code pour vous aider à créer un élément de rapport personnalisé qui restitue la sortie graphique de R sous la forme d’une image utilisable dans les rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  Avec l’élément de rapport personnalisé, vous pouvez :

+ Publier des graphiques et tracés créés à l’aide du périphérique graphique de R dans les tableaux de bord [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]

+ Passer des paramètres [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aux tracés R

> [!NOTE]
> Pour cet exemple, le code à utiliser avec le périphérique graphique de R pour Reporting Services doit être installé sur le serveur Reporting Services, ainsi que dans Visual Studio. Vous devez également effectuer manuellement la configuration et la compilation.

## <a name="next-steps"></a>Étapes suivantes

Les exemples SSIS et SSRS inclus dans cet article illustrent deux cas d’exécution de procédures stockées qui contiennent un script R ou Python incorporé. Le principal avantage est que vous pouvez mettre le script R ou Python à disposition pour n’importe quelle application ou n’importe quel outil qui est en mesure d’envoyer une requête d’exécution sur une procédure stockée. Autre avantage pour SSIS : vous pouvez créer des packages qui automatisent et planifient de nombreuses opérations, telles que l’acquisition, le nettoyage ou la manipulation de données, tout en incluant la fonctionnalité de science des données R ou Python dans la chaîne d’opérations. Pour plus d’informations et d’idées, consultez [Faire fonctionner votre code R à l’aide des procédures stockées dans SQL Server Machine Learning Services](operationalizing-your-r-code.md).