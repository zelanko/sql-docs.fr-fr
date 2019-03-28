---
title: Configurer un client de science des données pour le développement R - Services de SQL Server Machine Learning
description: Installer les outils et les bibliothèques R locales sur une station de travail de développement pour les connexions à distance à SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 12fefddcc01caeb9705c823a4e7283169dda1cc3
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510436"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Configurer un client de science des données pour le développement R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Intégration de R est disponible dans SQL Server 2016 ou version ultérieure lorsque vous incluez l’option de langage R dans un [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) ou [SQL Server 2017 Machine Learning Services (en base de données)](../install/sql-machine-learning-services-windows-install.md) installation. 

Pour développer et déployer des solutions R pour SQL Server, installez [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) sur votre station de travail de développement pour obtenir [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) et d’autres bibliothèques R. La bibliothèque RevoScaleR, qui est également requis sur l’instance distante de SQL Server, coordonne les demandes entre les deux systèmes informatiques. 

Dans cet article, découvrez comment configurer une station de travail du développement client R afin que vous pouvez interagir avec un serveur SQL distant activé pour l’apprentissage automatique et intégration de R. Après avoir effectué les étapes décrites dans cet article, vous devez les mêmes bibliothèques R que celles sur SQL Server. Vous saurez également comment envoyer des calculs à partir d’une session R locale à une session à distance de R sur SQL Server.

![Composants client-serveur](media/sqlmls-r-client-revo.png "des sessions R locales et distantes et des bibliothèques")

