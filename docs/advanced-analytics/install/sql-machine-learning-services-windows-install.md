---
title: Installer SQL Server Machine Learning Services (en base de données) sur Windows | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8297d57ad1a29778e23d2ce02198c426825abf02
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "40437689"
---
# <a name="install-sql-server-machine-learning-services-in-database-on-windows"></a>Installer SQL Server Machine Learning Services (en base de données) sur Windows 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

À compter de SQL Server 2017, R et Python pour la base de données analytique est prise en charge dans SQL Server Machine Learning Services, le successeur de la fonctionnalité R Services introduite dans SQL Server 2016. Bibliothèques de fonctions sont disponibles dans R et Python et l’exécutent en tant que script externe sur une instance du moteur de base de données. 

Cet article explique comment installer le composant d’apprentissage machine en exécutant le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant d’installation et suivant les invites à l’écran.

## <a name="bkmk_prereqs"> </a> Liste de vérification de préinstallation

+ Le programme d’installation de SQL Server 2017 est requis si vous souhaitez installer les Services Machine Learning avec prise en charge linguistique pour R, Python ou les deux. Si au lieu de cela, vous avez support d’installation de SQL Server 2016, vous pouvez installer [SQL Server 2016 R Services (en base de données)](sql-r-services-windows-install.md) pour obtenir la prise en charge du langage R.

+ Une instance du moteur de base de données est requise. Vous ne pouvez pas installer uniquement les fonctionnalités R ou Python, bien que vous puissiez les ajouter progressivement à une instance existante.

+ N’installez pas les Services Machine Learning sur un cluster de basculement. Le mécanisme de sécurité servant à isoler les processus R et Python n’est pas compatible avec un environnement de cluster de basculement Windows Server.

+ N’installez pas les Services Machine Learning sur un contrôleur de domaine. La partie de la Machine Learning Services du programme d’installation échoue.

+ N’installez pas **fonctionnalités partagées** > **Machine Learning Server (autonome)** sur le même ordinateur exécutant une instance de la base de données. Un serveur autonome est en concurrence pour les mêmes ressources, fragilisant ainsi les performances de ces deux installations.

+ Installation côte à côte avec d’autres versions de R et Python est pris en charge, mais pas recommandée. Il est pris en charge, car l’instance de SQL Server utilise ses propres copies des distributions Anaconda et R open source. Mais il n’est pas recommandé, car le code qui utilise R et Python sur l’ordinateur SQL Server en dehors de SQL Server en cours d’exécution peut entraîner divers problèmes :
    
  + Vous utilisez une autre bibliothèque et un fichier exécutable différent et obtenez des résultats différents, que vous effectuez lorsque vous exécutez dans SQL Server.
  + Les scripts R et Python qui s’exécutent dans des bibliothèques externes ne peuvent pas être gérés par SQL Server, ce qui conduit à des conflits de ressources.
  
> [!IMPORTANT]
> Une fois le programme d’installation est terminée, veillez à effectuer les étapes de post-configuration décrites dans cet article. Ces étapes comprennent l’activation de SQL Server à utiliser des scripts externes, puis en ajoutant les comptes requis pour SQL Server exécuter des travaux R et Python à votre place. Modifications de configuration nécessitent généralement un redémarrage de l’instance ou un redémarrage du service Launchpad.

## <a name="get-the-installation-media"></a>Obtenir le média d’installation

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="run-setup"></a>Exécutez le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrer l’Assistant Installation de SQL Server 2017. Vous pouvez télécharger 
  
2. Sur le **Installation** onglet, sélectionnez **nouvelle installation SQL Server autonome ou ajout de fonctionnalités à une installation existante**.

   ![Installer les Services de base de données d’apprentissage](media/2017setup-installation-page-mlsvcs.PNG)
   
3. Dans la page **Sélection de fonctionnalités** , sélectionnez les options suivantes :
  
    -   **Services Moteur de base de données**
  
         Pour utiliser R et Python avec SQL Server, vous devez installer une instance du moteur de base de données. Vous pouvez utiliser une valeur par défaut ou une instance nommée.
  
    -   **Machine Learning Services (dans la base de données)**
  
         Cette option installe les services de base de données qui prennent en charge de R et Python de l’exécution du script.

    -   **R**

        Cochez cette option pour ajouter le Microsoft R packages, interpréteur et open source R. 

    -   **Python**

        Cochez cette option pour ajouter les packages Python de Microsoft, le fichier exécutable Python 3.5, puis sélectionnez les bibliothèques à partir de la distribution Anaconda.
        
        ![Fonctionnalités des options pour R et Python](media/2017setup-features-page-mls-rpy.png "options d’installation de Python")

        > [!NOTE]
        > 
        > Ne sélectionnez pas l’option pour **Machine Learning Server (autonome)**. L’option d’installation de Machine Learning Server sous **fonctionnalités partagées** est conçue pour une utilisation sur un ordinateur distinct.

