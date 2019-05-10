---
title: Installez SQL Server 2016 R Services (en base de données) - SQL Server Machine Learning
description: Ajouter la prise en charge linguistique pour un moteur de base de données sur SQL Server 2016 R Services sur Windows de programmation R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/03/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 52935abf74fcf3ad7a4f7c8d78faa6b9b21d47e5
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65095942"
---
# <a name="install-sql-server-2016-r-services"></a>Installer SQL Server 2016 R Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment installer et configurer **SQL Server 2016 R Services**. Si vous avez SQL Server 2016, installez cette fonctionnalité pour permettre l’exécution de code R dans SQL Server.

Dans SQL Server 2017, l’intégration de R est disponible en [Machine Learning Services](../r/r-server-standalone.md), qui reflète l’ajout de Python. Si vous voulez une intégration de R et disposez du support d’installation de SQL Server 2017, consultez [installer SQL Server 2017 Machine Learning Services](sql-machine-learning-services-windows-install.md) pour ajouter la fonctionnalité. 

<a name="bkmk_prereqs"> </a> 

## <a name="pre-install-checklist"></a>Liste de vérification de préinstallation

+ Une instance du moteur de base de données est requise. Vous ne pouvez pas installer R simplement, bien que vous pouvez l’ajouter progressivement à une instance existante.

+ Pour la continuité d’activité, [toujours sur les groupes de disponibilité](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server) sont pris en charge pour R Services. Vous devez installer R Services et configurer des packages, sur chaque nœud.

+ N’installez pas de R Services sur un cluster de basculement. Le mécanisme de sécurité utilisé pour isoler les processus R n’est pas compatible avec un environnement de cluster de basculement Windows Server.

+ N’installez pas de R Services sur un contrôleur de domaine. La partie de R Services du programme d’installation échoue.

+ N’installez pas **fonctionnalités partagées** > **R Server (autonome)** sur le même ordinateur exécutant une instance de la base de données. 

  Installation côte à côte avec d’autres versions de R et Python sont possibles, car l’instance de SQL Server utilise ses propres copies des distributions Anaconda et R open source. Toutefois, le code qui utilise R et Python sur l’ordinateur SQL Server en dehors de SQL Server en cours d’exécution peut entraîner divers problèmes :
    
  + Vous utilisez une autre bibliothèque et un fichier exécutable différent et obtenez des résultats différents, que vous effectuez lorsque vous exécutez dans SQL Server.
  + Les scripts R et Python qui s’exécutent dans des bibliothèques externes ne peuvent pas être gérés par SQL Server, ce qui conduit à des conflits de ressources.
  
