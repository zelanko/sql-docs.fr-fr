---
title: Exécuter des fonctions R personnalisées sur SQL Server à l’aide de RevoScaleR rxExec - SQL Server Machine Learning
description: Didacticiel pas à pas expliquant comment exécuter un script R personnalisé sur SQL Server à l’aide de fonctions RevoScaleR.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: c9cb9d84637d20f3f0e73f97fa6565d84d12fb4e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961956"
---
# <a name="run-custom-r-functions-on-sql-server-using-rxexec"></a>Exécuter des fonctions R personnalisées sur SQL Server à l’aide de rxExec
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Vous pouvez exécuter des fonctions R personnalisées dans le contexte de SQL Server en passant votre fonction via [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec), en supposant que toutes les bibliothèques nécessite votre script sont également installés sur le serveur et ces bibliothèques sont compatibles avec la base distribution de R. 

Le **rxExec** fonctionner dans **RevoScaleR** fournit un mécanisme pour l’exécution de n’importe quel script R que vous avez besoin. En outre, **rxExec** est en mesure de répartir explicitement le travail sur plusieurs cœurs dans un seul serveur, ajout de mise à l’échelle vers des scripts qui sont sinon limités aux contraintes de ressources du moteur R natif.

Dans ce didacticiel, vous allez utiliser des données simulées pour illustrer l’exécution d’une fonction R personnalisée qui s’exécute sur un serveur distant.

## <a name="prerequisites"></a>Prérequis

+ [SQL Server 2017 Machine Learning Services (avec R)](../install/sql-machine-learning-services-windows-install.md) ou [SQL Server 2016 R Services (en base de données)](../install/sql-r-services-windows-install.md)
  
+ [Autorisations de base de données](../security/user-permission.md) et une connexion d’utilisateur de base de données SQL Server

+ [Une station de travail de développement avec les bibliothèques RevoScaleR](../r/set-up-a-data-science-client.md)

La distribution de R sur la station de travail cliente fournit un intégré **Rgui** outil que vous pouvez utiliser pour exécuter le script R dans ce didacticiel. Vous pouvez également utiliser un IDE tel que RStudio ou les outils R pour Visual Studio.

## <a name="create-the-remote-compute-context"></a>Créer le contexte de calcul à distance

Exécutez les commandes R suivantes sur une station de travail cliente. Par exemple, vous utilisez **Rgui**, démarrez-le à partir de cet emplacement : C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64\.

1. Spécifiez la chaîne de connexion pour l’instance de SQL Server où les calculs sont effectués. Le serveur doit être configuré pour l’intégration de R. Le nom de la base de données n’est pas utilisé dans cet exercice, mais la chaîne de connexion requiert un. Si vous avez une base de données de test ou d’exemple, vous pouvez l’utiliser.

    **Utilisation d’une connexion SQL**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL-Server-instance-name>; Database=<database-name>;Uid=<SQL-user-name>;Pwd=<password>"
    ```

    **Avec l’authentification Windows**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL-Server-instance-name>;Database=<database-name>;Trusted_Connection=True"
    ```

2. Créer un contexte de calcul à distance à l’instance de SQL Server référencé dans la chaîne de connexion.

    ```R
    sqlCompute <- RxInSqlServer(connectionString = sqlConnString)
    ```

3. Activer le contexte de calcul, puis retournez la définition d’objet comme une étape de confirmation. Vous devez voir les propriétés de l’objet de contexte de calcul.

    ```R
    rxSetComputeContext(sqlCompute)
    rxGetComputeContext()
    ```

## <a name="create-the-custom-function"></a>Créez la fonction personnalisée

Dans cet exercice, vous allez créer une fonction R personnalisée qui simule un casino commun consistant à lancer une paire de dés. Règles du jeu déterminent un résultat win ou perte :

+ À la version 7 ou 11 au premier lancer, vous gagnez.
+ À la version 2, 3 ou 12, vous perdez.
+ Déployer un 4, 5, 6, 8, 9 ou 10, ce nombre devient votre référence et continue à propagée jusqu'à ce que vous que soit restaurer à nouveau votre point de (auquel cas win) ou pour annuler un 7, dans lequel cas vous perdez.

