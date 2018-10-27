---
title: Utilisation de Python avec revoscalepy pour créer un modèle dans SQL Server | Microsoft Docs
description: Écrire le script Python à l’aide de revoscalepy fonctions pour créer des modèles de science des données qui s’exécutent à distance dans SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/25/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f554badcba282bad7fb386daf8c4c0f4106804b4
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100160"
---
# <a name="use-python-with-revoscalepy-to-create-a-model-that-runs-remotely-on-sql-server"></a>Utilisation de Python avec revoscalepy pour créer un modèle qui s’exécute à distance sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Le [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) bibliothèque Python à partir de Microsoft fournit des algorithmes de science des données pour l’exploration de données, de visualisation, de transformations et d’analyse. Cette bibliothèque a une importance stratégique dans les scénarios d’intégration de Python dans SQL Server. Sur un serveur multicœur, **revoscalepy** fonctions peuvent s’exécuter en parallèle. Dans une architecture distribuée avec une station de travail serveur et client centrale (séparer les ordinateurs physiques, tous ayant la même **revoscalepy** bibliothèque), vous pouvez écrire du code Python qui démarre localement, mais ensuite déplace l’exécution à un instance de SQL Server distante où les données résident.

Vous pouvez trouver **revoscalepy** dans les distributions et les produits Microsoft suivants :

