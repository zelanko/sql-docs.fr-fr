---
title: Comment effectuer la notation en temps réel ou la notation native dans SQL Server Machine Learning | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: dfea308f268d666ce070c21a7dd9afa513f95406
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2018
ms.locfileid: "40395319"
---
# <a name="how-to-perform-real-time-scoring-or-native-scoring-in-sql-server"></a>Comment effectuer la notation en temps réel ou la notation native dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique deux approches dans SQL Server pour prévoir les résultats en temps quasi réel à l’aide de modèles préentraînés écrites en R. Les scores en temps réel et notation native sont conçus pour vous permettent d’utiliser un modèle d’apprentissage sans devoir installer R. Étant donné un modèle préentraîné dans un format compatible - enregistré dans une base de données SQL Server - vous pouvez utiliser des techniques d’accès aux données standard pour générer rapidement des scores de prédiction sur les nouvelles entrées.

## <a name="choose-a-scoring-method"></a>Choisissez une méthode de notation

Les options suivantes sont prises en charge pour la prédiction par lot rapide :

+ **Notation native**: la fonction PREDICT de T-SQL dans SQL Server 2017 Windows, SQL Server 2017 Linux et Azure SQL Database.
+ **Calcul de score en temps réel**: à l’aide de la procédure stockée\_rxPredict de procédure stockée dans SQL Server 2016 ou SQL Server 2017 (Windows uniquement).

> [!NOTE]
> Utilisation de la fonction PREDICT est recommandée dans SQL Server 2017.
> Utilisation de sp\_rxPredict nécessite que vous activez l’intégration de SQLCLR. Prendre en compte les implications de sécurité avant d’activer cette option.

Le processus de préparation du modèle et générer des scores est similaire :

1. Créer un modèle à l’aide d’un algorithme pris en charge.
2. Sérialisation du modèle à l’aide d’un format binaire spécial.
3. Rendre disponible le modèle à SQL Server. En général, cela signifie stocker le modèle sérialisé dans une table SQL Server.
4. Appelez la procédure stockée ou fonction et passer le modèle et les données d’entrée.

### <a name="requirements"></a>Spécifications

+ La fonction PREDICT est disponible dans toutes les éditions de SQL Server 2017 et est activée par défaut. Vous n’avez pas besoin installer R ou activer des fonctionnalités supplémentaires.

