---
title: "Le programme d’installation et de configuration pour Python Machine Learning Services | Documents Microsoft"
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: e3142bcf06fa2ed88ead730d0cc127cf41cfde56
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="set-up-python-machine-learning-services-in-database"></a>Configurer les Python Machine Learning Services (de-de base de données)

  Vous installez les composants requis pour Python en exécutant le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Installation et suivez les instructions d’interactives comme décrit dans cette rubrique.

## <a name="machine-learning-options-in-sql-server-setup"></a>Apprentissage des options dans le programme d’installation de SQL Server

Choisissez le **Machine Learning Services** des fonctionnalités, puis sélectionnez **Python** comme langage.

Le **fonctionnalités partagées** section contient une option d’installation distinct, **Machine Learning Server (autonome)**. Cette option prend en charge à l’Opérationnalisation du code Python sur un serveur qui n’a pas de SQL Server, ou qui ne nécessite pas l’utilisation de contextes de calcul de SQL Server. Par conséquent, nous recommandons que vous *pas* l’installer sur le même ordinateur en tant qu’une instance de SQL Server. Au lieu de cela, installez Machine Learning Server (autonome) sur un ordinateur distinct.

Une fois l’installation terminée, reconfigurer l’instance pour permettre l’exécution de scripts qui utilisent un fichier exécutable externe. Vous devrez peut-être apporter des modifications supplémentaires au serveur pour prendre en charge les charges de travail machine learning. Modifications de configuration nécessitent généralement un redémarrage de l’instance, ou un redémarrage du service Launchpad.

### <a name="prerequisites"></a>Conditions préalables

+ SQL Server 2017 est requis. Intégration de Python n’est pas prise en charge des versions antérieures de SQL Server.
+ Veillez à installer le moteur de base de données. Une instance de SQL Server est requise pour exécuter les Python scripts dans la base de données.
+ Composants requis sont installés en tant que partie de l’installation du composant Python.
+ Vous ne pouvez pas installer l’apprentissage avec les services de Python sur un cluster de basculement. Le mécanisme de sécurité utilisé pour isoler les processus Python n’est pas compatible avec un environnement de cluster de basculement Windows Server.
   
  Pour résoudre ce problème, vous pouvez utiliser la réplication pour copier les tables nécessaires à une instance de SQL Server autonome qui utilise les services de Python. Vous pouvez également installer l’apprentissage avec les services de Python sur un ordinateur autonome qui utilise le paramètre AlwaysOn et fait partie d’un groupe de disponibilité.

+ Installation côte à côte avec d’autres versions de Python est possible, car l’instance de SQL Server utilise sa propre copie de la distribution Anaconda. Toutefois, le code qui utilise les Python sur l’ordinateur SQL Server en dehors de SQL Server en cours d’exécution peut entraîner divers problèmes :
    + Vous utilisez une autre bibliothèque et le fichier exécutable différent et obtenez des résultats différents que vous effectuez lors de l’exécution dans SQL Server.
    + Scripts Python en cours d’exécution des bibliothèques externes ne peuvent pas être gérés par SQL Server, conduisant à un conflit de ressources.
  
> [!IMPORTANT]
> Une fois l’installation terminée, veillez à exécuter les étapes à la configuration supplémentaires décrites dans cette rubrique. Notamment l’activation de SQL Server à utiliser des scripts externes, puis en ajoutant les comptes requis pour SQL Server exécuter des travaux de Python à votre place.

### <a name="unattended-installation"></a>Installation sans assistance

Pour effectuer une installation sans assistance, utilisez les options de ligne de commande pour le programme d’installation de SQL Server et les arguments spécifiques à Python. Pour plus d’informations, consultez [Unattended l’installation de SQL Server avec les Services de Python Machine Learning](unattended-installs-of-sql-server-python-services.md).

##  <a name="bkmk_installPythonInDatabase"></a>Étape 1 : Installer les Services (de-de base de données) sur SQL Server d’apprentissage

1. Exécutez l’Assistant Installation de SQL Server 2017.
  
2. Sur le **Installation** onglet, sélectionnez **nouvelle installation SQL Server autonome ou ajouter des fonctionnalités à une installation existante**.

    ![Installer Python dans la base de données](media/2017setup-installation-page-mlsvcs.PNG)
   
