---
title: "Utiliser Python avec revoscalepy pour créer un modèle | Documents Microsoft"
ms.custom: SQL2016_New_Updated
ms.date: 09/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "4"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: bb5d4aac51728ac090fb4cbeae8da6c87db22aea
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="use-python-with-revoscalepy-to-create-a-model"></a>Utiliser Python avec revoscalepy pour créer un modèle

Cet exemple montre comment vous pouvez créer un modèle de régression linéaire dans SQL Server, à l’aide d’un algorithme à partir de la **revoscalepy** package.

Le **revoscalepy** le package pour Python contient des objets, des transformations, et algorithmes similaires à ceux fournis pour la **RevoScaleR** package pour le langage R. Avec cette bibliothèque, vous pouvez créer un contexte de calcul, déplacer des données entre les contextes de calcul, transforment des données et l’apprentissage des modèles prédictifs à l’aide d’algorithmes populaires tels que la régression logistique et linéaire, les arbres de décision et bien plus encore.

Pour plus d’informations, consultez [What ' s revoscalepy ?](../python/what-is-revoscalepy.md) et [référence de fonction Python](https://docs.microsoft.com/r-server/python-reference/introducing-python-package-reference)

## <a name="prerequisites"></a>Conditions préalables

> [!IMPORTANT]
> Pour exécuter le code Python dans SQL Server, vous devez avoir installé SQL Server 2017 CTP 2.0 ou version ultérieur, et vous devez installer et activer la fonctionnalité, **Machine Learning Services** avec Python. Autres versions de SQL Server ne prennent pas en charge intégration de Python.

## <a name="run-the-sample-code"></a>Exécutez l’exemple de code

Ce code exécute les étapes suivantes :

1. Importe les bibliothèques requises et les fonctions
2. Crée une connexion à SQL Server et crée des objets de source de données pour travailler avec les données
3. Modifie les données afin qu’il peut être utilisé par l’algorithme de régression logistique
4. Appels `rx_lin_mod` et définit la formule utilisée pour ajuster le modèle
5. Génère un ensemble de prédictions basées sur le jeu de données d’origine
6. Crée un résumé basé sur les valeurs prédites

Toutes les opérations sont effectuées à l’aide d’une instance de SQL Server en tant que le contexte de calcul.

En règle générale, le processus d’appel Python dans un contexte de calcul à distance est similaire à la façon dont vous utilisez R dans un contexte de calcul à distance. Vous exécutez l’exemple sous forme de script Python à partir de la ligne de commande, ou à l’aide d’un environnement de développement Python qui inclut les composants d’intégration Python fournis dans cette version. Dans votre code, vous créez et utilisez un objet de contexte de calcul pour indiquer où vous voulez à effectuer des calculs spécifiques.

> [!NOTE]
> Veillez à modifier les noms de base de données et l’environnement comme il convient.
> 
> Pour une démonstration de cet exemple en cours d’exécution à partir de la ligne de commande, consultez cette vidéo : [Analytique SQL Server 2017 avancé Python](https://www.youtube.com/watch?v=FcoY795jTcc)


### <a name="sample-code"></a>Exemple de code

```python
from revoscalepy import RxComputeContext, RxInSqlServer, RxSqlServerData
from revoscalepy import rx_lin_mod, rx_predict, rx_summary
from revoscalepy import RxOptions, rx_import

from pandas import Categorical
import os

def test_linmod_sql():
    sql_server = os.getenv('PYTEST_SQL_SERVER', '.')
    
    sql_connection_string = 'Driver=SQL Server;Server=' + sqlServer + ';Database=PyTestDb;Trusted_Connection=True;'
    print("connectionString={0!s}".format(sql_connection_string))

    data_source = RxSqlServerData(
        sql_query = "select top 10 * from airlinedemosmall",
        connection_string = sql_connection_string,

        column_info = {
            "ArrDelay" : { "type" : "integer" },
            "DayOfWeek" : {
                "type" : "factor",
                "levels" : [ "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday" ]
            }
        })

    sql_compute_context = RxInSqlServer(
        connection_string = sql_connection_string,
        num_tasks = 4,
        auto_cleanup = False
        )

    #
    # Run linmod locally
    #
    linmod_local = rx_lin_mod("ArrDelay ~ DayOfWeek", data = data_source)
    #
    # Run linmod remotely
    #
    linmod = rx_lin_mod("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)

    # Predict results
    # 
    predict = rx_predict(linmod, data = rx_import(input_data = data_source))
    summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)
```

## <a name="discussion"></a>Discussion

Nous allons examiner le code et mettre en évidence certaines étapes clés.

### <a name="defining-a-data-source-and-compute-context"></a>Définition de données source et contexte de calcul

Une source de données est différente à partir d’un contexte de calcul. Le _source de données_ définit les données utilisées dans votre code. Le _contexte de calcul_ définit où le code sera exécuté.

1. Créez des variables de Python, tel que `sql_query` et `sql_connection_string`, qui définissent la source et les données que vous souhaitez utiliser. Passer ces variables à la [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) constructeur pour implémenter le **objet source de données** nommé `data_source`.
2. Créer un objet de contexte de calcul à l’aide de la [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserverdata) constructeur. Dans cet exemple, vous passez la chaîne de connexion que vous avez défini précédemment, en supposant que les données sont sur la même instance de SQL Server que vous utiliserez comme contexte de calcul. Toutefois, la source de données et le contexte de calcul peut être sur des serveurs différents. Résultant **objet de contexte de calcul** est nommé `sql_cc`.
3. Choisissez le contexte de calcul active. Par défaut, les opérations sont exécutées localement, ce qui signifie que si vous ne spécifiez pas un contexte de calcul différentes, les données seront extraites à partir de la source de données, et l’ajustement de modèle s’exécute dans votre environnement actuel de Python.

### <a name="changing-compute-contexts"></a>Modification des contextes de calcul

Dans cet exemple, vous définissez le contexte de calcul à l’aide d’un argument de la personne **rx** (fonction).
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

Ces conditions s’appliquent dans l’appel à **rxsummary**, où le contexte de calcul est réutilisé.

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

Vous pouvez également utiliser la fonction [rx_set_computecontext](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rx-set-compute-context) pour basculer entre les contextes de calcul qui ont déjà été définis.

### <a name="setting-the-degree-of-parallelism"></a>Définir le degré de parallélisme

Lorsque vous définissez le contexte de calcul, vous pouvez également définir les paramètres qui contrôlent comment les données sont gérées par le contexte de calcul. Ces paramètres diffèrent selon le type de source de données.

Pour les contextes de calcul de SQL Server, vous pouvez définir la taille de lot, ou fournir des conseils sur le degré de parallélisme à utiliser dans les tâches en cours d’exécution.

L’exemple a été exécuté sur un ordinateur équipé de quatre processeurs, et nous définissons le *num_tasks* paramètre 4. Si vous définissez cette valeur sur 0, SQL Server utilise la valeur par défaut, qui consiste à s’exécuter autant de tâches en parallèle que possible, sous les paramètres MAXDOP actuels pour le serveur. Toutefois, même dans les serveurs avec plusieurs processeurs, le nombre exact de tâches qui peuvent être alloués dépend de nombreux autres facteurs, tels que les paramètres du serveur et les autres tâches qui s’exécutent.

## <a name="related-samples"></a>Exemples associés

Consultez ces exemples de Python et des didacticiels de conseils avancés et des démonstrations de bout en bout.

+ [Python dans base de données pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Créer un modèle prédictif à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
+ [Déployer et utiliser des modèles de Python](../python/publish-consume-python-code.md)