+ Si vous utilisez sp\_rxPredict, quelques étapes supplémentaires sont nécessaires. Consultez [activer la notation en temps réel](#bkmk_enableRtScoring).

+ À ce stade, seuls les RevoScaleR et les MicrosoftML peuvent créer des modèles compatibles. Types de modèles supplémentaires peuvent être disponibles dans les futures. Pour la liste des algorithmes actuellement pris en charge, consultez [de score en temps réel](../real-time-scoring.md).

### <a name="serialization-and-storage"></a>Sérialisation et stockage

Pour utiliser un modèle avec des options de calcul de score rapides, enregistrez le modèle à l’aide d’un format sérialisé spéciaux, il a été optimisé pour la taille et l’efficacité de la notation.

+ Appelez `rxSerializeModel` pour écrire un modèle pris en charge pour le **brutes** format.
+ Appelez `rxUnserializeModel` pour reconstituer le modèle pour une utilisation dans un autre code R, ou pour afficher le modèle.

Pour plus d’informations, consultez [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel).

**À l’aide de SQL**

À partir de code SQL, vous pouvez former le modèle à l’aide `sp_execute_external_script`et insérer directement les modèles formés dans une table, dans une colonne de type **varbinary (max)**.

Pour obtenir un exemple simple, consultez [ce didacticiel](../tutorials/rtsql-create-a-predictive-model-r.md)

**À l’aide de R**

À partir du code R, il existe deux façons d’enregistrer le modèle à une table :

+ Appelez le `rxWriteObject` fonction, à partir du package RevoScaleR, pour écrire le modèle directement à la base de données.

  Le `rxWriteObject()` fonction peut récupérer des objets R à partir d’une source de données ODBC comme SQL Server, ou écrire des objets dans SQL Server. L’API est modélisée d’après un magasin clé-valeur simple.
  
  Si vous utilisez cette fonction, veillez à sérialiser le modèle à l’aide de la nouvelle fonction de sérialisation tout d’abord. Ensuite, définissez le *sérialiser* argument dans `rxWriteObject` sur FALSE, pour éviter de répéter l’étape de sérialisation.

+ Vous pouvez également enregistrer le modèle dans son format brut dans un fichier et ensuite lire à partir du fichier dans SQL Server. Cette option peut être utile si vous déplacez ou copiez les modèles entre les environnements.

## <a name="native-scoring-with-predict"></a>Notation avec PREDICT native

Dans cet exemple, vous créez un modèle et puis appelez la fonction de prédiction en temps réel à partir de T-SQL.

### <a name="step-1-prepare-and-save-the-model"></a>Étape 1. Préparer et enregistrer le modèle

Exécutez le code suivant pour créer la base de données exemple et les tables requises.

```SQL
CREATE DATABASE NativeScoringTest;
GO
USE NativeScoringTest;
GO
DROP TABLE IF EXISTS iris_rx_data;
GO
CREATE TABLE iris_rx_data (
  "Sepal.Length" float not null, "Sepal.Width" float not null
  , "Petal.Length" float not null, "Petal.Width" float not null
  , "Species" varchar(100) null
);
GO
```

Utilisez l’instruction suivante pour remplir la table de données avec des données à partir de la **iris** jeu de données.

```SQL
INSERT INTO iris_rx_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width" , "Species")
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

Maintenant, créez une table pour stocker les modèles.

```SQL
DROP TABLE IF EXISTS ml_models;
GO
CREATE TABLE ml_models ( model_name nvarchar(100) not null primary key
  , model_version nvarchar(100) not null
  , native_model_object varbinary(max) not null);
GO
```

Le code suivant crée un modèle basé sur le **iris** jeu de données et l’enregistre dans la table nommée **modèles**.

```SQL
DECLARE @model varbinary(max);
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'
    iris.sub <- c(sample(1:50, 25), sample(51:100, 25), sample(101:150, 25))
    iris.dtree <- rxDTree(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = iris[iris.sub, ])
    model <- rxSerializeModel(iris.dtree, realtimeScoringOnly = TRUE)
    '
  , @params = N'@model varbinary(max) OUTPUT'
  , @model = @model OUTPUT
  INSERT [dbo].[ml_models]([model_name], [model_version], [native_model_object])
  VALUES('iris.dtree','v1', @model) ;
```

> [!NOTE] 
> Veillez à utiliser le [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) fonction à partir de RevoScaleR pour enregistrer le modèle. Le standard de R `serialize` fonction ne peut pas générer le format requis.

Vous pouvez exécuter une instruction telle que la suivante pour afficher le modèle stocké au format binaire :

```SQL
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Étape 2. Exécutez PREDICT sur le modèle

L’instruction PREDICT simple suivante obtient une classification du modèle d’arborescence de décision à l’aide du **notation native** (fonction). Il prévoit l’espèce iris en fonction des attributs fournis, la longueur des pétales et la largeur.

```SQL
DECLARE @model varbinary(max) = (
  SELECT native_model_object
  FROM ml_models
  WHERE model_name = 'iris.dtree'
  AND model_version = 'v1');
SELECT d.*, p.*
  FROM PREDICT(MODEL = @model, DATA = dbo.iris_rx_data as d)
  WITH(setosa_Pred float, versicolor_Pred float, virginica_Pred float) as p;
go
```

Si vous obtenez l’erreur, « erreur s’est produite pendant l’exécution de la fonction PREDICT. Modèle est endommagé ou non valide », cela signifie généralement que votre requête n’a pas retourné d’un modèle. Vérifiez si vous avez correctement tapé le nom du modèle, ou si la table de modèles est vide.

> [!NOTE]
> Étant donné que les colonnes et les valeurs retournées par **PREDICT** peut varier selon le type de modèle, vous devez définir le schéma des données retournées à l’aide un **WITH** clause.

## <a name="real-time-scoring-with-sprxpredict"></a>Notation avec sp_rxPredict en temps réel

Cette section décrit les étapes requises pour configurer **en temps réel** prédiction et fournit un exemple montrant comment appeler la fonction à partir de T-SQL.

### <a name ="bkmk_enableRtScoring"></a> Étape 1. Activer la procédure de calcul de score en temps réel

Vous devez activer cette fonctionnalité pour chaque base de données que vous souhaitez utiliser pour calculer les scores. L’administrateur du serveur doit exécuter l’utilitaire de ligne de commande, RegisterRExt.exe, qui est inclus dans le package RevoScaleR.

> [!NOTE]
> Pour calculer les scores en temps réel pour fonctionner, les fonctionnalités SQL CLR doit être activés dans l’instance ; en outre, la base de données doit être marquée comme digne de confiance. Lorsque vous exécutez le script, ces actions sont effectuées pour vous. Toutefois, prendre en compte les implications de sécurité supplémentaires avant de faire cela !

1. Ouvrez une invite de commandes avec élévation de privilèges et accédez au dossier où se trouve RegisterRExt.exe. Le chemin d’accès suivant peut être utilisé dans une installation par défaut :
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Exécutez la commande suivante, en remplaçant le nom de votre instance et de la base de données cible dans lequel vous souhaitez activer les procédures stockées étendues :

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Par exemple, pour ajouter la procédure stockée étendue à la base de données CLRPredict sur l’instance par défaut, tapez :

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Le nom d’instance est facultatif si la base de données se trouve sur l’instance par défaut. Si vous utilisez une instance nommée, vous devez spécifier le nom d’instance.

3. RegisterRExt.exe crée les objets suivants :

    + Assemblys de confiance
    + La procédure stockée `sp_rxPredict`
    + Un nouveau rôle de base de données, `rxpredict_users`. L’administrateur de base de données peut utiliser ce rôle pour accorder l’autorisation aux utilisateurs qui utilisent la fonctionnalité de calcul de score en temps réel.

4. Ajouter des utilisateurs qui doivent exécuter `sp_rxPredict` au nouveau rôle.

> [!NOTE]
> 
> Dans SQL Server 2017, les mesures de sécurité supplémentaires sont en place pour éviter les problèmes avec l’intégration du CLR. Ces mesures imposent des restrictions supplémentaires sur l’utilisation de cette procédure stockée également. 

### <a name="step-2-prepare-and-save-the-model"></a>Étape 2. Préparer et enregistrer le modèle

Le format binaire requis par sp\_rxPredict est le même que le format requis pour utiliser la fonction PREDICT. Par conséquent, dans votre code R, incluez un appel à [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)et veillez à spécifier `realtimeScoringOnly = TRUE`, comme dans cet exemple :

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>Étape 3. Appel sp_rxPredict

Vous appelez sp\_rxPredict en tant que vous le feriez pour n’importe quel autre procédure stockée. Dans la version actuelle, la procédure stockée accepte uniquement deux paramètres :  _\@modèle_ pour le modèle au format binaire, et  _\@inputData_ pour les données à utiliser dans le calcul de score, défini en tant que une requête SQL valide.

Étant donné que le format binaire est le même que celui utilisé par la fonction PREDICT, vous pouvez utiliser la table de données et des modèles à partir de l’exemple précédent.

```SQL
DECLARE @irismodel varbinary(max)
SELECT @irismodel = [native_model_object] from [ml_models]
WHERE model_name = 'iris.dtree' 
AND model_version = 'v1''

EXEC sp_rxPredict
@model = @irismodel,
@inputData = N'SELECT * FROM iris_rx_data'
```

> [!NOTE]
> 
> L’appel à sp\_rxPredict échoue si les données d’entrée pour calculer les scores n’incluant pas les colonnes qui correspondent à la configuration requise du modèle. Actuellement, seuls les types de données de .NET suivants sont pris en charge : double, float, short, ushort, long, ulong et chaîne.
> 
> Par conséquent, vous devrez peut-être filtrer les types non pris en charge dans vos données d’entrée avant de l’utiliser pour calculer les scores en temps réel.
> 
> Pour plus d’informations sur les types SQL correspondants, consultez [le mappage de Type SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) ou [mappage des données de paramètre CLR](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

## <a name="disable-real-time-scoring"></a>Désactiver le calcul de score en temps réel

Pour désactiver les fonctionnalités de calcul de score en temps réel, ouvrez une invite de commandes avec élévation de privilèges et exécutez la commande suivante : `RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="real-time-scoring-in-other-microsoft-product"></a>Notation dans les autres produits Microsoft en temps réel

Si vous utilisez un serveur autonome ou un composant Microsoft Machine Learning Server au lieu d’analytique en base de données de SQL Server, vous disposez d’autres options en plus des procédures stockées et fonctions T-SQL pour générer des prédictions.

Le serveur autonome et le Machine Learning Server prennent en charge le concept d’un *service web* pour le déploiement de code. Vous pouvez les regrouper R ou Python préformés de modèle comme un service web, appelé au moment de l’exécution pour évaluer les nouvelles entrées de données. Pour plus d’informations, consultez ces articles :

+ [Quels sont les services web dans Machine Learning Server ?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services)
+ [Nouveautés d’Opérationnalisation ?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-operationalize-deploy-consume)
+ [Déployer un modèle Python comme un service web avec le Kit de développement logiciel modèle azureml gestion](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service)
+ [Publier un bloc de code R ou d’un modèle en temps réel comme un nouveau service web](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)
+ [package mrsdeploy pour R](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)
