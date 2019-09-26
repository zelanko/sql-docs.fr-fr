---
title: Installer SQL Server 2016 R Services (en base de données)
description: Ajoutez la prise en charge du langage de programmation R à un moteur de base de données sur SQL Server services R 2016 sur Windows.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/03/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: a255b70b71f29f9cc28e4022ecfdf2741f9a838d
ms.sourcegitcommit: 2f56848ec422845ee81fb84ed321a716c677aa0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71271882"
---
# <a name="install-sql-server-2016-r-services"></a>Installer SQL Server 2016 R services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment installer et configurer **SQL Server les services R 2016**. Si vous avez SQL Server 2016, installez cette fonctionnalité pour permettre l’exécution de code R dans SQL Server.

Dans SQL Server 2017, l’intégration de R est proposée dans [machine learning services](../r/r-server-standalone.md), reflétant l’ajout de Python. Si vous souhaitez intégrer R et que vous disposez d’un support d’installation SQL Server 2017, consultez [installer SQL Server machine learning services](sql-machine-learning-services-windows-install.md) pour ajouter la fonctionnalité. 

<a name="bkmk_prereqs"> </a> 

## <a name="pre-install-checklist"></a>Liste de vérification préalable à l’installation

+ Une instance du moteur de base de données est requise. Vous ne pouvez pas installer uniquement R, bien que vous puissiez l’ajouter de façon incrémentielle à une instance existante.

+ Pour la continuité des activités, les [groupes de disponibilité Always on](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server) sont pris en charge pour R services. Vous devez installer R services et configurer des packages sur chaque nœud.

+ N’installez pas R services sur un cluster de basculement. Le mécanisme de sécurité utilisé pour isoler les processus R n’est pas compatible avec un environnement de cluster de basculement Windows Server.

+ N’installez pas R services sur un contrôleur de domaine. La partie R services du programme d’installation va échouer.

+ N’installez pas de **fonctionnalités** > partagées**R Server (autonomes)** sur le même ordinateur exécutant une instance de dans la base de données. 

  L’installation côte à côte avec d’autres versions de R et Python est possible, car l’instance SQL Server utilise ses propres copies des distributions R et Anaconda Open source. Toutefois, l’exécution de code qui utilise R et Python sur l’ordinateur SQL Server en dehors de SQL Server peut entraîner différents problèmes:
    
  + Vous utilisez une autre bibliothèque et un autre fichier exécutable, et vous pouvez obtenir des résultats différents, que lorsque vous exécutez dans SQL Server.
  + Les scripts R et Python exécutés dans les bibliothèques externes ne peuvent pas être gérés par SQL Server, ce qui entraîne une contention des ressources.
  
