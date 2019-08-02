---
title: Utilisation de Python avec revoscalepy pour créer un modèle
description: Écrire un script Python à l’aide de fonctions revoscalepy pour créer des modèles de science des données qui s’exécutent à distance dans SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/25/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 596e5f6b5145dc258c781ca7b88a69fc962d7021
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714711"
---
# <a name="use-python-with-revoscalepy-to-create-a-model-that-runs-remotely-on-sql-server"></a>Utilisez Python avec revoscalepy pour créer un modèle qui s’exécute à distance sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La bibliothèque python [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) de Microsoft fournit des algorithmes de science des données pour l’exploration, la visualisation, les transformations et l’analyse des données. Cette bibliothèque a une importance stratégique dans les scénarios d’intégration python dans SQL Server. Sur un serveur multicœur, les fonctions **revoscalepy** peuvent s’exécuter en parallèle. Dans une architecture distribuée avec un serveur central et des stations de travail clientes (ordinateurs physiques distincts, qui ont toutes la même bibliothèque **revoscalepy** ), vous pouvez écrire du code Python qui démarre localement, mais qui décale l’exécution vers une instance de SQL Server distante où résident les données.

Vous pouvez trouver des **revoscalepy** dans les produits et distributions Microsoft suivants:

+ [SQL Server Machine Learning Services (dans la base de données)](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server (serveur non-SQL, serveur autonome)](https://docs.microsoft.com/machine-learning-server/index)
+ [Bibliothèques python côté client (pour les stations de travail de développement)](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) 

Cet exercice montre comment créer un modèle de régression linéaire basé sur [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), l’un des algorithmes dans **revoscalepy** qui accepte le contexte de calcul comme entrée. Le code que vous allez exécuter dans cet exercice décale l’exécution du code d’un environnement de calcul local vers un environnement distant, activé par les fonctions **revoscalepy** qui activent un contexte de calcul distant.

En suivant ce didacticiel, vous allez apprendre à:

> [!div class="checklist"]
> * Utiliser **revoscalepy** pour créer un modèle linéaire
> * Déplacer les opérations du contexte de calcul local vers le contexte de calcul distant

## <a name="prerequisites"></a>Prérequis

Les exemples de données utilisés dans cet exercice sont la base de données [**FlightData**](demo-data-airlinedemo-in-sql.md) .

Vous avez besoin d’un IDE pour exécuter l’exemple de code de cet article, et l’IDE doit être lié à l’exécutable Python.

Pour vous entraîner un changement de contexte de calcul, vous avez besoin d’une [station de travail locale](../python/setup-python-client-tools-sql.md) et d’une instance de moteur de base de données SQL Server avec [machine learning services](../install/sql-machine-learning-services-windows-install.md) et Python activés. 

> [!Tip]
> Si vous n’avez pas deux ordinateurs, vous pouvez simuler un contexte de calcul distant sur un ordinateur physique en installant les applications appropriées. Tout d’abord, une installation de [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md) agit en tant qu’instance «distante». Deuxièmement, une installation des [bibliothèques clientes python fonctionne](../python/setup-python-client-tools-sql.md) comme le client. Vous aurez deux copies de la même distribution Python et des bibliothèques python Microsoft sur le même ordinateur. Vous devez effectuer le suivi des chemins d’accès aux fichiers et de la copie de Python. exe que vous utilisez pour terminer l’exercice.

## <a name="remote-compute-contexts-and-revoscalepy"></a>Contextes de calcul à distance et revoscalepy

Cet exemple illustre le processus de création d’un modèle python dans un contexte de calcul distant, qui vous permet de travailler à partir d’un client, mais de choisir un environnement distant, tel que SQL Server, Spark ou Machine Learning Server, où les opérations sont réellement effectuées. L’objectif du contexte de calcul distant est d’amener le calcul à l’emplacement où résident les données.

Pour exécuter du code python dans SQL Server nécessite le package **revoscalepy** . Il s’agit d’un package Python spécial fourni par Microsoft, similaire au package **RevoScaleR** pour le langage R. Le package **revoscalepy** prend en charge la création de contextes de calcul et fournit l’infrastructure pour passer des données et des modèles entre une station de travail locale et un serveur distant. La fonction **revoscalepy** qui prend en charge l’exécution de code dans la base de données est [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).

Dans cette leçon, vous utilisez les données de SQL Server pour former un modèle linéaire basé sur [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), une fonction dans **revoscalepy** qui prend en charge la régression sur les jeux de données très volumineux. 

Cette leçon présente également les principes de base de la configuration et de l’utilisation d’un **contexte de calcul SQL Server** dans Python. Pour plus d’informations sur la façon dont les contextes de calcul fonctionnent avec d’autres plateformes, et sur les contextes de calcul pris en charge, consultez le [contexte de calcul pour l’exécution de scripts dans machine learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).


## <a name="run-the-sample-code"></a>Exécuter l’exemple de code

Une fois que vous avez préparé la base de données et que vous avez les données pour l’apprentissage stockées dans une table, ouvrez un environnement de développement Python et exécutez l’exemple de code.

Le code effectue les étapes suivantes:

1. Importe les bibliothèques et les fonctions requises.
2. Crée une connexion à SQL Server. Crée des objets de **source de données** pour l’utilisation des données.
3. Modifie les données à l' aide de transformations afin qu’elles puissent être utilisées par l’algorithme de régression logistique.
4. Appelle `rx_lin_mod` et définit la formule utilisée pour s’adapter au modèle.
5. Génère un ensemble de prédictions basées sur les données d’origine.
6. Crée un résumé basé sur les valeurs prédites.

Toutes les opérations sont effectuées à l’aide d’une instance de SQL Server comme contexte de calcul.

> [!NOTE]
> Pour une démonstration de cet exemple exécuté à partir de la ligne de commande, consultez cette vidéo: [SQL Server 2017 analytique avancée avec Python](https://www.youtube.com/watch?v=FcoY795jTcc)

### <a name="sample-code"></a>Exemple de code

```python
from revoscalepy import RxComputeContext, RxInSqlServer, RxSqlServerData
from revoscalepy import rx_lin_mod, rx_predict, rx_summary
from revoscalepy import RxOptions, rx_import

import os

def test_linmod_sql():
    sql_server = os.getenv('PYTEST_SQL_SERVER', '.')
    
    sql_connection_string = 'Driver=SQL Server;Server=' + sqlServer + ';Database=sqlpy;Trusted_Connection=True;'
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

### <a name="defining-a-data-source-vs-defining-a-compute-context"></a>Définition d’une source de données et définition d’un contexte de calcul

Une source de données est différente d’un contexte de calcul. La *source de données* définit les données utilisées dans votre code. Le contexte de calcul définit l’emplacement où le code sera exécuté. Toutefois, ils utilisent certaines des informations suivantes:

+ Les variables Python, telles `sql_query` que `sql_connection_string`et, définissent la source des données. 

    Transmettez ces variables au constructeur [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) pour implémenter l’objet de source `data_source`de **données** nommé.

+ Vous créez un **objet de contexte de calcul** à l’aide du constructeur [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) . L' **objet de contexte de calcul** résultant est `sql_cc`nommé.

    Cet exemple réutilise la même chaîne de connexion que celle que vous avez utilisée dans la source de données, en supposant que les données se trouvent sur la même instance de SQL Server que vous allez utiliser comme contexte de calcul. 
    
    Toutefois, la source de données et le contexte de calcul peuvent se trouver sur des serveurs différents.
 
### <a name="changing-compute-contexts"></a>Modification des contextes de calcul

Une fois que vous avez défini un contexte de calcul, vous devez définir le **contexte de calcul actif**. 

Par défaut, la plupart des opérations sont exécutées localement, ce qui signifie que si vous ne spécifiez pas un autre contexte de calcul, les données seront extraites de la source de données et le code s’exécutera dans votre environnement python actuel.

Il existe deux façons de définir le contexte de calcul actif:
+ En tant qu’argument d’une méthode ou d’une fonction
+ En appelant`rx_set_computecontext`

#### <a name="set-compute-context-as-an-argument-of-a-method-or-function"></a>Définir le contexte de calcul en tant qu’argument d’une méthode ou d’une fonction

Dans cet exemple, vous définissez le contexte de calcul à l’aide d’un argument de la fonction **RX** individuelle.
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

Ce contexte de calcul est réutilisé dans l’appel à [rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary):

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rxsetcomputecontext"></a>Définir explicitement un contexte de calcul à l’aide de rx_set_compute_context

La fonction [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) vous permet de basculer entre les contextes de calcul qui ont déjà été définis.

Une fois que vous avez défini le contexte de calcul actif, il reste actif jusqu’à ce que vous le modifiiez.

### <a name="using-parallel-processing-and-streaming"></a>Utilisation du traitement parallèle et de la diffusion en continu

Lorsque vous définissez le contexte de calcul, vous pouvez également définir des paramètres qui contrôlent la façon dont les données sont gérées par le contexte de calcul. Ces paramètres diffèrent en fonction du type de source de données.

Pour les contextes de calcul SQL Server, vous pouvez définir la taille du lot ou fournir des indications sur le degré de parallélisme à utiliser dans les tâches en cours d’exécution.

+ L’exemple a été exécuté sur un ordinateur doté de quatre processeurs `num_tasks` . par conséquent, le paramètre a la valeur 4 pour permettre une utilisation maximale des ressources. 
+ Si vous définissez cette valeur sur 0, SQL Server utilise la valeur par défaut, qui consiste à exécuter autant de tâches en parallèle que possible, sous les paramètres MAXDOP actuels du serveur. Toutefois, le nombre exact de tâches qui peuvent être allouées dépend de nombreux autres facteurs, tels que les paramètres du serveur, et d’autres travaux en cours d’exécution.

## <a name="next-steps"></a>Étapes suivantes

Ces exemples et didacticiels python supplémentaires illustrent des scénarios de bout en bout utilisant des sources de données plus complexes, ainsi que l’utilisation de contextes de calcul distants.

+ [Python en base de données pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Créer un modèle prédictif à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
