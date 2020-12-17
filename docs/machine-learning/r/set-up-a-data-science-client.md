---
title: Configurer un client de science des données R
description: Installez des bibliothèques et outils R locaux sur une station de travail de développement pour les connexions à distance à SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 06/13/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 7f738e20a84c82879361e999ef795825c31bf311
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470770"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Configurer un client de science des données pour le développement R sur SQL Server
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

L’intégration de R est disponible dans SQL Server 2016 (et versions ultérieures) quand vous incluez l’option de langage R dans [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) ou une installation [Machine Learning Services (en base de données)](../install/sql-machine-learning-services-windows-install.md). 

Pour développer et déployer des solutions R pour SQL Server, installez [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) sur votre station de travail de développement pour obtenir [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) ainsi que d’autres bibliothèques R. La bibliothèque RevoScaleR, qui est également requise sur l’instance SQL Server distante, coordonne les demandes de traitement entre les deux systèmes. 

Cet article explique comment configurer une station de travail de développement de client R pour interagir avec une instance SQL Server distante activée pour le Machine Learning et l’intégration de R. Après avoir effectué les étapes décrites dans cet article, vous aurez les mêmes bibliothèques R que celles disponibles sur SQL Server. Vous saurez également comment envoyer (push) les calculs d’une session R locale vers une session R à distance sur SQL Server.

![Composants client-serveur](media/sqlmls-r-client-revo.png "Sessions et bibliothèques R locales et distantes")

