---
title: 'Démarrage rapide : Écrire des fonctions Python'
titleSuffix: SQL Server Machine Learning Services
description: Dans ce guide de démarrage rapide, vous allez découvrir comment écrire une fonction Python pour un calcul statistique avancé avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 08f43c6406d0ca2c95cc21a207cae63af6e86902
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727010"
---
# <a name="quickstart-write-advanced-python-functions-with-sql-server-machine-learning-services"></a>Démarrage rapide : Écrire des fonctions Python avancées avec SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Ce guide de démarrage rapide explique comment incorporer les fonctions mathématiques et utilitaires de Python dans une procédure stockée SQL avec SQL Server Machine Learning Services. Les fonctions statistiques avancées qui sont difficiles à implémenter dans T-SQL peuvent être effectuées dans Python avec une seule ligne de code.

## <a name="prerequisites"></a>Conditions préalables requises

- Ce guide de démarrage rapide nécessite l’accès à une instance de SQL Server avec [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) ainsi que l’installation du langage Python.

  Votre instance SQL Server peut se trouver sur une machine virtuelle Azure ou être locale. N’oubliez pas que la fonctionnalité de script externe est désactivée par défaut. Par conséquent, vous devrez peut-être [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifier que le **service SQL Server Launchpad** est en cours d’exécution avant de commencer.

- Vous aurez également besoin d’un outil pour exécuter des requêtes SQL qui contiennent des scripts Python. Vous pouvez exécuter ces scripts à l’aide de n’importe quel outil de gestion de base de données ou de requête, à condition qu’il puisse se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce guide de démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Créer une procédure stockée pour générer des nombres aléatoires

Pour plus de simplicité, nous allons utiliser le package Python `numpy` qui est installé et chargé par défaut dans SQL Server Machine Learning Services avec Python installé. Le package contient des centaines de fonctions qui permettent d’effectuer des tâches statistiques courantes, notamment la fonction `random.normal`, qui génère un nombre spécifié de nombres aléatoires en utilisant la distribution normale, avec un écart type et une moyenne donnés.

Par exemple, le code Python suivant retourne 100 nombres sur une moyenne de 50, compte tenu d’un écart type de 3.

```Python
numpy.random.normal(size=100, loc=50, scale=3)
```

Pour appeler cette ligne de Python à partir de T-SQL, ajoutez la fonction Python dans le paramètre de script Python de `sp_execute_external_script`. La sortie attend une trame de données, alors utilisez `pandas` pour la convertir.

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import numpy
import pandas
OutputDataSet = pandas.DataFrame(numpy.random.normal(size=100, loc=50, scale=3));
'
    , @input_data_1 = N'   ;'
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

Vous souhaitez générer plus facilement un autre ensemble de nombres aléatoires ?

C’est facile lorsqu’il est combiné avec SQL Server. Vous définissez une procédure stockée qui obtient les arguments de l’utilisateur, puis transmettez ces arguments dans le script Python en tant que variables.

```sql
CREATE PROCEDURE MyPyNorm (
      @param1 INT
    , @param2 INT
    , @param3 INT
    )
AS
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import numpy
import pandas
OutputDataSet = pandas.DataFrame(numpy.random.normal(size=mynumbers, loc=mymean, scale=mysd));
'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

- La première ligne définit chaque paramètre d’entrée SQL nécessaire pendant l’exécution de la procédure stockée.

- La ligne commençant par `@params` définit toutes les variables utilisées par le code Python, ainsi que les types de données SQL correspondants.

- Les lignes qui viennent juste après mappent les noms de paramètres SQL aux noms de variables Python correspondants.

Maintenant que vous avez inclus la fonction Python dans une procédure stockée, vous pouvez l’appeler facilement et passer des valeurs différentes, comme ceci :

```sql
EXECUTE MyPyNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-python-utility-functions-for-troubleshooting"></a>Utiliser les fonctions utilitaires Python pour résoudre les problèmes

Les packages Python fournissent diverses fonctions utilitaires pour l’examen de l’environnement Python actuel. Ces fonctions peuvent être utiles si vous constatez des différences de fonctionnement du code Python dans SQL Server et les environnements extérieurs.

Par exemple, vous pouvez utiliser les fonctions de minutage du système dans le package `time` pour mesurer la durée des processus Python et de l’analyse des problèmes de performances.

```sql
EXECUTE sp_execute_external_script
      @language = N'Python'
    , @script = N'
import time
start_time = time.time()

# Run Python processes

elapsed_time = time.time() - start_time
'
    , @input_data_1 = N' ;';
```

## <a name="next-steps"></a>Étapes suivantes

Pour créer un modèle Machine Learning à l’aide de Python dans SQL Server, suivez ce guide de démarrage rapide :

> [!div class="nextstepaction"]
> [Démarrage rapide : Créer un modèle prédictif doté d’un score en Python avec SQL Server Machine Learning Services](quickstart-python-train-score-model.md)

Pour plus d’informations sur SQL Server Machine Learning Services, consultez :

- [Qu’est-ce que SQL Server Machine Learning Services (Python et R)?](../what-is-sql-server-machine-learning.md)
