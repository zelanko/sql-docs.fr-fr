---
title: 'Didacticiel Python : Préparer les données (régression linéaire)'
description: Dans ce didacticiel, vous allez utiliser Python et la régression linéaire dans SQL Server Machine Learning Services pour prédire le nombre de locations de ski. Vous allez préparer des données à partir d’une base de données SQL Server à l’aide de Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c6c4d5fb4ffc5049f7e1325267b7623dc195e9d8
ms.sourcegitcommit: ecb19d0be87c38a283014dbc330adc2f1819a697
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70242497"
---
# <a name="python-tutorial-prepare-data-to-train-a-linear-regression-model-in-sql-server-machine-learning-services"></a>Didacticiel Python : Préparer les données pour l’apprentissage d’un modèle de régression linéaire dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans la deuxième partie de cette série de didacticiels en quatre parties, vous allez préparer des données à partir d’une base de données SQL Server à l’aide de Python. Plus loin dans cette série, vous utiliserez ces données pour effectuer l’apprentissage et le déploiement d’un modèle de régression linéaire dans Python avec SQL Server Machine Learning Services.

Dans cet article, vous allez apprendre à :

> [!div class="checklist"]
> * Charger les données de la base de données SQL Server dans une trame de données **pandas**
> * Préparer les données dans Python en supprimant des colonnes

Dans la [première partie](python-ski-rental-linear-regression.md), vous avez appris à restaurer l’exemple de base de données.

Dans la [troisième partie](python-ski-rental-linear-regression-train-model.md), vous apprendrez à effectuer l’apprentissage d’un modèle de régression linéaire machine learning dans Python.

Dans la [quatrième partie](python-ski-rental-linear-regression-deploy-model.md), vous apprendrez à stocker le modèle dans SQL Server, puis à créer des procédures stockées à partir des scripts Python que vous avez développés dans les deux parties et trois. Les procédures stockées sont exécutées dans SQL Server pour effectuer des prédictions en fonction de nouvelles données.

## <a name="prerequisites"></a>Prérequis

* La deuxième partie de ce didacticiel suppose que vous avez terminé la [première partie](python-ski-rental-linear-regression.md) et les conditions préalables.

## <a name="explore-and-prepare-the-data"></a>Explorer et préparer les données

Pour utiliser les données dans Python, vous allez charger les données de la base de données SQL Server dans une trame de données pandas.

Créez un nouveau bloc-notes python dans Azure Data Studio et exécutez le script suivant. Remplacez `<SQL Server>` par le nom de votre SQL Server.

Le script Python ci-dessous importe le DataSet à partir de la table **dbo. rental_data** de votre base de données vers une trame de données pandas **DF**.

```python
import pandas as pd
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error
from revoscalepy import RxComputeContext, RxInSqlServer, RxSqlServerData
from revoscalepy import rx_import

# Connection string to your SQL Server instance
conn_str = 'Driver=SQL Server;Server=<SQL Server>;Database=TutorialDB;Trusted_Connection=True;'

# Define the columns you will import
 column_info = {
         "Year" : { "type" : "integer" },
         "Month" : { "type" : "integer" },
         "Day" : { "type" : "integer" },
         "RentalCount" : { "type" : "integer" },
         "WeekDay" : {
             "type" : "factor",
             "levels" : ["1", "2", "3", "4", "5", "6", "7"]
         },
         "Holiday" : {
             "type" : "factor",
             "levels" : ["1", "0"]
         },
         "Snow" : {
             "type" : "factor",
             "levels" : ["1", "0"]
         }
     }

# Get the data from the SQL Server table
data_source = RxSqlServerData(table="dbo.rental_data",
                               connection_string=conn_str, column_info=column_info)
computeContext = RxInSqlServer(
     connection_string = conn_str,
     num_tasks = 1,
     auto_cleanup = False
)

RxInSqlServer(connection_string=conn_str, num_tasks=1, auto_cleanup=False)

# import data source and convert to pandas dataframe
df = pd.DataFrame(rx_import(input_data = data_source))
print("Data frame:", df)

# Get all the columns from the dataframe.
columns = df.columns.tolist()

# Filter the columns to remove ones we don't want to use in the training
columns = [c for c in columns if c not in ["Year"]]
```

Vous devez voir des résultats similaires à ce qui suit.

```results
Rows Processed: 453
Data frame:      Day  Holiday  Month  RentalCount  Snow  WeekDay  Year
0     20        1      1          445     2        2  2014
1     13        2      2           40     2        5  2014
2     10        2      3          456     2        1  2013
3     31        2      3           38     2        2  2014
4     24        2      4           23     2        5  2014
5     11        2      2           42     2        4  2015
6     28        2      4          310     2        1  2013
...
[453 rows x 7 columns]
```

## <a name="next-steps"></a>Étapes suivantes

Dans la deuxième partie de cette série de didacticiels, vous avez effectué les étapes suivantes :

* Charger les données de la base de données SQL Server dans une trame de données **pandas**
* Préparer les données dans Python en supprimant des colonnes

Pour effectuer l’apprentissage d’un modèle de Machine Learning qui utilise des données de la base de données TutorialDB, suivez la troisième partie de cette série de didacticiels :

> [!div class="nextstepaction"]
> [Didacticiel Python : Effectuer l’apprentissage d’un modèle de régression linéaire](python-ski-rental-linear-regression-train-model.md)