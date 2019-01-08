---
title: Guide de démarrage rapide montrant R - fonctions SQL Server Machine Learning
description: Dans ce démarrage rapide, découvrez comment écrire une fonction R pour le calcul de statistiques avancée.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: d33034a2d18736f47fb32c4d35221bbcd702927d
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046791"
---
# <a name="quickstart-using-r-functions"></a>Démarrage rapide : Utilisation des fonctions R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Si vous avez terminé les Démarrages rapides précédents, vous êtes familiarisé avec les opérations de base et prêt pour une valeur plus complexe, comme les fonctions statistiques. Fonctions statistiques avancées qui sont difficiles à implémenter dans T-SQL peuvent être effectuées dans R avec uniquement une seule ligne de code.

Dans ce démarrage rapide, vous allez incorporer R mathématique et les fonctions utilitaires dans un serveur SQL Server de procédure stockée.

## <a name="prerequisites"></a>Prérequis

Un guide de démarrage rapide précédent, [R vérifier existe dans SQL Server](quickstart-r-verify.md), fournit des informations et des liens pour la configuration de l’environnement R requis pour ce démarrage rapide.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Créer une procédure stockée pour générer des nombres aléatoires

Par souci de simplicité, nous allons utiliser le R `stats` package, qui est installé et chargé par défaut lorsque vous installez la prise en charge des fonctionnalités de R dans SQL Server. Le package contient des centaines de fonctions qui permettent d’effectuer des tâches statistiques courantes, notamment la fonction `rnorm`, qui génère un nombre spécifié de nombres aléatoires en utilisant la distribution normale, avec un écart type et une moyenne donnés.

Par exemple, ce code R retourne 100 nombres sur une moyenne de 50, compte tenu d’un écart type de 3.

```R
as.data.frame(rnorm(100, mean = 50, sd = 3));
```

Pour appeler cette ligne de code R à partir de T-SQL, exécutez sp_execute_external_script et ajoutez la fonction R dans le paramètre de script R, comme ceci :

```sql
EXEC sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(100, mean = 50, sd =3));'
    , @input_data_1 = N'   ;'
      WITH RESULT SETS (([Density] float NOT NULL));
```

Vous souhaitez générer plus facilement un autre ensemble de nombres aléatoires ?

C’est très facile lorsqu’elles sont combinées avec SQL Server : définir une procédure stockée qui obtienne les arguments de l’utilisateur. Vous devez ensuite passer ces arguments dans le script R sous forme de variables.

```sql
CREATE PROCEDURE MyRNorm (@param1 int, @param2 int, @param3 int)
AS
    EXEC sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynumbers, mymean, mysd));'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
    WITH RESULT SETS (([Density] float NOT NULL));
```

+ La première ligne définit chaque paramètre d’entrée SQL nécessaire pendant l’exécution de la procédure stockée.

+ La ligne commençant par `@params` définit toutes les variables utilisées par le code R, ainsi que les types de données SQL correspondants.

+ Les lignes qui viennent de suite après mappent les noms de paramètres SQL aux noms de variables R correspondants.

Maintenant que vous avez inclus la fonction R dans une procédure stockée, vous pouvez l’appeler facilement et passer des valeurs différentes, comme ceci :

```sql
EXEC MyRNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-r-utility-functions-for-troubleshooting"></a>Utiliser les fonctions utilitaires R pour résoudre les problèmes

Par défaut, une installation de R inclut le `utils` package, qui fournit un éventail de fonctions utilitaires pour examiner l’environnement R actuel. Cela peut être utile si vous constatez des différences de fonctionnement du code R dans SQL Server et les environnements extérieurs.

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

Beaucoup d’utilisateurs souhaitent utiliser les fonctions de minutage système dans R, tel que `system.time` et `proc.time`, pour capturer l’heure utilisée par les processus R et analyser les problèmes de performances.

Pour obtenir un exemple, consultez ce didacticiel : [Créer des caractéristiques de données](../tutorials/walkthrough-create-data-features.md). Dans cette procédure pas à pas, les fonctions de minutage R sont incorporées dans la solution pour comparer les performances des deux méthodes de création de caractéristiques à partir des données : Visual Studio de fonctions R. aux fonctions T-SQL.

## <a name="next-steps"></a>Étapes suivantes

Ensuite, vous allez créer un modèle prédictif en utilisant R dans SQL Server.

> [!div class="nextstepaction"]
> [Démarrage rapide : Créer un modèle prédictif](quickstart-r-create-predictive-model.md)
