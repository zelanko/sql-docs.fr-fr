---
title: 'Démarrage rapide : Écrire des fonctions R'
titleSuffix: SQL Server Machine Learning Services
description: Dans ce démarrage rapide, découvrez comment écrire une fonction R pour un calcul statistique avancé avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e725282aaacde748b43a37a317037b5471efd009
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73726886"
---
# <a name="quickstart-write-advanced-r-functions-with-sql-server-machine-learning-services"></a>Démarrage rapide : Écrire des fonctions R avancées avec SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Ce démarrage rapide explique comment incorporer les fonctions mathématiques et utilitaires de R dans une procédure stockée SQL avec SQL Server Machine Learning Services. Les fonctions statistiques avancées qui sont difficiles à implémenter dans T-SQL peuvent être créées dans R avec une seule ligne de code.

## <a name="prerequisites"></a>Conditions préalables requises

- Ce démarrage rapide nécessite l’accès à une instance de SQL Server avec [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), ainsi que l’installation du langage R.

  Votre instance SQL Server peut se trouver sur une machine virtuelle Azure ou être locale. N’oubliez pas que la fonctionnalité de script externe est désactivée par défaut. Par conséquent, vous devrez peut-être [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifier que le **service SQL Server Launchpad** est en cours d’exécution avant de commencer.

- Vous aurez également besoin d’un outil pour exécuter des requêtes SQL qui contiennent des scripts R. Vous pouvez exécuter ces scripts à l’aide de n’importe quel outil de gestion de base de données ou de requête, à condition qu’il puisse se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Créer une procédure stockée pour générer des nombres aléatoires

Pour plus de simplicité, nous allons utiliser le package `stats` R qui est installé et chargé par défaut dans SQL Server Machine Learning Services avec R installé. Le package contient des centaines de fonctions qui permettent d’effectuer des tâches statistiques courantes, notamment la fonction `rnorm`, qui génère un nombre spécifié de nombres aléatoires en utilisant la distribution normale, avec un écart type et une moyenne donnés.

Par exemple, le code R suivant retourne 100 nombres sur une moyenne de 50, compte tenu d’un écart type de 3.

```R
as.data.frame(rnorm(100, mean = 50, sd = 3));
```

Pour appeler cette ligne de code R à partir de T-SQL, ajoutez la fonction R dans le paramètre de script R de `sp_execute_external_script`, comme ceci :

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(100, mean = 50, sd =3));'
    , @input_data_1 = N'   ;'
      WITH RESULT SETS (([Density] float NOT NULL));
```

Vous souhaitez générer plus facilement un autre ensemble de nombres aléatoires ?

C’est facile lorsqu’il est combiné avec SQL Server. Vous définissez une procédure stockée qui obtient les arguments de l’utilisateur, puis transmettez ces arguments dans le script R en tant que variables.

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

Le package **utils**, installé par défaut propose diverses fonctions utilitaires destinées à analyser l’environnement R actuel. Ces fonctions peuvent être utiles si vous constatez des différences de fonctionnement du code R dans SQL Server et les environnements extérieurs.

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
> De nombreux utilisateurs aiment utiliser les fonctions de minutage système dans R, telles que `system.time` et `proc.time`, pour capturer le temps utilisé par les processus R et analyser les problèmes de performances. Pour obtenir un exemple, consultez le didacticiel [Créer des fonctionnalités de données à l’aide de R et SQL Server (procédure pas à pas)](../tutorials/walkthrough-create-data-features.md) où les fonctions de minutage R sont incorporées à la solution.

## <a name="next-steps"></a>Étapes suivantes

Pour créer un modèle Machine Learning à l’aide de R dans SQL Server, suivez ce démarrage rapide :

> [!div class="nextstepaction"]
> [Créer et évaluer un modèle prédictif dans R avec SQL Server Machine Learning Services](quickstart-r-train-score-model.md)

Pour plus d’informations sur SQL Server Machine Learning Services, consultez :

- [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
