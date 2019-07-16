---
title: Créer des flux de travail SSIS et de SSRS avec R - Services de SQL Server Machine Learning
description: Scénarios d’intégration combinant SQL Server Machine Learning Services et R Services, Reporting Services (SSRS) et SQL Server Integration Services (SSIS).
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/17/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: a9f3a76ac1829f529e0f3e5459ab842dcafa7c80
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962696"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>Créer des flux de travail SSIS et de SSRS avec R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment utiliser le script incorporé de R et Python avec les fonctionnalités de science des données et de langue de SQL Server Machine Learning Services deux fonctionnalités importantes de SQL Server : SQL Server Integration Services (SSIS) et SQL Server Reporting Services SSRS. Les bibliothèques R et Python dans SQL Server fournissent des fonctions statistiques et prédictives. SSIS et SSRS fournissent coordonnée de transformation d’ETL et de visualisations, respectivement. Cet article explique comment rassembler toutes ces fonctionnalités dans ce modèle de flux de travail :

> [!div class="checklist"]
> * Créer une procédure stockée qui contient l’exécutable R ou Python
> * Exécutez la procédure stockée à partir de SSIS ou SSRS

Les exemples dans cet article concernent principalement R et SSIS, mais les concepts et les étapes s’appliquent également à Python. La deuxième section fournit des liens pour les visualisations de SSRS.

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-automation"></a>Utiliser SSIS pour l’automatisation

Les workflows de science des données sont hautement itératifs et impliquent beaucoup de transformations de données, notamment la mise à l'échelle, les agrégations, le calcul des probabilités, le renommage et la fusion des attributs. Les scientifiques des données sont habitués à effectuer une grande partie de ces tâches dans R, Python ou un autre langage, mais l’exécution de ces flux de travail sur des données d’entreprise nécessite une intégration transparente avec les outils et processus ETL.