3. Dans la page **Sélection de fonctionnalités** , sélectionnez les options suivantes :
  
    -   **Services Moteur de base de données**
  
         Pour utiliser Python avec SQL Server, vous devez installer une instance du moteur de base de données. Vous pouvez utiliser une valeur par défaut ou une instance nommée.
  
    -   **Apprentissage des Services (de-de base de données)**
  
         Cette option installe les services de base de données qui prennent en charge l’exécution du script Python.

    -   **Python** Activez cette option pour obtenir de l’exécutable de Python 3.5 et sélectionner des bibliothèques à partir de la distribution Anaconda. Installer qu’une seule langue par instance.
        
        ![Fonctionnalité des options pour Python](media/ml-svcs-features-python-highlight.png "options d’installation de Python")

        > [!NOTE]
        > 
        > Ne sélectionnez pas l’option pour **Machine Learning Server (autonome)**. L’option d’installation du serveur d’apprentissage Machine sous **fonctionnalités partagées** est prévu pour une utilisation sur un ordinateur distinct. Par exemple, vous souhaiterez installer la même version de composants sur un autre ordinateur qui est utilisé pour le développement de projet, par exemple un ordinateur portable de votre spécialiste des données d’apprentissage.

4. Sur le **donner son consentement pour installer les Python** page, sélectionnez **accepter**.
  
     Ce contrat de licence est nécessaire pour télécharger l’exécutable, Python packages Python à partir de Anaconda.
     
     ![Contrat de licence de Python](media/ml-svcs-license-python.png "contrat pour Python de licence")
  
    > [!NOTE]
    >  Si l’ordinateur que vous utilisez n’a pas accès à internet, vous pouvez interrompre l’installation à ce stade pour télécharger les programmes d’installation séparément. Pour plus d’informations, consultez [l’installation des composants sans accès à internet](../r/installing-ml-components-without-internet-access.md).
  
     Sélectionnez **accepter**, attendez que le **suivant** devient active et sélectionnez **suivant**.
  
5. Sur le **prêt pour l’installation** , vérifiez que ces sélections sont incluses, puis sélectionnez **installer**.
  
     + Services Moteur de base de données
     + Machine Learning Services (en base de données)
     + Python
  
    Ces sélections représentent la configuration minimale requise pour utiliser Python avec [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)].
    
    ![Prêt à installer Python](media/ready-to-install-python.png "les composants requis pour l’installation de Python")

    Si vous le souhaitez, prenez note de l’emplacement du dossier sous le chemin d’accès `..\Setup Bootstrap\Log` où sont stockés les fichiers de configuration. Lorsque le programme d’installation est terminée, vous pouvez examiner les composants installés dans le fichier de résumé.

6. Lorsque l’installation est terminée, redémarrez l’ordinateur.

##  <a name="bkmk_enableFeature"></a>Étape 2 : Activer l’exécution du script Python

1. Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. S’il n’est pas déjà installé, vous pouvez exécuter l’Assistant Installation de SQL Server pour ouvrir un lien de téléchargement et l’installer.
  
2. Connectez-vous à l’instance où vous avez installé les Services de Machine Learning et exécutez la commande suivante :

   ```SQL
   sp_configure
   ```

    La propriété `external scripts enabled` a normalement la valeur **0** à ce stade. C’est parce que la fonctionnalité est désactivée par défaut. La fonctionnalité doit être activée explicitement par un administrateur avant de pouvoir exécuter des scripts R ou Python.
    
3.  Pour activer la fonctionnalité de script externe qui prend en charge de Python, exécutez l’instruction suivante :
    
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    Si vous avez déjà activé la fonctionnalité du langage R, vous ne devez exécuter reconfigure une deuxième fois pour Python. La plateforme d’extensibilité sous-jacente prend en charge les deux langages.

