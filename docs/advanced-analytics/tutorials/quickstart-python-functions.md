---
title: 'Démarrage rapide : Fonctions Python'
description: Dans ce guide de démarrage rapide, vous apprendrez à utiliser les fonctions mathématiques et utilitaires de Python avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2020
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d939e04c4a82575cf8210f2c11e734b9912c0fe5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "76831407"
---
# <a name="quickstart-python-functions-with-sql-server-machine-learning-services"></a>Démarrage rapide : Fonctions Python avancées avec SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce guide de démarrage rapide, vous apprendrez à utiliser les fonctions mathématiques et utilitaires de Python avec SQL Server Machine Learning Services. Les fonctions statistiques sont souvent complexes à implémenter dans T-SQL, mais elles peuvent l’être en Python avec seulement quelques lignes de code.

## <a name="prerequisites"></a>Prérequis

- Ce démarrage rapide nécessite l’accès à une instance de SQL Server avec [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), ainsi que l’installation du langage Python.

  Votre instance SQL Server peut se trouver sur une machine virtuelle Azure ou être locale. Sachez simplement que la fonctionnalité de script externe est désactivée par défaut. Avant de commencer, vous serez donc peut-être amené à [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifier que le **service SQL Server Launchpad** est en cours d’exécution.

- Vous avez également besoin d’un outil pour exécuter des requêtes SQL qui contiennent des scripts Python. Vous pouvez exécuter ces scripts à l’aide de n’importe quel outil de gestion de base de données ou de requête, à condition qu’il puisse se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

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

Que se passe-t-il si vous voulez simplifier la génération d’un autre ensemble de nombres alétaoires ?

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

- La première ligne définit chacun des paramètres d’entrée SQL exigés quand la procédure stockée est exécutée.

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

- [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
