---
title: Écrire des fonctions python avancées
titleSuffix: SQL Server Machine Learning Services
description: Dans ce guide de démarrage rapide, Découvrez comment écrire une fonction Python pour un calcul statistique avancé avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e369e83c99543cc31287932a25949c2ddec98e89
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72007719"
---
# <a name="quickstart-write-advanced-python-functions-with-sql-server-machine-learning-services"></a>Démarrage rapide : Écrire des fonctions python avancées avec SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Ce guide de démarrage rapide explique comment incorporer python mathématiques et les fonctions utilitaires dans une procédure stockée SQL avec SQL Server Machine Learning Services. Les fonctions statistiques avancées qui sont complexes à implémenter dans T-SQL peuvent être effectuées dans Python avec une seule ligne de code.

## <a name="prerequisites"></a>Prérequis

- Ce guide de démarrage rapide nécessite l’accès à une instance de SQL Server avec [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md) avec le langage Python installé.

  Votre instance de SQL Server peut se trouver dans une machine virtuelle Azure ou en local. N’oubliez pas que la fonctionnalité de script externe est désactivée par défaut. par conséquent, vous devrez peut-être [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifier que **SQL Server Launchpad service** est en cours d’exécution avant de commencer.

- Vous avez également besoin d’un outil pour exécuter des requêtes SQL qui contiennent des scripts Python. Vous pouvez exécuter ces scripts à l’aide de n’importe quel outil de gestion de base de données ou de requête, à condition qu’il puisse se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce guide de démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Créer une procédure stockée pour générer des nombres aléatoires

Pour plus de simplicité, nous allons utiliser le package Python `numpy`, qui est installé et chargé par défaut dans SQL Server Machine Learning Services avec Python installé. Le package contient des centaines de fonctions qui permettent d’effectuer des tâches statistiques courantes, notamment la fonction `random.normal`, qui génère un nombre spécifié de nombres aléatoires en utilisant la distribution normale, avec un écart type et une moyenne donnés.

Par exemple, le code python suivant retourne 100 chiffres sur une moyenne de 50, selon un écart type de 3.

```Python
numpy.random.normal(size=100, loc=50, scale=3)
```

Pour appeler cette ligne de Python à partir de T-SQL, ajoutez la fonction python dans le paramètre de script Python de `sp_execute_external_script`. La sortie attend une trame de données, donc utilisez `pandas` pour la convertir.

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

- Les lignes qui suivent immédiatement mappent les noms de paramètres SQL aux noms de variable python correspondants.

Maintenant que vous avez encapsulé la fonction python dans une procédure stockée, vous pouvez facilement appeler la fonction et passer des valeurs différentes, comme suit :

```sql
EXECUTE MyPyNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-python-utility-functions-for-troubleshooting"></a>Utilisation des fonctions de l’utilitaire Python pour la résolution des problèmes

Les packages python fournissent diverses fonctions utilitaires pour l’examen de l’environnement python actuel. Ces fonctions peuvent être utiles si vous recherchez des différences dans la façon dont votre code python s’exécute dans SQL Server et dans des environnements externes.

Par exemple, vous pouvez utiliser les fonctions de minutage du système dans le package `time` pour mesurer la durée d’utilisation des processus Python et analyser les problèmes de performances.

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

Pour créer un modèle de Machine Learning à l’aide de Python dans SQL Server, suivez ce guide de démarrage rapide :

> [!div class="nextstepaction"]
> [Démarrage rapide : Créer et évaluer un modèle prédictif dans Python avec SQL Server Machine Learning Services @ no__t-0

Pour plus d’informations sur SQL Server Machine Learning Services, consultez :

- [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