Pour valider l’installation, vous pouvez utiliser intégrée **RGUI** comme décrit dans cet article, l’outil ou [lier les bibliothèques](#install-ide) RStudio ou n’importe quel IDE d’un autre que vous utilisez normalement.

> [!Tip]
> Pour une démonstration vidéo de ces exercices, consultez [exécuter de R et Python à distance dans SQL Server à partir des blocs-notes Jupyter](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/).

> [!Note]
> Une alternative à l’installation de la bibliothèque cliente utilise un [serveur autonome](../install/sql-machine-learning-standalone-windows-install.md) comme client riche, certains clients préfèrent pour le travail de scénario plus approfondie. Un serveur autonome est entièrement dissocié de SQL Server, mais, car il possède les mêmes bibliothèques R, vous pouvez l’utiliser en tant que client pour l’analytique en base de données de SQL Server. Vous pouvez également l’utiliser pour le travail non liés à SQL, y compris la possibilité d’importer et de modéliser des données à partir d’autres plateformes de données. Si vous installez un serveur autonome, vous pouvez trouver l’exécutable de R à cet emplacement : `C:\Program Files\Microsoft SQL Server\140\R_SERVER`. Pour valider votre installation, [ouvrir une application de console R](#R-tools) pour exécuter des commandes à l’aide de la R.exe à cet emplacement.

## <a name="commonly-used-tools"></a>Outils couramment utilisés

Si vous êtes un développeur R SQL ou SQL développeur R et dans la base de données analytique, vous devez à la fois un outil de développement R et un éditeur de requête T-SQL comme [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) pour tester toutes les fonctionnalités de la base de données analytique.

Pour les scénarios de développement R simples, vous pouvez utiliser l’interface RGUI exécutable, regroupés dans la distribution R de base dans MRO et SQL Server. Cet article explique comment utiliser RGUI pour les sessions R locale et distantes. Pour une productivité améliorée, vous devez utiliser un IDE complet, tel que [RStudio ou Visual Studio](#install-ide).

SSMS est un téléchargement distinct, utile pour la création et exécution de procédures stockées sur SQL Server, y compris celles contenant du code R. Presque n’importe quel code R que vous écrivez dans un environnement de développement peut être incorporé dans une procédure stockée. Vous pouvez parcourir d’autres didacticiels pour en savoir plus sur [SSMS et R incorporé](../tutorials/sqldev-in-database-r-for-sql-developers.md).

## <a name="1---install-r-packages"></a>1 - installer des packages R

Les packages R de Microsoft sont disponibles dans plusieurs produits et services. Sur une station de travail locale, nous vous recommandons d’installer Microsoft R Client. R Client fournit [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler), [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package), [SQLRUtils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)et d’autres packages R.

1. [Télécharger Microsoft R Client](https://aka.ms/rclient/download).

2. Dans l’Assistant installation, acceptez ou modifiez le chemin d’installation par défaut, accepter ou modifier la liste des composants et accepter les termes du contrat de licence de Microsoft R Client.

  Lors de l’installation terminée, un écran de bienvenue vous présente le produit et la documentation.

3. Créer une variable d’environnement système MKL_CBWR pour garantir une sortie cohérente sur des calculs d’Intel Math Kernel Library (MKL).

  + Dans le panneau de configuration, cliquez sur **système et sécurité** > **système** > **paramètres système avancés**  >   **Variables d’environnement**.
  + Créer une nouvelle variable système nommée **MKL_CBWR**, avec une valeur définie sur **automatique**.

## <a name="2---locate-executables"></a>2 - localiser des exécutables

Rechercher et répertorier le contenu du dossier d’installation pour confirmer que R.exe, RGUI et autres packages sont installés. 

1. Dans l’Explorateur de fichiers, ouvrez le dossier C:\Program Files\Microsoft\R Client\R_SERVER\bin pour vérifier l’emplacement de R.exe.

2. Sous-dossier Open le x64 pour confirmer **RGUI**. Vous allez utiliser cet outil à l’étape suivante.

3. Ouvrez C:\Program Files\Microsoft\R Client\R_SERVER\library pour passer en revue la liste des packages installés avec R Client, y compris RevoScaleR, MicrosoftML et autres.


<a name="R-tools"></a>
 
## <a name="3---start-rgui"></a>3 - début RGUI

Lorsque vous installez R avec SQL Server, vous obtenez les mêmes outils R standard pour toute installation de base de R, telle que RGui et Rterm ainsi de suite. Ces outils sont légers et utile pour la vérification des informations de package et de bibliothèque, l’exécution des commandes ad hoc ou un script ou parcourant les didacticiels. Vous pouvez utiliser ces outils pour obtenir des informations de version de R et vérifier la connectivité.

1. Ouvrez C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64 et double-cliquez sur **RGui** pour démarrer une session de R avec une invite de commandes R.

  Lorsque vous démarrez une session R à partir d’un dossier de programme Microsoft, plusieurs packages, y compris RevoScaleR, chargent automatiquement. 

2. Entrez `print(Revo.version)` à l’invite de commande pour retourner RevoScaleR les informations de version du package. Vous devez avoir la version 9.2.1 ou 9.3.0 pour RevoScaleR.

3. Entrez **search()** à l’invite R pour obtenir la liste des packages installés.

   ![Informations de version lors du chargement de R](../install/media/rclient-rgui-r-prompt.png "ouvrez une invite de R")


## <a name="4---get-sql-permissions"></a>4 - obtenir les autorisations SQL

Dans R Client, traitement de R est limité à deux threads et les données en mémoire. Traitement évolutif à l’aide de plusieurs cœurs et les jeux de données volumineux, vous pouvez décaler l’exécution (appelé *contexte de calcul*) pour les jeux de données et la puissance de calcul d’une instance distante de SQL Server. C’est l’approche recommandée pour l’intégration de client avec une instance de SQL Server de production, et que vous avez besoin des autorisations et informations de connexion pour qu’il fonctionne.

Pour vous connecter à une instance de SQL Server pour exécuter des scripts et charger des données, vous devez disposer d’une connexion valide sur le serveur de base de données. Vous pouvez utiliser un compte de connexion SQL ou l’authentification Windows intégrée. Nous recommandons généralement que vous utilisez l’authentification intégrée de Windows, mais à l’aide de la connexion SQL est plus simple pour certains scénarios, en particulier lorsque votre script contient les chaînes de connexion à des données externes.

Au minimum, le compte utilisé pour exécuter du code doit avoir l’autorisation de lire à partir de bases de données, vous travaillez, ainsi que l’autorisation spéciale exécuter n’importe quel SCRIPT externe. En outre, la plupart des développeurs nécessitent des autorisations pour créer des procédures stockées et d’écrire des données dans des tables contenant des données d’apprentissage ou notées des données. 

Demandez à l’administrateur de base de données [configurer les autorisations suivantes pour votre compte](../security/user-permission.md), dans la base de données dans lequel vous utilisez r :

+ **EXECUTE ANY EXTERNAL SCRIPT** pour exécuter le script R sur le serveur.
+ **db_datareader** des privilèges pour exécuter les requêtes utilisées pour l’apprentissage du modèle.
+ **db_datawriter** pour écrire des données d’apprentissage ou de données au score calculé.
+ **db_owner** pour créer des objets tels que des procédures stockées, tables, de fonctions. 
  Vous devez également **db_owner** pour créer des bases de données exemple et de test. 

Si votre code requiert les packages qui ne sont pas installés par défaut avec SQL Server, organiser avec l’administrateur de base de données pour que les packages installés avec l’instance. SQL Server est un environnement sécurisé et il existe des restrictions sur où les packages peuvent être installés. Pour plus d’informations, consultez [installer de nouveaux packages R sur SQL Server](install-additional-r-packages-on-sql-server.md).

## <a name="5---test-connections"></a>5 - test des connexions

 En guise de vérification, utilisez **RGUI** et RevoScaleR pour vérifier la connectivité au serveur distant. SQL Server doit être activé pour [connexions à distance](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server) et vous devez disposer des autorisations, y compris une connexion d’utilisateur et de se connecter à une base de données. 

Les étapes suivantes supposent que la base de données de démonstration, [NYCTaxi_Sample](../tutorials/demo-data-nyctaxi-in-sql.md)et l’authentification Windows.

1. Ouvrez **RGUI** sur la station de travail client. Par exemple, accédez à `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` et double-cliquez sur **RGui.exe** pour le démarrer.

2. RevoScaleR charge automatiquement. Confirmer que revoscaler est opérationnel en exécutant la commande suivante : `print(Revo.version)`

3. Entrez le script de démonstration qui s’exécute sur le serveur distant. Vous devez modifier l’exemple de script suivant pour inclure un nom valide pour une instance distante de SQL Server. Cette session commence en tant qu’une session locale, mais la **rxSummary** fonction s’exécute sur l’instance distante de SQL Server.

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

  Ce script se connecte à une base de données sur le serveur distant, fournit une requête, crée un contexte de calcul `cc` instruction pour l’exécution de code à distance, puis fournit la fonction RevoScaleR **rxSummary** pour retourner une statistique Résumé des résultats de la requête.

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

4. Obtenir et définir le contexte de calcul. Une fois que vous définissez un contexte de calcul, il reste en vigueur pendant la durée de la session. Si vous ne savez pas si le calcul est local ou distant, exécutez la commande suivante pour découvrir. Les résultats qui spécifient une chaîne de connexion indiquent un contexte de calcul à distance.

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

5. Retourner des informations sur les variables dans la source de données, y compris le nom et le type.

  ```R
  rxGetVarInfo(data = inDataSource)
  ```
  Résultats incluent des 23 variables.


6. Générer un nuage de points pour Explorer s’il existe des dépendances entre les deux variables. 

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

  La capture d’écran suivante montre la sortie de traçage d’entrée et à nuages de points.

   ![Nuage de points dans RGUI](media/rclient-setup-scatterplot.png "nuage de points de données de démonstration NYC Taxi")

<a name="install-ide"></a>

## <a name="6---link-tools-to-rexe"></a>6 - lien Outils R.exe

Pour les projets de développement durable et grave, vous devez installer un environnement de développement intégré (IDE). Outils SQL Server et les outils R intégrés ne sont pas équipés pour le développement R lourd. Une fois que vous avez le code de travail, vous pouvez le déployer comme une procédure stockée pour une exécution sur SQL Server.

Pointez votre IDE sur les bibliothèques R locales : de base R, RevoScaleR et ainsi de suite. Charges de travail en cours d’exécution sur un serveur SQL distant se produit pendant l’exécution du script, lorsque votre script appelle un contexte de calcul à distance sur SQL Server, l’accès aux données et les opérations sur ce serveur.

### <a name="rstudio"></a>RStudio

Lorsque vous utilisez [RStudio](https://www.rstudio.com/), vous pouvez configurer l’environnement pour utiliser les bibliothèques R et les fichiers exécutables qui correspondent à ceux présents sur un serveur SQL distant.

1. Vérifiez les versions de packages R installées sur SQL Server. Pour plus d’informations, consultez [les informations de package R obtenir](determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).

1. Installez Microsoft R Client ou une des options de serveur autonome pour ajouter RevoScaleR et les autres packages R, y compris la distribution R de base utilisée par votre instance de SQL Server. Choisissez une version à la même ou un niveau inférieur (packages sont à compatibilité descendante) qui fournit les mêmes versions de package comme sur le serveur. Informations de version, voir la version de la carte dans cet article : [Mettre à niveau les composants R et Python](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

1. Dans RStudio, [mettre à jour votre chemin R](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R) pour pointer vers l’environnement R en fournissant RevoScaleR, Microsoft R Open et autres packages de Microsoft. 

  + Pour une installation de R Client, recherchez C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64
  + Pour un serveur autonome, recherchez C:\Program Files\Microsoft SQL Server\140\R_SERVER\Library ou C:\Program Files\Microsoft SQL Server\130\R_SERVER\Library

2. Fermez, puis ouvrez RStudio.

Lorsque vous rouvrez RStudio, l’exécutable à partir de R Client (ou un serveur autonome) R est le moteur R par défaut.


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

## <a name="next-steps"></a>Étapes suivantes

Deux didacticiels différents incluent des exercices afin que vous pouvez vous entraîner le basculement du contexte de calcul local à une instance distante de SQL Server.

+ [Didacticiel : Utiliser les fonctions RevoScaleR R avec des données de SQL Server](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [Procédure pas à pas pour une solution complète de science des données](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)