Si vous avez utilisé des versions antérieures de l’environnement de développement Revolution Analytique ou les packages RevoScaleR, ou si vous avez installé des versions préliminaires de SQL Server 2016, vous devez les désinstaller. Versions anciennes et récentes de RevoScaleR et d’autres packages propriétaires en cours d’exécution n’est pas pris en charge. Pour supprimer les versions précédentes, consultez [mise à niveau et FAQ d’Installation de SQL Server Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

> [!IMPORTANT]
> Une fois le programme d’installation est terminée, veillez à effectuer les étapes de post-configuration supplémentaires décrites dans cet article. Ces étapes comprennent l’activation de SQL Server à utiliser des scripts externes, puis en ajoutant les comptes requis pour SQL Server exécuter des travaux R à votre place. Modifications de configuration nécessitent généralement un redémarrage de l’instance ou un redémarrage du service Launchpad.

## <a name="get-the-installation-media"></a>Obtenir le média d’installation

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

<a name="bkmk_ga_instalpatch"></a>

 ### <a name="install-patch-requirement"></a>Installer le correctif obligatoire 

Microsoft a identifié un problème avec la version spécifique des fichiers binaires Microsoft VC++ 2013 Runtime qui sont installés en tant que composants requis par SQL Server. Si cette mise à jour des fichiers binaires du runtime VC n’est pas installée, SQL Server risque de rencontrer des problèmes de stabilité dans certains scénarios. Avant d’installer SQL Server, suivez les instructions données dans [Notes de publication de SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) pour voir si votre ordinateur nécessite un correctif pour les fichiers binaires du runtime VC.  

<a name="bkmk2016top"></a>

## <a name="run-setup"></a>Exécutez le programme d’installation

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

## <a name="set-environment-variables"></a>Jeu de variables d’environnement

Pour R fonctionnalité d’intégration uniquement, vous devez définir le **MKL_CBWR** variable d’environnement [résultat homogène](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) des calculs d’Intel Math Kernel Library (MKL).

1. Dans le panneau de configuration, cliquez sur **système et sécurité** > **système** > **paramètres système avancés**  >   **Variables d’environnement**.

2. Créer une nouvelle variable utilisateur ou système. 

  + Nom de variable du jeu `MKL_CBWR`
  + La valeur est la valeur de variable `AUTO`

Cette étape nécessite un redémarrage du serveur. Si vous êtes sur le point d’activer l’exécution du script, vous pouvez différez lors du redémarrage jusqu'à ce que tout le travail de configuration est terminée.

<a name="bkmk_enableFeature"></a>

##  <a name="enable-script-execution"></a>Activer l’exécution du script

1. Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > Vous pouvez télécharger et installer la version appropriée à partir de cette page : [Téléchargez SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > Vous pouvez également essayer la version préliminaire de [Azure Data Studio](../../azure-data-studio/what-is.md), qui prend en charge les tâches d’administration et les requêtes SQL Server.
  
2. Connectez-vous à l’instance où vous avez installé les Services Machine Learning, cliquez sur **nouvelle requête** pour ouvrir une fenêtre de requête, exécutez la commande suivante :

   ```sql
   sp_configure
   ```
    La propriété `external scripts enabled` a normalement la valeur **0** à ce stade. C’est parce que la fonctionnalité est désactivée par défaut. La fonctionnalité doit être activée explicitement par un administrateur avant de pouvoir exécuter des scripts R ou Python.
     
3. Pour activer la fonctionnalité de script externe, exécutez l’instruction suivante :
  
    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
## <a name="restart-the-service"></a>Redémarrez le service.

Lorsque l’installation est terminée, redémarrez le moteur de base de données avant de continuer à l’autre, l’activation de l’exécution du script.

Le redémarrage du service automatiquement redémarre connexe [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service.

Vous pouvez redémarrer le service à l’aide de clic droit **redémarrer** commande pour l’instance dans SSMS, ou à l’aide de la **Services** dans le panneau de configuration ou à l’aide du Panneau de configuration [Gestionnaire de Configuration SQL Server ](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Vérifier l'installation

Vérifier l’état d’installation de l’instance à l’aide [des rapports personnalisés](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

Utilisez les étapes suivantes pour vérifier que tous les composants utilisés pour lancer le script externe sont en cours d’exécution.

1. Dans SQL Server Management Studio, ouvrez une nouvelle fenêtre de requête et exécutez la commande suivante :
    
    ```sql
    EXEC sp_configure  'external scripts enabled'
    ```

    La valeur **run_value** doit maintenant être définie sur 1.

2. Ouvrez le **Services** panneau ou le Gestionnaire de Configuration SQL Server et vérifiez **Launchpad de SQL Server service** est en cours d’exécution. Vous devez disposer d’un service pour chaque instance du moteur de base de données qui a R ou Python est installé. Pour plus d’informations sur le service, consultez [Extensibility framework](../concepts/extensibility-framework.md).

7. Si Launchpad est en cours d’exécution, il se peut que vous devez être en mesure d’exécuter R simple pour vérifier que les runtimes de script externes peut communiquer avec SQL Server. 

    Ouvrez une nouvelle **requête** fenêtre dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis exécutez un script comme ci-dessous :
    
    ```sql
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

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Appliquer des mises à jour

Nous vous recommandons d’appliquer la mise à jour cumulative la plus récente pour le moteur de base de données et les composants d’apprentissage.

Sur les appareils connectés à internet, les mises à jour cumulatives sont appliqués en général via Windows Update, mais vous pouvez également utiliser les étapes ci-dessous pour les mises à jour contrôlés. Lorsque vous appliquez la mise à jour pour le moteur de base de données, le programme d’installation extrait les mises à jour cumulatives pour les bibliothèques R que vous avez installé sur la même instance. 

Sur les serveurs hors connexion, des étapes supplémentaires sont nécessaires. Pour plus d’informations, consultez [installer sur des ordinateurs sans accès à internet > appliquer des mises à jour cumulatives](sql-ml-component-install-without-internet-access.md#apply-cu).

1. Démarrez avec une instance de la ligne de base déjà installée : Version initiale de SQL Server 2016, SQL Server 2016 Service Pack 1 ou SQL Server 2016 Service Pack 2.

2. Accédez à la liste de mise à jour cumulative : [Mises à jour de SQL Server 2016](https://sqlserverupdates.com/sql-server-2016-updates/)

3. Sélectionnez la mise à jour cumulative la plus récente. Un fichier exécutable est téléchargé et extrait automatiquement.

4. Exécutez le programme d'installation. Acceptez les termes du contrat de licence et sur la page de sélection de fonctionnalités, passez en revue les fonctionnalités pour lesquelles les mises à jour cumulatives sont appliquées. Vous devez voir toutes les fonctionnalités installées pour l’instance actuelle, y compris les Services R. Le programme d’installation télécharge les fichiers CAB nécessaires pour mettre à jour toutes les fonctionnalités.

5. Suivez les instructions de l’Assistant en acceptant les termes du contrat de licence pour la distribution de R. 

<a name="bkmk_FollowUp"></a> 

## <a name="additional-configuration"></a>Configuration supplémentaire

Si l’étape de vérification de script externe a réussi, vous pouvez exécuter des commandes de Python à partir de SQL Server Management Studio, Visual Studio Code ou tout autre client capable d’envoyer des instructions T-SQL sur le serveur.

Si vous rencontrez une erreur lors de l’exécution de la commande, passez en revue les étapes de configuration supplémentaires dans cette section. Vous devrez peut-être effectuer des configurations supplémentaires appropriées vers le service ou d’une base de données.

Au niveau de l’instance, une configuration supplémentaire peut-être inclure :

* [Configuration du pare-feu pour SQL Server Machine Learning Services](../../advanced-analytics/security/firewall-configuration.md)
* [Activer des protocoles réseau supplémentaires](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Activer les connexions distantes](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Gérer les quotas de disque](https://docs.microsoft.com/windows/desktop/fileio/managing-disk-quotas) afin d’éviter de saturer l’espace disque des tâches en cours d’exécution de scripts externes

<a name="bkmk_configureAccounts"></a>
<a name="bkmk_AllowLogon"></a>

Sur la base de données, vous devrez peut-être les mises à jour de configuration suivantes :

* [Autoriser les utilisateurs à SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md)
* [Ajouter SQLRUserGroup comme utilisateur de base de données](../../advanced-analytics/security/add-sqlrusergroup-to-database.md)

> [!NOTE]
> Pas toutes les modifications répertoriées sont requises, et aucun peut être requise. Configuration requise dépend de votre schéma de sécurité, où vous avez installé SQL Server, et que les utilisateurs pour se connecter à la base de données et exécuter des scripts externes. Vous trouverez ici des conseils de dépannage supplémentaires : [FAQ sur la mise à niveau et l’installation](../r/upgrade-and-installation-faq-sql-server-r-services.md)

## <a name="suggested-optimizations"></a>Optimisations proposées

Maintenant que vous avez ce que tout fonctionne, vous souhaiterez également optimiser le serveur pour prendre en charge d’apprentissage, ou installer des modèles préformés.

### <a name="add-more-worker-accounts"></a>Ajouter plusieurs comptes de travail

Si vous pensez que vous pouvez utiliser largement R, ou si vous prévoyez de nombreux utilisateurs d’être en cours d’exécution de scripts simultanément, vous pouvez augmenter le nombre de comptes de travail qui sont affectés au service Launchpad. Pour plus d’informations, consultez [modifier le pool de comptes d’utilisateur pour SQL Server Machine Learning Services](../administration/modify-user-account-pool.md).

<a name="bkmk_optimize"></a>

### <a name="optimize-the-server-for-external-script-execution"></a>Optimiser le serveur pour l’exécution du script externe

Les paramètres par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation sont destinées à optimiser l’équilibre du serveur pour un large éventail de services qui sont pris en charge par le moteur de base de données, ce qui peut inclure extraction, transformation et processus de chargement (ETL), création de rapports, l’audit, et les applications qui utilisent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données. Par conséquent, les paramètres par défaut, vous constaterez peut-être que les ressources pour l’apprentissage sont parfois restreintes ou limitées, en particulier dans les opérations gourmandes en mémoire.

Pour vous assurer que les travaux machine learning est classés par priorité et ressourcées, nous vous recommandons d’utiliser le gouverneur de ressources SQL Server pour configurer un pool de ressources externes. Vous souhaiterez également modifier la quantité de mémoire qui est allouée à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur de base de données ou augmenter le nombre de comptes qui s’exécutent sous le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service.

- Pour configurer un pool de ressources pour la gestion des ressources externes, consultez [créer un pool de ressources externe](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Pour modifier la quantité de mémoire réservée pour la base de données, consultez [options de configuration de mémoire serveur](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Pour modifier le nombre de comptes R qui peuvent être démarrés par [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], consultez [modifier le pool de comptes d’utilisateur pour l’apprentissage](../administration/modify-user-account-pool.md).

Si vous utilisez l’Édition Standard et que vous ne disposez pas du gouverneur de ressources, vous pouvez utiliser les vues de gestion dynamique (DMV) et les événements étendus, ainsi que Windows contrôle des événements pour aider à gérer les ressources serveur utilisées par R. Pour plus d’informations, consultez [surveillance et gestion des Services de R](../r/managing-and-monitoring-r-solutions.md).

### <a name="install-additional-r-packages"></a>Installer des packages R supplémentaires

Les solutions R que vous créez pour SQL Server peuvent appeler des fonctions de base R, de fonctions à partir des packages propriétaires installés avec SQL Server, les packages R de tiers compatibles avec la version de R open source installé par SQL Server.

Installez les packages que vous souhaitez utiliser à partir de SQL Server dans la bibliothèque par défaut qui est utilisée par l’instance. Si vous avez une installation distincte de R sur l’ordinateur, ou si vous avez installé des packages dans les bibliothèques utilisateur, vous ne pourrez pas utiliser ces packages à partir de T-SQL.

Le processus d’installation et de gestion des packages R est différent dans SQL Server 2016 et SQL Server 2017. Dans SQL Server 2016, un administrateur de base de données doit installer les packages R que les utilisateurs ont besoin. Dans SQL Server 2017, vous pouvez configurer des groupes d’utilisateurs de partager les packages sur un niveau par base de données ou configurer des rôles de base de données pour permettre aux utilisateurs d’installer leurs propres packages. Pour plus d’informations, consultez [installer de nouveaux packages R](../r/install-additional-r-packages-on-sql-server.md).

## <a name="next-steps"></a>Étapes suivantes

Aux développeurs R peuvent démarrer avec des exemples simples et apprendre les bases du fonctionne de R avec SQL Server. Pour votre prochaine étape, consultez les liens suivants :

+ [Tutoriel : Exécuter R dans T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutoriel : Analytique en base de données pour les développeurs R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Pour afficher des exemples d’apprentissage qui sont basées sur des scénarios réels, consultez [d’apprentissage didacticiels](../tutorials/machine-learning-services-tutorials.md).