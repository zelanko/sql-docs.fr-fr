---
title: Installer SQL Server 2016 R Services (en base de données) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4f5c39c62b63aa3d2bf8daf83b9212423cf258a1
ms.sourcegitcommit: e4e9f02b5c14f3bb66e19dec98f38c012275b92c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118507"
---
# <a name="install-sql-server-2016-r-services"></a>Installer SQL Server 2016 R Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment installer et configurer **SQL Server 2016 R Services (en base de données)**. Si vous avez SQL Server 2016, installez cette fonctionnalité pour permettre l’exécution de code R dans SQL Server.

## <a name="bkmk_prereqs"> </a> Liste de vérification de préinstallation

+ Le programme d’installation de SQL Server 2016 est nécessaire si vous souhaitez installer R Services. Si au lieu de cela, vous avez support d’installation de SQL Server 2017, vous devez installer [SQL Server 2017 Machine Learning Services (en base de données)](sql-machine-learning-services-windows-install.md) pour obtenir l’intégration de R pour cette version de SQL Server.

+ Une instance du moteur de base de données est requise. Vous ne pouvez pas installer R simplement, bien que vous pouvez l’ajouter progressivement à une instance existante.

+ N’installez pas de R Services sur un cluster de basculement. Le mécanisme de sécurité utilisé pour isoler les processus R n’est pas compatible avec un environnement de cluster de basculement Windows Server.

+ N’installez pas de R Services sur un contrôleur de domaine. La partie de R Services du programme d’installation échoue.

+ N’installez pas **fonctionnalités partagées** > **R Server (autonome)** sur le même ordinateur exécutant une instance de la base de données. 

+ Installation côte à côte avec d’autres versions de R et Python sont possibles, car l’instance de SQL Server utilise ses propres copies des distributions Anaconda et R open source. Toutefois, le code qui utilise R et Python sur l’ordinateur SQL Server en dehors de SQL Server en cours d’exécution peut entraîner divers problèmes :
    
  + Vous utilisez une autre bibliothèque et un fichier exécutable différent et obtenez des résultats différents, que vous effectuez lorsque vous exécutez dans SQL Server.
  + Les scripts R et Python qui s’exécutent dans des bibliothèques externes ne peuvent pas être gérés par SQL Server, ce qui conduit à des conflits de ressources.
  