4. Redémarrez le service SQL Server pour l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Redémarrage du service SQL Server également le redémarrage automatique connexe [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service.

    Vous pouvez redémarrer le service à l’aide de la **Services** dans le panneau de configuration ou à l’aide du Panneau de configuration [Gestionnaire de Configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md).

## <a name="step-3-verify-that-the-external-script-execution-feature-is-running"></a>Étape 3 : Vérifier que la fonctionnalité d’exécution de script externe est en cours d’exécution.

Prenez un moment pour vérifier que tous les composants utilisés pour lancer le script Python sont en cours d’exécution.

1. Dans SQL Server Management Studio, ouvrez une nouvelle fenêtre de requête et exécutez la commande suivante :
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    La valeur **run_value** doit maintenant être définie sur 1.
    
2. Ouvrez le **Services** Panneau de configuration ou le Gestionnaire de Configuration SQL Server et vérifiez que le service Launchpad de votre instance est en cours d’exécution. Si la zone de lancement ne fonctionne pas, redémarrez le service.
  
    Si vous avez installé plusieurs instances de SQL Server, n’importe quelle instance ayant R ou Python activé a son propre service Launchpad.

    Si vous installez R et Python sur une instance unique, seul Launchpad est installé. Un lanceur séparé et spécifiques au langage de DLL est ajouté pour chaque langue. Pour plus d’informations, consultez [composants pour prendre en charge l’intégration Python](new-components-in-sql-server-to-support-python-integration.md). 
   
3. Si le Launchpad est en cours d’exécution, vous devez être en mesure d’exécuter des scripts Python simples comme suit dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'Python',
    @script=N'OutputDataSet = InputDataSet',
    @input_data_1 = N'SELECT 1 AS col'
    ```
    
    **Résultats**
    
    *<code>&nbsp;&nbsp;</code>* *1*

> [!NOTE]
> Colonnes ou les en-têtes utilisés dans le script Python ne sont pas renvoyées par conception. Pour ajouter des noms de colonnes pour la sortie, vous devez spécifier le schéma pour le jeu de données de retour. Cela l’aide du paramètre avec les résultats de la procédure stockée, les colonnes d’affectation de noms et en spécifiant le type de données SQL.
> 
> Par exemple, vous pouvez ajouter la ligne suivante pour générer un nom de colonne arbitraire :`WITH RESULT SETS ((Col1 AS int))`

## <a name="step-4-additional-configuration"></a>Étape 4 : Une configuration supplémentaire

Si la commande précédente a réussi, vous pouvez exécuter des commandes de Python à partir de SQL Server Management Studio, Visual Studio Code ou tout autre client qui peut envoyer des instructions T-SQL sur le serveur.

Si vous avez obtenu une erreur lors de l’exécution de la commande, passez en revue la liste suivante. Vous devrez peut-être effectuer des configurations supplémentaires appropriées pour le service ou d’une base de données.

> [!NOTE]
> 
> Pas toutes les modifications répertoriées sont requises, et aucun peut être requise. Conditions requises dépendent de votre schéma de sécurité, où vous avez installé SQL Server, et que les utilisateurs pour se connecter à la base de données et exécuter des scripts externes.

###  <a name="bkmk_configureAccounts"></a>Activer l’authentification implicite pour un groupe de comptes Launchpad

Pendant l’installation, plusieurs comptes d’utilisateur Windows sont créés pour exécuter les tâches situées dans le jeton de sécurité du service [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Lorsqu’un utilisateur envoie un script Python ou R à partir d’un client externe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Active un compte de travail disponibles. Puis il mappe à l’identité de l’utilisateur appelant et exécute le script de la part de l’utilisateur.

Il s’agit *l’authentification implicite*, est un service du moteur de base de données. Ce service prend en charge l’exécution sécurisée des scripts externes SQL Server 2016 et SQL Server 2017.

Vous pouvez afficher ces comptes dans le groupe d’utilisateurs Windows, **SQLRUserGroup**. Par défaut, 20 comptes de travail sont créés, ce qui est habituellement des tâches plus que suffisant pour l’exécution de script externe.

> [!IMPORTANT]
> Le groupe de travail est nommé **SQLRUserGroup** indépendamment de si vous avez installé R ou Python. Il existe un groupe unique pour chaque instance.

Si vous avez besoin exécuter des scripts à partir d’un client de science des données distantes, et vous utilisez l’authentification Windows, il existe des considérations supplémentaires. Ces comptes de travail doivent recevoir l’autorisation de se connecter à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance à votre place.

1. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l’Explorateur d’objets, développez **sécurité**. Avec le bouton droit puis **connexions**, puis sélectionnez **nouvelle connexion**.
2. Dans le **nouvelle connexion** boîte de dialogue, sélectionnez **recherche**.
3. Sélectionnez **les Types d’objets**, puis sélectionnez **groupes**. Désactivez tout le reste.
4. Dans **Entrez le nom de l’objet à sélectionner**, type *SQLRUserGroup*, puis sélectionnez **vérifier les noms**.
5. Le nom du groupe local associé au service Launchpad de l’instance doit ressembler à quelque chose comme *nom_instance\SQLRUserGroup*. Sélectionnez **OK**.
6. Par défaut, le groupe est affecté à la **public** rôle, et est autorisé à se connecter au moteur de base de données.
7. Sélectionnez **OK**.

> [!NOTE]
> Si vous utilisez un **connexion SQL** pour exécuter des scripts dans un contexte de calcul de SQL Server, cette étape supplémentaire n’est pas requise.

### <a name="give-users-permission-to-run-external-scripts"></a>Autoriser les utilisateurs à exécuter des scripts externes

Si vous avez installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous-même et que vous exécutez scripts Python dans votre propre instance, en général, vous exécutez des scripts en tant qu’administrateur. Par conséquent, vous avez une autorisation implicite sur toutes les données dans la base de données et les diverses opérations.

La plupart des utilisateurs, toutefois, n’ont pas de telles autorisations avec élévation de privilèges. Par exemple, les utilisateurs d’une organisation qui utilisent des connexions SQL pour accéder à la base de données généralement n’ont pas des autorisations élevées. Par conséquent, pour chaque utilisateur qui est à l’aide de Python, vous devez accorder aux utilisateurs des Services de Machine Learning l’autorisation d’exécuter des scripts externes dans chaque base de données où les Python est utilisé. Voici comment :

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> Autorisations ne sont pas spécifiques au langage de script pris en charge. En d’autres termes, il ne sont pas des niveaux d’autorisation distinct pour le script R et script Python. Si vous devez mettre à jour les autorisations distinctes pour ces langues, vous devez installer R et Python sur des instances distinctes.

### <a name="give-your-users-read-write-or-data-definition-language-ddl-permissions-to-databases"></a>Accorder des autorisations de language (DDL) sur les bases de données de votre définition de données, d’écriture ou en lecture aux utilisateurs

Pendant l’exécution de scripts est un utilisateur, l’utilisateur peut avoir besoin lire des données à partir d’autres bases de données. L’utilisateur peut également besoin créer des tables pour stocker les résultats et écrire des données dans des tables.

Pour chaque compte d’utilisateur Windows ou un compte de connexion SQL qui est en cours d’exécution des scripts R ou Python, assurez-vous qu’il dispose des autorisations appropriées sur la base de données : `db_datareader`, `db_datawriter`, ou `db_ddladmin`.

Par exemple, [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction donne la connexion SQL *MySQLLogin* les droits pour exécuter des requêtes T-SQL le *ML_Samples* base de données. Pour exécuter cette instruction, la connexion SQL doit déjà exister dans le contexte de sécurité du serveur.

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Pour plus d’informations sur les autorisations incluses dans chaque rôle, consultez [rôles au niveau de la base de données](../../relational-databases/security/authentication-access/database-level-roles.md).

### <a name="ensure-that-the-sql-server-installation-supports-remote-connections"></a>Assurez-vous que l’installation de SQL Server prend en charge les connexions à distance

Si vous ne pouvez pas vous connecter à partir d’un ordinateur distant, vérifiez si le pare-feu autorise l’accès à SQL Server. Dans une installation par défaut, les connexions à distance peuvent être désactivées ou le port spécifique utilisé par SQL Server risque d’être bloqué par le pare-feu. Pour plus d’informations, consultez [configurer le pare-feu Windows pour accéder au moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).

### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Créer une source de données ODBC pour l’instance sur votre client de science des données

Vous pouvez créer une solution sur un ordinateur client de science des données d’apprentissage. Si vous avez besoin exécuter du code à l’aide de l’ordinateur SQL Server en tant que le contexte de calcul, vous avez deux options : accéder à l’instance à l’aide d’une connexion SQL ou à l’aide d’une fenêtre de compte.

+ Pour les connexions SQL : Vérifiez que la connexion dispose des autorisations appropriées sur la base de données où vous lisez des données. Ce faire, vous pouvez ajouter *se connecter à* et *sélectionnez* autorisations, ou en ajoutant de la connexion à la `db_datareader` rôle. Pour créer des objets, assignez `DDL_admin` droits. Si vous devez enregistrer les données à des tables, ajouter à la `db_datawriter` rôle.

+ Pour l’authentification Windows : vous devrez peut-être créer une source de données ODBC sur le client de science des données qui spécifie le nom d’instance et d’autres informations de connexion. Pour plus d’informations, consultez [administrateur de sources de données ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="additional-optimizations"></a>Optimisations supplémentaires

Maintenant que vous avez tout fonctionne, vous pouvez également souhaiter d’optimiser le serveur pour prendre en charge d’apprentissage, ou installer pretrained modèles.

### <a name="add-more-worker-accounts"></a>Ajoutez d’autres comptes de travail

Si vous pensez que de nombreux utilisateurs d’exécuter simultanément des scripts, vous pouvez augmenter le nombre de comptes de travail qui sont affectés au service Launchpad. Pour plus d’informations, consultez [modifier le pool de comptes d’utilisateur pour SQL Server Machine Learning Services](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="optimize-the-server-for-script-execution"></a>Optimiser le serveur pour l’exécution du script

Les paramètres par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation optimiser l’équilibre entre le serveur pour une multitude de services. Ces services incluent ETL processus, création de rapports, l’audit et les applications qui utilisent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données.

Si vous utilisez les paramètres par défaut, vous constaterez que les ressources pour l’exécution de scripts externes seront limitées ou limitées, en particulier dans les opérations gourmandes en mémoire. Si l’apprentissage est une priorité, modifiez les paramètres de base de données par défaut pour vous assurer que les tâches de script externe sont classés par priorité et avec la ressource appropriée. Ces modifications peuvent inclure :

+ Réduire la quantité de mémoire allouée à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur de base de données.
+ Augmentation du nombre de comptes en cours d’exécution sous le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service. Cela n’augmente pas le nombre de ressources, mais augmente le nombre de scripts qui peuvent s’exécuter simultanément.

Si vous disposez de SQL Server Enterprise Edition, utilisez le gouverneur de ressources pour configurer un pool de ressources externes pour Python. Pour plus d'informations, consultez les articles suivants :

-   Configurer un pool de ressources pour gérer des ressources externes
  
     [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)
  
-   Modifier la quantité de mémoire réservée au moteur de base de données
  
     [Options de configuration de serveur de mémoire serveur](../../database-engine/configure-windows/server-memory-server-configuration-options.md)
  
-   Modifier le nombre de comptes de travail qui peut être démarrée par[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]
  
     [Modifier le pool de comptes d’utilisateur pour SQL Server R Services](../r/modify-the-user-account-pool-for-sql-server-r-services.md)

Si vous utilisez SQL Server Standard Edition et n’avez pas le gouverneur de ressources, vous pouvez utiliser les événements étendus et les vues de gestion dynamique pour vous aider à gérer les ressources du serveur. Vous pouvez également utiliser l’analyse des événements Windows à cet effet. Pour plus d’informations, consultez [analyse et la gestion des Services de R](../r/managing-and-monitoring-r-solutions.md).

### <a name="upgrade-the-machine-learning-components"></a>Mettre à niveau les composants d’apprentissage automatique

Lorsque vous installez les Services de Machine Learning à l’aide de SQL Server 2017, vous obtiendrez la version des composants au moment de que la publication de la mise en production. Chaque fois que des correctifs ou de la mise à niveau de l’instance de SQL Server, les composants d’apprentissage machine sont mis à niveau ainsi.

Vous pouvez mettre à niveau les composants sur une planification plus rapide qu’est pris en charge d’apprentissage automatique par les versions de SQL Server en installant Microsoft Machine Learning Server. Lorsque vous procédez ainsi, vous obtenez également des nouvelles fonctionnalités prises en charge dans la dernière version de la Machine Learning serveur, telles que :

+ Mises à jour des packages Python pour [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) et [microsoftml pour Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).
+ [Modèles de pretrained](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models) pour l’analyse de texte et de classification d’image.

Pour plus d’informations sur la mise à niveau une instance, consultez [composants R de mise à niveau via la liaison](..\r\use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="tutorials"></a>Didacticiels

Reportez-vous aux didacticiels suivants pour obtenir des exemples de la façon dont vous pouvez utiliser Python avec SQL Server pour créer et déployer des solutions d’apprentissage machine :

[À l’aide de Python dans T-SQL](../tutorials/run-python-using-t-sql.md)

[Créer un modèle de Python à l’aide de revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md)