Vous pouvez facilement simuler le jeu en R, en créant une fonction personnalisée, puis en l’exécutant plusieurs fois.

1.  Créez la fonction personnalisée à l’aide du code R suivant :
  
    ```R
    rollDice <- function()
    {
        result <- NULL
        point <- NULL
        count <- 1
            while (is.null(result))
            {
                roll <- sum(sample(6, 2, replace=TRUE))
  
                if (is.null(point))
                { point <- roll }
                if (count == 1 && (roll == 7 || roll == 11))
                {  result <- "Win" }
                else if (count == 1 && (roll == 2 || roll == 3 || roll == 12))
                { result <- "Loss" }
                else if (count > 1 && roll == 7 )
                { result <- "Loss" }
                else if (count > 1 && point == roll)
                { result <- "Win" }
                else { count <- count + 1 }
            }
            result
    }
    ```
  
2.  Simuler un jeu de dés unique par la fonction en cours d’exécution.
  
    ```R
    rollDice()
    ```
  
    Avez-vous gagné ou perdu ?
  
Maintenant que vous disposez d’un script opérationnels, nous allons voir comment vous pouvez utiliser **rxExec** pour exécuter la fonction plusieurs fois afin de créer une simulation qui permet de déterminer la probabilité d’une victoire.

## <a name="pass-rolldice-in-rxexec"></a>Transmettez rollDice() rxExec

Pour exécuter une fonction arbitraire dans le contexte d’un serveur SQL distant, appelez le **rxExec** (fonction).

1. Appelez la fonction personnalisée en tant qu’argument à **rxExec**, avec les autres paramètres qui modifient la simulation.
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    + Utilisez l’argument *timesToRun* pour indiquer le nombre d’exécutions de la fonction.  Dans ce cas, vous lancez les dés 20 fois.
  
    + Les arguments *RNGseed* et *RNGkind* peuvent être utilisés pour contrôler la génération de nombres aléatoires. Quand *RNGseed* est défini sur **auto**, un flux de nombres aléatoires parallèle est initialisé sur chaque processus de travail.
  
2. La fonction **rxExec** crée une liste comportant un élément pour chaque exécution. Toutefois, vous ne verrez pas grand-chose se produire tant que la liste n’est pas complète. Lorsque toutes les itérations sont terminées, la ligne commençant par **longueur** retournera une valeur.
  
    Vous pouvez ensuite passer à l’étape suivante pour obtenir un résumé de votre bilan de victoires et de pertes.
  
3. Convertissez la liste renvoyée en vecteur utilisant la fonction **unlist** de R, et résumez les résultats à l’aide de la fonction **table** .
  
    ```R
    table(unlist(sqlServerExec))
    ```
  
    Vos résultats doivent se présenter comme suit :
  
     *Perte Win* *12 8*

## <a name="conclusion"></a>Conclusion

Bien que cet exercice est simpliste, il montre un moyen important pour l’intégration des fonctions R arbitraires dans le script R s’exécutant sur SQL Server. Pour résumer les points clés qui rendent cette technique possible :

+ SQL Server doit être configuré pour l’apprentissage automatique et intégration de R : [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) avec la fonctionnalité R, ou [SQL Server 2016 R Services (en base de données)](../install/sql-r-services-windows-install.md).

+ Les bibliothèques Open source ou tierces utilisées dans votre fonction, y compris toutes les dépendances, doivent être installés sur SQL Server. Pour plus d’informations, consultez [installer de nouveaux packages R](../r/install-additional-r-packages-on-sql-server.md).

+ Déplacement de script à partir d’un environnement de développement vers un environnement de production renforcée peut introduire des restrictions de pare-feu et du réseau. Tester soigneusement pour vous assurer que votre script est en mesure d’effectuer comme prévu.

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir un exemple plus complexe de l’utilisation de **rxExec**, consultez cet article : [Parallélisme de granularité grossière avec foreach et rxExec](https://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)
