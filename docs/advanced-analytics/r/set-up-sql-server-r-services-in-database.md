---
title: "Configurer SQL Server Machine Learning Services (de-de base de données) | Documents Microsoft"
ms.custom: 
ms.date: 09/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- Installation de SQL Server R Services
ms.assetid: 4d773c74-c779-4fc2-b1b6-ec4b4990950d
caps.latest.revision: 36
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: e76675099ab290d29231d434eb74e92b613185b7
ms.openlocfilehash: 9b3449e8c1f19ee69b36107f3530eac80fae0227
ms.contentlocale: fr-fr
ms.lasthandoff: 09/29/2017

---
# <a name="set-up-sql-server-machine-learning-services-in-database"></a>Configurer SQL Server Machine Learning Services (de-de base de données)

Cette rubrique explique comment configurer la Machine Learning Services dans SQL Server à l’aide de le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant installation.

**S’applique à :** SQL Server 2016 R Services (R uniquement), SQL Server 2017 Machine Learning (R et Python)

## <a name="machine-learning-options-in-sql-server-setup"></a>Apprentissage des options dans le programme d’installation de SQL Server

Le programme d’installation de SQL Server fournit les options suivantes pour l’installation d’apprentissage :

* Installer un apprentissage avec la base de données SQL Server

  Cette option vous permet d’exécuter des scripts R ou Python à l’aide d’une procédure stockée. Vous pouvez également utiliser l’ordinateur SQL Server comme contexte de calcul à distance pour les scripts R ou Python qui sont exécutés à partir d’une connexion externe.

  Pour installer cette option :
  
  * Dans SQL Server 2016, sélectionnez **R Services (de-de base de données)**.
  * Dans SQL Server 2017, sélectionnez **Machine Learning Services (de-de base de données)**.


* Installer un serveur d’apprentissage machine autonome

  Cette option permet de créer un environnement de développement pour l’apprentissage des solutions qui ne requièrent pas ou utilisez SQL Server. Par conséquent, nous déconseillons généralement que vous installez cette option sur un autre ordinateur que le serveur hôte SQL Server. Pour plus d’informations sur cette option, consultez [créer un Standalone R Server](../r/create-a-standalone-r-server.md).

Le processus d’installation nécessite plusieurs étapes, dont certains sont facultatifs. Les aspects facultatif dépendent des deux comment vous envisagez d’utiliser l’apprentissage automatique et l’état de votre environnement de sécurité. 

## <a name="bkmk_prereqs"></a> Conditions préalables

*  Évitez d’installer R Server et les Services de R en même temps. En général vous installer R Server (autonome) pour créer un environnement un chercheur de données ou le développeur utilise pour se connecter à SQL Server et déployer des solutions R. Vous n’avez donc pas besoin de les installer sur le même ordinateur.

