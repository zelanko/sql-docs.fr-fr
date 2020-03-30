---
title: Créer plusieurs modèles avec rxExecBy
description: Utilisez la fonction rxExecBy de la bibliothèque RevoScaleR pour créer plusieurs petits modèles avec les données de machine stockées dans SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: dbba63ae69997c9c5dbdccf49ec590b3f4eba652
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "73727483"
---
# <a name="creating-multiple-models-using-rxexecby"></a>Création de plusieurs modèles à l’aide de rxExecBy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La fonction **rxExecBy** dans RevoScaleR prend en charge le traitement parallèle de plusieurs modèles associés. Au lieu d’effectuer l’apprentissage d’un unique modèle volumineux basé sur des données provenant de plusieurs entités similaires, un scientifique des données peut créer rapidement de nombreux modèles associés, chacun utilisant des données spécifiques d’une entité unique. 

Par exemple, imaginons que vous surveilliez les défaillances des appareils, en capturant les données issues de nombreux types d’équipement différents. À l’aide de rxExecBy, vous pouvez fournir en entrée un unique jeu de données volumineux, spécifier une colonne sur laquelle doit s’effectuer la stratification du jeu de données, comme le type d’appareil, puis créer plusieurs modèles pour des appareils individuels.

Ce cas d’usage est qualifié d’[« agréablement parallèle »](https://en.wikipedia.org/wiki/Embarrassingly_parallel), car il divise un problème complexe important en parties de composant pour un traitement simultané.

Les applications typiques de cette approche incluent les prévisions pour le compteur connecté d’un ménage, la prévision du chiffre d’affaires pour des gammes de produits distinctes ou la création de modèles pour l’approbation de prêts adaptés à chaque filiale d’une banque.

## <a name="how-rxexec-works"></a>Fonctionnement de rxExec

La fonction rxExecBy dans RevoScaleR est conçue pour un traitement parallèle de gros volumes sur un grand nombre de petits jeux de données.

1. Vous pouvez appeler la fonction rxExecBy dans le cadre de votre code R et vous transmettez alors un jeu de données non ordonnées.
2. Spécifiez la partition selon laquelle les données doivent être regroupées et triées.
3. Définissez la fonction de transformation ou de modélisation à appliquer à chaque partition de données
4. Lorsque la fonction s’exécute, les requêtes de données sont traitées en parallèle si votre environnement prend en charge ce type de traitement. En outre, les tâches de modélisation ou de transformation sont distribuées entre les cœurs individuels et exécutées en parallèle. Les contextes de calcul pris en charge pour ces opérations incluent RxSpark et RxInSQLServer.
5. Plusieurs résultats sont retournés.

## <a name="rxexecby-syntax-and-examples"></a>Syntaxe de rxExecBy et exemples

**rxExecBy** prend quatre entrées, l’une d’elles étant un jeu de données ou un objet source de données qui peut être partitionné sur une colonne **clé** spécifiée. La fonction retourne une sortie pour chaque partition. La forme de la sortie dépend de la fonction qui est transmise comme argument. Par exemple, si vous transmettez une fonction de modélisation telle que rxLinMod, vous pouvez retourner un modèle entraîné distinct pour chaque partition du jeu de données.

### <a name="supported-functions"></a>Fonctions prises en charge

Modélisation : `rxLinMod`, `rxLogit`, `rxGlm`, `rxDtree`

Scoring : `rxPredict`

Transformation ou analyse : `rxCovCor`

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer plusieurs modèles à l’aide du jeu de données Airline, partitionné dans la colonne [DayOfWeek]. La fonction définie par l’utilisateur `delayFunc`, est appliquée à chacune des partitions en appelant rxExecBy. La fonction crée des modèles distincts pour les lundis, les mardis, etc.

```sql
EXEC sp_execute_external_script
@language = N'R'
, @script = N'
delayFunc <- function(key, data, params) { 
    df <- rxImport(inData = airlineData) 
    rxLinMod(ArrDelay ~ CRSDepTime, data = df) 
} 
OutputDataSet <- rxExecBy(airlineData, c("DayOfWeek"), delayFunc)
'
, @input_data_1 = N'select ArrDelay, DayOfWeek, CRSDepTime from AirlineDemoSmall]'
, @input_data_1_name = N'airlineData'

```

Si vous recevez l’erreur `varsToPartition is invalid`, vérifiez si le nom de la ou des colonnes clés est entré correctement. Le langage R respecte la casse.

Cet exemple spécifique n’est pas optimisé pour SQL Server, et vous pouvez, dans de nombreux cas, obtenir de meilleures performances en utilisant SQL pour regrouper les données. Toutefois, à l’aide de rxExecBy, vous pouvez créer des travaux parallèles à partir de R.

L’exemple suivant illustre le processus dans R, en utilisant SQL Server comme contexte de calcul :

```R
sqlServerConnString <- "SERVER=hostname;DATABASE=TestDB;UID=DBUser;PWD=Password;"
inTable <- paste("airlinedemosmall")
sqlServerDataDS <- RxSqlServerData(table = inTable, connectionString = sqlServerConnString)

# user function
".Count" <- function(keys, data, params)
{
  myDF <- rxImport(inData = data)
  return (nrow(myDF))
}

# Set SQL Server compute context with level of parallelism = 2
sqlServerCC <- RxInSqlServer(connectionString = sqlServerConnString, numTasks = 4)
rxSetComputeContext(sqlServerCC)

# Execute rxExecBy in SQL Server compute context
sqlServerCCResults <- rxExecBy(inData = sqlServerDataDS, keys = c("DayOfWeek"), func = .Count)
```