Étant donné que [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] vous permet d’exécuter des opérations complexes dans R par le biais de Transact-SQL et des procédures stockées, vous pouvez intégrer des tâches de science des données avec des processus ETL existants. Plutôt que d’effectuer une chaîne de tâches gourmandes en mémoire, les préparation des données peut être optimisée à l’aide des outils les plus efficaces, y compris [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et [!INCLUDE[tsql](../../includes/tsql-md.md)]. 

Voici quelques idées pour comment vous pouvez automatiser le traitement de vos données et modélisation des pipelines en [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ Extraire les données en local ou dans le cloud des sources pour générer des données d’apprentissage 
+ Générer et exécuter des modèles R ou Python dans le cadre d’un workflow d’intégration de données
+ Reformer des modèles régulièrement (planifiée)
+ Charger les résultats à partir du script R ou Python à d’autres destinations telles que Excel, Power BI, Oracle et Teradata, etc.
+ Tâches SSIS permet de créer des fonctionnalités de données dans la base de données SQL
+ Utiliser le branchement conditionnel pour basculer le contexte de calcul pour les travaux R et Python

## <a name="ssis-example"></a>Exemple SSIS

L’exemple suivant provient d’un billet de blog MSDN mis hors-service maintenant créé par Jimmy Wong à cette URL : `https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`

Cet exemple montre comment automatiser des tâches à l’aide de SSIS. Vous créez des procédures stockées avec R incorporé à l’aide de SQL Server Management Studio et puis exécuter ces procédures stockées à partir de [tâches d’exécution T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) dans un package SSIS.

Pour parcourir cet exemple, vous devez connaître avec Management Studio, SSIS, concepteur SSIS, conception du package et T-SQL. Le package SSIS utilise trois [tâches d’exécution T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) qui insérer des données d’apprentissage dans une table les données de modèle et noter les données pour obtenir la sortie de la prédiction.

### <a name="load-training-data"></a>Charger des données d’apprentissage

Exécutez le script suivant dans SQL Server Management Studio pour créer une table pour stocker les données. Vous devez créer et utiliser une base de données de test pour cet exercice. 

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

Créer une procédure stockée qui charge des données d’apprentissage dans la trame de données. Cet exemple utilise le jeu de données Iris intégré. 

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

Dans le concepteur SSIS, créez un [tâche d’exécution SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) qui exécute la procédure stockée que vous venez de définir. Le script pour **SQLStatement** supprime les données existantes, spécifie les données à insérer, puis appelle la procédure stockée pour fournir les données.

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

![Insérer des données](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "insérer des données")

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

Créer une procédure stockée qui génère un modèle linéaire à l’aide [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod). Bibliothèques RevoScaleR et revoscalepy sont automatiquement disponibles dans les sessions R et Python sur SQL Server, il est donc pas nécessaire pour importer la bibliothèque.

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

Dans le concepteur SSIS, créez un [tâche d’exécution SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) pour exécuter le **generate_iris_rx_model** procédure stockée. Le modèle est sérialisé et enregistré dans la table ssis_iris_models. Le script pour **SQLStatement** se présente comme suit :

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

![Génère un modèle linéaire](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "génère un modèle linéaire")

Comme un point de contrôle, une fois cette tâche terminée, vous pouvez interroger le ssis_iris_models pour voir qu’il contient un modèle binaire.

### <a name="predict-score-outcomes-using-the-trained-model"></a>Prédire les résultats (score) à l’aide du modèle « formé »

Maintenant que vous avez le code qui charge les données d’apprentissage et génère un modèle, la seule étape gauche est à l’aide du modèle pour générer des prédictions. 

Pour ce faire, placez le script R dans la requête SQL pour déclencher le [rxPredict](https://docs.microsoft.com//machine-learning-server/r-reference/revoscaler/rxpredict) fonction R intégrée sur ssis_iris_model. Une procédure stockée appelée **predict_species_length** effectue cette tâche.

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

Dans le concepteur SSIS, créez un [tâche d’exécution SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) qui exécute le **predict_species_length** procédure stockée pour générer la longueur des pétales prédite.

```T-SQL
exec predict_species_length 'rxLinMod';
```

![Générer des prédictions](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "générer des prédictions")

### <a name="run-the-solution"></a>Exécuter la solution

Dans le concepteur SSIS, appuyez sur F5 pour exécuter le package. Vous devez voir un résultat semblable à la capture d’écran suivante.

![F5 pour exécuter en mode débogage](../media/create-workflows-using-r-in-sql-server/ssis-exec-F5-run.png "F5 pour exécuter en mode débogage")

<a name="bkmk_ssrs"></a> 

## <a name="use-ssrs-for-visualizations"></a>Utiliser SSRS pour les visualisations

R peut créer des graphiques et des visualisations intéressantes, mais il n’est pas très bien intégré avec des sources de données externes, ce qui signifie que chaque diagramme ou graphique doit être produit individuellement. Le partage peut également être difficile.

À l’aide de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], vous pouvez exécuter des opérations complexes dans R avec [!INCLUDE[tsql](../../includes/tsql-md.md)] des procédures stockées, qui peuvent facilement être utilisées par divers outils, y compris de rapports d’entreprise [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et Power BI.

### <a name="ssrs-example"></a>Exemple SSRS

[Périphérique graphique de R de Microsoft Reporting Services (SSRS)](https://rgraphicsdevice.codeplex.com/)

Ce projet CodePlex fournit le code pour vous aider à créer un élément de rapport personnalisé qui restitue la sortie graphique de R en tant qu’image qui peut être utilisée dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] rapports.  Avec l’élément de rapport personnalisé, vous pouvez :

+ Publier des graphiques et tracés créés à l’aide du périphérique graphique de R dans les tableaux de bord [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]

+ Passer des paramètres [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aux tracés R

> [!NOTE]
> Pour cet exemple, le code qui prend en charge le périphérique graphique R pour Reporting Services doit être installé sur le serveur Reporting Services, ainsi que dans Visual Studio. Vous devez également effectuer manuellement la configuration et la compilation.

## <a name="next-steps"></a>Étapes suivantes

Les exemples SSIS et de SSRS dans cet article illustrent les deux cas de l’exécution de procédures stockées contenant le script R ou Python incorporé. Un élément clé à retenir est que vous pouvez proposer script R ou Python à toute application ou un outil qui peut envoyer une demande d’exécution sur une procédure stockée. Un élément à retenir supplémentaire pour SSIS est que vous pouvez créer des packages qui automatisent et planifier un large éventail d’opérations, telles que l’acquisition de données, de nettoyage, de manipulation et ainsi de suite, avec R ou Python fonctionnalité de science de données incluse dans la chaîne des opérations. Pour plus d’informations et des idées, consultez [code R de faire fonctionner à l’aide de procédures stockées dans SQL Server Machine Learning Services](operationalizing-your-r-code.md).