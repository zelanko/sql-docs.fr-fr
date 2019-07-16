---
title: Création de plusieurs modèles à l’aide de rxExecBy - SQL Server Machine Learning Services
description: Utilisez la fonction rxExecBy à partir de la bibliothèque RevoScaleR pour générer plusieurs modèles mini-vidages sur les données machine stockées dans SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: b0316cf40acff1a64aa40a14911f323eb913efc1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962686"
---
# <a name="creating-multiple-models-using-rxexecby"></a>Création de plusieurs modèles à l’aide de rxExecBy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Le **rxExecBy** fonction dans RevoScaleR prend en charge le traitement parallèle de plusieurs modèles associés. Au lieu de former un modèle de grande taille selon les données à partir de plusieurs entités similaire, un spécialiste des données peuvent créer rapidement de nombreux modèles connexes, chacune utilisant des données spécifiques à une entité unique. 

Par exemple, supposons que vous analysez des échecs de l’appareil, et capture de données pour de nombreux types différents de l’équipement. À l’aide de rxExecBy, vous pouvez fournir un unique jeu de données volumineux en tant qu’entrée, spécifier une colonne sur laquelle effectuer la stratification sur le jeu de données, tels que le type de périphérique et puis créer plusieurs modèles pour les appareils individuels.

Ce cas d’usage a été appelé [« pleasingly parallel »](https://en.wikipedia.org/wiki/Embarrassingly_parallel) , car il fractionne un grand problème complexe en composants pour un traitement simultané.

Les applications classiques de cette approche incluent des prévisions pour les capteurs intelligents de ménages individuels, la création des projections de chiffre d’affaires de gammes de produits distincts ou la création de modèles pour les approbations de prêt qui sont adaptées aux succursales individuels.

## <a name="how-rxexec-works"></a>Fonctionne de rxExec

La fonction rxExecBy dans RevoScaleR est conçue pour le traitement sur un grand nombre de petits jeux de données de parallèle de haut volume.

1. Vous appelez la fonction rxExecBy dans le cadre de votre code R et passez d’un jeu de données non ordonnées.
2. Spécifiez la partition par lequel les données doivent être groupées ou triées.
3. Définir une transformation ou une fonction qui doit être appliquée à chaque partition de données de modélisation
4. Lorsque la fonction s’exécute, les requêtes de données sont traitées en parallèle si votre environnement prend en charge. En outre, les tâches de modélisation ou de transformation sont distribuées entre les cœurs individuels et exécutées en parallèle. Contexte de calcul pris en charge pour les opérations incluent RxSpark et RxInSQLServer.
5. Plusieurs résultats sont retournés.

## <a name="rxexecby-syntax-and-examples"></a>rxExecBy syntaxe et des exemples

**rxExecBy** prend quatre entrées, une des entrées en cours d’un objet de source de données ou le jeu de données qui peut être partitionné sur une certaine **clé** colonne. La fonction retourne une sortie pour chaque partition. La forme de sortie dépend de la fonction qui est passée en tant qu’argument. Par exemple, si vous passez une fonction de modélisation tels que rxLinMod, vous pouvez retourner un modèle formé distinct pour chaque partition du jeu de données.

### <a name="supported-functions"></a>Fonctions prises en charge

Modélisation : `rxLinMod`, `rxLogit`, `rxGlm`, `rxDtree`

Calcul de score : `rxPredict`,

Transformation ou l’analyse : `rxCovCor`

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer plusieurs modèles qui utilisent le jeu de données de compagnies aériennes, lequel est partitionné sur la colonne [DayOfWeek]. La fonction définie par l’utilisateur, `delayFunc`, est appliqué à chacune des partitions en appelant rxExecBy. La fonction crée des modèles distincts pour le lundi, mardi, et ainsi de suite.

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

Si vous obtenez l’erreur, `varsToPartition is invalid`, vérifiez si le nom de l’ou les colonnes clés est correct. Le langage R respecte la casse.

Cet exemple particulier n’est pas optimisé pour SQL Server, et vous pouvez souvent obtenir de meilleures performances pour regrouper les données à l’aide de SQL. Toutefois, à l’aide de rxExecBy, vous pouvez créer des travaux parallèles de R.

L’exemple suivant illustre le processus dans R, à l’aide de SQL Server comme contexte de calcul :

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