4. Sur le **donner son consentement pour installer R** page, sélectionnez **Accept**. Ce contrat de licence couvre Microsoft R Open, qui inclut une distribution des packages de base de R open source et des outils, ainsi que les packages R améliorés et des fournisseurs de connectivité de l’équipe de développement Microsoft.

5. Sur le **donner son consentement pour l’installation de Python** page, sélectionnez **Accept**. Le contrat de licence open source Python couvre également Anaconda et les outils associés, ainsi que certaines nouvelles bibliothèques Python à partir de l’équipe de développement Microsoft.
     
     ![Contrat de licence de Python](media/2017setup-python-license.png "licence d’accord pour Python")
  
    > [!NOTE]
    >  Si l’ordinateur que vous utilisez n’a pas accès à internet, vous pouvez suspendre le programme d’installation à ce stade pour télécharger les programmes d’installation séparément. Pour plus d’informations, consultez [installer les composants d’apprentissage automatique sans accès à internet](../install/sql-ml-component-install-without-internet-access.md).
  
     Sélectionnez **Accept**, attendez que le **suivant** bouton devienne active, puis sélectionnez **suivant**.
  
6. Sur le **prêt pour l’installation** page, vérifiez que ces sélections sont incluses, puis sélectionnez **installer**.
  
    + Services Moteur de base de données
    + Machine Learning Services (en base de données)
    + R ou Python

    Note de l’emplacement du dossier sous le chemin d’accès `..\Setup Bootstrap\Log` où sont stockés les fichiers de configuration. Lorsque le programme d’installation est terminée, vous pouvez examiner les composants installés dans le fichier de synthèse.

7. Une fois l’installation terminée, si vous êtes invité à redémarrer l’ordinateur, faites-le maintenant. Il est important de lire le message affiché par l'Assistant Installation à la fin de l'installation. Pour plus d'informations, consultez [View and Read SQL Server Setup Log Files](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files).

## <a name="bkmk_enableFeature"></a>Activer l’exécution du script externe

1. Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > Vous pouvez télécharger et installer la version appropriée à partir de cette page : [télécharger SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > Vous pouvez également essayer la version préliminaire de [SQL Operations Studio](https://docs.microsoft.com/sql/sql-operations-studio/what-is), qui prend en charge les tâches d’administration et les requêtes SQL Server.
  
2. Connectez-vous à l’instance où vous avez installé les Services Machine Learning, cliquez sur **nouvelle requête** pour ouvrir une fenêtre de requête, exécutez la commande suivante :

   ```SQL
   sp_configure
   ```

    La propriété `external scripts enabled` a normalement la valeur **0** à ce stade. C’est parce que la fonctionnalité est désactivée par défaut. La fonctionnalité doit être activée explicitement par un administrateur avant de pouvoir exécuter des scripts R ou Python.
    
3.  Pour activer la fonctionnalité de script externe, exécutez l’instruction suivante :
    
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    Si vous avez déjà activé la fonctionnalité pour le langage R, ne s’exécutent pas reconfigurer une deuxième fois pour Python. La plateforme sous-jacente d’extensibilité prend en charge les deux langages.

## <a name="restart-the-service"></a>Redémarrez le service.

Lorsque l’installation est terminée, redémarrez le moteur de base de données avant de continuer à l’autre, l’activation de l’exécution du script.

Le redémarrage du service automatiquement redémarre connexe [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service.

Vous pouvez redémarrer le service à l’aide de clic droit **redémarrer** commande pour l’instance dans SSMS, ou à l’aide de la **Services** dans le panneau de configuration ou à l’aide du Panneau de configuration [Gestionnaire de Configuration SQL Server ](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Vérifier l'installation

Utilisez les étapes suivantes pour vérifier que tous les composants utilisés pour lancer le script externe sont en cours d’exécution.

1. Dans SQL Server Management Studio, ouvrez une nouvelle fenêtre de requête et exécutez la commande suivante :
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    La valeur **run_value** doit maintenant être définie sur 1.
    
2. Ouvrez le **Services** panneau ou le Gestionnaire de Configuration SQL Server et vérifiez **Launchpad de SQL Server service** est en cours d’exécution. Vous devez disposer d’un service pour chaque instance du moteur de base de données qui a R ou Python est installé. Pour plus d’informations, consultez [composants pour prendre en charge d’intégration de Python](../python/new-components-in-sql-server-to-support-python-integration.md). 
   
3. Si Launchpad est en cours d’exécution, vous devez être en mesure d’exécuter des scripts R et Python simples pour vérifier que les runtimes de script externes peut communiquer avec SQL Server.

   Ouvrez une nouvelle **requête** fenêtre dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis exécutez un script comme ci-dessous :
    
    + Pour R
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    + Pour Python
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'Python',
    @script=N'
    OutputDataSet = InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

 **Résultats**

    Le script peut prendre un certain à exécuter, la première fois l’exécution de script externe est chargé. Les résultats doivent être quelque chose comme ceci :

    | hello |
    |----|
    | 1|


> [!NOTE]
> Les colonnes ou les en-têtes utilisés dans le script Python ne sont pas renvoyées par conception. Pour ajouter des noms de colonne pour votre sortie, vous devez spécifier le schéma pour le jeu de données de retour. Cela l’aide du paramètre avec les résultats de la procédure stockée, les colonnes d’affectation de noms et en spécifiant le type de données SQL.
> 
> Par exemple, vous pouvez ajouter la ligne suivante pour générer un nom de colonne arbitraire : `WITH RESULT SETS ((Col1 AS int))`

## <a name="additional-configuration"></a>Configuration supplémentaire

Si l’étape de vérification de script externe a réussi, vous pouvez exécuter des commandes de Python à partir de SQL Server Management Studio, Visual Studio Code ou tout autre client capable d’envoyer des instructions T-SQL sur le serveur.

Si vous rencontrez une erreur lors de l’exécution de la commande, passez en revue les étapes de configuration supplémentaires dans cette section. Vous devrez peut-être effectuer des configurations supplémentaires appropriées vers le service ou d’une base de données.

Scénarios courants qui nécessitent des modifications supplémentaires sont les suivantes :

* [Configurer le pare-feu Windows pour les connexions entrantes](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [Activer des protocoles réseau supplémentaires](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Activer les connexions distantes](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Étendre des autorisations intégrées aux utilisateurs distants](#bkmk_configureAccounts)
* [Accorder l’autorisation d’exécuter des scripts externes](#permissions-external-script)
* [Accorder l’accès aux bases de données individuelles](#permissions-db)

> [!NOTE]
> Pas toutes les modifications répertoriées sont requises, et aucun peut être requise. Configuration requise dépend de votre schéma de sécurité, où vous avez installé SQL Server, et que les utilisateurs pour se connecter à la base de données et exécuter des scripts externes. Conseils de dépannage supplémentaires, consultez : [FAQ d’installation et de mise à niveau](../r/upgrade-and-installation-faq-sql-server-r-services.md)

###  <a name="bkmk_configureAccounts"></a> Activer l’authentification implicite pour le groupe de comptes Launchpad

Pendant l’installation, plusieurs comptes d’utilisateur Windows sont créés pour exécuter les tâches situées dans le jeton de sécurité du service [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Lorsqu’un utilisateur envoie un script Python ou R à partir d’un client externe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Active un compte de travail disponibles. Il est mappé à l’identité de l’utilisateur appelant, puis exécute le script pour le compte de l’utilisateur.

Il s’agit *l’authentification implicite*, est un service du moteur de base de données. Ce service prend en charge l’exécution sécurisée des scripts externes SQL Server 2016 et SQL Server 2017.

Vous pouvez afficher ces comptes dans le groupe d’utilisateurs Windows, **SQLRUserGroup**. Par défaut, 20 comptes de travail sont créés, ce qui est généralement plus que suffisant pour l’exécution de script externe de travaux.

> [!IMPORTANT]
> Le groupe de travail est nommé **SQLRUserGroup** indépendamment de si vous avez installé R ou Python. Il existe un groupe unique pour chaque instance.

Si vous avez besoin exécuter des scripts à partir d’un client de science des données distantes, et que vous utilisez l’authentification Windows, il existe des considérations supplémentaires. Ces comptes de travail doivent obtenir l’autorisation de se connecter à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance en votre nom.

1. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l’Explorateur d’objets, développez **sécurité**. Avec le bouton droit puis **connexions**, puis sélectionnez **nouvelle connexion**.
2. Dans le **nouvelle connexion** boîte de dialogue, sélectionnez **recherche**.
3. Sélectionnez **Types d’objets**, puis sélectionnez **groupes**. Effacer tout le reste.
4. Dans **Entrez le nom de l’objet à sélectionner**, type *SQLRUserGroup*, puis sélectionnez **vérifier les noms**.
5. Le nom du groupe local associé au service Launchpad de l’instance doit ressembler à quelque chose comme *nom_instance\SQLRUserGroup*. Sélectionnez **OK**.
6. Par défaut, le groupe est affecté à la **public** rôle, et est autorisé à se connecter au moteur de base de données.
7. Sélectionnez **OK**.

> [!NOTE]
> Si vous utilisez un **connexion SQL** pour exécuter des scripts dans un contexte de calcul de SQL Server, cette étape supplémentaire n’est pas nécessaire.

### <a name="permissions-external-script"></a> Autoriser les utilisateurs à exécuter des scripts externes

Si vous avez installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous-même et que vous exécutez des scripts R ou Python dans votre propre instance, en général, vous exécutez les scripts en tant qu’administrateur. Par conséquent, vous avez une autorisation implicite sur différentes opérations et toutes les données dans la base de données.

La plupart des utilisateurs, toutefois, n’ont pas de ces autorisations élevées. Par exemple, les utilisateurs d’une organisation qui utilisent des connexions SQL pour accéder à la base de données généralement n’ont pas des autorisations élevées. Par conséquent, pour chaque utilisateur qui est à l’aide de R ou Python, vous devez accorder aux utilisateurs des Services Machine Learning l’autorisation d’exécuter des scripts externes dans chaque base de données où la langue est utilisée. Voici comment :

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> Autorisations ne sont pas spécifiques au langage de script pris en charge. En d’autres termes, il ne sont pas des niveaux d’autorisation distincts pour le script R et le script Python. Si vous avez besoin de mettre à jour les autorisations distinctes pour ces langues, vous devez installer R et Python sur des instances distinctes.

### <a name="permissions-db"></a> Autoriser vos utilisateurs en lecture, écriture ou définition de données (DDL) de langage à bases de données

Pendant l’exécution de scripts est un utilisateur, l’utilisateur devra peut-être lire les données à partir d’autres bases de données. L’utilisateur peut également besoin créer des tables pour stocker les résultats et écrire des données dans des tables.

Pour chaque compte d’utilisateur Windows ou un compte de connexion SQL qui est en cours d’exécution des scripts R ou Python, vérifiez qu’il possède les autorisations appropriées sur la base de données : `db_datareader`, `db_datawriter`, ou `db_ddladmin`.

Par exemple, ce qui suit [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction donne la connexion SQL *MySQLLogin* les droits pour exécuter des requêtes T-SQL le *ML_Samples* base de données. Pour exécuter cette instruction, la connexion SQL doit déjà exister dans le contexte de sécurité du serveur.

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Pour plus d’informations sur les autorisations incluses dans chaque rôle, consultez [rôles au niveau de la base de données](../../relational-databases/security/authentication-access/database-level-roles.md).


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Créer une source de données ODBC pour l’instance sur votre client de science des données

Vous pouvez créer une solution sur un ordinateur client de science des données d’apprentissage. Si vous avez besoin exécuter du code à l’aide de l’ordinateur SQL Server comme contexte de calcul, vous avez deux options : accéder à l’instance à l’aide d’une connexion SQL ou à l’aide d’un Windows du compte.

+ Pour une connexion SQL : Assurez-vous que la connexion dispose des autorisations appropriées sur la base de données où vous lisez les données. Ce faire, vous pouvez ajouter *se connecter à* et *sélectionnez* autorisations, ou en ajoutant la connexion à la `db_datareader` rôle. Pour créer des objets, assignez `DDL_admin` droits. Si vous devez enregistrer les données dans les tables, ajouter à la `db_datawriter` rôle.

+ Pour l’authentification Windows : vous devrez peut-être créer une source de données ODBC sur le client de science des données qui spécifie le nom d’instance et d’autres informations de connexion. Pour plus d’informations, consultez [administrateur de sources de données ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="suggested-optimizations"></a>Optimisations proposées

Maintenant que vous avez ce que tout fonctionne, vous souhaiterez également optimiser le serveur pour prendre en charge d’apprentissage, ou installer des modèles préformés.

### <a name="add-more-worker-accounts"></a>Ajouter plusieurs comptes de travail

Si vous prévoyez de nombreux utilisateurs d’exécuter simultanément des scripts, vous pouvez augmenter le nombre de comptes de travail qui sont affectés au service Launchpad. Pour plus d’informations, consultez [modifier le pool de comptes d’utilisateur pour SQL Server Machine Learning Services](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="optimize-the-server-for-script-execution"></a>Optimiser le serveur pour l’exécution du script

Les paramètres par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation sont destinées à optimiser l’équilibre du serveur pour un large éventail de services qui sont pris en charge par le moteur de base de données, ce qui peut inclure extraction, transformation et processus de chargement (ETL), création de rapports, l’audit, et les applications qui utilisent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données. Par conséquent, les paramètres par défaut, vous constaterez peut-être que les ressources pour l’apprentissage sont parfois restreintes ou limitées, en particulier dans les opérations gourmandes en mémoire.

Pour vous assurer que les travaux machine learning est classés par priorité et ressourcées, nous vous recommandons d’utiliser le gouverneur de ressources SQL Server pour configurer un pool de ressources externes. Vous souhaiterez également modifier la quantité de mémoire qui est allouée à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur de base de données ou augmenter le nombre de comptes qui s’exécutent sous le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service.

- Pour configurer un pool de ressources pour la gestion des ressources externes, consultez [créer un pool de ressources externe](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Pour modifier la quantité de mémoire réservée pour la base de données, consultez [options de configuration de mémoire serveur](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Pour modifier le nombre de comptes R qui peuvent être démarrés par [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], consultez [modifier le pool de comptes d’utilisateur pour l’apprentissage](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

Si vous utilisez l’Édition Standard et que vous ne disposez pas du gouverneur de ressources, vous pouvez utiliser les vues de gestion dynamique (DMV) et les événements étendus, ainsi que Windows contrôle des événements pour aider à gérer les ressources du serveur. Pour plus d’informations, consultez [surveillance et gestion des Services de R](../r/managing-and-monitoring-r-solutions.md) et [surveillance et gestion des Services de Python](../python/managing-and-monitoring-python-solutions.md).

### <a name="install-additional-r-packages"></a>Installer des packages R supplémentaires

Les solutions R que vous créez pour SQL Server peuvent appeler des fonctions de base R, de fonctions à partir des packages propriétaires installés avec SQL Server, les packages R de tiers compatibles avec la version de R open source installé par SQL Server.

Installez les packages que vous souhaitez utiliser à partir de SQL Server dans la bibliothèque par défaut qui est utilisée par l’instance. Si vous avez une installation distincte de R sur l’ordinateur, ou si vous avez installé des packages dans les bibliothèques utilisateur, vous ne pourrez pas utiliser ces packages à partir de T-SQL.

Le processus d’installation et de gestion des packages R est différent dans SQL Server 2016 et SQL Server 2017. Dans SQL Server 2016, un administrateur de base de données doit installer les packages R que les utilisateurs ont besoin. Dans SQL Server 2017, vous pouvez configurer des groupes d’utilisateurs de partager les packages sur un niveau par base de données ou configurer des rôles de base de données pour permettre aux utilisateurs d’installer leurs propres packages. Pour plus d’informations, consultez [installer de nouveaux packages R dans SQL Server](../r/install-additional-r-packages-on-sql-server.md).


## <a name="get-help"></a>Obtenir de l’aide

Besoin d’aide avec l’installation ou mise à niveau ? Pour obtenir des réponses aux questions courantes et les problèmes connus, consultez l’article suivant :

* [Mise à niveau et installation FAQ - Services Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Pour vérifier l’état d’installation de l’instance et résoudre les problèmes courants, essayez ces rapports personnalisés.

* [Rapports personnalisés pour SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Étapes suivantes

Aux développeurs R peuvent démarrer avec des exemples simples et apprendre les bases du fonctionne de R avec SQL Server. Pour votre prochaine étape, consultez les liens suivants :

+ [Didacticiel : Exécuter R dans T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Didacticiel : De base de données analytique pour les développeurs R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Les développeurs Python peuvent apprendre à utiliser Python avec SQL Server en suivant ces didacticiels :

+ [Didacticiel : Exécuter Python dans T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Didacticiel : De base de données analytique pour les développeurs Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Pour afficher des exemples d’apprentissage qui sont basées sur des scénarios réels, consultez [d’apprentissage didacticiels](../tutorials/machine-learning-services-tutorials.md).
