---
title: 'Tutoriel Python : Préparer les données'
description: Dans ce tutoriel, vous allez utiliser Python et la régression linéaire dans SQL Server Machine Learning Services pour prédire le nombre de locations de ski. Vous allez préparer des données à partir d’une base de données SQL Server à l’aide de Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6424a453bff2f0f6d62caa8c9870ccc2ec10d578
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727058"
---
# <a name="python-tutorial-prepare-data-to-train-a-linear-regression-model-in-sql-server-machine-learning-services"></a>Tutoriel Python : Préparer des données pour effectuer l’apprentissage d’un modèle de régression linéaire dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans la deuxième partie de cette série de didacticiels en quatre parties, vous allez préparer des données à partir d’une base de données SQL Server à l’aide de Python. Plus loin dans cette série, vous utiliserez ces données pour effectuer l’apprentissage et le déploiement d’un modèle de régression linéaire dans Python avec SQL Server Machine Learning Services.

Dans cet article, vous allez apprendre à :

> [!div class="checklist"]
> * Charger les données issues de la base de données SQL Server dans une trame de données **pandas**
> * Préparer les données dans Python en supprimant des colonnes

Dans la [première partie](python-ski-rental-linear-regression.md), vous avez appris à restaurer l’exemple de base de données.

Dans la [troisième partie](python-ski-rental-linear-regression-train-model.md), vous apprendrez à effectuer l’apprentissage d’un modèle de Machine Learning de régression linéaire dans Python.

Dans la [quatrième partie](python-ski-rental-linear-regression-deploy-model.md), vous apprendrez à stocker le modèle dans SQL Server, puis à créer des procédures stockées à partir des scripts Python que vous avez développés dans les parties 2 et 3. Les procédures stockées sont exécutées dans SQL Server pour effectuer des prédictions en fonction de nouvelles données.

## <a name="prerequisites"></a>Conditions préalables requises

* La deuxième partie de ce tutoriel suppose que vous avez terminé la [première partie](python-ski-rental-linear-regression.md) et ses conditions préalables.

## <a name="explore-and-prepare-the-data"></a>Explorer et préparer les données

Pour utiliser les données dans Python, vous allez charger les données issues de la base de données SQL Server dans une trame de données pandas.

Créez un nouveau bloc-notes Python dans Azure Data Studio et exécutez le script suivant. Remplacez `<SQL Server>` par le nom de votre propre serveur SQL Server.

Le script Python ci-dessous importe le jeu de données à partir de la table **dbo. rental_data** de votre base de données vers une trame de données pandas **df**.

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

Vous devez obtenir des résultats similaires à ce qui suit :

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

Dans la deuxième partie de cette série de tutoriels, vous avez effectué les étapes suivantes :

* Charger les données issues de la base de données SQL Server dans une trame de données **pandas**
* Préparer les données dans Python en supprimant des colonnes

Pour effectuer l’apprentissage d’un modèle de Machine Learning qui utilise des données de la base de données TutorialDB, suivez la troisième partie de cette série de tutoriels :

> [!div class="nextstepaction"]
> [Tutoriel Python : Effectuer l’apprentissage d’un modèle de régression linéaire](python-ski-rental-linear-regression-train-model.md)