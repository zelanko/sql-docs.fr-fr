---
title: Création de plusieurs modèles à l’aide de rxExecBy
description: Utilisez la fonction rxExecBy de la bibliothèque RevoScaleR pour créer plusieurs modèles minimaux sur les données machine stockées dans SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 1c51691ad55ac8aa340eb71257489bd14c0099a5
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345542"
---
# <a name="creating-multiple-models-using-rxexecby"></a>Création de plusieurs modèles à l’aide de rxExecBy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

La fonction **rxExecBy** dans RevoScaleR prend en charge le traitement parallèle de plusieurs modèles associés. Au lieu d’effectuer l’apprentissage d’un modèle volumineux basé sur des données provenant de plusieurs entités similaires, un scientifique des données peut créer rapidement de nombreux modèles associés, chacun utilisant des données spécifiques à une entité unique. 

Par exemple, supposez que vous surveillez les défaillances des appareils, en capturant les données pour de nombreux types d’équipement différents. À l’aide de rxExecBy, vous pouvez fournir un seul jeu de données volumineux comme entrée, spécifier une colonne sur laquelle stratification le jeu de données, tel que le type d’appareil, puis créer plusieurs modèles pour des appareils individuels.

Ce cas d’usage a été dit [«très convivial»](https://en.wikipedia.org/wiki/Embarrassingly_parallel) , car il répartit un problème complexe important en parties de composant pour un traitement simultané.

Les applications typiques de cette approche incluent les prévisions pour les compteurs intelligents de ménage, la création de projections de chiffre d’affaires pour des gammes de produits distinctes ou la création de modèles pour les approbations de prêts qui sont adaptées à des branches bancaires individuelles.

## <a name="how-rxexec-works"></a>Fonctionnement de rxExec

La fonction rxExecBy dans RevoScaleR est conçue pour un traitement parallèle à volume élevé sur un grand nombre de petits jeux de données.

1. Vous appelez la fonction rxExecBy dans le cadre de votre code R et vous transmettez un jeu de données de données non ordonnées.
2. Spécifiez la partition par laquelle les données doivent être regroupées et triées.
3. Définir une fonction de transformation ou de modélisation qui doit être appliquée à chaque partition de données
4. Lorsque la fonction s’exécute, les requêtes de données sont traitées en parallèle si votre environnement la prend en charge. En outre, les tâches de modélisation ou de transformation sont distribuées entre les cœurs individuels et exécutées en parallèle. Le contexte de calcul pris en charge pour les opérations de ce qui inclut RxSpark et RxInSQLServer.
5. Plusieurs résultats sont retournés.

## <a name="rxexecby-syntax-and-examples"></a>Syntaxe rxExecBy et exemples

**rxExecBy** prend quatre entrées, l’une des entrées étant un DataSet ou un objet de source de données qui peut être partitionné sur une colonne **clé** spécifiée. La fonction retourne une sortie pour chaque partition. La forme de la sortie dépend de la fonction qui est passée comme argument. Par exemple, si vous transmettez une fonction de modélisation telle que rxLinMod, vous pouvez retourner un modèle formé distinct pour chaque partition du jeu de données.

### <a name="supported-functions"></a>Fonctions prises en charge

Modélisation: `rxLinMod`, `rxLogit`, `rxGlm`,`rxDtree`

Notation: `rxPredict`,

Transformation ou analyse:`rxCovCor`

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer plusieurs modèles à l’aide du jeu de données d’une compagnie aérienne, partitionnée dans la colonne [DayOfWeek]. La fonction définie par l’utilisateur `delayFunc`,, est appliquée à chacune des partitions en appelant rxExecBy. La fonction crée des modèles distincts pour les lundis, les mardis, etc.

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

Si vous recevez l’erreur, `varsToPartition is invalid`Vérifiez si le nom de la ou des colonnes clés est tapé correctement. Le langage R respecte la casse.

Cet exemple spécifique n’est pas optimisé pour SQL Server, et vous pouvez, dans de nombreux cas, obtenir de meilleures performances en utilisant SQL pour regrouper les données. Toutefois, à l’aide de rxExecBy, vous pouvez créer des tâches parallèles à partir de R.

L’exemple suivant illustre le processus dans R, en utilisant SQL Server comme contexte de calcul:

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