Si vous avez utilisé des versions antérieures de l’environnement de développement Revolution Analytics ou des packages RevoScaleR, ou si vous avez installé des versions préliminaires de SQL Server 2016, vous devez les désinstaller. L’exécution de versions plus anciennes et plus récentes de RevoScaleR et d’autres packages propriétaires n’est pas prise en charge. Pour obtenir de l’aide sur la suppression de versions antérieures, consultez le [Forum aux questions sur la mise à niveau et l’installation de SQL Server machine learning services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

> [!IMPORTANT]
> Une fois l’installation terminée, veillez à suivre les étapes de configuration supplémentaires décrites dans cet article. Ces étapes incluent l’activation de SQL Server pour utiliser des scripts externes et l’ajout de comptes requis pour SQL Server pour exécuter des travaux R en votre nom. Les modifications de configuration nécessitent généralement un redémarrage de l’instance ou un redémarrage du service launchpad.

## <a name="get-the-installation-media"></a>Obtenir le média d’installation

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

<a name="bkmk_ga_instalpatch"></a>

 ### <a name="install-patch-requirement"></a>Installer les correctifs requis 

Microsoft a identifié un problème avec la version spécifique des fichiers binaires Microsoft VC++ 2013 Runtime qui sont installés en tant que composants requis par SQL Server. Si cette mise à jour des fichiers binaires du runtime VC n’est pas installée, SQL Server risque de rencontrer des problèmes de stabilité dans certains scénarios. Avant d’installer SQL Server, suivez les instructions données dans [Notes de publication de SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) pour voir si votre ordinateur nécessite un correctif pour les fichiers binaires du runtime VC.  

<a name="bkmk2016top"></a>

## <a name="run-setup"></a>Exécuter le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrez l’Assistant Installation de SQL Server 2016.

2. Sous l’onglet **installation** , sélectionnez **nouvelle SQL Server installation autonome ou ajout de fonctionnalités à une installation existante**.
    
   ![Installer R services (dans la base de données)](media/2016-setup-installation-rsvcs.png "Démarrer l’installation du moteur de base de données avec R services")
   
3. Dans la page **sélection de fonctionnalités** , sélectionnez les options suivantes:

   - Sélectionnez **moteur de base de données services**. Le moteur de base de données est requis dans chaque instance qui utilise Machine Learning.
   - Sélectionnez **R services (dans la base de données)** . Installe la prise en charge de l’utilisation de R dans la base de données.
    
     ![Sélection des fonctionnalités R services](media/2016setup-rsvcs-features.png "Sélectionner ces fonctionnalités pour R services dans la base de données")

    > [!IMPORTANT]
    > N’installez pas R Server et R services en même temps. En général, vous installez R Server (autonome) pour créer un environnement qu’un développeur ou scientifique des données utilise pour se connecter à SQL Server et déployer des solutions R. Vous n’avez donc pas besoin de les installer sur le même ordinateur.

4.  Sur la page **consentement pour installer Microsoft R Open** , cliquez sur **accepter**.
  
    Ce contrat de licence est requis pour télécharger Microsoft R Open, qui comprend une distribution des packages de base et des outils R Open source, ainsi que des packages et fournisseurs de connectivité R améliorés de l’équipe de développement Microsoft R.
  
5. Une fois que vous avez accepté le contrat de licence, une brève pause s’est produite pendant la préparation du programme d’installation. Cliquez sur **suivant** lorsque le bouton devient disponible.

6. Sur la page **prêt pour l’installation** , vérifiez que les éléments suivants sont inclus, puis sélectionnez **installer**.

   + Services Moteur de base de données
   + R Services (dans la base de données)

    Notez l’emplacement du dossier sous le chemin d’accès `..\Setup Bootstrap\Log` où sont stockés les fichiers de configuration. Une fois l’installation terminée, vous pouvez passer en revue les composants installés dans le fichier Résumé.

7. Une fois l’installation terminée, si vous êtes invité à redémarrer l’ordinateur, faites-le maintenant. Il est important de lire le message affiché par l'Assistant Installation à la fin de l'installation. Pour plus d'informations, consultez [View and Read SQL Server Setup Log Files](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files).

## <a name="set-environment-variables"></a>Définir des variables d’environnement

Pour l’intégration de fonctionnalités R uniquement, vous devez définir la variable d’environnement **MKL_CBWR** pour [garantir la cohérence](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) de la sortie des calculs d’Intel Math Kernel Library (MKL).

1. Dans le panneau de configuration, cliquez sur système **et sécurité** >  > **paramètres** > système avancés**variables d’environnement**.

2. Créez un utilisateur ou une variable système. 

  + Définir le nom de la variable sur`MKL_CBWR`
  + Affectez à la variable la valeur`AUTO`

Cette étape nécessite un redémarrage du serveur. Si vous êtes sur le ou l’activation du script, vous pouvez maintenir le redémarrage jusqu’à ce que le travail de configuration soit terminé.

<a name="bkmk_enableFeature"></a>

##  <a name="enable-script-execution"></a>Activer l’exécution du script

1. Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > Vous pouvez télécharger et installer la version appropriée à partir de cette page: [Téléchargez SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > Vous pouvez également essayer la version préliminaire de [Azure Data Studio](../../azure-data-studio/what-is.md), qui prend en charge les tâches administratives et les requêtes sur SQL Server.
  
2. Connectez-vous à l’instance où vous avez installé Machine Learning Services, cliquez sur **nouvelle requête** pour ouvrir une fenêtre de requête, puis exécutez la commande suivante:

   ```sql
   sp_configure
   ```
    La propriété `external scripts enabled` a normalement la valeur **0** à ce stade. Cela est dû au fait que la fonctionnalité est désactivée par défaut. Pour que vous puissiez exécuter des scripts R ou python, la fonctionnalité doit être activée de manière explicite par un administrateur.
     
3. Pour activer la fonctionnalité de script externe, exécutez l’instruction suivante:
  
    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
## <a name="restart-the-service"></a>Redémarrez le service.

Une fois l’installation terminée, redémarrez le moteur de base de données avant de passer à la suivante, en activant l’exécution du script.

Le redémarrage du service redémarre également automatiquement le service associé [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] .

Vous pouvez redémarrer le service à l’aide de la commande de redémarrage du bouton droit de l’instance dans SSMS, ou à l’aide du panneau **services** du panneau de configuration, ou à l’aide de [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Vérifier l'installation

Vérifiez l’état d’installation de l’instance à l’aide de [rapports personnalisés](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

Procédez comme suit pour vérifier que tous les composants utilisés pour lancer le script externe sont en cours d’exécution.

1. Dans SQL Server Management Studio, ouvrez une nouvelle fenêtre de requête, puis exécutez la commande suivante:
    
    ```sql
    EXEC sp_configure  'external scripts enabled'
    ```

    La valeur **run_value** doit maintenant être définie sur 1.

2. Ouvrez le panneau **services** ou gestionnaire de configuration SQL Server, puis vérifiez **SQL Server Launchpad service** est en cours d’exécution. Vous devez disposer d’un service pour chaque instance du moteur de base de données sur laquelle R ou python est installé. Pour plus d’informations sur le service, consultez [extensibilité Framework](../concepts/extensibility-framework.md).

7. Si Launchpad est en cours d’exécution, vous devez être en mesure d’exécuter un R simple pour vérifier que les runtimes de script externes peuvent communiquer avec SQL Server. 

    Ouvrez une nouvelle fenêtre de requête [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]dans, puis exécutez un script tel que le suivant:
    
    ```sql
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    L’exécution du script peut prendre un peu de temps, la première fois que l’exécution du script externe est chargée. Les résultats doivent ressembler à ceci:

    | hello |
    |----|
    | 1|

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Appliquer les mises à jour

Nous vous recommandons d’appliquer la dernière mise à jour cumulative au moteur de base de données et aux composants de Machine Learning.

Sur les appareils connectés à Internet, les mises à jour cumulatives sont généralement appliquées par le biais de Windows Update, mais vous pouvez également suivre les étapes ci-dessous pour contrôler les mises à jour. Lorsque vous appliquez la mise à jour du moteur de base de données, le programme d’installation extrait les mises à jour cumulatives pour les bibliothèques R que vous avez installées sur la même instance. 

Sur les serveurs déconnectés, des étapes supplémentaires sont requises. Pour plus d’informations, consultez [installer sur des ordinateurs sans accès internet > appliquer des mises à jour cumulatives](sql-ml-component-install-without-internet-access.md#apply-cu).

1. Démarrer avec une instance de ligne de base déjà installée: SQL Server 2016, SQL Server 2016 SP 1 ou SQL Server 2016 SP 2.

2. Accédez à la liste des mises à jour cumulatives: [Mises à jour de SQL Server 2016](https://sqlserverupdates.com/sql-server-2016-updates/)

3. Sélectionnez la dernière mise à jour cumulative. Un fichier exécutable est téléchargé et extrait automatiquement.

4. Exécutez le programme d'installation. Acceptez les termes du contrat de licence et, dans la page sélection de fonctionnalités, passez en revue les fonctionnalités pour lesquelles des mises à jour cumulatives sont appliquées. Vous devez voir toutes les fonctionnalités installées pour l’instance actuelle, y compris R services. Le programme d’installation télécharge les fichiers CAB nécessaires à la mise à jour de toutes les fonctionnalités.

5. Poursuivez avec l’Assistant, en acceptant les termes du contrat de licence pour la distribution R. 

<a name="bkmk_FollowUp"></a> 

## <a name="additional-configuration"></a>Configuration supplémentaire

Si l’étape de vérification du script externe a réussi, vous pouvez exécuter des commandes Python à partir de SQL Server Management Studio, Visual Studio Code ou tout autre client qui peut envoyer des instructions T-SQL au serveur.

Si vous avez rencontré une erreur lors de l’exécution de la commande, passez en revue les étapes de configuration supplémentaires de cette section. Vous devrez peut-être apporter des configurations appropriées supplémentaires au service ou à la base de données.

Au niveau de l’instance, une configuration supplémentaire peut inclure:

* [Configuration du pare-feu pour SQL Server Machine Learning Services](../../advanced-analytics/security/firewall-configuration.md)
* [Activer les protocoles réseau supplémentaires](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Activer les connexions à distance](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Gérer les quotas de disque](https://docs.microsoft.com/windows/desktop/fileio/managing-disk-quotas) pour éviter les scripts externes exécutant des tâches qui épuisent l’espace disque

<a name="bkmk_configureAccounts"></a>
<a name="bkmk_AllowLogon"></a>

Sur la base de données, vous pouvez avoir besoin des mises à jour de configuration suivantes:

* [Accorder aux utilisateurs l’autorisation d’SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md)
* [Ajouter SQLRUserGroup comme utilisateur de base de données](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md)

> [!NOTE]
> Toutes les modifications répertoriées ne sont pas requises, et aucune n’est requise. La configuration requise dépend de votre schéma de sécurité, de l’emplacement d’installation de SQL Server et de la façon dont les utilisateurs se connectent à la base de données et exécutent des scripts externes. Vous trouverez des conseils de dépannage supplémentaires ici: [FAQ sur la mise à niveau et l’installation](../r/upgrade-and-installation-faq-sql-server-r-services.md)

## <a name="suggested-optimizations"></a>Optimisations suggérées

Maintenant que tout fonctionne, vous souhaiterez peut-être également optimiser le serveur pour prendre en charge Machine Learning ou installer des modèles préformés.

### <a name="add-more-worker-accounts"></a>Ajouter d’autres comptes de travail

Si vous pensez que vous pouvez utiliser R de manière intensive ou si vous prévoyez que de nombreux utilisateurs exécutent des scripts simultanément, vous pouvez augmenter le nombre de comptes de travail affectés au service launchpad. Pour plus d’informations, consultez [modifier le pool de comptes d’utilisateurs pour SQL Server machine learning services](../administration/modify-user-account-pool.md).

<a name="bkmk_optimize"></a>

### <a name="optimize-the-server-for-external-script-execution"></a>Optimiser le serveur pour l’exécution de scripts externes

Les paramètres par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le programme d’installation de sont destinés à optimiser l’équilibre du serveur pour divers services pris en charge par le moteur de base de données, qui peuvent inclure des processus d’extraction, de transformation et de chargement (ETL), de création de rapports, d’audit et applications qui utilisent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des données. Par conséquent, dans les paramètres par défaut, vous constaterez peut-être que les ressources pour Machine Learning sont parfois limitées ou limitées, en particulier dans les opérations gourmandes en mémoire.

Pour vous assurer que les travaux de Machine Learning sont classés par ordre de priorité et resourcement appropriés, nous vous recommandons d’utiliser SQL Server Resource Governor pour configurer un pool de ressources externes. Vous pouvez également modifier la quantité de mémoire allouée au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur de base de données ou augmenter le nombre de comptes qui s’exécutent sous le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service.

- Pour configurer un pool de ressources pour la gestion des ressources externes, consultez [créer un pool de ressources externes](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Pour modifier la quantité de mémoire réservée pour la base de données, consultez Options de configuration de la [mémoire du serveur](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Pour modifier le nombre de comptes R qui peuvent être démarrés [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]par, consultez [modifier le pool de comptes d’utilisateur pour machine learning](../administration/modify-user-account-pool.md).

Si vous utilisez l’édition standard et que vous n’avez pas Resource Governor, vous pouvez utiliser des vues de gestion dynamique (DMV) et des événements étendus, ainsi que l’analyse des événements Windows, pour faciliter la gestion des ressources serveur utilisées par R. Pour plus d’informations, consultez [surveillance et gestion de R services](../r/managing-and-monitoring-r-solutions.md).

### <a name="install-additional-r-packages"></a>Installer des packages R supplémentaires

Les solutions R que vous créez pour SQL Server peuvent appeler des fonctions R de base, des fonctions des packages propriétaires installés avec SQL Server et des packages R tiers compatibles avec la version de R Open source installée par SQL Server.

Installez les packages que vous souhaitez utiliser à partir de SQL Server dans la bibliothèque par défaut qui est utilisée par l’instance. Si vous disposez d’une installation distincte de R sur l’ordinateur, ou si vous avez installé des packages dans les bibliothèques utilisateur, vous ne pourrez pas utiliser ces packages à partir de T-SQL.

Le processus d’installation et de gestion des packages R est différent dans SQL Server 2016 et SQL Server 2017. Dans SQL Server 2016, un administrateur de base de données doit installer les packages R dont les utilisateurs ont besoin. Dans SQL Server 2017, vous pouvez configurer des groupes d’utilisateurs pour partager des packages au niveau de chaque base de données ou configurer des rôles de base de données pour permettre aux utilisateurs d’installer leurs propres packages. Pour plus d’informations, consultez [installer de nouveaux packages R](../r/install-additional-r-packages-on-sql-server.md).

## <a name="next-steps"></a>Étapes suivantes

Les développeurs peuvent démarrer avec quelques exemples simples et découvrir les principes de base du fonctionnement de R avec SQL Server. Pour l’étape suivante, consultez les liens suivants :

+ [Tutoriel : Exécuter R dans T-SQL](../tutorials/quickstart-r-create-script.md)
+ [Tutoriel : Analytique dans la base de données pour les développeurs R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Pour consulter des exemples d’apprentissage automatique basés sur des scénarios réels, consultez les [Didacticiels d’apprentissage automatique](../tutorials/machine-learning-services-tutorials.md).