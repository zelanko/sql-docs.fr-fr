---
title: Configurer un client de science des données pour le développement R
description: Installez les bibliothèques et les outils R locaux sur une station de travail de développement pour les connexions à distance à SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7c81a69181d1bc723e622bac9ffeb5ff67fd0280
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69633637"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Configurer un client de science des données pour le développement R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

L’intégration de r est disponible dans SQL Server 2016 ou ultérieur lorsque vous incluez l’option de langage R dans une installation [SQL Server 2016 R services](../install/sql-r-services-windows-install.md) ou [SQL Server machine learning services (en base de données)](../install/sql-machine-learning-services-windows-install.md) . 

Pour développer et déployer des solutions R pour SQL Server, installez [Microsoft R client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) sur votre station de travail de développement pour obtenir [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) et d’autres bibliothèques r. La bibliothèque RevoScaleR, qui est également requise sur l’instance de SQL Server distante, coordonne les demandes de calcul entre les deux systèmes. 

Dans cet article, Découvrez comment configurer une station de travail de développement R client pour pouvoir interagir avec une SQL Server distante activée pour l’intégration de Machine Learning et de R. Après avoir effectué les étapes de cet article, vous aurez les mêmes bibliothèques R que celles sur SQL Server. Vous saurez également comment effectuer un push des calculs d’une session R locale vers une session R distante sur SQL Server.

![Composants client-serveur](media/sqlmls-r-client-revo.png "Sessions et bibliothèques R locales et") distantes

