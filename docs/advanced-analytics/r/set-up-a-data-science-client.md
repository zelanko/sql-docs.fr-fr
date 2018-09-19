---
title: Configurer un client de science des données pour le développement R sur SQL Server | Microsoft Docs
description: Installer les outils et les bibliothèques R locales sur une station de travail de développement pour les connexions à distance à SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 309a78a2195f55a3ec39604b0c2bd385bb06a271
ms.sourcegitcommit: 9d0ff4f3e40db48fc01788684d34719065d159b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44724313"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Configurer un client de science des données pour le développement R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Une fois que vous avez configuré une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour prendre en charge d’apprentissage, vous devez configurer un environnement de développement R capable de se connecter au serveur pour l’exécution à distance et le déploiement.

### <a name="evaluation-and-independent-development"></a>Évaluation et développement indépendant
 
Si vous avez l’édition développeur et un plan pour travailler localement sur le script R que vous voulez déplacer vers SQL Server, vous pouvez passer directement à [installer un IDE](#install-ide) et pointez l’outil sur les bibliothèques R locales utilisés par SQL Server.

> [!Tip]
> Pour une démonstration et une procédure pas à pas vidéo, consultez [exécuter de R et Python à distance dans SQL Server à partir de Jupyter Notebooks ou n’importe quel IDE](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/) ou cela [vidéo YouTube](https://youtu.be/D5erljpJDjE).

## <a name="1---install-r-packages"></a>1 - installer des packages R

Fonctionnalités de R dans les produits Microsoft sont multicouche. Il commence par la distribution R de la base de code source ouvert de Microsoft, mais est ensuite étendu avec des packages spécifiques au produit, tel que [RevoScaleR](revoscaler-overview.md), qui permettent des contextes de calcul distants et l’exécution parallèle de tâches R.

Opérations coordonnées entre un client et le serveur distant nécessitent les deux systèmes comportant les mêmes packages. Pour obtenir une gamme complète de bibliothèques sur une station de travail client, installez un des packages logiciels dans le tableau suivant. 

| Fournisseur de bibliothèque | Utilisation  |
|------------------|--------------------------------|
| [Microsoft R Client](http://aka.ms/rclient/download) |  Ce téléchargement gratuit fournit RevoScaleR, MicrosoftML et autres packages R, mais est limité à deux threads et les données en mémoire. Toutefois, vous pouvez toujours créer des solutions R démarrer localement et déplacer l’exécution (appelé *contexte de calcul*) pour accéder aux données et la puissance de calcul d’une instance distante de SQL Server. Il s’agit de l’approche recommandée pour l’intégration de client avec une instance de SQL Server de production. Pour plus d’informations sur cet outil, consultez [What ' s Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client).|
| Serveurs autonomes | Sous **les fonctionnalités partagées**, le programme d’installation de SQL Server inclut des options d’installation de serveur autonome pour l’apprentissage de SQL Server 2016 R Services et SQL Server 2017. Il s’agit de serveurs complète, entièrement découplées à partir de SQL Server, avec la possibilité de se connecter à et consommer des données à partir de plusieurs plateformes de données. Mais vous pouvez potentiellement utiliser le logiciel dans une capacité d’un client pour accéder aux instance du moteur de base de données SQL Server en cours d’exécution des tâches R et Python. [SQL Server 2017 Machine Learning Server (autonome)](../install/sql-machine-learning-standalone-windows-install.md) a les mêmes bibliothèques comme instance SQL Server 2017 machine learning. [SQL Server 2016 R Server (autonome)](../install/sql-r-standalone-windows-install.md) a les mêmes bibliothèques comme SQL Server 2016 R Services. |


<a name="r-tool"></a>
 
## <a name="2---open-an-r-prompt"></a>2 - ouvrez une invite de R

Lorsque vous installez R avec SQL Server, vous obtenez les mêmes outils R standard pour toute installation de base de R, telle que RGui et Rterm ainsi de suite. Ces outils sont légers et utile pour la vérification des informations de package et de bibliothèque, l’exécution des commandes ad hoc ou un script ou parcourant les didacticiels. Vous pouvez utiliser ces outils pour obtenir des informations de version de R et vérifier la connectivité.

Pour utiliser la version de R installé avec SQL Server ou de R Client, ouvrez une invite de R à partir du dossier de programme SQL Server ou de R Client. Les étapes suivantes sont pour R Client et RGui.exe.

1. Pour R Client, accédez à `~\Program Files\Microsoft\R Client\R_SERVER\bin\x64`.
2. Double-cliquez sur **RGui.exe** pour démarrer une session de R avec une invite de commandes R.

Lorsque vous démarrez une session R à partir d’un dossier de programme Microsoft, plusieurs packages, y compris RevoScaleR, chargent automatiquement. Entrez **search()** à l’invite R à confirmer l’opération.

   ![Informations de version lors du chargement de R](../install/media/rclient-rgui-r-prompt.png "ouvrez une invite de R")

### <a name="tool-list-and-location"></a>Emplacement et la liste d’outils

| Tool | Description | 
|------|-------------|
| **RTerm**: | Un terminal de ligne de commande pour l’exécution de scripts R | 
| **RGui.exe** | Un simple éditeur interactif pour R. Les arguments de ligne de commande sont les mêmes pour RGui.exe et RTerm. |
| **RScript** | Un outil de ligne de commande pour l’exécution de scripts R en mode batch. |

Outils se trouvent dans **bin** dossier de base R en tant que l’installation de SQL Server ou de R Client. Les chemins suivants sont des emplacements valides pour les outils, en fonction de quelle version du produit et la fonctionnalité que vous avez installé :

| Produit Microsoft | Emplacement de l’outil R |
|-------------------|-----------------|
| Microsoft R Client | `~\Program Files\Microsoft\R Client\R_SERVER\bin\x64` |
| Microsoft Machine Learning (R) Server | `~\Program Files\Microsoft\R_SERVER\bin\x64`
| SQL Server 2016 R Services | `~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`|
| SQL Server 2016 R Server autonome | `~\Program Files\Microsoft SQL Server\130\R_SERVER\bin\x64` 
| SQL Server 2017 Services Machine Learning (R) | `~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`|
| Serveur autonome SQL Server 2017 Machine Learning (R) | `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` |

## <a name="3---permissions"></a>3 - autorisations

Pour vous connecter à une instance de SQL Server pour exécuter des scripts et charger des données, vous devez disposer d’une connexion valide sur le serveur de base de données. Vous pouvez utiliser un compte de connexion SQL ou l’authentification Windows intégrée. Nous recommandons généralement que vous utilisez l’authentification intégrée de Windows, mais à l’aide de la connexion SQL est plus simple pour certains scénarios.

Au minimum, le compte utilisé pour exécuter du code doit avoir l’autorisation de lire à partir de bases de données, vous travaillez, ainsi que l’autorisation spéciale exécuter n’importe quel SCRIPT externe. La plupart des développeurs également nécessitent des autorisations pour créer des objets sous la forme de procédures stockées contenant votre script et écrire des données dans des tables contenant des données d’apprentissage ou un score de données. 

Demandez à l’administrateur de base de données pour configurer les autorisations suivantes pour le compte, dans la base de données dans lequel vous utilisez r :

+ **EXECUTE ANY EXTERNAL SCRIPT** d’exécuter R sur le serveur.
+ **db_datareader** des privilèges pour exécuter les requêtes utilisées pour l’apprentissage du modèle.
+ **db_datawriter** pour écrire des données d’apprentissage ou de données au score calculé.
+ **db_owner** pour créer des objets tels que des procédures stockées, tables, de fonctions. 
  Vous devez également **db_owner** pour créer des bases de données exemple et de test. 

Si votre code requiert les packages qui ne sont pas installés par défaut avec SQL Server, organiser avec l’administrateur de base de données pour que les packages installés avec l’instance. SQL Server est un environnement sécurisé et il existe des restrictions sur où les packages peuvent être installés. Installation ad hoc des packages dans le cadre de votre code est déconseillée, même si vous disposez des droits. En outre, toujours avec soin les implications de sécurité avant d’installer de nouveaux packages dans la bibliothèque du serveur.

> [!Tip]
> Si vous n’êtes pas familiarisé avec SQL Server et l’utilisation dans un environnement de développement local, vous pouvez parcourir ce didacticiel pour en savoir plus sur les connexions et définition des autorisations : [approfondie RevoScaleR](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)

## <a name="4---test-connections"></a>4 - tester les connexions

SQL Server doit être activé pour [connexions à distance](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md) et vous devez disposer des autorisations, y compris une connexion d’utilisateur et de se connecter à une base de données. Les étapes suivantes supposent que la base de données de démonstration, [NYCTaxi_Sample](../tutorials/sqldev-download-the-sample-data.md) et l’authentification Windows.

 En guise de vérification, utilisez un outil intégré et un RevoScaleR pour vérifier la connectivité au serveur distant.

1. Commencez par [ouverture d’un outil R](#r-tool) sur la station de travail client. RevoScaleR charge automatiquement. Par exemple, accédez à `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` et double-cliquez sur **RGui.exe** pour le démarrer.

2. Confirmer que revoscaler est opérationnel en exécutant la commande suivante, qui retourne un résumé statistique sur un dataset de démonstration. Vérifiez que vous fournissez un nom de serveur valide pour l’instance du moteur de base de données SQL Server.

```r
connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
testQuery <-"SELECT DISTINCT TOP(100) tip_amount FROM [dbo].nyctaxi_sample ORDER BY tip_amount DESC;"
cc <-RxInSqlServer(connectionString=connStr)
rxSummary(formula = ~ ., data = RxSqlServerData(sqlQuery=testQuery, connectionString=connStr), computeContext=cc)
```
Ce script se connecte à une base de données sur le serveur distant, fournit une requête, crée un contexte de calcul `cc` instruction pour l’exécution de code à distance, puis fournit la fonction RevoScaleR **rxSummary** pour retourner une statistique Résumé des résultats de la requête.

<a name="install-ide"></a>

## <a name="5---install-an-ide"></a>5 - installer un IDE

Pour les projets de développement durable et grave, vous devez installer un environnement de développement intégré (IDE). Outils SQL Server et les outils R intégrés ne sont pas équipés pour le développement R lourd. Une fois que vous avez le code de travail, vous pouvez le déployer comme une procédure stockée pour une exécution sur SQL Server.

Vous devez faire votre IDE pour les bibliothèques R locales : de base R, RevoScaleR et ainsi de suite. Charges de travail en cours d’exécution sur un serveur SQL distant se produit pendant l’exécution du script, lorsque votre script appelle un contexte de calcul à distance sur SQL Server, l’accès aux données et les opérations sur ce serveur.

### <a name="rstudio"></a>RStudio

Lorsque vous utilisez [RStudio](https://www.rstudio.com/), vous pouvez configurer l’environnement pour utiliser les bibliothèques R et les fichiers exécutables qui correspondent à ceux présents sur un serveur SQL distant.

1. Vérifiez les versions de packages R installées sur SQL Server. Pour plus d’informations, consultez [les informations de package R obtenir](determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).

1. Installez Microsoft R Client ou une des options de serveur autonome pour ajouter RevoScaleR et les autres packages R, y compris la distribution R de base utilisée par votre instance de SQL Server. Choisissez une version à la même ou un niveau inférieur (packages sont à compatibilité descendante) qui fournit les mêmes versions de package que celles sur le serveur. Informations de version, voir la version de la carte dans cet article : [les composants de mise à niveau de R et Python](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

1. Dans RStudio, [mettre à jour votre chemin R](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R) pour pointer vers l’environnement R en fournissant RevoScaleR, Microsoft R Open et autres packages de Microsoft. Selon la façon dont vous avez obtenu RevoScaleR et autres bibliothèques, il est probablement l’un des chemins suivants :

  + C:\Program Files\Microsoft SQL Server\130\R_SERVER\Library
  + C:\Program Files\Microsoft SQL Server\140\R_SERVER\Library
  + C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64

### <a name="r-tools-for-visual-studio-rtvs"></a>Outils R pour Visual Studio (RTVS)

Si vous ne disposez pas un IDE préféré pour R, nous vous recommandons de **outils R pour Visual Studio**.

+ [Télécharger R Tools pour Visual Studio (RTVS)](https://visualstudio.microsoft.com/vs/features/rtvs/)
+ [Instructions d’installation](https://docs.microsoft.com/visualstudio/rtvs/installing-r-tools-for-visual-studio) -RTVS est disponible dans plusieurs versions de Visual Studio.
+ [Bien démarrer avec outils R pour Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r)

### <a name="connect-to-sql-server-from-rtvs"></a>Se connecter à SQL Server à partir de RTVS

Cet exemple utilise Visual Studio 2017 Community Edition, avec la charge de travail de science des données installée.

1. À partir de la **fichier** menu, sélectionnez **New** , puis sélectionnez **projet**.

2. Le volet gauche contient une liste de modèles préinstallés. Cliquez sur **R**, puis sélectionnez **projet R**. Dans le **nom** , tapez `dbtest` et cliquez sur **OK**. 

  Visual Studio crée un nouveau dossier de projet et un fichier de script par défaut, `Script.R`. 

3. Type `.libPaths()` sur la première ligne du script de fichier, puis appuyez sur CTRL + ENTRÉE.

  Le chemin d’accès de bibliothèque R actuel doit être affiché dans le **Interactive R** fenêtre. 

4. Cliquez sur le **outils R** menu et sélectionnez **Windows** pour afficher une liste des autres fenêtres propres à R que vous pouvez afficher dans votre espace de travail.
 
    + Afficher l’aide sur les packages dans la bibliothèque en cours en appuyant sur CTRL + 3.
    + Consultez des variables R dans le **Explorateur de variables**, en appuyant sur CTRL + 8.

5. Créer une chaîne de connexion à une instance de SQL Server et utiliser la chaîne de connexion dans le constructeur RxInSqlServer pour créer un objet de source de données SQL Server. 

    ```r
    connStr <- "Driver=SQL Server;Server=MyServer;Database=MyTestDB;Uid=;Pwd="
    sqlShareDir <- paste("C:\\AllShare\\", Sys.getenv("USERNAME"), sep = "")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    cc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    sampleDataQuery <- "SELECT TOP 100 * from [dbo].[MyTestTable]"
    inDataSource <- RxSqlServerData(sqlQuery = sampleDataQuery, connectionString = connStr, rowsPerRead = 500)
    ```
    > [!TIP]
    > Pour exécuter un lot, sélectionnez les lignes que vous voulez exécuter et appuyez sur CTRL + ENTRÉE.

6. Définissez le contexte de calcul sur le serveur et puis exécuter du code R simples sur les données.

    ```r
    rxSetComputeContext(cc)
    rxGetVarInfo(data = inDataSource)
    ```

    Résultats sont retournés dans le **Interactive R** fenêtre.
    
    Si vous souhaitez vous assurer que le code est en cours d’exécution sur l’instance de SQL Server, vous pouvez utiliser Profiler pour créer une trace.

## <a name="next-steps"></a>Étapes suivantes

Deux didacticiels différents incluent des exercices afin que vous pouvez vous entraîner le basculement du contexte de calcul local à une instance distante de SQL Server.

+ [Didacticiel : Les fonctions utilisent RevoScaleR R avec des données SQL Server](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [Procédure pas à pas pour une solution complète de science des données](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)