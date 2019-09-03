---
title: 'Tutoriel : Préparer les données pour effectuer le clustering dans python'
description: Dans la deuxième partie de cette série de didacticiels en quatre parties, vous allez préparer les données à partir d’une base de données SQL Server pour exécuter le clustering dans Python avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/30/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a71d92023c76b7eafb25efba0bb13b1d1da1f695
ms.sourcegitcommit: 3de1fb410de2515e5a00a5dbf6dd442d888713ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2019
ms.locfileid: "70211963"
---
# <a name="tutorial-prepare-data-to-perform-clustering-in-python-with-sql-server-machine-learning-services"></a>Tutoriel : Préparer les données pour effectuer le clustering dans Python avec SQL Server Machine Learning Services

Dans la deuxième partie de cette série de didacticiels en quatre parties, vous allez importer et préparer les données à partir d’une base de données SQL à l’aide de Python. Plus loin dans cette série, vous utiliserez ces données pour effectuer l’apprentissage et le déploiement d’un modèle de clustering dans Python avec SQL Server Machine Learning Services.

Dans cet article, vous allez apprendre à:

> [!div class="checklist"]
> * Séparer les clients en fonction de leurs dimensions à l’aide de Python
> * Charger les données de la base de données SQL dans une trame de données python

Dans la [première partie](tutorial-python-clustering-model.md), vous avez installé les composants requis et importé l’exemple de base de données.

Dans la [troisième partie](tutorial-python-clustering-model-build.md), vous apprendrez à créer et à former un modèle de clustering K-means dans Python.

Dans la [quatrième partie](tutorial-python-clustering-model-deploy.md), vous apprendrez à créer une procédure stockée dans une base de données SQL qui peut effectuer un clustering dans Python en fonction de nouvelles données.

## <a name="prerequisites"></a>Prérequis

* La deuxième partie de ce didacticiel suppose que vous avez rempli les conditions préalables de la [**première partie**](tutorial-python-clustering-model.md).

## <a name="separate-customers"></a>Clients distincts

Pour préparer le clustering des clients, vous devez d’abord séparer les clients selon les dimensions suivantes:

* **orderRatio** = ratio d’ordre de retour (nombre total de commandes partiellement ou entièrement retournées par rapport au nombre total de commandes)
* **itemsRatio** = ratio d’élément retourné (nombre total d’éléments retournés par rapport au nombre d’articles achetés)
* **monetaryRatio** = ratio des montants renvoyés (nombre total d’articles retournés par rapport au montant acheté)
* **Frequency** = fréquence de retour

Ouvrez un nouveau bloc-notes dans Azure Data Studio et entrez le script suivant.

Dans la chaîne de connexion, remplacez les détails de connexion en fonction des besoins.

```python
# Load packages.
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import revoscalepy as revoscale
from scipy.spatial import distance as sci_distance
from sklearn import cluster as sk_cluster

################################################################################################

## Connect to DB and select data

################################################################################################

# Connection string to connect to SQL Server named instance.
conn_str = 'Driver=SQL Server;Server=localhost;Database=tpcxbb_1gb;Trusted_Connection=True;'

input_query = '''SELECT
ss_customer_sk AS customer,
ROUND(COALESCE(returns_count / NULLIF(1.0*orders_count, 0), 0), 7) AS orderRatio,
ROUND(COALESCE(returns_items / NULLIF(1.0*orders_items, 0), 0), 7) AS itemsRatio,
ROUND(COALESCE(returns_money / NULLIF(1.0*orders_money, 0), 0), 7) AS monetaryRatio,
COALESCE(returns_count, 0) AS frequency
FROM
(
  SELECT
    ss_customer_sk,
    -- return order ratio
    COUNT(distinct(ss_ticket_number)) AS orders_count,
    -- return ss_item_sk ratio
    COUNT(ss_item_sk) AS orders_items,
    -- return monetary amount ratio
    SUM( ss_net_paid ) AS orders_money
  FROM store_sales s
  GROUP BY ss_customer_sk
) orders
LEFT OUTER JOIN
(
  SELECT
    sr_customer_sk,
    -- return order ratio
    count(distinct(sr_ticket_number)) as returns_count,
    -- return ss_item_sk ratio
    COUNT(sr_item_sk) as returns_items,
    -- return monetary amount ratio
    SUM( sr_return_amt ) AS returns_money
FROM store_returns
GROUP BY sr_customer_sk ) returned ON ss_customer_sk=sr_customer_sk'''


# Define the columns we wish to import.
column_info = {
    "customer": {"type": "integer"},
    "orderRatio": {"type": "integer"},
    "itemsRatio": {"type": "integer"},
    "frequency": {"type": "integer"}
}
```

## <a name="load-the-data-into-a-data-frame"></a>Charger les données dans une trame de données

Les résultats de la requête sont retournés à python à l’aide de la fonction revoscalepy **RxSqlServerData** . Dans le cadre du processus, vous utiliserez les informations de colonne que vous avez définies dans le script précédent.

```python
data_source = revoscale.RxSqlServerData(sql_query=input_query, column_Info=column_info,
                                        connection_string=conn_str)
revoscale.RxInSqlServer(connection_string=conn_str, num_tasks=1, auto_cleanup=False)
# import data source and convert to pandas dataframe.
customer_data = pd.DataFrame(revoscale.rx_import(data_source))
```

À présent, affichez le début de la trame de données pour vérifier qu’elle semble correcte.

```python
print("Data frame:", customer_data.head(n=5))
```

```results
Rows Read: 37336, Total Rows Processed: 37336, Total Chunk Time: 0.172 seconds
Data frame:     customer  orderRatio  itemsRatio  monetaryRatio  frequency
0    29727.0    0.000000    0.000000       0.000000          0
1    97643.0    0.068182    0.078176       0.037034          3
2    57247.0    0.000000    0.000000       0.000000          0
3    32549.0    0.086957    0.068657       0.031281          4
4     2040.0    0.000000    0.000000       0.000000          0
```

## <a name="clean-up-resources"></a>Supprimer des ressources

Si vous n’allez pas poursuivre ce didacticiel, supprimez la base de données tpcxbb_1gb de SQL Server.

## <a name="next-steps"></a>Étapes suivantes

Dans la deuxième partie de cette série de didacticiels, vous avez effectué les étapes suivantes:

* Séparer les clients en fonction de leurs dimensions à l’aide de Python
* Charger les données de la base de données SQL dans une trame de données python

Pour créer un modèle de Machine Learning qui utilise ces données client, suivez la troisième partie de cette série de didacticiels:

> [!div class="nextstepaction"]
> [Tutoriel : Créer un modèle prédictif dans Python avec SQL Server Machine Learning Services](tutorial-python-clustering-model-build.md)
