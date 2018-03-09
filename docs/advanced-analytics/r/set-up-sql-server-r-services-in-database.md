---
title: "Configurer SQL Server Machine Learning Services (de-de base de données) | Documents Microsoft"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- Installation de SQL Server R Services
- installation de SQL Server Machine Learning Services
- Configurer les Services de R
- "installer l’apprentissage de SQL"
ms.assetid: 4d773c74-c779-4fc2-b1b6-ec4b4990950d
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Active
ms.openlocfilehash: 4d18a45b40c7f80ae2b46514f6c8245b80f6b142
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2018
---
# <a name="set-up-sql-server-machine-learning-services-in-database"></a>Configurer SQL Server Machine Learning Services (de-de base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette rubrique explique comment installer et configurer le fonctionnalités qui prennent en charge dans base de données analytique dans SQL Server d’apprentissage suivante :

+ **SQL Server 2016 R Services (de-de base de données)**. Si vous disposez de SQL Server 2016, installez cette fonctionnalité pour permettre l’exécution du code R dans SQL Server. Nécessite le moteur de base de données.

    [Configurer d’apprentissage dans SQL Server 2016](#bkmk_2016top)

+ **SQL Server 2017 Machine Learning Services (de-de base de données)**. Si vous disposez de SQL Server 2017, installez cette option pour exécuter le code R (ou Python) dans SQL Server. Nécessite le moteur de base de données. 

    [Configurer SQL Server 2017 apprentissage](#bkmk_2017top)

+ Un serveur d’apprentissage machine avec **aucune** SQL Server

    [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation inclut également la possibilité d’installer une version « autonome » de l’apprentissage automatique des composants qui ne nécessite pas le moteur de base de données et ne s’exécute pas dans SQL Server.  En règle générale, nous recommandons que vous installez cette option sur un ordinateur autre que l’ordinateur qui héberge SQL Server.
    
    [Configurer un serveur autonome apprentissage](create-a-standalone-r-server.md).

Cet article décrit le processus du programme d’installation utilise le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant installation. Pour l’installation de ligne de commande, ou pour télécharger les programmes d’installation à utiliser dans les serveurs en mode hors connexion, consultez les articles suivants :

+ [Installer R pour SQL Server à partir de la ligne de commande](unattended-installs-of-sql-server-r-services.md)
+ [Installez Python pour SQL Server à partir de la ligne de commande](../python/unattended-installs-of-sql-server-python-services.md)
+ [Installer un serveur autonome machine learning à partir de la ligne de commande](install-microsoft-r-server-from-the-command-line.md)
+ [Installer les composants de la machine learning sur un serveur avec aucune ACE internet](installing-ml-components-without-internet-access.md)

**S’applique à :** SQL Server 2016, SQL Server 2017

## <a name="bkmk_prereqs"></a> Liste de vérification de préinstallation

+ Machine learning dans-base de données nécessite SQL Server 2016 ou version ultérieure. 

+ Langues prises en charge : 

    + SQL Server 2016 prend uniquement en charge R. 

    + R est également disponible sous une fonctionnalité d’aperçu dans la base de données SQL Azure, avec certaines limitations. Pour plus d’informations, consultez [à l’aide de R dans la base de données SQL Azure](using-r-in-azure-sql-database.md)

    + Pour utiliser Python nécessite SQL Server 2017 ou version ultérieure.

+ Si vous avez utilisé les versions antérieures de l’environnement de développement Revolution Analytique ou les packages RevoScaleR, ou si vous avez installé des versions préliminaires de SQL Server 2016, vous devez les désinstaller. Installation de côte à côte n’est pas prise en charge. Pour supprimer les versions précédentes, consultez [mise à niveau et Installation Forum aux questions sur SQL Server Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

+ Vous ne pouvez pas installer SQL Server 2016 R Services ou SQL Server 2017 Machine Learning Services sur un contrôleur de domaine. La partie de R Services ou Machine Learning Services du programme d’installation échoue.

+ Vous ne pouvez pas installer les fonctionnalités sur un cluster de basculement d’apprentissage automatique. Le mécanisme de sécurité qui est utilisé pour isoler les processus de script externe n’est pas compatible avec un environnement de cluster de basculement Windows Server. Pour résoudre ce problème, vous pouvez effectuer les opérations suivantes :
    * Utiliser la réplication pour copier les tables nécessaires à une instance de SQL Server avec machine learning est activé.
    * Installez l’apprentissage sur un ordinateur autonome qui utilise AlwaysOn et fait partie d’un groupe de disponibilité.

+ L’infrastructure d’apprentissage automatique requiert une configuration supplémentaire après l’installation. Les étapes exactes dépendent de votre organisation et les stratégies de sécurité, les configuration du serveur et les utilisateurs prévus. Nous vous recommandons d’examiner toutes les étapes et déterminer une configuration supplémentaire qui peut être nécessaire dans votre environnement.

## <a name="bkmk2016top"></a>Installer SQL Server 2016 R Services (de-de base de données)

> [!div class="checklist"]
> * Installer le moteur de base de données et l’apprentissage des fonctionnalités
> * Les étapes de post-installation requises : activer l’apprentissage et redémarrer
> * Les étapes de post-installation facultatives : ajouter des règles de pare-feu, d’ajouter des utilisateurs, de modifier ou de configurer des comptes de service, configurer un client de science des données distantes

**À l’aide de l’Assistant Installation de SQL Server 2016**

1. Ouvrez l’Assistant Installation de SQL Server.

2. Sur le **Installation** onglet, sélectionnez **nouvelle installation SQL Server autonome ou ajouter des fonctionnalités à une installation existante**.

    
     ![Installer R Services (de-de base de données)](media/2016-setup-installation-rsvcs.png "démarrer l’installation du moteur de base de données avec R Services")
   
3. Sur le **sélection des fonctionnalités** , sélectionnez les options suivantes :

   - Sélectionnez **Services moteur de base de données**. Le moteur de base de données est requise dans chaque instance qui utilise l’apprentissage.
   - Sélectionnez **R Services (de-de base de données)**. Installe la prise en charge pour une utilisation dans base de données de R.
    
     ![Sélection des fonctionnalités de R Services](media/2016setup-rsvcs-features.png ", sélectionnez ces fonctionnalités pour R Services dans-base de données")

    > [!IMPORTANT]
    > N’installez pas le serveur R et R Services en même temps. En général vous installer R Server (autonome) pour créer un environnement un chercheur de données ou le développeur utilise pour se connecter à SQL Server et déployer des solutions R. Vous n’avez donc pas besoin de les installer sur le même ordinateur.

4.  Sur le **donner son consentement pour installer Microsoft R Open** , cliquez sur **accepter**.
  
    Ce contrat de licence est nécessaire pour télécharger Microsoft R Open, qui inclut une distribution des packages de base R open source et des outils, ainsi que les packages R améliorés et des fournisseurs de connectivité de l’équipe de développement Microsoft R.
  
    Si l’ordinateur que vous utilisez n’a pas accès à internet, vous pouvez interrompre l’installation à ce stade pour télécharger les programmes d’installation séparément, comme décrit dans [composants d’installation de R sans accès à internet](installing-ml-components-without-internet-access.md).
  
5. Une fois que vous avez accepté le contrat de licence, il existe une brève pause pendant que le programme d’installation est prêt. Cliquez sur **suivant** lorsque le bouton devient disponible.

6. Sur le **prêt pour l’installation** , vérifiez que les éléments suivants sont inclus, puis sélectionnez **installer**.

   + Services Moteur de base de données
   + R Services (dans la base de données)

7. Lors de l’installation est terminée, redémarrez votre ordinateur.


## <a name="bkmk2017top"></a>Installer SQL Server 2017 Machine Learning Services (de-de base de données)

> [!div class="checklist"]
> * Installer le moteur de base de données et l’apprentissage des fonctionnalités
> * Les étapes de post-installation requises : activer l’apprentissage et redémarrer
> * Les étapes de post-installation facultatives : ajouter des règles de pare-feu, d’ajouter des utilisateurs, de modifier ou de configurer des comptes de service, configurer un client de science des données distantes.

**Prise en main**

1. Exécutez le programme d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
2. Sur le **Installation** onglet, sélectionnez **nouvelle installation SQL Server autonome ou ajouter des fonctionnalités à une installation existante**.

     ![Installer les Services de formation d’ordinateur (de-de base de données)](media/2017setup-installation-page-mlsvcs.png "démarrer l’installation du moteur de base de données avec les Services de Machine Learning")

3. Sur le **sélection des fonctionnalités** , sélectionnez les options suivantes :
   
    + Sélectionnez **Services moteur de base de données**. Le moteur de base de données est requise dans chaque instance qui utilise l’apprentissage.

    + Sélectionnez **(de-de base de données) de Services d’apprentissage**. Cette option installe la prise en charge pour une utilisation dans base de données de R. Une fois que vous sélectionnez cette option, vous pouvez sélectionner la langue d’apprentissage. Vous pouvez sélectionner uniquement les R, ou vous pouvez ajouter à la fois R et Python.
   
    ![Sélection des fonctionnalités de machine Learning Services](media/2017setup-features-page-mls-rpy.png ", sélectionnez ces fonctionnalités pour R Services dans-base de données")

    Si vous ne sélectionnez pas les options de langage Python ou R, l’Assistant Installation installe uniquement l’infrastructure d’extensibilité, qui inclut SQL Server approuvée Launchpad et n’installe pas les composants spécifiques à une langue.  En règle générale, nous vous recommandons d’installer au moins une langue pour commencer. Toutefois, vous pouvez utiliser cette option si vous envisagez d’utiliser immédiatement le processus de liaison pour mettre à niveau les composants d’apprentissage automatique. Pour plus d’informations, consultez [SqlBindR utilisé pour mettre à niveau une instance de R Services](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

    Il est recommandé que vous **pas** installation autonome et la base de données sur le même ordinateur et jamais les installer en même temps. Vous installerez habituellement Machine Learning Server (autonome) pour créer un environnement un chercheur de données ou le développeur utilise pour se connecter à SQL Server lors du déploiement de solutions. Vous n’avez donc pas besoin de les installer sur le même ordinateur.

4.  Pour l’apprentissage des contrats de licence : selon les langues que vous installez, vous devez accepter les contrats de licence pour R ou Python.

    + Termes du contrat de licence de ce contrat de licence de r : couvre Microsoft R Open, qui inclut une distribution des packages de base R open source et des outils, ainsi que les packages R améliorés et des fournisseurs de connectivité de l’équipe de développement Microsoft.
  
    + Termes du contrat de licence pour Python. Le contrat de licence open source Python couvre également Anaconda et les outils connexes, ainsi que certaines bibliothèques Python de nouveau à partir de l’équipe de développement Microsoft.

    Cliquez sur **accepter** pour indiquer votre accord. Il existe une brève pause pendant que les composants sont prêts, le **suivant** bouton devient disponible.

    Si l’ordinateur que vous utilisez n’a pas accès à internet, vous pouvez interrompre l’installation à ce stade pour télécharger les programmes d’installation séparément, comme décrit ici : [installer les composants d’apprentissage ordinateur sans accès à internet](installing-ml-components-without-internet-access.md).

6. Sur le **prêt pour l’installation** , vérifiez que les éléments suivants sont inclus, puis sélectionnez **installer**.

   - Services Moteur de base de données
   - Machine Learning Services (en base de données)
   - R ou Python ou les deux

7. Une fois l’installation terminée, prenez note de l’emplacement du journal d’installation, puis redémarrez votre ordinateur.

###  <a name="bkmk_enableFeature"></a>Étapes de post-installation requises

Pour des raisons de sécurité, la fonctionnalité d’apprentissage machine n’est pas activée par défaut même si la fonctionnalité a été installée. Un administrateur de serveur doit activer la fonctionnalité et redémarrez l’instance. 

Cette section décrit comment reconfigurer l’instance pour l’apprentissage. Configuration définit les comptes de service externe et démarre le service Launchpad.

1. Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. S’il n’est pas déjà installé, vous pouvez réexécuter l’Assistant de configuration de SQL Server pour ouvrir un lien de téléchargement et l’installer.
  
2. Connectez-vous à l’instance où vous avez installé l’apprentissage et puis exécutez la commande suivante :

   ```SQL
   sp_configure
   ```

    Recherchez la valeur de la **scripts externes activés** propriété, qui doit être **0**. C’est parce que la fonctionnalité est désactivée par défaut afin de réduire la surface d’exposition.
     
3. Pour activer la fonctionnalité de script externe, exécutez l’instruction suivante :
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
4. Redémarrez le service SQL Server pour l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Redémarrage du service SQL Server également le redémarrage automatique connexe [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service.

    Vous pouvez redémarrer le service à l’aide de la **Services** Panneau de configuration dans le panneau de configuration ou à l’aide du Gestionnaire de Configuration SQL Server.

5. Pour vérifier que le service d’exécution de script externe est activé dans SQL Server Management Studio, ouvrez une nouvelle **requête** fenêtre, puis exécutez la commande suivante :
  
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```
    La valeur **run_value** doit maintenant être définie sur 1.
    
6. Ouvrez le **Services** panneau et vérifiez que le service Launchpad de votre instance est en cours d’exécution. Si vous installez plusieurs instances, chaque instance a son propre service Launchpad.

7. Il est judicieux d’exécuter un script simple pour vérifier que les exécutions de scripts externes peuvent communiquer avec SQL Server. 

    Ouvrez une nouvelle **requête** fenêtre dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis exécutez un script tel que le suivant :
    
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

    Le script peut prendre un peu pendant le chargement à exécuter, la première fois que l’exécution du script externe. Les résultats doivent être quelque chose comme ceci :

    | hello |
    |----|
    | 1|


8. Si vous obtenez des erreurs, passez à la section décrivant les autres modifications facultatif que vous devrez peut-être effectuer une fois l’installation terminée, ou consultez le guide de dépannage :

    + [Les étapes de post-installation facultatives : configurer le service et les autorisations](#bkmk_FollowUp) 
    + [Résolution des problèmes d’apprentissage dans SQL Server](upgrade-and-installation-faq-sql-server-r-services.md)

## <a name="bkmk_FollowUp"></a>Étapes de post-installation facultatives

En fonction de votre cas d’usage pour l’apprentissage, vous devrez peut-être apporter des modifications supplémentaires pour le serveur, le pare-feu, les comptes utilisés par le service, ou les autorisations de base de données. Les modifications que vous devez effectuer varient selon le cas.

Scénarios courants qui nécessitent des modifications supplémentaires sont les suivantes :

* Modification des règles de pare-feu pour autoriser les connexions entrantes vers SQL Server.
* L’activation des protocoles réseau supplémentaires.
* S’assurer que le serveur prend en charge les connexions à distance.
* L’activation de *l’authentification implicite*, si les utilisateurs accéder aux données SQL Server à partir d’un client de science des données à distance et d’exécuter du code à l’aide du package RODBC ou un autre fournisseur ODBC.
* Donnez aux utilisateurs l’accès aux bases de données individuelles.
* Résolution des problèmes de sécurité qui empêchent la communication avec le service Launchpad.
* S’assurer que les utilisateurs sont autorisés à exécuter du code ou installer des packages.

> [!NOTE]
> Pas toutes les modifications répertoriées peuvent être nécessaire. Toutefois, nous vous recommandons de consulter tous les éléments pour voir si elles sont applicables à votre scénario.

Conseils de dépannage supplémentaires se trouve ici : [FAQ d’installation et de mise à niveau](../r/upgrade-and-installation-faq-sql-server-r-services.md)

### <a name="bkmk_configureAccounts"></a>Activer l’authentification implicite pour le groupe de comptes Launchpad

Pendant l’installation, certains nouveaux comptes d’utilisateur Windows sont créés pour l’exécution de tâches sous le jeton de sécurité de le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service. Lorsqu’un utilisateur envoie un script R à partir d’un client externe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Active un compte de travail disponible, il est mappé à l’identité de l’utilisateur appelant et exécute le script R pour le compte de l’utilisateur. Ce nouveau service du moteur de base de données prend en charge l’exécution sécurisée de scripts externes, appelé *l’authentification implicite*.

Vous pouvez afficher ces comptes dans le groupe d’utilisateurs Windows **SQLRUserGroup**. Par défaut, 20 comptes de travail sont créés, qui est généralement plus que suffisant pour R en cours d’exécution des travaux.

Toutefois, si vous avez besoin d’exécuter des scripts R à partir d’un client de science des données distantes et utilisez l’authentification Windows, vous devez accorder ces comptes de travailleur autorisé à se connecter à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance à votre place.

1. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l’Explorateur d’objets, développez **Sécurité**, cliquez avec le bouton droit sur **Connexions**, puis sélectionnez **Nouvelle connexion**.
2. Dans le **nouvelle connexion** boîte de dialogue, sélectionnez **recherche**.
3. Sélectionnez le **les Types d’objets** et **groupes** cases à cocher et désactivez toutes les autres cases à cocher.
4. Cliquez sur **avancé**, vérifiez que l’emplacement de recherche est l’ordinateur actuel et puis cliquez sur **Rechercher maintenant**.
5. Faites défiler la liste des comptes de groupe sur le serveur jusqu'à ce que vous trouviez une commençant par `SQLRUserGroup`.
    
    + Le nom du groupe associé avec le service Launchpad pour le _instance par défaut_ est toujours simplement **SQLRUserGroup**. Sélectionner ce compte uniquement pour l’instance par défaut.
    + Si vous utilisez un _instance nommée_, le nom d’instance est ajouté au nom par défaut, `SQLRUserGroup`. Par conséquent, si votre instance est nommée « MLTEST », le nom du groupe utilisateur par défaut pour cette instance serait **SQLRUserGroupMLTest**.
5. Cliquez sur **OK** pour fermer la boîte de dialogue Recherche avancée, vérifiez que vous avez sélectionné le compte approprié pour l’instance. Chaque instance peut utiliser uniquement son propre service Launchpad et le groupe créé pour ce service.
6. Cliquez sur **OK** pour fermer la **sélectionner utilisateur ou groupe** boîte de dialogue.
7. Dans le **nouvelle connexion** boîte de dialogue, cliquez sur **OK**. Par défaut, la connexion est affectée au rôle **public** et est autorisée à se connecter au moteur de base de données.

### <a name="bkmk_AllowLogon"></a>Autoriser les utilisateurs à exécuter des scripts externes

> [!NOTE]
> Si vous utilisez une connexion SQL pour l’exécution des scripts R dans un contexte de calcul de SQL Server, cette étape n’est pas requise.

Si vous avez installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans votre propre instance, vous sont généralement l’exécution de scripts en tant qu’administrateur, ou au moins en tant que propriétaire de base de données, et qui n’ont donc des autorisations implicites pour diverses opérations, toutes les données dans la base de données et la possibilité d’installer de nouveaux packages en fonction des besoins.

Toutefois, dans un scénario d’entreprise, la plupart des utilisateurs, y compris les utilisateurs qui accèdent à la base de données à l’aide de connexions SQL, n’ont pas de telles autorisations avec élévation de privilèges. Par conséquent, pour chaque utilisateur qui exécutent des scripts R ou Python, vous devez accorder les autorisations utilisateur pour exécuter des scripts dans chaque base de données où les scripts externes seront utilisés.

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!TIP]
> Besoin d’aide pour la configuration ? Vous n’êtes pas sûr d’avoir effectué toutes les étapes ? Utilisez ces rapports personnalisés pour vérifier l’état de l’installation et d’exécuter des étapes supplémentaires. 
> 
> [Surveiller les Services d’apprentissage Machine à l’aide de rapports personnalisés](monitor-r-services-using-custom-reports-in-management-studio.md).

### <a name="ensure-that-the-sql-server-computer-supports-remote-connections"></a>Assurez-vous que l’ordinateur SQL Server prend en charge les connexions à distance

Si vous ne pouvez pas vous connecter à partir d’un ordinateur distant, vérifiez si le serveur autorise les connexions à distance. Les connexions à distance sont parfois désactivées par défaut.

Vérifiez également si le pare-feu autorise l’accès à SQL Server. Par défaut, le port utilisé par SQL Server est souvent bloqué par le pare-feu. Si vous utilisez le pare-feu Windows, consultez [configurer le pare-feu Windows pour accéder au moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).

### <a name="give-your-users-read-write-or-ddl-permissions-to-the-database"></a>Donnez à vos utilisateurs de lecture, écriture ou les autorisations de DDL pour la base de données

Le compte d’utilisateur qui est utilisé pour exécuter R ou Python peut doivent lire les données à partir d’autres bases de données, créer des tables pour stocker les résultats et écrire des données dans des tables. Par conséquent, pour chaque utilisateur qui doit exécuter les scripts R ou Python, vérifiez que l’utilisateur dispose des autorisations appropriées sur la base de données : *db_datareader*, *db_datawriter*, ou *db_ ddladmin*.

Par exemple, l’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante donne à la connexion SQL *MySQLLogin* les droits nécessaires pour exécuter des requêtes T-SQL dans la base de données *RSamples* . Pour exécuter cette instruction, la connexion SQL doit déjà exister dans le contexte de sécurité du serveur.

```SQL
USE RSamples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Pour plus d’informations sur les autorisations incluses dans chaque rôle, consultez [rôles au niveau de la base de données](../../relational-databases/security/authentication-access/database-level-roles.md).

### <a name="use-machine-learning-in-an-azure-vm"></a>Utiliser machine learning dans une machine virtuelle Azure

Si vous avez installé les Services de Machine Learning (ou R Services) sur une machine virtuelle Azure, vous devrez peut-être modifier certains paramètres par défaut supplémentaires. Pour plus d’informations, consultez [l’installation de SQL Server Machine Learning sur une machine virtuelle Azure](installing-sql-server-r-services-on-an-azure-virtual-machine.md).

### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Créer une source de données ODBC pour l’instance sur votre client de science des données

Si vous créez une solution R sur un ordinateur client de science des données et que vous avez besoin exécuter du code à l’aide de l’ordinateur SQL Server en tant que le contexte de calcul, vous pouvez utiliser un compte de connexion SQL ou l’authentification Windows intégrée.

* Pour une connexion SQL : vérifiez que la connexion a les autorisations appropriées sur la base de données dans laquelle vous allez lire des données. Vous pouvez le faire en ajoutant *se connecter à* et *sélectionnez* autorisations, ou en ajoutant de la connexion à la *db_datareader* rôle. Pour les connexions que vous avez besoin pour créer des objets, ajoutez *DDL_admin* droits. Pour les connexions qui doivent enregistrer les données dans les tables, ajoutez la connexion à la *db_datawriter* rôle.

* Pour l’authentification Windows : vous devrez peut-être configurer une source de données ODBC sur le client de science des données qui spécifie le nom d’instance et d’autres informations de connexion. Pour plus d’informations, consultez [administrateur de sources de données ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="next-steps"></a>Étapes suivantes

Après avoir vérifié que la fonctionnalité de l’exécution du script fonctionne dans SQL Server, vous pouvez exécuter des commandes R et Python à partir de SQL Server Management Studio, Visual Studio Code ou tout autre client qui peut envoyer des instructions T-SQL sur le serveur. Avant cela, vous pourriez apporter des modifications à la configuration du système pour prendre en charge une utilisation intensive de l’apprentissage, ou ajouter de nouveaux packages R.

Cette section répertorie certaines optimisations courantes et les activités d’apprentissage pour l’apprentissage.

### <a name="add-more-worker-accounts"></a>Ajoutez d’autres comptes de travail

Si vous pensez que vous pouvez utiliser R importante, ou si vous prévoyez de nombreux utilisateurs d’être en cours d’exécution des scripts en même temps, vous pouvez augmenter le nombre de comptes de travail qui sont affectés au service Launchpad. Pour plus d’informations, consultez [modifier le pool de comptes d’utilisateur pour SQL Server Machine Learning Services](modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="bkmk_optimize"></a>Optimiser le serveur pour l’exécution du script externe

Les paramètres par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation sont destinées à optimiser l’équilibre entre le serveur pour une multitude de services qui sont pris en charge par le moteur de base de données, ce qui peut inclure extraction, transformation et processus de chargement (ETL), création de rapports, l’audit, et les applications qui utilisent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données. Par conséquent, les paramètres par défaut, vous constaterez que les ressources pour l’apprentissage sont parfois restreinte ou limitées, en particulier dans les opérations gourmandes en mémoire.

Pour vous assurer que les tâches d’apprentissage machine sont classés par priorité et avec la ressource appropriée, nous vous recommandons d’utiliser le gouverneur de ressources SQL Server pour configurer un pool de ressources externes. Vous pouvez également modifier la quantité de mémoire qui est allouée à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du moteur de base de données, ou augmentez le nombre de comptes qui s’exécutent sous le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service.

- Pour configurer un pool de ressources pour la gestion des ressources externes, consultez [créer un pool de ressources externes](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Pour modifier la quantité de mémoire réservée à la base de données, consultez [mémoire option de configuration](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Pour modifier le nombre de comptes R qui peut être démarrée par [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], consultez [modifier le pool de comptes d’utilisateur pour l’apprentissage](modify-the-user-account-pool-for-sql-server-r-services.md).

Si vous utilisez l’Édition Standard et que vous n’avez pas le gouverneur de ressources, vous pouvez utiliser les vues de gestion dynamique (DMV) et les événements étendus, ainsi que les événements Windows analyse, pour aider à gérer les ressources de serveur qui sont utilisées par R. Pour plus d’informations, consultez [analyse et la gestion des Services de R](managing-and-monitoring-r-solutions.md).

### <a name="install-additional-r-packages"></a>Installer des packages R supplémentaires

Prenez une minute pour installer les packages R supplémentaires que vous allez utiliser.

Installez les packages que vous souhaitez utiliser à partir de SQL Server dans la bibliothèque par défaut qui est utilisée par l’instance. Si vous avez une installation distincte de R sur l’ordinateur, ou si vous avez installé les packages dans les bibliothèques utilisateur, vous ne pourrez pas utiliser ces packages à partir de T-SQL.

Le processus d’installation et la gestion des packages R est différent dans SQL Server 2016 et SQL Server 2017. Par exemple, dans SQL Server 2017, vous pouvez définir des groupes d’utilisateurs de partager des packages sur un niveau de base de données ou configurer des rôles de base de données pour permettre aux utilisateurs d’installer leurs propres packages. Pour plus d’informations, consultez [gestion des packages](r-package-management-for-sql-server-r-services.md).

Dans SQL Server 2016, un administrateur de base de données doit installer des packages R les utilisateurs ont besoin.

Accès d’administration est également requis pour installer des packages Python supplémentaires dans la bibliothèque de l’instance.

### <a name="upgrade-the-machine-learning-components"></a>Mettre à niveau les composants d’apprentissage automatique

Lorsque vous installez des fonctionnalités de machine learning dans SQL Server, vous obtiendrez la version des composants R ou Python qui a été actualisée lors de la mise en production ou le service pack a été publié. Chaque fois que des correctifs ou de mettre à niveau le serveur, les machine learning composants sont mis à niveau ainsi.

Toutefois, vous pouvez mettre à niveau les composants sur une planification plus rapide qu’est pris en charge d’apprentissage par les versions de SQL Server, à l’aide d’un processus appelé _liaison_. Lorsque vous liez une instance de SQL Server, vous les mettez à niveau les versions de R ou Python et modifiez à une stratégie de prise en charge différentes qui prend en charge les mises à jour plus fréquentes. 

Ces mises à jour peuvent inclure :

* Nouveaux packages R
+ Nouvelles API pour Microsoft les packages tels que [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package).
* [Modèles de pretrained](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models) pour l’analyse de texte et de classification d’image.

Pour plus d’informations sur la mise à niveau une instance de SQL Server, consultez [mise à niveau des composants de machine learning via la liaison](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).


### <a name="tutorials"></a>Didacticiels

Pour commencer avec des exemples simples et découvrez comment R fonctionne avec SQL Server, consultez [du code à l’aide de R dans Transact-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).

Pour afficher des exemples d’apprentissage automatique qui sont basées sur des scénarios concrets, consultez [Machine learning didacticiels](../tutorials/machine-learning-services-tutorials.md).

### <a name="troubleshooting"></a>Dépannage

Vous rencontrez des problèmes ? La tentative de mise à niveau ? Pour obtenir des réponses aux questions les plus fréquentes et les problèmes connus, consultez l’article suivant :

* [Mise à niveau et installation FAQ - Machine Learning Services](upgrade-and-installation-faq-sql-server-r-services.md)

Pour vérifier l’état d’installation de l’instance et résoudre les problèmes courants, essayez de ces rapports personnalisés.

* [Rapports personnalisés pour SQL Server R Services](\r\monitor-r-services-using-custom-reports-in-management-studio.md)