+ [SQL Server Machine Learning Services (en base de données)](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server (non-SQL, serveur autonome)](https://docs.microsoft.com/machine-learning-server/index)
+ [Bibliothèques de Python côté client (pour les stations de travail de développement)](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) 

Cet exercice montre comment créer un modèle de régression linéaire basé sur [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), un des algorithmes dans **revoscalepy** qui accepte le contexte de calcul en tant qu’entrée. Le code dans cet exercice, vous allez exécuter déplace l’exécution de code à partir d’une variable locale pour environnement informatique distant, activée par **revoscalepy** contexte de calcul de fonctions qui permettent à un référentiel distant.

En suivant ce didacticiel, vous allez apprendre comment :

> [!div class="checklist"]
> * Utilisez **revoscalepy** pour créer un modèle linéaire
> * Déplacer les opérations de local au contexte de calcul à distance

## <a name="prerequisites"></a>Prérequis

Exemples de données utilisés dans cet exercice est la [ **flightdata** ](demo-data-airlinedemo-in-sql.md) base de données.

Vous avez besoin d’un IDE pour exécuter l’exemple de code dans cet article, et l’IDE doit être lié à l’exécutable de Python.

Pour vous entraîner un changement de contexte de calcul, vous devez un [station de travail locale](../python/setup-python-client-tools-sql.md) et une instance du moteur de base de données SQL Server avec [Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) et Python est activée. 

> [!Tip]
> Si vous n’avez pas deux ordinateurs, vous pouvez simuler un contexte de calcul à distance sur un ordinateur physique en installant des applications pertinentes. Tout d’abord, une installation de [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) fonctionne comme l’instance « distante ». Ensuite, une installation de la [opère des bibliothèques de client Python](../python/setup-python-client-tools-sql.md) que le client. Vous aurez deux copies de la même distribution de Python et les bibliothèques de Python de Microsoft sur le même ordinateur. Vous devrez effectuer le suivi des chemins de fichiers et de quelle copie de la Python.exe que vous utilisez pour terminer l’exercice avec succès.

## <a name="remote-compute-contexts-and-revoscalepy"></a>Revoscalepy et contextes de calcul à distance

Cet exemple montre le processus de création d’un modèle Python dans un contexte de calcul à distance, qui vous permet de travailler à partir d’un client, mais choisissez un environnement distant, tel que SQL Server, Spark ou Machine Learning Server, où les opérations sont effectuées. L’objectif de contexte de calcul à distance consiste à mettre le calcul sur lequel résident les données.

Pour exécuter le code Python dans SQL Server nécessite le **revoscalepy** package. Il s’agit d’un package Python spécial fourni par Microsoft, similaire à la **RevoScaleR** package pour le langage R. Le **revoscalepy** package prend en charge de la création de contextes de calcul et fournit l’infrastructure pour le transfert des données et des modèles entre une station de travail locale et un serveur distant. Le **revoscalepy** fonction qui prend en charge l’exécution de code de la base de données est [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).

Dans cette leçon, vous utilisez données dans SQL Server pour former un modèle linéaire selon [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), une fonction dans **revoscalepy** qui prend en charge la régression sur les jeux de données très volumineux. 

Cette leçon explique également comment configurer et utiliser ensuite un **contexte de calcul de SQL Server** dans Python. Pour plus d’informations des contextes de calcul fonctionnent avec d’autres plates-formes et contextes de calcul qui sont pris en charge, consultez [contexte de calcul pour l’exécution du script dans Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).


## <a name="run-the-sample-code"></a>Exécutez l’exemple de code

Une fois que vous avez préparé la base de données et les données pour l’apprentissage stockés dans une table, ouvrez un environnement de développement Python et exécuter l’exemple de code.

Le code effectue les étapes suivantes :

1. Importe les bibliothèques requises et les fonctions.
2. Crée une connexion à SQL Server. Crée **source de données** objets pour travailler avec les données.
3. Modifie les données à l’aide **transformations** afin qu’il peut être utilisé par l’algorithme de régression logistique.
4. Appels `rx_lin_mod` et définit la formule utilisée pour ajuster le modèle.
5. Génère un ensemble de prédictions basées sur les données d’origine.
6. Crée une synthèse basée sur les valeurs prédites.

Toutes les opérations sont effectuées à l’aide d’une instance de SQL Server comme contexte de calcul.

> [!NOTE]
> Pour une démonstration de cet exemple en cours d’exécution à partir de la ligne de commande, consultez cette vidéo : [SQL Server 2017 Advanced Analytique avec Python](https://www.youtube.com/watch?v=FcoY795jTcc)

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

### <a name="defining-a-data-source-vs-defining-a-compute-context"></a>Définition d’une source de données et la définition d’un contexte de calcul

Une source de données est différente à partir d’un contexte de calcul. Le *source de données* définit les données utilisées dans votre code. Le contexte de calcul définit où le code sera exécuté. Toutefois, ils utilisent certaines de ces mêmes informations :

+ Variables de Python, tel que `sql_query` et `sql_connection_string`, définir la source de données. 

    Passer ces variables pour le [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) constructeur pour implémenter le **objet source de données** nommé `data_source`.

+ Vous créez un **objet de contexte de calcul** à l’aide de la [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserverdata) constructeur. Résultant **objet de contexte de calcul** est nommé `sql_cc`.

    Cet exemple utilise de nouveau la même chaîne de connexion que vous avez utilisé dans la source de données, en supposant que les données sont sur la même instance de SQL Server que vous utiliserez comme contexte de calcul. 
    
    Toutefois, la source de données et le contexte de calcul peut être sur des serveurs différents.
 
### <a name="changing-compute-contexts"></a>Modification des contextes de calcul

Après avoir défini un contexte de calcul, vous devez définir le **contexte de calcul active**. 

Par défaut, la plupart des opérations sont exécutées localement, ce qui signifie que si vous ne spécifiez pas un contexte de calcul différents, les données seront extraites à partir de la source de données, et le code s’exécute dans votre environnement Python actuel.

Il existe deux façons de définir le contexte de calcul active :
+ En tant qu’argument d’une méthode ou une fonction
+ En appelant `rx_set_computecontext`

#### <a name="set-compute-context-as-an-argument-of-a-method-or-function"></a>Définir le contexte de calcul en tant qu’argument d’une méthode ou une fonction

Dans cet exemple, vous définissez le contexte de calcul en utilisant un argument de la personne **rx** (fonction).
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

Ce contexte de calcul est réutilisé dans l’appel à [rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary):

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rxsetcomputecontext"></a>Définir un contexte de calcul explicitement à l’aide de rx_set_compute_context

La fonction [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) vous permet de basculer entre les contextes qui ont déjà été définies de calcul.

Une fois que vous avez défini contexte de calcul actif, il reste actif jusqu'à ce que vous le changiez.

### <a name="using-parallel-processing-and-streaming"></a>À l’aide d’un traitement parallèle et diffusion en continu

Lorsque vous définissez le contexte de calcul, vous pouvez également définir les paramètres qui contrôlent comment les données sont gérées par le contexte de calcul. Ces paramètres diffèrent selon le type de source de données.

Pour les contextes de calcul de SQL Server, vous pouvez définir la taille de lot, ou fournir des conseils sur le degré de parallélisme à utiliser dans les tâches en cours d’exécution.

+ L’exemple a été exécuté sur un ordinateur équipé de quatre processeurs, donc la `num_tasks` paramètre est défini à 4 pour autoriser l’utilisation maximale des ressources. 
+ Si vous définissez cette valeur sur 0, SQL Server utilise la valeur par défaut, qui consiste à s’exécuter autant de tâches en parallèle que possible, sous les paramètres MAXDOP actuels pour le serveur. Toutefois, le nombre exact de tâches qui peuvent être alloués dépend de nombreux autres facteurs, tels que les paramètres de serveur et d’autres tâches qui sont en cours d’exécution.

## <a name="next-steps"></a>Étapes suivantes

Ces exemples Python supplémentaires et des didacticiels illustrent des scénarios de bout en bout à l’aide de sources de données plus complexes, ainsi que l’utilisation de contextes de calcul distants.

+ [Python dans base de données pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Créer un modèle prédictif à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
