---
title: Écrire des fonctions R avancées
titleSuffix: SQL Server Machine Learning Services
description: Dans ce guide de démarrage rapide, vous apprendrez à écrire une fonction R pour un calcul statistique avancé avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 747a6b06d1c9ad198971ff50068ac48d862a83da
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72006027"
---
# <a name="quickstart-write-advanced-r-functions-with-sql-server-machine-learning-services"></a>Démarrage rapide : Écrire des fonctions R avancées avec SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Ce guide de démarrage rapide explique comment incorporer des fonctions de l’utilitaire et du langage R mathématiques dans une procédure stockée SQL avec SQL Server Machine Learning Services. Les fonctions statistiques avancées qui sont complexes à implémenter dans T-SQL peuvent être effectuées dans R avec une seule ligne de code.

## <a name="prerequisites"></a>Prérequis

- Ce guide de démarrage rapide nécessite l’accès à une instance de SQL Server avec [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md) avec le langage R installé.

  Votre instance de SQL Server peut se trouver dans une machine virtuelle Azure ou en local. N’oubliez pas que la fonctionnalité de script externe est désactivée par défaut. par conséquent, vous devrez peut-être [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifier que **SQL Server Launchpad service** est en cours d’exécution avant de commencer.

- Vous avez également besoin d’un outil pour exécuter des requêtes SQL qui contiennent des scripts R. Vous pouvez exécuter ces scripts à l’aide de n’importe quel outil de gestion de base de données ou de requête, à condition qu’il puisse se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce guide de démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Créer une procédure stockée pour générer des nombres aléatoires

Pour plus de simplicité, nous allons utiliser le package R `stats`, qui est installé et chargé par défaut dans SQL Server Machine Learning Services avec R installé. Le package contient des centaines de fonctions qui permettent d’effectuer des tâches statistiques courantes, notamment la fonction `rnorm`, qui génère un nombre spécifié de nombres aléatoires en utilisant la distribution normale, avec un écart type et une moyenne donnés.

Par exemple, le code R suivant retourne 100 chiffres sur une moyenne de 50, selon un écart type de 3.

```R
as.data.frame(rnorm(100, mean = 50, sd = 3));
```

Pour appeler cette ligne de R à partir de T-SQL, ajoutez la fonction R dans le paramètre de script R de `sp_execute_external_script`, comme suit :

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(100, mean = 50, sd =3));'
    , @input_data_1 = N'   ;'
      WITH RESULT SETS (([Density] float NOT NULL));
```

Vous souhaitez générer plus facilement un autre ensemble de nombres aléatoires ?

C’est facile lorsqu’il est combiné avec SQL Server. Vous définissez une procédure stockée qui obtient les arguments de l’utilisateur, puis transmettez ces arguments dans le script R sous forme de variables.

```sql
CREATE PROCEDURE MyRNorm (
    @param1 INT
    , @param2 INT
    , @param3 INT
    )
AS
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynumbers, mymean, mysd));'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

- La première ligne définit chaque paramètre d’entrée SQL nécessaire pendant l’exécution de la procédure stockée.

- La ligne commençant par `@params` définit toutes les variables utilisées par le code R, ainsi que les types de données SQL correspondants.

- Les lignes qui viennent de suite après mappent les noms de paramètres SQL aux noms de variables R correspondants.

Maintenant que vous avez inclus la fonction R dans une procédure stockée, vous pouvez l’appeler facilement et passer des valeurs différentes, comme ceci :

```sql
EXECUTE MyRNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-r-utility-functions-for-troubleshooting"></a>Utiliser les fonctions utilitaires R pour résoudre les problèmes

Le package **utils** , installé par défaut, fournit diverses fonctions utilitaires pour l’examen de l’environnement R actuel. Ces fonctions peuvent être utiles si vous recherchez des différences dans la façon dont votre code R s’exécute dans SQL Server et dans des environnements externes.

Par exemple, vous pouvez utiliser la fonction `memory.limit()` R pour affecter de la mémoire à l’environnement R actif. Comme le package `utils` est installé par défaut mais pas chargé, vous devez utiliser la fonction `library()` pour le charger en premier lieu.

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N'
        library(utils);
        mymemory <- memory.limit();
        OutputDataSet <- as.data.frame(mymemory);'
    , @input_data_1 = N' ;'
WITH RESULT SETS (([Col1] int not null));
```

> [!TIP]
> De nombreux utilisateurs aiment utiliser les fonctions de minutage du système dans R, telles que `system.time` et `proc.time`, pour capturer le temps utilisé par les processus R et analyser les problèmes de performances. Pour obtenir un exemple, consultez le didacticiel [créer des fonctionnalités de données](../tutorials/walkthrough-create-data-features.md) où les fonctions de minutage R sont incorporées dans la solution.

## <a name="next-steps"></a>Étapes suivantes

Pour créer un modèle de Machine Learning à l’aide de R dans SQL Server, suivez ce guide de démarrage rapide :

> [!div class="nextstepaction"]
> [Créer et évaluer un modèle prédictif dans R avec SQL Server Machine Learning Services](quickstart-r-train-score-model.md)

Pour plus d’informations sur SQL Server Machine Learning Services, consultez :

- [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