Pour valider l’installation, vous pouvez utiliser l’outil **RGUI** intégré, tel que décrit dans cet article, ou [lier les bibliothèques](#install-ide) à RStudio ou à tout autre IDE que vous utilisez normalement.

> [!Note]
> Une alternative à l’installation de la bibliothèque cliente consiste à utiliser un [serveur autonome](../install/sql-machine-learning-standalone-windows-install.md) comme client riche, que certains clients préfèrent pour un travail de scénario plus approfondi. Un serveur autonome est entièrement découplé de SQL Server, mais étant donné qu’il a les mêmes bibliothèques R, vous pouvez l’utiliser en tant que client pour SQL Server analytique dans la base de données. Vous pouvez également l’utiliser pour du travail non lié à SQL, y compris la possibilité d’importer et de modéliser des données à partir d’autres plateformes de données. Si vous installez un serveur autonome, vous pouvez trouver l’exécutable R à l’emplacement suivant: `C:\Program Files\Microsoft SQL Server\140\R_SERVER`. Pour valider votre installation, [ouvrez une application console r](#R-tools) pour exécuter des commandes à l’aide de r. exe à cet emplacement.

## <a name="commonly-used-tools"></a>Outils couramment utilisés

Que vous soyez un développeur R nouveau dans SQL ou un développeur SQL nouveau dans R et une analytique en base de données, vous aurez besoin à la fois d’un outil de développement R et d’un éditeur de requête T-SQL comme [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) pour exercer toutes les fonctionnalités de dans la base de données. analyse.

Pour les scénarios de développement R simples, vous pouvez utiliser l’exécutable RGUI, fourni avec la distribution R de base dans MRO et SQL Server. Cet article explique comment utiliser l’RGUI pour les sessions R locales et à distance. Pour améliorer la productivité, vous devez utiliser un environnement de développement intégré (IDE) complet, tel que [RStudio ou Visual Studio](#install-ide).

SSMS est un téléchargement distinct, utile pour créer et exécuter des procédures stockées sur SQL Server, y compris celles contenant du code R. Presque tout code R que vous écrivez dans un environnement de développement peut être incorporé dans une procédure stockée. Vous pouvez parcourir d’autres didacticiels pour en savoir plus sur [SSMS et Embedded R](../tutorials/sqldev-in-database-r-for-sql-developers.md).

## <a name="1---install-r-packages"></a>1-installer les packages R

Les packages R de Microsoft sont disponibles dans plusieurs produits et services. Sur une station de travail locale, nous vous recommandons d’installer Microsoft R Client. R client fournit [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler), [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package), [SQLRUtils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)et d’autres packages R.

1. [Téléchargez Microsoft R client](https://aka.ms/rclient/download).

2. Dans l’Assistant Installation, acceptez ou modifiez le chemin d’installation par défaut, acceptez ou modifiez la liste des composants et acceptez les termes du contrat de licence Microsoft R Client.

  Une fois l’installation terminée, un écran de bienvenue vous présente le produit et la documentation.

3. Créez une variable d’environnement système MKL_CBWR pour garantir une sortie cohérente sur les calculs d’Intel Math Kernel Library (MKL).

  + Dans le panneau de configuration, cliquez sur système **et sécurité** >  > **paramètres** > système avancés**variables d’environnement**.
  + Créez une variable système nommée **MKL_CBWR**, avec une valeur définie sur **auto**.

## <a name="2---locate-executables"></a>2-localiser les exécutables

Localisez et répertoriez le contenu du dossier d’installation pour confirmer que R. exe, RGUI et d’autres packages sont installés. 

1. Dans l’Explorateur de fichiers, ouvrez le dossier C:\Program Files\Microsoft\R Client\R_SERVER\bin pour confirmer l’emplacement de R. exe.

2. Ouvrez le sous-dossier x64 pour confirmer l' **RGUI**. Vous allez utiliser cet outil à l’étape suivante.

3. Ouvrez C:\Program Files\Microsoft\R Client\R_SERVER\library pour passer en revue la liste des packages installés avec R client, y compris RevoScaleR, MicrosoftML et d’autres.


<a name="R-tools"></a>
 
## <a name="3---start-rgui"></a>3-démarrer RGUI

Lorsque vous installez R avec SQL Server, vous bénéficiez des mêmes outils R standard pour toute installation de base de R, tels que RGui, Rterm et ainsi de suite. Ces outils sont légers et utiles pour vérifier les informations de package et de bibliothèque, exécuter des commandes ou des scripts ad hoc ou exécuter pas à pas les didacticiels. Vous pouvez utiliser ces outils pour accéder aux informations de version de R et vérifier la connectivité.

1. Ouvrez C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64, puis double-cliquez sur **RGui** pour démarrer une session r à l’aide d’une invite de commandes r.

  Lorsque vous démarrez une session R à partir d’un dossier de programme Microsoft, plusieurs packages, y compris RevoScaleR, se chargent automatiquement. 

2. Entrez `print(Revo.version)` à l’invite de commandes pour retourner les informations de version du package RevoScaleR. Vous devez disposer de la version 9.2.1 ou 9.3.0 pour RevoScaleR.

3. Entrez **Search ()** à l’invite R pour obtenir la liste des packages installés.

   ![Informations de version lors du chargement de R](../install/media/rclient-rgui-r-prompt.png "Ouvrir une invite R")


## <a name="4---get-sql-permissions"></a>4-récupérer les autorisations SQL

Dans R client, le traitement R est limité à deux threads et à des données en mémoire. Pour un traitement évolutif à l’aide de plusieurs cœurs et de jeux de données volumineux, vous pouvez déplacer l’exécution (appelée « *contexte de calcul*») vers les jeux de données et la puissance de calcul d’une instance de SQL Server distante. Il s’agit de l’approche recommandée pour l’intégration du client à une instance de SQL Server de production, et vous aurez besoin d’autorisations et d’informations de connexion pour le faire fonctionner.

Pour vous connecter à une instance de SQL Server pour exécuter des scripts et charger des données, vous devez disposer d’une connexion valide sur le serveur de base de données. Vous pouvez utiliser un compte de connexion SQL ou l’authentification Windows intégrée. Nous vous recommandons généralement d’utiliser l’authentification intégrée de Windows, mais l’utilisation de la connexion SQL est plus simple pour certains scénarios, en particulier lorsque votre script contient des chaînes de connexion à des données externes.

Au minimum, le compte utilisé pour exécuter le code doit avoir l’autorisation de lire dans les bases de données avec lesquelles vous travaillez, et l’autorisation spéciale exécuter n’importe quel SCRIPT externe. La plupart des développeurs requièrent également des autorisations pour créer des procédures stockées et écrire des données dans des tables contenant des données d’apprentissage ou des données notées. 

Demandez à l’administrateur de base de données de [configurer les autorisations suivantes pour votre compte](../security/user-permission.md), dans la base de données où vous utilisez R:

+ **Exécutez un script externe** pour exécuter le script R sur le serveur.
+ privilèges **db_datareader** pour exécuter les requêtes utilisées pour l’apprentissage du modèle.
+ **db_datawriter** pour écrire des données d’apprentissage ou des données notées.
+ **db_owner** pour créer des objets tels que des procédures stockées, des tables et des fonctions. 
  Vous avez également besoin de **db_owner** pour créer des exemples et des bases de données de test. 

Si votre code nécessite des packages qui ne sont pas installés par défaut avec SQL Server, contactez l’administrateur de base de données pour que les packages soient installés avec l’instance. SQL Server est un environnement sécurisé et il existe des restrictions sur l’emplacement d’installation des packages. Pour plus d’informations, consultez [installer de nouveaux packages R sur SQL Server](install-additional-r-packages-on-sql-server.md).

## <a name="5---test-connections"></a>5-tester les connexions

 En guise d’étape de vérification, utilisez **RGUI** et RevoScaleR pour vérifier la connectivité au serveur distant. SQL Server doit être activé pour les [connexions à distance](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server) et vous devez disposer d’autorisations, y compris une connexion utilisateur et une base de données à laquelle se connecter. 

Les étapes suivantes supposent la base de données de démonstration, [NYCTaxi_Sample](../tutorials/demo-data-nyctaxi-in-sql.md)et l’authentification Windows.

1. Ouvrez **RGUI** sur la station de travail cliente. Par exemple, accédez à `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` , puis double-cliquez sur **RGui. exe** pour le démarrer.

2. RevoScaleR se charge automatiquement. Vérifiez que RevoScaleR est opérationnel en exécutant la commande suivante:`print(Revo.version)`

3. Entrez le script de démonstration qui s’exécute sur le serveur distant. Vous devez modifier l’exemple de script suivant pour inclure un nom valide pour une instance de SQL Server distante. Cette session démarre en tant que session locale, mais la fonction **rxSummary** s’exécute sur l’instance SQL Server distante.

  ```R
  # Define a connection. Replace server with a valid server name.
  connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
  
  # Specify the input data in a SQL query.
  sampleQuery <-"SELECT DISTINCT TOP(100) tip_amount FROM [dbo].nyctaxi_sample ORDER BY tip_amount DESC;"
  
  # Define a remote compute context based on the remote server.
  cc <-RxInSqlServer(connectionString=connStr)

  # Execute the function using the remote compute context.
  rxSummary(formula = ~ ., data = RxSqlServerData(sqlQuery=sampleQuery, connectionString=connStr), computeContext=cc)
  ```

  **Résultats :**

  Ce script se connecte à une base de données sur le serveur distant, fournit une requête, crée `cc` une instruction de contexte de calcul pour l’exécution de code à distance, puis fournit la fonction RevoScaleR **rxSummary** pour retourner un résumé statistique de la requête. about.

  ```R
    Call:
  rxSummary(formula = ~., data = RxSqlServerData(sqlQuery = sampleQuery, 
      connectionString = connStr), computeContext = cc)

  Summary Statistics Results for: ~.
  Data: RxSqlServerData(sqlQuery = sampleQuery, connectionString = connStr) (RxSqlServerData Data Source)
  Number of valid observations: 100 
  
  Name       Mean   StdDev   Min Max ValidObs MissingObs
  tip_amount 63.245 31.61087 36  180 100      0     
  ```

4. Obtient et définit le contexte de calcul. Une fois que vous avez défini un contexte de calcul, il reste en vigueur pendant la durée de la session. Si vous ne savez pas si le calcul est local ou distant, exécutez la commande suivante pour le savoir. Les résultats qui spécifient une chaîne de connexion indiquent un contexte de calcul distant.

  ```R
  # Return the current compute context.
  rxGetComputeContext()

  # Revert to a local compute context.
  rxSetComputeContext("local")
  rxGetComputeContext()

  # Switch back to remote.
  connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
  cc <-RxInSqlServer(connectionString=connStr)
  rxSetComputeContext(cc)
  rxGetComputeContext()
  ```  

5. Retourne des informations sur les variables dans la source de données, y compris le nom et le type.

  ```R
  rxGetVarInfo(data = inDataSource)
  ```
  Les résultats incluent 23 variables.


6. Générez un nuage de points pour déterminer s’il existe des dépendances entre deux variables. 

  ```R
  # Set the connection string. Substitute a valid server name for the placeholder.
  connStr <- "Driver=SQL Server;Server=<your database name>;Database=NYCTaxi_Sample;Trusted_Connection=true"

  # Specify a query on the nyctaxi_sample table.
  # For variables on each axis, remove nulls. Use a WHERE clause and <> to do this.
  sampleQuery <-"SELECT DISTINCT TOP 100 * from [dbo].[nyctaxi_sample] WHERE fare_amount <> '' AND  tip_amount <> ''"
  cc <-RxInSqlServer(connectionString=connStr)

  # Generate a scatter plot.
  rxLinePlot(fare_amount ~ tip_amount, data = RxSqlServerData(sqlQuery=sampleQuery, connectionString=connStr, computeContext=cc), type="p")
  ```

  La capture d’écran suivante montre la sortie du nuage d’entrée et du nuage de points.

   ![Nuage de points dans RGUI](media/rclient-setup-scatterplot.png "Nuage de points sur les données de démonstration du taxi de New") York

<a name="install-ide"></a>

## <a name="6---link-tools-to-rexe"></a>6-lier les outils à R. exe

Pour les projets de développement importants et prolongés, vous devez installer un environnement de développement intégré (IDE). Les outils de SQL Server et les outils R intégrés ne sont pas équipés pour un développement R lourd. Une fois que vous avez du code fonctionnel, vous pouvez le déployer en tant que procédure stockée pour l’exécuter sur SQL Server.

Pointez votre IDE vers les bibliothèques R locales: base R, RevoScaleR, et ainsi de suite. L’exécution de charges de travail sur un SQL Server distant se produit pendant l’exécution du script, lorsque votre script appelle un contexte de calcul distant sur SQL Server, en accédant aux données et aux opérations sur ce serveur.

### <a name="rstudio"></a>RStudio

Lorsque vous utilisez [RStudio](https://www.rstudio.com/), vous pouvez configurer l’environnement pour utiliser les bibliothèques R et les exécutables qui correspondent à ceux d’une SQL Server distante.

1. Vérifiez que les versions de package R sont installées sur SQL Server. Pour plus d’informations, consultez [obtenir des informations sur les packages R](../package-management/r-package-information.md).

1. Installez Microsoft R Client ou l’une des options de serveur autonomes pour ajouter RevoScaleR et d’autres packages R, y compris la distribution R de base utilisée par votre instance de SQL Server. Choisissez une version au même niveau ou moins (les packages sont à compatibilité descendante) qui fournissent les mêmes versions de package que sur le serveur. Pour plus d’informations sur la version, consultez la carte des versions dans cet article: [Mettez à niveau les composants R et Python](../install/upgrade-r-and-python.md).

1. Dans RStudio, [Mettez à jour votre chemin r](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R) pour qu’il pointe vers l’environnement r fournissant RevoScaleR, Microsoft R Open et d’autres packages Microsoft. 

  + Pour une installation du client R, recherchez C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64
  + Pour un serveur autonome, recherchez C:\Program Files\Microsoft SQL Server\140\R_SERVER\Library ou C:\Program Files\Microsoft SQL Server\130\R_SERVER\Library

2. Fermez, puis ouvrez RStudio.

Lorsque vous rouvrez RStudio, l’exécutable R de R client (ou serveur autonome) est le moteur R par défaut.


### <a name="r-tools-for-visual-studio-rtvs"></a>Outils R pour Visual Studio (RTVS)

Si vous ne disposez pas déjà d’un IDE préféré pour R, nous vous recommandons de **Outils R pour Visual Studio**.

+ [Télécharger Outils R pour Visual Studio (RTVS)](https://visualstudio.microsoft.com/vs/features/rtvs/)
+ [Instructions d’installation](https://docs.microsoft.com/visualstudio/rtvs/installing-r-tools-for-visual-studio) : RTVS est disponible dans plusieurs versions de Visual Studio.
+ [Prise en main de Outils R pour Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r)

### <a name="connect-to-sql-server-from-rtvs"></a>Se connecter à SQL Server à partir de RTVS

Cet exemple utilise l’édition Community de Visual Studio 2017, avec la charge de travail science des données installée.

1. Dans le menu **fichier** , sélectionnez **nouveau** , puis **projet**.

2. Le volet gauche contient une liste de modèles préinstallés. Cliquez sur **r**, puis sélectionnez **projet r**. Dans la zone **nom** , tapez `dbtest` et cliquez sur **OK**. 

  Visual Studio crée un dossier de projet et un fichier de script par `Script.R`défaut,. 

3. Tapez `.libPaths()` sur la première ligne du fichier de script, puis appuyez sur Ctrl + Entrée.

  Le chemin d’accès de la bibliothèque R actuelle doit s’afficher dans la fenêtre de **fenêtre interactive R** . 

4. Cliquez sur le menu **Outils r** et sélectionnez **Windows** pour afficher la liste des autres fenêtres spécifiques à R que vous pouvez afficher dans votre espace de travail.
 
  + Affichez l’aide sur les packages dans la bibliothèque actuelle en appuyant sur CTRL + 3.
  + Consultez variables R dans le **Explorateur de variables**, en appuyant sur Ctrl + 8.

## <a name="next-steps"></a>Étapes suivantes

Deux didacticiels différents incluent des exercices qui vous permettent de passer du contexte de calcul local à une instance de SQL Server distante.

+ [Tutoriel : Utiliser des fonctions R RevoScaleR avec des données SQL Server](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [Procédure pas à pas pour une solution complète de science des données](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)