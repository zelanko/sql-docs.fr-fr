---
title: Exécuter des fonctions R personnalisées sur SQL Server à l’aide de RevoScaleR rxExec
description: Didacticiel pas à pas sur la façon d’exécuter un script R personnalisé sur SQL Server à l’aide des fonctions RevoScaleR.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: d90e2d4887154d3545884a77d0290e632f04a569
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470597"
---
# <a name="run-custom-r-functions-on-sql-server-using-rxexec"></a>Exécuter des fonctions R personnalisées sur SQL Server à l’aide de rxExec
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Vous pouvez exécuter des fonctions R personnalisées dans le contexte d’SQL Server en passant votre fonction via [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec), en supposant que toutes les bibliothèques requises par votre script sont également installées sur le serveur et que ces bibliothèques sont compatibles avec la distribution de base de R. 

La fonction **rxExec** dans **RevoScaleR** fournit un mécanisme permettant d’exécuter n’importe quel script R dont vous avez besoin. En outre, **rxExec** est en mesure de distribuer explicitement le travail entre plusieurs cœurs sur un seul serveur, en ajoutant une mise à l’échelle aux scripts qui sont autrement limités aux contraintes de ressources du moteur R natif.

Dans ce didacticiel, vous allez utiliser des données simulées pour illustrer l’exécution d’une fonction R personnalisée qui s’exécute sur un serveur distant.

## <a name="prerequisites"></a>Prérequis

+ [SQL Server 2017 machine learning services (avec R)](../install/sql-machine-learning-services-windows-install.md) ou [SQL Servers 2016 r services (en base de données)](../install/sql-r-services-windows-install.md)
  
+ [Autorisations de base de](../security/user-permission.md) données et connexion utilisateur de base de données SQL Server

+ [Une station de travail de développement avec les bibliothèques RevoScaleR](../r/set-up-a-data-science-client.md)

La distribution R sur la station de travail cliente fournit un outil **RGUI** intégré que vous pouvez utiliser pour exécuter le script R dans ce didacticiel. Vous pouvez également utiliser un IDE tel que RStudio ou Outils R pour Visual Studio.

## <a name="create-the-remote-compute-context"></a>Créer le contexte de calcul distant

Exécutez les commandes R suivantes sur une station de travail cliente. Par exemple, vous utilisez **RGUI**, démarrez-le à partir de cet emplacement: C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64\.

1. Spécifiez la chaîne de connexion pour l’instance de SQL Server dans laquelle les calculs sont effectués. Le serveur doit être configuré pour l’intégration R. Le nom de la base de données n’est pas utilisé dans cet exercice, mais la chaîne de connexion en requiert une. Si vous disposez d’un test ou d’un exemple de base de données, vous pouvez l’utiliser.

    **Utilisation d’une connexion SQL**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL-Server-instance-name>; Database=<database-name>;Uid=<SQL-user-name>;Pwd=<password>"
    ```

    **Avec l’authentification Windows**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL-Server-instance-name>;Database=<database-name>;Trusted_Connection=True"
    ```

2. Créez un contexte de calcul distant pour l’instance SQL Server référencée dans la chaîne de connexion.

    ```R
    sqlCompute <- RxInSqlServer(connectionString = sqlConnString)
    ```

3. Activez le contexte de calcul, puis retournez la définition de l’objet en tant qu’étape de confirmation. Vous devez voir les propriétés de l’objet de contexte de calcul.

    ```R
    rxSetComputeContext(sqlCompute)
    rxGetComputeContext()
    ```

## <a name="create-the-custom-function"></a>Créer la fonction personnalisée

Dans cet exercice, vous allez créer une fonction R personnalisée qui simule un casino courant consistant à rouler une paire de dés. Les règles du jeu déterminent un résultat de réussite ou de perte:

+ En reportant 7 ou 11 sur votre rouleau initial, vous gagnez.
+ Le Roll 2, 3 ou 12, vous perdez.
+ Si vous avez 4, 5, 6, 8, 9 ou 10, ce nombre devient votre point, et vous continuez à rouler jusqu’à ce que vous reportiez à nouveau votre point (auquel cas vous gagnez) ou que vous remontez un 7, auquel cas vous perdez.

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
  
2.  Simulez un seul jeu de dés en exécutant la fonction.
  
    ```R
    rollDice()
    ```
  
    Avez-vous gagné ou perdu ?
  
Maintenant que vous avez un script opérationnel, voyons comment vous pouvez utiliser **rxExec** pour exécuter la fonction plusieurs fois afin de créer une simulation qui permet de déterminer la probabilité d’une victoire.

## <a name="pass-rolldice-in-rxexec"></a>Pass rollDice () dans rxExec

Pour exécuter une fonction arbitraire dans le contexte d’un SQL Server distant, appelez la fonction **rxExec** .

1. Appelez la fonction personnalisée comme argument de **rxExec**, ainsi que d’autres paramètres qui modifient la simulation.
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    + Utilisez l’argument *timesToRun* pour indiquer le nombre d’exécutions de la fonction.  Dans ce cas, vous lancez les dés 20 fois.
  
    + Les arguments *RNGseed* et *RNGkind* peuvent être utilisés pour contrôler la génération de nombres aléatoires. Quand *RNGseed* est défini sur **auto**, un flux de nombres aléatoires parallèle est initialisé sur chaque processus de travail.
  
2. La fonction **rxExec** crée une liste comportant un élément pour chaque exécution. Toutefois, vous ne verrez pas grand-chose se produire tant que la liste n’est pas complète. Lorsque toutes les itérations sont terminées, la ligne qui commence par **Length** retourne une valeur.
  
    Vous pouvez ensuite passer à l’étape suivante pour obtenir un résumé de votre bilan de victoires et de pertes.
  
3. Convertissez la liste renvoyée en vecteur utilisant la fonction **unlist** de R, et résumez les résultats à l’aide de la fonction **table** .
  
    ```R
    table(unlist(sqlServerExec))
    ```
  
    Vos résultats doivent se présenter comme suit :
  
     *Perte de victoire* *12 8*

## <a name="conclusion"></a>Conclusion

Bien que cet exercice soit simple, il montre un mécanisme important pour l’intégration de fonctions R arbitraires dans le script R exécuté sur SQL Server. Pour résumer les points clés qui rendent cette technique possible:

+ SQL Server devez être configuré pour l’intégration de Machine Learning et de R: [SQL Server 2017 machine learning services](../install/sql-machine-learning-services-windows-install.md) avec la fonctionnalité r ou [SQL Server 2016 r services (en base de données)](../install/sql-r-services-windows-install.md).

+ Les bibliothèques Open source ou tierces utilisées dans votre fonction, y compris les dépendances, doivent être installées sur SQL Server. Pour plus d’informations, consultez [installer de nouveaux packages R](../r/install-additional-r-packages-on-sql-server.md).

+ Le déplacement du script d’un environnement de développement vers un environnement de production renforcé peut introduire des restrictions de pare-feu et de réseau. Testez soigneusement pour vous assurer que votre script peut s’exécuter comme prévu.

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir un exemple plus complexe de l’utilisation de **rxExec**, consultez cet article: [Parallélisme de grain grossier avec foreach et rxExec](https://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)