Pour valider l’installation, vous pouvez utiliser l’outil **RGUI** intégré comme décrit dans cet article ou [lier les bibliothèques](#install-ide) à RStudio ou à tout autre IDE que vous utilisez généralement.

> [!Note]
> Au lieu d’installer les bibliothèques clientes, vous pouvez également utiliser un [serveur autonome](../install/sql-machine-learning-standalone-windows-install.md) comme client riche, option privilégiée par certains clients pour une utilisation dans des scénarios plus poussés. Un serveur autonome est entièrement découplé de SQL Server. Cependant, comme il possède les mêmes bibliothèques R, vous pouvez l’utiliser comme client pour l’analytique en base de données SQL Server. Vous pouvez également l’utiliser pour les tâches non liées à SQL et notamment pour importer et modéliser des données à partir d’autres plateformes de données. Si vous installez un serveur autonome, vous pouvez trouver l’exécutable R à l’emplacement suivant : `C:\Program Files\Microsoft SQL Server\140\R_SERVER`. Pour valider votre installation, [ouvrez une application console R](#R-tools) afin d’exécuter des commandes à l’aide de R.exe (disponible à cet emplacement).

## <a name="commonly-used-tools"></a>Outils couramment utilisés

Que vous soyez un développeur R qui débute avec SQL ou un développeur SQL qui découvre R et l’analytique en base de données, vous aurez besoin d’un outil de développement R et d’un éditeur de requête T-SQL comme [SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md) pour exploiter toutes les fonctionnalités de l’analytique en base de données.

Pour les scénarios de développement R simples, vous pouvez utiliser l’exécutable RGUI fourni avec la distribution R de base dans MRO et SQL Server. Cet article explique comment utiliser RGUI pour les sessions R locales et distantes. Pour améliorer la productivité, vous devez utiliser un IDE complet, tel que [RStudio ou Visual Studio](#install-ide).

Disponible en téléchargement distinct, SSMS permet de créer et d’exécuter des procédures stockées sur SQL Server, y compris celles contenant du code R. Presque tout le code R que vous écrivez dans un environnement de développement peut être incorporé à une procédure stockée. Vous pouvez consulter d’autres didacticiels pour en savoir plus sur [SSMS et le code R incorporé](../tutorials/r-taxi-classification-introduction.md).

## <a name="1---install-r-packages"></a>1 - Installer des packages R

Les packages R de Microsoft sont disponibles dans plusieurs produits et services. Sur une station de travail locale, nous vous recommandons d’installer Microsoft R Client. R Client fournit [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler), [MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package), [SQLRUtils](/machine-learning-server/r-reference/sqlrutils/sqlrutils) et d’autres packages R.

1. [Téléchargez Microsoft R Client](https://aka.ms/rclient/download).

2. Dans l’Assistant Installation, acceptez ou modifiez le chemin d’installation par défaut, acceptez ou modifiez la liste des composants et acceptez les termes du contrat de licence Microsoft R Client.

   Une fois l’installation terminée, un écran de bienvenue vous présente le produit et la documentation.

3. Créez une variable d’environnement MKL_CBWR pour garantir la cohérence de la sortie des calculs d’Intel Math Kernel Library (MKL).

   + Dans le Panneau de configuration, cliquez sur **Système et sécurité** > **Système** > **Paramètres système avancés** > **Variables d’environnement**.
   + Créez une nouvelle variable système nommée **MKL_CBWR**, avec une valeur définie sur **AUTO**.

## <a name="2---locate-executables"></a>2 - Localiser les exécutables

Localisez et listez le contenu du dossier d’installation pour vérifier que R.exe, RGUI et les autres packages sont installés. 

1. Dans l’Explorateur de fichiers, ouvrez le dossier C:\Program Files\Microsoft\R Client\R_SERVER\bin pour vérifier l’emplacement de R.exe.

2. Ouvrez le sous-dossier x64 pour vérifier la présence de **RGUI**. Vous allez utiliser cet outil à l’étape suivante.

3. Ouvrez C:\Program Files\Microsoft\R Client\R_SERVER\library pour passer en revue la liste des packages installés avec R Client, y compris RevoScaleR, MicrosoftML et d’autres.


<a name="R-tools"></a>
 
## <a name="3---start-rgui"></a>3 - Démarrer RGUI

Lorsque vous installez R avec SQL Server, vous bénéficiez des mêmes outils R standard pour toutes les installations de base de R, comme RGui, Rterm et ainsi de suite. Ces outils sont légers. Ils sont utiles pour vérifier les informations de package et de bibliothèque, exécuter des commandes ou des scripts ad hoc ou suivre des didacticiels. Vous pouvez utiliser ces outils pour accéder aux informations de version de R et vérifier la connectivité.

1. Ouvrez C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64, puis double-cliquez sur **RGui** pour démarrer une session R à l’aide d’une invite de commandes R.

   Lorsque vous démarrez une session R à partir d’un dossier de programme Microsoft, plusieurs packages, y compris RevoScaleR, se chargent automatiquement. 

2. Entrez `print(Revo.version)` dans l’invite de commandes pour retourner les informations sur la version du package RevoScaleR. Vous devez disposer de la version 9.2.1 ou 9.3.0 pour RevoScaleR.

3. Entrez **search()** dans l’invite R pour obtenir la liste des packages installés.

   ![Informations de version lors du chargement de R](../install/media/rclient-rgui-r-prompt.png "Ouverture d’une invite R")


## <a name="4---get-sql-permissions"></a>4 - Obtenir les autorisations SQL

Dans R Client, le traitement de R est limité à deux threads et aux données en mémoire. Pour un traitement évolutif à l’aide de plusieurs cœurs et jeux de données volumineux, vous pouvez déplacer l’exécution (appelée *contexte de calcul*) vers les jeux de données et la puissance de calcul d’une instance de SQL Server distante. Il s’agit de l’approche recommandée pour l’intégration du client à une instance de SQL Server en production, et vous aurez besoin d’autorisations et d’informations de connexion pour que ça fonctionne.

Pour vous connecter à une instance de SQL Server afin d’exécuter des scripts et de charger des données, vous devez disposer d’un compte de connexion valide sur le serveur de base de données. Vous pouvez utiliser un compte de connexion SQL ou l’authentification Windows intégrée. Nous recommandons généralement d’utiliser l’authentification Windows intégrée. Il est cependant plus simple d’utiliser une connexion SQL dans certains scénarios, en particulier quand votre script contient des chaînes de connexion à des données externes.

Le compte utilisé pour exécuter le code doit disposer au minimum d’une autorisation de lecture à partir des bases de données avec lesquelles vous travaillez et de l’autorisation spéciale EXECUTE ANY EXTERNAL SCRIPT. La plupart des développeurs ont également besoin des autorisations permettant de créer des procédures stockées et d’écrire des données dans des tables contenant des données d’entraînement ou des données notées. 

Demandez à l’administrateur de base de données de [configurer les autorisations suivantes pour votre compte](../security/user-permission.md) dans la base de données dans laquelle vous utilisez R :

+ **EXECUTE ANY EXTERNAL SCRIPT** pour exécuter un script R sur le serveur.
+ Privilèges **db_datareader** pour exécuter les requêtes utilisées pour l’entraînement du modèle.
+ **db_datawriter** pour écrire les données d’entraînement ou les données notées.
+ **db_owner** pour créer des objets tels que des procédures stockées, des tables et des fonctions. 
  Vous avez également besoin de **db_owner** pour créer des exemples de base de données et des bases de données de test. 

Si votre code nécessite des packages qui ne sont pas installés par défaut avec SQL Server, demandez à l’administrateur de base de données de prévoir l’installation des packages avec l’instance. SQL Server est un environnement sécurisé, qui impose des restrictions quant à l’emplacement d’installation des packages. Pour plus d’informations, consultez la page [Install new R packages on SQL Server](../package-management/install-additional-r-packages-on-sql-server.md) (Installer de nouveaux packages R sur SQL Server).

## <a name="5---test-connections"></a>5 - Tester les connexions

En guise d’étape de vérification, utilisez **RGUI** et RevoScaleR pour vérifier la connectivité au serveur distant. SQL Server doit être activé pour les [connexions à distance](../../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md) et vous devez disposer des autorisations requises, y compris des informations de connexion utilisateur et une base de données à laquelle se connecter. 

Les étapes suivantes nécessitent la base de données de démonstration [NYCTaxi_Sample](../tutorials/demo-data-nyctaxi-in-sql.md) et l’authentification Windows.

1. Ouvrez **RGUI** sur la station de travail cliente. Par exemple, accédez à `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` et double-cliquez sur **RGui. exe** pour le démarrer.

2. RevoScaleR se charge automatiquement. Vérifiez que RevoScaleR est opérationnel en exécutant la commande suivante : `print(Revo.version)`

3. Entrez le script de démonstration qui s’exécute sur le serveur distant. Vous devez modifier l’exemple de script suivant pour donner un nom valide à une instance de SQL Server distante. Cette session démarre comme une session locale, mais la fonction **rxSummary** s’exécute sur l’instance de SQL Server distante.

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

   Ce script se connecte à une base de données sur le serveur distant, fournit une requête, crée une instruction `cc` de contexte de calcul pour l’exécution de code à distance, puis fournit la fonction RevoScaleR **rxSummary** pour retourner un résumé statistique des résultats de la requête.

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

4. Obtenez et spécifiez le contexte de calcul. Une fois que vous avez défini un contexte de calcul, il reste actif pendant la durée de la session. Si vous ne savez pas si le calcul s’effectue en local ou à distance, exécutez la commande suivante. Les résultats qui spécifient une chaîne de connexion indiquent un contexte de calcul distant.

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

5. Retournez les informations sur les variables dans la source de données, y compris le nom et le type.

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

   La capture d’écran suivante montre l’entrée et le nuage de points en sortie.

   ![Nuage de points dans RGUI](media/rclient-setup-scatterplot.png "Nuage de points sur les données de démonstration Taxis de New York")

<a name="install-ide"></a>

## <a name="6---link-tools-to-rexe"></a>6 - Lier les outils à R.exe

Pour les projets de développement importants et soutenus, vous devez installer un environnement de développement intégré (IDE). Les outils de SQL Server et les outils intégrés à R ne sont pas équipés pour un développement R lourd. Une fois que vous avez un code fonctionnel, vous pouvez le déployer en tant que procédure stockée pour l’exécuter sur SQL Server.

Faites pointer votre IDE vers les bibliothèques R locales : base R, RevoScaleR, etc. L’exécution de charges de travail sur une instance de SQL Server distante se produit pendant l’exécution du script, quand votre script appelle un contexte de calcul distant sur SQL Server, en accédant aux données et aux opérations de ce serveur.

### <a name="rstudio"></a>RStudio

Lorsque vous utilisez [RStudio](https://www.rstudio.com/), vous pouvez configurer l’environnement pour utiliser les bibliothèques R et les exécutables qui correspondent à celles d’une instance de SQL Server distante.

1. Vérifiez la version des packages R installés sur SQL Server. Pour plus d’informations, consultez la section [Obtenir des informations sur le package R](../package-management/r-package-information.md).

1. Installez Microsoft R Client ou l’une des options de serveur autonome pour ajouter RevoScaleR et d’autres packages R, y compris la distribution R de base utilisée par votre instance de SQL Server. Choisissez une version au même niveau ou d’un niveau inférieur (les packages sont à compatibilité descendante) qui fournit les mêmes versions de package que celles qui se trouvent sur le serveur. Pour plus d’informations sur la version, consultez la carte des versions dans l’article suivant : [Mise à niveau des éléments R et Python](../install/upgrade-r-and-python.md).

1. Dans RStudio, [mettez à jour votre chemin R](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R) pour qu’il pointe vers l’environnement R qui fournit RevoScaleR, Microsoft R Open et d’autres packages Microsoft. 

   + Pour une installation du client R, accédez au dossier C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64
   + Pour un serveur autonome, accédez à C:\Program Files\Microsoft SQL Server\140\R_SERVER\Library ou C:\Program Files\Microsoft SQL Server\130\R_SERVER\Library

1. Fermez, puis ouvrez à nouveau RStudio.

Lorsque vous rouvrez RStudio, l’exécutable R de R Client (ou serveur autonome) est le moteur R par défaut.


### <a name="r-tools-for-visual-studio-rtvs"></a>Outils R pour Visual Studio (RTVS)

Si vous ne disposez pas déjà d’un IDE dédié à R, nous vous recommandons **Outils R pour Visual Studio**.

+ [Télécharger Outils R pour Visual Studio (RTVS)](https://marketplace.visualstudio.com/items?itemName=MikhailArkhipov007.RTVS2019)
+ [Instructions d’installation](/visualstudio/rtvs/installing-r-tools-for-visual-studio) - RTVS est disponible dans plusieurs versions de Visual Studio.
+ [Prise en main d’Outils R pour Visual Studio](/visualstudio/rtvs/getting-started-with-r)

### <a name="connect-to-sql-server-from-rtvs"></a>Connexion à SQL Server depuis RTVS

Cet exemple utilise Visual Studio 2017 Community Edition, avec la charge de travail de science des données installée.

1. Dans le menu **File** (Fichier), sélectionnez **New** (Nouveau), puis **Project** (Projet).

2. Le volet gauche contient une liste de modèles préinstallés. Cliquez sur **R** et sélectionnez **R Project** (Projet R). Dans la zone **Name** (Nom), entrez `dbtest` et cliquez sur **OK**. 

   Visual Studio crée un dossier de projet et un fichier de script par défaut, `Script.R`. 

3. Entrez `.libPaths()` sur la première ligne du fichier de script, puis appuyez sur CTRL + ENTRÉE.

   Le chemin d’accès à la bibliothèque R actuelle doit s’afficher dans la **fenêtre interactive R**. 

4. Cliquez sur le menu **R Tools** (Outils R) et sélectionnez **Windows** (Fenêtres) pour afficher la liste des autres fenêtres spécifiques à R que vous pouvez afficher dans votre espace de travail.
 
   + Affichez l’aide sur les packages dans la bibliothèque actuelle en appuyant sur CTRL + 3.
   + Pour afficher les variables R dans l’**Explorateur de variables**, appuyez sur CTRL + 8.

## <a name="next-steps"></a>Étapes suivantes

Deux didacticiels différents incluent des exercices qui vous permettent de transmettre le contexte de calcul entre une instance de SQL Server locale et distante.

+ [Tutoriel : Utilisation des fonctions R de RevoScaleR avec les données SQL Server](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [Procédure pas à pas pour une solution complète de science des données](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)