* Si vous avez utilisé les versions antérieures de l’environnement de développement Revolution Analytique ou les packages RevoScaleR, ou si vous avez installé des versions préliminaires de SQL Server 2016, vous devez les désinstaller. Installation de côte à côte n’est pas prise en charge. Pour supprimer les versions précédentes, consultez [mise à niveau et Installation Forum aux questions sur SQL Server R Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

* Vous ne pouvez pas installer les Services de Machine Learning sur un cluster de basculement. La raison est que le mécanisme de sécurité qui est utilisé pour isoler les processus de script externe n’est pas compatible avec un environnement de cluster de basculement Windows Server. Pour résoudre ce problème, vous pouvez effectuer les opérations suivantes :
    * Utiliser la réplication pour copier les tables nécessaires à une instance de SQL Server autonome avec R Services.
    * Installer [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sur un ordinateur autonome qui utilise AlwaysOn et fait partie d’un groupe de disponibilité.

> [!IMPORTANT]
> Une fois l’installation terminée, certaines étapes supplémentaires sont requises pour activer la fonctionnalité d’apprentissage. Vous pourrez également besoin pour accorder des autorisations aux utilisateurs sur les bases de données spécifiques, modifier ou configurer les comptes d’ou configurer un client de science des données distantes.

##  <a name="bkmk_installExt"></a>Étape 1 : Installer les fonctionnalités d’extensibilité et choisissez une langue d’apprentissage

Pour utiliser l’apprentissage automatique, vous devez installer SQL Server 2016 ou version ultérieure. Pour utiliser [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], au moins une instance du moteur de base de données est requise. Vous pouvez utiliser l’instance par défaut ou une instance nommée.

1. Exécutez le programme d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    Pour plus d’informations sur la façon d’effectuer des installations sans assistance, consultez [Unattended l’installation de SQL Server R Services](../r/unattended-installs-of-sql-server-r-services.md).
  
2. Sur le **Installation** onglet, sélectionnez **nouvelle installation SQL Server autonome ou ajouter des fonctionnalités à une installation existante**.
   
3. Sur le **sélection des fonctionnalités** tâches de page, pour installer les services de base de données utilisées par R et installe les extensions qui prennent en charge des scripts et processus externes, sélectionnez les options suivantes :
   
   **SQL Server 2016**
   - Sélectionnez **Services moteur de base de données**.
   - Sélectionnez **R Services (de-de base de données)**.

   **SQL Server 2017**
   - Sélectionnez **Services moteur de base de données**.
   - Sélectionnez **(de-de base de données) de Services d’apprentissage**.
   - Sélectionnez au moins un apprentissage de langue à activer. Vous pouvez sélectionner uniquement les R, ou vous pouvez ajouter à la fois R et Python.
   
   > [!NOTE]
   > Si vous ne sélectionnez pas les options de langage Python ou R, l’Assistant Installation installe uniquement l’infrastructure d’extensibilité, qui inclut le Launchpad de confiance de SQL Server, mais il n’installe pas les composants spécifiques à une langue. Cette option est pour la liaison de l’instance SQL Server R ou Python dans le cadre de la stratégie de cycle de vie moderne de Microsoft. Pour plus d’informations, consultez [SqlBindR utilisé pour mettre à niveau une instance de R Services](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

4.  Sur le **donner son consentement pour installer Microsoft R Open** page, sélectionnez **accepter**.
  
     Ce contrat de licence est nécessaire pour télécharger Microsoft R Open, qui inclut une distribution des packages de base R open source et des outils, ainsi que les packages R améliorés et des fournisseurs de connectivité de l’équipe de développement Microsoft R.
  
    > [!NOTE]
    >  Si l’ordinateur que vous utilisez n’a pas accès à internet, vous pouvez interrompre l’installation à ce stade pour télécharger les programmes d’installation séparément, comme décrit dans [composants d’installation de R sans accès à internet](installing-ml-components-without-internet-access.md).
  
5. Sélectionnez **Suivant**.

6. Sur le **prêt pour l’installation** , vérifiez que les éléments suivants sont inclus, puis sélectionnez **installer**.

   **SQL Server 2017**
   - Services Moteur de base de données
   - Machine Learning Services (en base de données)
   - R ou Python ou les deux

   **SQL Server 2016**
   - Services Moteur de base de données
   - R Services (dans la base de données)

7. Une fois l’installation terminée, redémarrez votre ordinateur.

##  <a name="bkmk_enableFeature"></a>Étape 2 : Activer les services de script externe

1. Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. S’il n’est pas déjà installé, vous pouvez réexécuter l’Assistant de configuration de SQL Server pour ouvrir un lien de téléchargement et l’installer.
  
2. Connectez-vous à l’instance où vous avez installé l’apprentissage et puis exécutez la commande suivante :

   ```SQL
   sp_configure
   ```

    La valeur de la **scripts externes activés** propriété doit maintenant être **0**. C’est parce que la fonctionnalité est désactivée par défaut afin de réduire la surface d’exposition, et il doit être explicitement activé par un administrateur.
     
3. Pour activer la fonctionnalité de script externe, exécutez l’instruction suivante :
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
4. Redémarrez le service SQL Server pour l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Redémarrage du service SQL Server également le redémarrage automatique connexe [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service.

    Vous pouvez redémarrer le service à l’aide de la **Services** Panneau de configuration dans le panneau de configuration ou à l’aide du Gestionnaire de Configuration SQL Server.

## <a name="bkmk_TestScript"></a>Étape 3 : Vérifier que l’exécution du script fonctionne localement

Vérifiez que le service d’exécution de script externe est activé.

1. Dans SQL Server Management Studio, ouvrez une nouvelle **requête** fenêtre, puis exécutez la commande suivante :
  
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```
    La valeur **run_value** doit maintenant être définie sur 1.
    
2. Ouvrez le **Services** panneau et vérifiez que le service Launchpad de votre instance est en cours d’exécution. Si vous installez plusieurs instances, chaque instance a son propre service Launchpad.
   
3. Ouvrez une nouvelle **requête** fenêtre dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis exécutez un script R simple telle que la suivante :
  
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```
  
    **Résultats**
  
    *Hello* *1*
  
   Si la commande s’exécute sans erreur, passez aux étapes suivantes. Si vous obtenez une erreur, pour obtenir la liste de certains problèmes courants, consultez [FAQ d’installation et de mise à niveau](../r/upgrade-and-installation-faq-sql-server-r-services.md).

## <a name="bkmk_FollowUp"></a>Étape 4 : Une configuration supplémentaire

En fonction de votre cas d’utilisation de R ou Python, vous devrez peut-être apporter des modifications supplémentaires pour le serveur, le pare-feu, les comptes utilisés par le service, ou les autorisations de base de données. Les modifications que vous devez effectuer varient selon le cas.

Scénarios courants qui nécessitent des modifications supplémentaires sont les suivantes :

* Modification des règles de pare-feu pour autoriser les connexions entrantes vers SQL Server.
* L’activation des protocoles réseau supplémentaires.
* S’assurer que le serveur prend en charge les connexions à distance.
* L’activation de *l’authentification implicite*, si les utilisateurs accéder aux données SQL Server à partir d’un terminal de développement R distant et exécutent le code R à l’aide du package RODBC ou un autre fournisseur de Microsoft ODBC Open Database Connectivity ().
* Octroi d’autorisations appropriées pour exécuter le script R ou utiliser des bases de données.
* Résolution des problèmes de sécurité qui empêchent la communication avec le service Launchpad.
* S’assurer que les utilisateurs sont autorisés à exécuter le code R ou installer des packages.

> [!NOTE]
> Pas toutes les modifications répertoriées peuvent être nécessaire. Toutefois, nous vous recommandons de consulter tous les éléments pour voir si elles sont applicables à votre scénario.

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

Si vous avez installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et sont en cours d’exécution des scripts R dans votre propre instance, vous exécutez généralement des scripts en tant qu’administrateur, ou au moins en tant que propriétaire de base de données, et qui n’ont donc des autorisations implicites pour diverses opérations, toutes les données dans la base de données et la capacité Pour installer de nouveaux packages R en tant que nécessaire.

Toutefois, dans un scénario d’entreprise, la plupart des utilisateurs, y compris les utilisateurs qui accèdent à la base de données à l’aide de connexions SQL, n’ont pas de telles autorisations avec élévation de privilèges. Par conséquent, pour chaque utilisateur qui exécutent des scripts R ou Python, vous devez accorder les autorisations utilisateur pour exécuter des scripts dans chaque base de données où les scripts externes seront utilisés.

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!TIP]
> Besoin d’aide pour la configuration ? Vous n’êtes pas sûr d’avoir effectué toutes les étapes ? Utilisez ces rapports personnalisés pour vérifier l’état d’installation de R Services. Pour plus d’informations, consultez [Analyser R Services à l’aide de rapports personnalisés](monitor-r-services-using-custom-reports-in-management-studio.md).

### <a name="ensure-that-the-sql-server-computer-supports-remote-connections"></a>Assurez-vous que l’ordinateur SQL Server prend en charge les connexions à distance

Si vous ne pouvez pas vous connecter à partir d’un ordinateur distant, vérifiez si le serveur autorise les connexions à distance. Les connexions à distance sont parfois désactivées par défaut.

Vérifiez également si le pare-feu autorise l’accès à SQL Server. Par défaut, le port utilisé par SQL Server est souvent bloqué par le pare-feu. Si vous utilisez le pare-feu Windows, consultez [configurer le pare-feu Windows pour accéder au moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).

### <a name="give-your-users-read-write-or-ddl-permissions-to-the-database"></a>Donnez à vos utilisateurs de lecture, écriture ou les autorisations de DDL pour la base de données

Pendant son exécution des scripts R, le compte d’utilisateur ou un compte de connexion SQL peut besoin pour lire des données à partir d’autres bases de données, créer des tables pour stocker les résultats et écrire des données dans des tables.

Pour chaque compte d’utilisateur ou un compte de connexion SQL exécutant des scripts R, veillez à ce que le compte ou le compte de connexion dispose des autorisations appropriées sur la base de données : *db_datareader*, *db_datawriter*, ou  *db_ddladmin*.

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

Après avoir vérifié que la fonctionnalité de l’exécution du script fonctionne dans SQL Server, vous pouvez exécuter des commandes R et Python à partir de SQL Server Management Studio, Visual Studio Code ou tout autre client qui peut envoyer des instructions T-SQL sur le serveur.

Toutefois, vous souhaiterez peut-être apporter des modifications à la configuration du système pour prendre en charge une utilisation intensive de l’apprentissage, ou ajouter de nouveaux packages R.

Cette section répertorie certaines modifications courantes que vous pouvez apporter à prendre en charge d’apprentissage.

### <a name="add-more-worker-accounts"></a>Ajoutez d’autres comptes de travail

Si vous pensez que vous pouvez utiliser R importante, ou si vous prévoyez de nombreux utilisateurs d’être en cours d’exécution des scripts en même temps, vous pouvez augmenter le nombre de comptes de travail qui sont affectés au service Launchpad. Pour plus d’informations, consultez [modifier le pool de comptes d’utilisateur pour SQL Server R Services](modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="bkmk_optimize"></a>Optimiser le serveur pour l’exécution du script externe

Les paramètres par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation sont destinées à optimiser l’équilibre entre le serveur pour une multitude de services qui sont pris en charge par le moteur de base de données, ce qui peut inclure extraction, transformation et processus de chargement (ETL), création de rapports, l’audit, et les applications qui utilisent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données. Par conséquent, les paramètres par défaut, vous constaterez que les ressources pour l’apprentissage sont parfois restreinte ou limitées, en particulier dans les opérations gourmandes en mémoire.

Pour vous assurer que les tâches d’apprentissage machine sont classés par priorité et avec la ressource appropriée, nous vous recommandons d’utiliser le gouverneur de ressources SQL Server pour configurer un pool de ressources externes. Vous pouvez également modifier la quantité de mémoire qui est allouée à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du moteur de base de données, ou augmentez le nombre de comptes qui s’exécutent sous le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service.

- Pour configurer un pool de ressources pour la gestion des ressources externes, consultez [créer un pool de ressources externes](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Pour modifier la quantité de mémoire réservée à la base de données, consultez [mémoire option de configuration](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Pour modifier le nombre de comptes R qui peut être démarrée par [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], consultez [modifier le pool de comptes d’utilisateur pour l’apprentissage](modify-the-user-account-pool-for-sql-server-r-services.md).

Si vous utilisez l’Édition Standard et que vous n’avez pas le gouverneur de ressources, vous pouvez utiliser les vues de gestion dynamique (DMV) et les événements étendus, ainsi que les événements Windows analyse, pour aider à gérer les ressources de serveur qui sont utilisées par R. Pour plus d’informations, consultez [analyse et la gestion des Services de R](managing-and-monitoring-r-solutions.md).

### <a name="install-additional-r-packages"></a>Installer des packages R supplémentaires

Prenez une minute pour installer les packages R supplémentaires que vous allez utiliser.

Installez les packages que vous souhaitez utiliser à partir de SQL Server dans la bibliothèque par défaut qui est utilisée par l’instance. Si vous avez une installation distincte de R sur l’ordinateur, ou si vous avez installé les packages dans les bibliothèques utilisateur, vous ne pourrez pas utiliser ces packages à partir de T-SQL. Pour plus d’informations, consultez [installer des packages R supplémentaires sur SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md).

Vous pouvez également définir des groupes d’utilisateurs de partager des packages sur un niveau de base de données ou configurer des rôles de base de données pour permettre aux utilisateurs d’installer leurs propres packages. Pour plus d’informations, consultez [gestion des packages](r-package-management-for-sql-server-r-services.md).

### <a name="upgrade-the-machine-learning-components"></a>Mettre à niveau les composants d’apprentissage automatique

Lorsque vous installez R Services à l’aide de SQL Server 2016, vous obtiendrez la version des composants R qui a été mise à jour lors de la mise en production ou le service pack a été publié. Chaque fois que des correctifs ou de mettre à niveau le serveur, les machine learning composants sont mis à niveau ainsi.

Toutefois, vous pouvez mettre à niveau les composants sur une planification plus rapide qu’est pris en charge d’apprentissage par les versions de SQL Server en installant Microsoft R Server et de votre instance de liaison. Lorsque vous mettez à niveau, vous obtenez également les nouvelles fonctionnalités suivantes, qui sont pris en charge dans les versions récentes de Microsoft R Server :

* Nouveaux packages R, y compris [sqlrutils](https://docs.microsoft.com/r-server/r-reference/sqlrutils/sqlrutils), [olapR](https://docs.microsoft.com/r-server/r-reference/olapr/olapr), et [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package).
* [Modèles de pretrained](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models) pour l’analyse de texte et de classification d’image.

Pour plus d’informations sur la mise à niveau une instance de SQL Server 2016, consultez [composants R de mise à niveau via la liaison](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

Si vous ne savez pas quelle version de R est associée à l’instance, vous pouvez exécuter une commande telle que les éléments suivants :

```SQL
EXEC sp_execute_external_script  @language =N'R',
@script=N'
myvar <- version$version.string
OutputDataSet <- as.data.frame(myvar);'
```

> [!NOTE]
> Mises à jour via le processus de liaison prendra en charge pour SQL Server 2017 également. Toutefois, les mises à niveau à un actuellement sont prises en charge uniquement pour les instances de SQL Server 2016.

### <a name="tutorials"></a>Didacticiels

Pour commencer avec des exemples simples et découvrez comment R fonctionne avec SQL Server, consultez [du code à l’aide de R dans Transact-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).

Pour afficher des exemples d’apprentissage automatique qui sont basées sur des scénarios concrets, consultez [Machine learning didacticiels](../tutorials/machine-learning-services-tutorials.md).

### <a name="troubleshooting"></a>Dépannage

Vous rencontrez des problèmes ? La tentative de mise à niveau ? Pour obtenir des réponses aux questions les plus fréquentes et les problèmes connus, consultez l’article suivant :

* [Mise à niveau et installation FAQ - Machine Learning Services](upgrade-and-installation-faq-sql-server-r-services.md)

Pour vérifier l’état d’installation de l’instance et résoudre les problèmes courants, essayez de ces rapports personnalisés.

* [Rapports personnalisés pour SQL Server R Services](monitor-r-services-using-custom-reports-in-management-studio.md)

