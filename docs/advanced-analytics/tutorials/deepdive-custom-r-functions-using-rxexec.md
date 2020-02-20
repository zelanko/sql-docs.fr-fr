---
title: Fonctions R personnalisées utilisant rxExec
description: 'Tutoriel RevoScaleR 14 : Comment exécuter des scripts R personnalisés sur SQL Server à l’aide des fonctions RevoScaleR.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 15e8eb433ac10c5f187b7483f55ccf47ae74220a
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76910552"
---
# <a name="run-custom-r-functions-on-sql-server-using-rxexec-sql-server-and-revoscaler-tutorial"></a>Exécuter des fonctions R personnalisées sur SQL Server à l’aide de rxExec (turotiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Il s’agit du tutoriel 14 sur la [série de tutoriels RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) qui traite de l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans ce tutoriel, vous allez utiliser des données simulées pour illustrer l’exécution d’une fonction R personnalisée qui s’exécute sur un serveur distant.

Vous pouvez exécuter des fonctions R personnalisées dans le contexte de SQL Server en passant votre fonction via [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec), en supposant que toutes les bibliothèques requises par votre script sont également installées sur le serveur et que ces bibliothèques sont compatibles avec la distribution de base de R. 

La fonction **rxExec** dans **RevoScaleR** fournit un mécanisme permettant d’exécuter n’importe quel script R requis. En outre, **rxExec** peut répartir explicitement le travail entre plusieurs cœurs sur un seul serveur, en ajoutant une mise à l’échelle aux scripts qui sont sinon limités aux contraintes de ressources du moteur R natif.

## <a name="prerequisites"></a>Conditions préalables requises

+ [SQL Server Machine Learning Services (avec R)](../install/sql-machine-learning-services-windows-install.md) ou [SQL Server 2016 R Services (dans la base de données)](../install/sql-r-services-windows-install.md)
  
+ [Autorisations de base de données](../security/user-permission.md) et une connexion d’utilisateur de base de données SQL Server

+ [Une station de travail de développement avec les bibliothèques RevoScaleR](../r/set-up-a-data-science-client.md)

La distribution R sur la station de travail cliente fournit un outil **Rgui** intégré que vous pouvez utiliser pour exécuter le script R dans ce tutoriel. Vous pouvez également utiliser un IDE tel que RStudio ou Outils R pour Visual Studio.

## <a name="create-the-remote-compute-context"></a>Créer le contexte de calcul distant

Exécutez les commandes R suivantes sur une station de travail cliente. Par exemple, vous utilisez **Rgui**, démarrez-le à partir de cet emplacement : C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64\.

1. Spécifiez la chaîne de connexion pour l’instance SQL Server dans laquelle ont lieu les calculs. Le serveur doit être configuré pour l’intégration de R. Le nom de la base de données n’est pas utilisé dans cet exercice, bien que la chaîne de connexion en requière un. Si vous disposez d’un exemple de base de données ou d’une base de données test, vous pouvez l’utiliser.

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

3. Activez le contexte de calcul, puis renvoyez la définition de l’objet comme étape de confirmation. Vous devez voir les propriétés de l’objet de contexte de calcul.

    ```R
    rxSetComputeContext(sqlCompute)
    rxGetComputeContext()
    ```

## <a name="create-the-custom-function"></a>Créer la fonction personnalisée

Dans cet exercice, vous allez créer une fonction R personnalisée qui simule un jeu de casino courant consistant à lancer une paire de dés. Les règles du jeu déterminent la réussite ou l’échec :

+ Si vous obtenez 7 ou 11 au premier lancer, vous gagnez.
+ Si vous obtenez 2, 3 ou 12, vous perdez.
+ Si vous obtenez 4, 5, 6, 8, 9 ou 10, ce nombre devient votre référence et vous continuez à lancer les dés jusqu’à ce que vous que retombiez sur cette référence (lancer gagnant) ou que vous obteniez 7 (lancer perdant).

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
  
2.  Simulez un jeu de dés unique en exécutant la fonction.
  
    ```R
    rollDice()
    ```
  
    Avez-vous gagné ou perdu ?
  
Maintenant que votre script est opérationnel, nous allons voir comment vous pouvez utiliser **rxExec** pour exécuter la fonction à plusieurs reprises, pour créer une simulation qui permet de déterminer la probabilité d’une victoire.

## <a name="pass-rolldice-in-rxexec"></a>Passer rollDice() dans rxExec

Pour exécuter une fonction arbitraire dans le contexte d’un serveur SQL Server distant appelez la fonction **rxExec**.

1. Appelez la fonction personnalisée comme argument de **rxExec**, ainsi que d’autres paramètres qui modifient la simulation.
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    + Utilisez l’argument *timesToRun* pour indiquer le nombre d’exécutions de la fonction.  Dans ce cas, vous lancez les dés 20 fois.
  
    + Les arguments *RNGseed* et *RNGkind* peuvent être utilisés pour contrôler la génération de nombres aléatoires. Quand *RNGseed* est défini sur **auto**, un flux de nombres aléatoires parallèle est initialisé sur chaque processus de travail.
  
2. La fonction **rxExec** crée une liste comportant un élément pour chaque exécution. Toutefois, vous ne verrez pas grand-chose se produire tant que la liste n’est pas complète. Quand toutes les itérations sont terminées, la ligne commençant par **length** renvoie une valeur.
  
    Vous pouvez ensuite passer à l’étape suivante pour obtenir un résumé de votre bilan de victoires et de pertes.
  
3. Convertissez la liste renvoyée en vecteur utilisant la fonction **unlist** de R, et résumez les résultats à l’aide de la fonction **table** .
  
    ```R
    table(unlist(sqlServerExec))
    ```
  
    Vos résultats doivent se présenter comme suit :
  
     *Loss  Win* *12  8*

## <a name="conclusion"></a>Conclusion

Bien que cet exercice soit simple, il montre un mécanisme important pour l’intégration de fonctions R arbitraires dans le script R exécuté sur SQL Server. Pour résumer les points clés qui rendent cette technique possible :

+ SQL Server devez être configuré pour l’intégration du Machine Learning et de R : [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) avec la fonctionnalité R ou [SQL Server 2016 R Services (dans la base de données)](../install/sql-r-services-windows-install.md).

+ Les bibliothèques Open source ou tierces utilisées dans votre fonction, y compris les dépendances, doivent être installées sur SQL Server. Pour plus d’informations, consultez la page [Install new R packages](../r/install-additional-r-packages-on-sql-server.md) (Installer de nouveaux packages R).

+ Le déplacement du script d’un environnement de développement vers un environnement de production renforcé peut introduire des restrictions de pare-feu et de réseau. Procédez à des tests minutieux pour vous assurer que votre script peut s’exécuter comme prévu.

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir un exemple plus complexe d’utilisation de **rxExec**, consultez cet article : [Parallélisme approximatif avec foreach et rxExec](https://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)