Si vous avez utilisé des versions antérieures de l’environnement de développement Revolution Analytique ou les packages RevoScaleR, ou si vous avez installé des versions préliminaires de SQL Server 2016, vous devez les désinstaller. Versions anciennes et récentes de RevoScaleR et d’autres packages propriétaires en cours d’exécution n’est pas pris en charge. Pour supprimer les versions précédentes, consultez [mise à niveau et FAQ d’Installation de SQL Server Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

> [!IMPORTANT]
> Une fois le programme d’installation est terminée, veillez à effectuer les étapes de post-configuration supplémentaires décrites dans cet article. Ces étapes comprennent l’activation de SQL Server à utiliser des scripts externes, puis en ajoutant les comptes requis pour SQL Server exécuter des travaux R à votre place. Modifications de configuration nécessitent généralement un redémarrage de l’instance ou un redémarrage du service Launchpad.

## <a name="get-the-installation-media"></a>Obtenir le média d’installation

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> Installer le correctif obligatoire 

Microsoft a identifié un problème avec la version spécifique des fichiers binaires Microsoft VC++ 2013 Runtime qui sont installés en tant que composants requis par SQL Server. Si cette mise à jour des fichiers binaires du runtime VC n’est pas installée, SQL Server risque de rencontrer des problèmes de stabilité dans certains scénarios. Avant d’installer SQL Server, suivez les instructions données dans [Notes de publication de SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) pour voir si votre ordinateur nécessite un correctif pour les fichiers binaires du runtime VC.  

## <a name="bkmk2016top"></a>Exécutez le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrer l’Assistant Installation de SQL Server 2016.

2. Sur le **Installation** onglet, sélectionnez **nouvelle installation SQL Server autonome ou ajout de fonctionnalités à une installation existante**.
    
   ![Installer R Services (en base de données)](media/2016-setup-installation-rsvcs.png "démarrer l’installation du moteur de base de données avec R Services")
   
3. Sur le **sélection des fonctionnalités** page, sélectionnez les options suivantes :

   - Sélectionnez **Services moteur de base de données**. Le moteur de base de données est requise dans chaque instance qui utilise l’apprentissage.
   - Sélectionnez **R Services (en base de données)**. Installe la prise en charge pour l’utilisation de la base de données de R.
    
     ![Sélection des fonctionnalités de R Services](media/2016setup-rsvcs-features.png "sélectionner ces fonctionnalités pour R Services de base de données")

    > [!IMPORTANT]
    > N’installez pas de R Server et R Services en même temps. En règle générale vous installez R Server (autonome) pour créer un environnement un scientifique des données ou un développeur utilise pour se connecter à SQL Server et déployer des solutions R. Vous n’avez donc pas besoin de les installer sur le même ordinateur.

4.  Sur le **donner son consentement pour installer Microsoft R Open** , cliquez sur **Accept**.
  
    Ce contrat de licence est nécessaire pour télécharger Microsoft R Open, qui inclut une distribution des packages de base de R open source et des outils, ainsi que les packages R améliorés et des fournisseurs de connectivité à partir de l’équipe de développement de Microsoft R.
  
5. Une fois que vous avez accepté le contrat de licence, il existe une brève pause pendant que le programme d’installation est prêt. Cliquez sur **suivant** lorsque le bouton devient disponible.

6. Sur le **prêt pour l’installation** , vérifiez que les éléments suivants sont inclus, puis sélectionnez **installer**.

   + Services Moteur de base de données
   + R Services (dans la base de données)

    Note de l’emplacement du dossier sous le chemin d’accès `..\Setup Bootstrap\Log` où sont stockés les fichiers de configuration. Lorsque le programme d’installation est terminée, vous pouvez examiner les composants installés dans le fichier de synthèse.

7. Une fois l’installation terminée, si vous êtes invité à redémarrer l’ordinateur, faites-le maintenant. Il est important de lire le message affiché par l'Assistant Installation à la fin de l'installation. Pour plus d'informations, consultez [View and Read SQL Server Setup Log Files](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files).


##  <a name="bkmk_enableFeature"></a>Activer l’exécution du script

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
     
3. Pour activer la fonctionnalité de script externe, exécutez l’instruction suivante :
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
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

7. Si Launchpad est en cours d’exécution, il se peut que vous devez être en mesure d’exécuter R simple pour vérifier que les runtimes de script externes peut communiquer avec SQL Server. 

    Ouvrez une nouvelle **requête** fenêtre dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis exécutez un script comme ci-dessous :
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    Le script peut prendre un certain à exécuter, la première fois l’exécution de script externe est chargé. Les résultats doivent être quelque chose comme ceci :

    | hello |
    |----|
    | 1|

## <a name="bkmk_FollowUp"></a> Configuration supplémentaire

Si l’étape de vérification de script externe a réussi, vous pouvez exécuter des commandes de Python à partir de SQL Server Management Studio, Visual Studio Code ou tout autre client capable d’envoyer des instructions T-SQL sur le serveur.

Si vous rencontrez une erreur lors de l’exécution de la commande, passez en revue les étapes de configuration supplémentaires dans cette section. Vous devrez peut-être effectuer des configurations supplémentaires appropriées vers le service ou d’une base de données.

Scénarios courants qui nécessitent des modifications supplémentaires sont les suivantes :

* [Configurer le pare-feu Windows pour les connexions entrantes](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [Activer des protocoles réseau supplémentaires](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Activer les connexions distantes](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Étendre des autorisations intégrées aux utilisateurs distants](#bkmk_configureAccounts)
* [Accorder l’autorisation d’exécuter des scripts externes](#bkmk_AllowLogon)
* [Accorder l’accès aux bases de données individuelles](#permissions-db)

> [!NOTE]
> Pas toutes les modifications répertoriées sont requises, et aucun peut être requise. Configuration requise dépend de votre schéma de sécurité, où vous avez installé SQL Server, et que les utilisateurs pour se connecter à la base de données et exécuter des scripts externes. Conseils de dépannage supplémentaires, consultez : [FAQ d’installation et de mise à niveau](../r/upgrade-and-installation-faq-sql-server-r-services.md)

### <a name="bkmk_configureAccounts"></a>Activer l’authentification implicite pour le groupe de comptes Launchpad

Pendant l’installation, certains nouveaux comptes d’utilisateur Windows sont créés pour l’exécution des tâches situées dans le jeton de sécurité de le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service. Lorsqu’un utilisateur envoie un script R à partir d’un client externe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Active un compte de travail disponible, est mappé à l’identité de l’utilisateur appelant, et exécute le script R pour le compte de l’utilisateur. Ce nouveau service du moteur de base de données prend en charge l’exécution sécurisée de scripts externes, appelé *l’authentification implicite*.

Vous pouvez afficher ces comptes dans le groupe d’utilisateurs Windows **SQLRUserGroup**. Par défaut, 20 comptes de travail sont créés, ce qui est généralement plus que suffisant pour l’exécution de R de travaux.

Toutefois, si vous avez besoin d’exécuter des scripts R à partir d’un client de science des données à distance et que vous utilisez l’authentification Windows, vous devez accorder ces comptes de travail autorisation de se connecter à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance en votre nom.

1. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l’Explorateur d’objets, développez **Sécurité**, cliquez avec le bouton droit sur **Connexions**, puis sélectionnez **Nouvelle connexion**.
2. Dans le **nouvelle connexion** boîte de dialogue, sélectionnez **recherche**.
3. Sélectionnez le **Types d’objets** et **groupes** cases à cocher et désactivez toutes les autres cases à cocher.
4. Cliquez sur **avancé**, vérifiez que l’emplacement auquel rechercher est l’ordinateur actuel, puis cliquez sur **Rechercher maintenant**.
5. Faites défiler la liste des comptes de groupe sur le serveur jusqu'à ce que vous trouviez une commençant par `SQLRUserGroup`.
    
    + Le nom du groupe associé avec le service Launchpad de le _instance par défaut_ est toujours simplement **SQLRUserGroup**. Sélectionnez ce compte uniquement pour l’instance par défaut.
    + Si vous utilisez un _instance nommée_, le nom d’instance est ajouté au nom par défaut, `SQLRUserGroup`. Par conséquent, si votre instance est nommée « MLTEST », le nom du groupe utilisateur par défaut pour cette instance serait **SQLRUserGroupMLTest**.
5. Cliquez sur **OK** pour fermer la boîte de dialogue Recherche avancée, vérifiez que vous avez sélectionné le compte approprié pour l’instance. Chaque instance peut utiliser uniquement dans son propre service Launchpad et le groupe créé pour ce service.
6. Cliquez sur **OK** pour fermer la **sélectionner utilisateur ou groupe** boîte de dialogue.
7. Dans le **nouvelle connexion** boîte de dialogue, cliquez sur **OK**. Par défaut, la connexion est affectée au rôle **public** et est autorisée à se connecter au moteur de base de données.

### <a name="bkmk_AllowLogon"></a>Autoriser les utilisateurs à exécuter des scripts externes

> [!NOTE]
> Si vous utilisez une connexion SQL pour l’exécution des scripts R dans un contexte de calcul de SQL Server, cette étape n’est pas requise.

Si vous avez installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans votre propre instance, vous sont généralement l’exécution de scripts en tant qu’administrateur, ou au moins en tant que propriétaire de base de données, et par conséquent avoir des autorisations implicites pour diverses opérations, toutes les données dans la base de données et la possibilité d’installer de nouveaux packages en fonction des besoins.

Toutefois, dans un scénario d’entreprise, la plupart des utilisateurs, y compris les utilisateurs qui accèdent à la base de données à l’aide de connexions SQL, n’ont pas de ces autorisations élevées. Par conséquent, pour chaque utilisateur qui exécutent des scripts R, vous devez accorder les autorisations utilisateur pour exécuter des scripts dans chaque base de données sur laquelle les scripts externes seront utilisées.

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!TIP]
> Besoin d’aide pour la configuration ? Vous n’êtes pas sûr d’avoir effectué toutes les étapes ? Utilisez ces rapports personnalisés pour vérifier l’état de l’installation et exécuter des étapes supplémentaires. 
> 
> [Surveiller les Services Machine Learning à l’aide de rapports personnalisés](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

### <a name="permissions-db"></a> Donnez à vos utilisateurs lecture, écriture ou les autorisations DDL pour la base de données

Le compte d’utilisateur qui est utilisé pour exécuter R peut doivent lire les données à partir d’autres bases de données, créer des tables pour stocker les résultats et écrire des données dans des tables. Par conséquent, pour chaque utilisateur qui va exécuter des scripts R, vérifiez que l’utilisateur dispose des autorisations appropriées sur la base de données : *db_datareader*, *db_datawriter*, ou *db_ddladmin*.

Par exemple, l’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante donne à la connexion SQL *MySQLLogin* les droits nécessaires pour exécuter des requêtes T-SQL dans la base de données *RSamples* . Pour exécuter cette instruction, la connexion SQL doit déjà exister dans le contexte de sécurité du serveur.

```SQL
USE RSamples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Pour plus d’informations sur les autorisations incluses dans chaque rôle, consultez [rôles au niveau de la base de données](../../relational-databases/security/authentication-access/database-level-roles.md).


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Créer une source de données ODBC pour l’instance sur votre client de science des données

Si vous créez une solution R sur un ordinateur client de science des données et que vous avez besoin exécuter du code à l’aide de l’ordinateur SQL Server comme contexte de calcul, vous pouvez utiliser une connexion SQL ou l’authentification Windows intégrée.

* Pour une connexion SQL : vérifiez que la connexion a les autorisations appropriées sur la base de données dans laquelle vous allez lire des données. Vous pouvez le faire en ajoutant *se connecter à* et *sélectionnez* autorisations, ou en ajoutant la connexion à la *db_datareader* rôle. Pour les connexions dont avez besoin pour créer des objets, ajoutez *DDL_admin* droits. Pour les connexions qui doivent enregistrer les données dans les tables, ajoutez la connexion à la *db_datawriter* rôle.

* Pour l’authentification Windows : vous devrez peut-être configurer une source de données ODBC sur le client de science des données qui spécifie le nom d’instance et d’autres informations de connexion. Pour plus d’informations, consultez [administrateur de sources de données ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="suggested-optimizations"></a>Optimisations proposées

Maintenant que vous avez ce que tout fonctionne, vous souhaiterez également optimiser le serveur pour prendre en charge d’apprentissage, ou installer des modèles préformés.

### <a name="add-more-worker-accounts"></a>Ajouter plusieurs comptes de travail

Si vous pensez que vous pouvez utiliser largement R, ou si vous prévoyez de nombreux utilisateurs d’être en cours d’exécution de scripts simultanément, vous pouvez augmenter le nombre de comptes de travail qui sont affectés au service Launchpad. Pour plus d’informations, consultez [modifier le pool de comptes d’utilisateur pour SQL Server Machine Learning Services](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="bkmk_optimize"></a>Optimiser le serveur pour l’exécution du script externe

Les paramètres par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation sont destinées à optimiser l’équilibre du serveur pour un large éventail de services qui sont pris en charge par le moteur de base de données, ce qui peut inclure extraction, transformation et processus de chargement (ETL), création de rapports, l’audit, et les applications qui utilisent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données. Par conséquent, les paramètres par défaut, vous constaterez peut-être que les ressources pour l’apprentissage sont parfois restreintes ou limitées, en particulier dans les opérations gourmandes en mémoire.

Pour vous assurer que les travaux machine learning est classés par priorité et ressourcées, nous vous recommandons d’utiliser le gouverneur de ressources SQL Server pour configurer un pool de ressources externes. Vous souhaiterez également modifier la quantité de mémoire qui est allouée à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur de base de données ou augmenter le nombre de comptes qui s’exécutent sous le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service.

- Pour configurer un pool de ressources pour la gestion des ressources externes, consultez [créer un pool de ressources externe](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Pour modifier la quantité de mémoire réservée pour la base de données, consultez [options de configuration de mémoire serveur](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Pour modifier le nombre de comptes R qui peuvent être démarrés par [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], consultez [modifier le pool de comptes d’utilisateur pour l’apprentissage](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

Si vous utilisez l’Édition Standard et que vous ne disposez pas du gouverneur de ressources, vous pouvez utiliser les vues de gestion dynamique (DMV) et les événements étendus, ainsi que Windows contrôle des événements pour aider à gérer les ressources serveur utilisées par R. Pour plus d’informations, consultez [surveillance et gestion des Services de R](../r/managing-and-monitoring-r-solutions.md).

### <a name="install-additional-r-packages"></a>Installer des packages R supplémentaires

Les solutions R que vous créez pour SQL Server peuvent appeler des fonctions de base R, de fonctions à partir des packages propriétaires installés avec SQL Server, les packages R de tiers compatibles avec la version de R open source installé par SQL Server.

Installez les packages que vous souhaitez utiliser à partir de SQL Server dans la bibliothèque par défaut qui est utilisée par l’instance. Si vous avez une installation distincte de R sur l’ordinateur, ou si vous avez installé des packages dans les bibliothèques utilisateur, vous ne pourrez pas utiliser ces packages à partir de T-SQL.

Le processus d’installation et de gestion des packages R est différent dans SQL Server 2016 et SQL Server 2017. Dans SQL Server 2016, un administrateur de base de données doit installer les packages R que les utilisateurs ont besoin. Dans SQL Server 2017, vous pouvez configurer des groupes d’utilisateurs de partager les packages sur un niveau par base de données ou configurer des rôles de base de données pour permettre aux utilisateurs d’installer leurs propres packages. Pour plus d’informations, consultez [installer de nouveaux packages R](../r/install-additional-r-packages-on-sql-server.md).


## <a name="get-help"></a>Obtenir de l’aide

Besoin d’aide avec l’installation ou mise à niveau ? Pour obtenir des réponses aux questions courantes et les problèmes connus, consultez l’article suivant :

* [Mise à niveau et installation FAQ - Services Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Pour vérifier l’état d’installation de l’instance et résoudre les problèmes courants, essayez ces rapports personnalisés.

* [Rapports personnalisés pour SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Étapes suivantes

Aux développeurs R peuvent démarrer avec des exemples simples et apprendre les bases du fonctionne de R avec SQL Server. Pour votre prochaine étape, consultez les liens suivants :

+ [Didacticiel : Exécuter R dans T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Didacticiel : De base de données analytique pour les développeurs R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Pour afficher des exemples d’apprentissage qui sont basées sur des scénarios réels, consultez [d’apprentissage didacticiels](../tutorials/machine-learning-services-tutorials.md).


