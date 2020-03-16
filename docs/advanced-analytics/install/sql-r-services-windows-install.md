---
title: Installer SQL Server 2016 R Services (en base de données)
description: Ajoutez la prise en charge du langage de programmation R à un moteur de base de données sur SQL Server services R 2016 sous Windows.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 6fcb4245d4efff00002dea9b490312792e0d83d6
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79286103"
---
# <a name="install-sql-server-2016-r-services"></a>Installer SQL Server 2016 R Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment installer et configurer **SQL Server 2016 R Services**. Si vous avez SQL Server 2016, installez cette fonctionnalité pour permettre l’exécution de code R dans SQL Server.

Dans SQL Server 2017, l’intégration de R est proposée dans [Machine Learning Services](../r/r-server-standalone.md), pour refléter l’ajout de Python. Si vous souhaitez intégrer R et que vous disposez d’un support d’installation SQL Server 2017, consultez la page [Installer SQL Server Machine Learning Services](sql-machine-learning-services-windows-install.md) pour ajouter la fonctionnalité. 

<a name="bkmk_prereqs"> </a> 

## <a name="pre-install-checklist"></a>Liste de contrôle avant l’installation

+ Une instance du moteur de base de données est nécessaire. Vous ne pouvez pas installer uniquement R, même si vous pouvez les ajouter de façon incrémentielle à une instance existante.

+ Pour assurer la continuité de l’activité, R Services prend en charge les [groupes de disponibilité Always On](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server). Vous devez installer R Services et configurer des packages sur chaque nœud.

+ N’installez pas R Services sur un cluster de basculement. Le mécanisme de sécurité servant à isoler les processus R n’est pas compatible avec un environnement de cluster de basculement Windows Server.

+ N’installez pas R Services sur un contrôleur de domaine. La partie du programme d’installation dédiée à R échouerait.

+ N’installez pas **Fonctionnalités partagées** > **R Server (autonome)** sur l’ordinateur exécutant une instance en base de données. 

  L’installation côte à côte avec d’autres versions de R et Python est possible, car l’instance SQL Server utilise ses propres copies des distributions R et Anaconda open source. Cependant, l’exécution de code utilisant R et Python sur l’ordinateur SQL Server en dehors de SQL Server peut entraîner différents problèmes :
    
  + La bibliothèque et le fichier exécutable utilisés et les résultats obtenus ne sont pas les mêmes qu’avec une exécution dans SQL Server.
  + Les scripts R et Python exécutés dans des bibliothèques externes ne peuvent pas être gérés par SQL Server, ce qui entraîne un conflit de ressources.
  
Si vous avez utilisé des versions antérieures de l’environnement de développement Revolution Analytics ou des packages RevoScaleR, ou si vous avez installé des préversions de SQL Server2016, vous devez les désinstaller. L’exécution de versions plus anciennes et plus récentes de RevoScaleR et d’autres packages propriétaires n’est pas prise en charge. Pour obtenir de l’aide sur la désinstallation des versions antérieures, consultez [FAQ sur la mise à niveau et l’installation de SQL Server Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md).

> [!IMPORTANT]
> Une fois l’installation terminée, veillez à suivre les étapes supplémentaires consécutives à la configuration décrites dans cet article. Ces étapes incluent l’activation de l’utilisation de scripts externes par SQL Server et l’ajout des comptes nécessaires pour que SQL Server exécute les travaux R à votre place. Les modifications de configuration nécessitent généralement un redémarrage de l’instance ou du service Launchpad.

## <a name="get-the-installation-media"></a>Obtenir le média d’installation

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

<a name="bkmk_ga_instalpatch"></a>

 ### <a name="install-patch-requirement"></a>Installer le correctif obligatoire 

Microsoft a identifié un problème avec la version spécifique des fichiers binaires Microsoft VC++ 2013 Runtime qui sont installés en tant que composants requis par SQL Server. Si cette mise à jour des fichiers binaires du runtime VC n’est pas installée, SQL Server risque de rencontrer des problèmes de stabilité dans certains scénarios. Avant d’installer SQL Server, suivez les instructions données dans [Notes de publication de SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) pour voir si votre ordinateur nécessite un correctif pour les fichiers binaires du runtime VC.  

<a name="bkmk2016top"></a>

## <a name="run-setup"></a>Exécuter le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrez l’Assistant Installation de SQL Server 2016.

2. Sous l’onglet **Installation**, sélectionnez **Nouvelle installation autonome de SQL Server ou ajout de fonctionnalités à une installation existante**.
    
   ![Installer R Services (dans la base de données)](media/2016-setup-installation-rsvcs.png "Démarrer l’installation du moteur de base de données avec R Services")
   
3. Sur la page **Sélection des fonctionnalités**, sélectionnez les options suivantes :

   - Sélectionnez **Services Moteur de base de données**. Le moteur de base de données est requis dans chaque instance qui utilise le Machine Learning.
   - Sélectionnez **R Services (dans la base de données)** . Installe la prise en charge de l’utilisation de R dans la base de données.
    
     ![Sélection de fonctionnalités R Services](media/2016setup-rsvcs-features.png "Sélectionner ces fonctionnalités pour R Services dans la base de données")

    > [!IMPORTANT]
    > N’installez pas R Server et R Services en même temps. Normalement, vous installeriez R Server (autonome) pour créer un environnement à partir duquel un spécialiste en science des données ou un développeur peut se connecter à SQL Server et déployer des solutions R. Vous n’avez donc pas besoin de les installer sur le même ordinateur.

4.  Sur la page **Consentement à l’installation de Microsoft R Open**, cliquez sur **Accepter**.
  
    Vous devez accepter le contrat de licence pour télécharger Microsoft R Open, qui comprend une distribution des packages de base et des outils R open source ainsi que des packages et fournisseurs de connectivité R améliorés de l’équipe de développement R de Microsoft.
  
5. Une fois que vous avez accepté le contrat de licence, le programme d’installation est préparé. Cliquez sur **Suivant** lorsque le bouton devient disponible.

6. Sur la page **Prêt pour l’installation**, vérifiez que les éléments suivants sont inclus, puis choisissez **Installer**.

   + Services Moteur de base de données
   + R Services (dans la base de données)

    Notez l’emplacement du dossier sous le chemin `..\Setup Bootstrap\Log` où sont stockés les fichiers config. Une fois l’installation terminée, vous pouvez passer en revue les composants installés dans le fichier de synthèse.

7. Si vous êtes invité redémarrer l’ordinateur après l’installation, faites-le dès à présent. Il est important de lire le message affiché par l'Assistant Installation à la fin de l'installation. Pour plus d'informations, consultez [View and Read SQL Server Setup Log Files](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files).

## <a name="set-environment-variables"></a>Définir des variables d’environnement

Pour l’intégration de fonctionnalités R uniquement, vous devez définir la variable d’environnement **MKL_CBWR** pour [garantir la cohérence de la sortie](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) des calculs d’Intel Math Kernel Library (MKL).

1. Dans le Panneau de configuration, cliquez sur **Système et sécurité** > **Système** > **Paramètres système avancés** > **Variables d’environnement**.

2. Créez une variable Utilisateur ou Système. 

  + Nommez la variable `MKL_CBWR`.
  + Définissez la valeur de la variable sur `AUTO`.

Cette étape nécessite un redémarrage du serveur. Si vous vous apprêtez à activer l’exécution de scripts, vous pouvez reporter le redémarrage jusqu’à ce que le travail de configuration soit complètement terminé.

<a name="bkmk_enableFeature"></a>

##  <a name="enable-script-execution"></a>Activer l’exécution de scripts

1. Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > Vous pouvez télécharger et installer la version appropriée à partir de cette page : [Téléchargez SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > Vous pouvez également utiliser [Azure Data Studio](../../azure-data-studio/what-is.md), qui prend en charge les requêtes et les tâches d’administration sur SQL Server.
  
2. Connectez-vous à l’instance sur laquelle vous avez installé Machine Learning Services, cliquez sur **Nouvelle requête** pour ouvrir une fenêtre de requête, puis exécutez la commande suivante :

   ```sql
   sp_configure
   ```
    La propriété `external scripts enabled` a normalement la valeur **0** à ce stade. En effet, la fonctionnalité est désactivée par défaut. Elle doit être activée de manière explicite par un administrateur pour que vous puissiez exécuter des scripts R ou Python.
     
3. Pour activer la fonctionnalité d’exécution de scripts externes, exécutez l’instruction suivante :
  
    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
## <a name="restart-the-service"></a>Redémarrez le service.

Une fois l’installation terminée, redémarrez le moteur de base de données avant de poursuivre pour activer l’exécution de scripts.

Le redémarrage du service entraîne également le redémarrage automatique du service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] associé.

Pour redémarrer le service, vous pouvez cliquer avec le bouton droit sur la commande **Redémarrer** pour l’instance dans SSMS, utiliser le panneau **Services** dans le Panneau de configuration ou utiliser le [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Vérifier l'installation

Vérifiez l’état d’installation de l’instance à l’aide des [rapports personnalisés](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

Effectuez les étapes suivantes pour vérifier que tous les composants utilisés pour lancer un script externe sont en cours d’exécution.

1. Dans SQL Server Management Studio, ouvrez une nouvelle fenêtre de requête et exécutez la commande suivante :
    
    ```sql
    EXEC sp_configure  'external scripts enabled'
    ```

    La valeur **run_value** doit maintenant être définie sur 1.

2. Ouvrez le panneau **Services** ou le Gestionnaire de configuration SQL Server, puis vérifiez que le service **SQL Server Launchpad** est en cours d’exécution. Vous devez disposer d’un service pour chaque instance du moteur de base de données sur laquelle R ou Python est installé. Pour plus d’informations sur le service, consultez [Framework d’extensibilité](../concepts/extensibility-framework.md).

7. Si le service Launchpad est en cours d’exécution, vous devez être en mesure d’exécuter des scripts R simples pour vérifier que les runtimes de script externes peuvent communiquer avec SQL Server. 

    Ouvrez une nouvelle fenêtre **Requête** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis exécutez un script de ce type :
    
    ```sql
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    L’exécution du script peut prendre un certain temps lors du premier chargement du runtime de script externe. Les résultats doivent se présenter comme suit :

    | hello |
    |----|
    | 1|

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Appliquer des mises à jour

Nous vous recommandons d’appliquer la mise à jour cumulative la plus récente au moteur de base de données et aux composants de machine learning.

Sur les appareils connectés à Internet, les mises à jour cumulatives sont généralement appliquées par le biais de Windows Update. Cependant, vous pouvez également contrôler les mises à jour en effectuant les étapes ci-dessous. Quand vous appliquez la mise à jour au moteur de base de données, le programme d’installation extrait les mises à jour cumulatives pour toutes les bibliothèques R que vous avez installées sur la même instance. 

Sur les serveurs non connectés, des étapes supplémentaires sont nécessaires. Pour plus d’informations, consultez [Installation sur des ordinateurs sans accès à Internet > Appliquer des mises à jour cumulatives](sql-ml-component-install-without-internet-access.md#apply-cu).

1. Commencez avec une instance de base déjà installée : Version initiale de SQL Server 2016, SQL Server 2016 SP 1 ou SQL Server 2016 SP 2.

2. Accédez à la liste des mises à jour cumulatives : [Mises à jour de SQL Server 2016](https://sqlserverupdates.com/sql-server-2016-updates/)

3. Sélectionnez la mise à jour cumulative la plus récente. Un fichier exécutable est téléchargé et extrait automatiquement.

4. Exécutez le programme d'installation. Acceptez les termes du contrat de licence, puis, dans la page Sélection de fonctionnalités, passez en revue les fonctionnalités pour lesquelles des mises à jour cumulatives sont appliquées. Vous devez voir toutes les fonctionnalités installées pour l’instance actuelle, y compris R Services. Le programme d’installation télécharge les fichiers CAB nécessaires à la mise à jour de toutes les fonctionnalités.

5. Poursuivez avec l’Assistant en acceptant les termes du contrat de licence pour la distribution R. 

<a name="bkmk_FollowUp"></a> 

## <a name="additional-configuration"></a>Configuration supplémentaire

Si l’étape de vérification des scripts externes réussit, vous pouvez exécuter des commandes Python à partir de SQL Server Management Studio, de Visual Studio Code ou de tout autre client capable d’envoyer des instructions T-SQL au serveur.

Si une erreur s’est produite lors de l’exécution de la commande, passez en revue les étapes de configuration supplémentaires de cette section. Vous devrez peut-être apporter des configurations supplémentaires spécifiques au service ou à la base de données.

Au niveau de l’instance, ces configurations supplémentaires peuvent inclure :

* [Configurer le pare-feu pour SQL Server Machine Learning Services](../../advanced-analytics/security/firewall-configuration.md)
* [Activer des protocoles réseau supplémentaires](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Activer des connexions à distance](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Gestion des quotas de disque](https://docs.microsoft.com/windows/desktop/fileio/managing-disk-quotas) pour éviter que les scripts externes n’exécutent des tâches qui saturent l’espace disque

<a name="bkmk_configureAccounts"></a>
<a name="bkmk_AllowLogon"></a>

Vous aurez peut-être besoin d’effectuer les mises à jour de configuration suivantes sur la base de données :

* [Accorder des autorisations utilisateur pour SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md)
* [Ajouter SQLRUserGroup comme utilisateur de base de données](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md)

> [!NOTE]
> Toutes les modifications répertoriées ne sont pas requises, et il se peut qu’aucune ne le soit. Les exigences dépendent de votre schéma de sécurité, de l’emplacement d’installation de SQL Server et de la façon dont les utilisateurs sont supposés se connecter à la base de données et exécuter des scripts externes. Vous trouverez ici des conseils de dépannage supplémentaires : [FAQ sur la mise à niveau et l’installation](../r/upgrade-and-installation-faq-sql-server-r-services.md)

## <a name="suggested-optimizations"></a>Optimisations suggérées

Maintenant que tout fonctionne, vous souhaitez peut-être optimiser le serveur en vue de la prise en charge du machine learning ou installer des modèles préalablement entraînés.

### <a name="add-more-worker-accounts"></a>Ajouter des comptes de travail

Si vous pensez utiliser R intensément, ou que de nombreux utilisateurs exécuteront des scripts simultanément, vous pouvez augmenter le nombre de comptes de travail affectés au service Launchpad. Pour plus d’informations, voir [Modifier le pool de comptes d’utilisateur pour SQL Server Machine Learning Services](../administration/modify-user-account-pool.md).

<a name="bkmk_optimize"></a>

### <a name="optimize-the-server-for-external-script-execution"></a>Optimiser le serveur pour l’exécution de scripts externes

Les paramètres par défaut pour la configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont destinés à optimiser l’équilibre du serveur pour un éventail de services pris en charge par le moteur de base de données, ce qui peut inclure les processus d’extraction, transformation et chargement (ETL, extract, transform, load), la création de rapports, l’audit et les applications qui utilisent les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ceci explique pourquoi, dans les paramètres par défaut, les ressources sont parfois restreintes ou limitées pour le machine learning, en particulier dans les opérations utilisant beaucoup de mémoire.

Pour vous assurer que les travaux de machine learning sont classés par ordre de priorité et correctement ressourcés, nous vous recommandons d’utiliser la fonctionnalité Resource Governor de SQL Server pour configurer un pool de ressources externes. Vous pouvez aussi modifier la quantité de mémoire allouée au moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou augmenter le nombre de comptes s’exécutant sous le service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)].

- Pour configurer un pool de ressources afin de gérer des ressources externes, consultez [Créer un pool de ressources externes](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Pour modifier la quantité de mémoire réservée à la base de données, consultez [Options de configuration de la mémoire du serveur](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Pour modifier le nombre de comptes R qui peuvent être démarrés par [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], consultez la page [Modify the user account pool for Machine Learning](../administration/modify-user-account-pool.md) (Modifier le pool de compte d’utilisateur pour le Machine Learning).

Si vous utilisez l’édition Standard et que vous n’avez pas le composant Resource Governor, vous pouvez utiliser la fonctionnalité Dynamic Management Views (DMV), les événements étendus ainsi que la surveillance d’événements Windows pour mieux gérer les ressources serveur utilisées par R. Pour plus d’informations, consultez [Surveillance et gestion de R Services](../r/managing-and-monitoring-r-solutions.md).

### <a name="install-additional-r-packages"></a>Installer des packages R supplémentaires

Les solutions R que vous créez pour SQL Server peuvent appeler des fonctions R de base, des fonctions des packages propriétaires installés avec SQL Server et des packages R tiers compatibles avec la version de R open source installée par SQL Server.

Installez les packages que vous souhaitez utiliser à partir de SQL Server dans la bibliothèque par défaut qui est utilisée par l’instance. Si vous avez installé R séparément sur l’ordinateur, ou installé des packages dans des bibliothèques utilisateur, vous ne pourrez pas utiliser ces packages à partir de T-SQL.

Le processus d’installation et de gestion des packages R est différent dans SQL Server 2016 et SQL Server 2017. Dans SQL Server 2016, un administrateur de base de données doit installer les packages R dont les utilisateurs ont besoin. Dans SQL Server 2017, vous pouvez configurer des groupes d’utilisateurs afin de partager des packages individuellement pour chaque base de données ou configurer des rôles de base de données pour permettre aux utilisateurs d’installer leurs propres packages. Pour plus d’informations, consultez la page [Install new R packages](../r/install-additional-r-packages-on-sql-server.md) (Installer de nouveaux packages R).

## <a name="next-steps"></a>Étapes suivantes

Les développeurs peuvent démarrer avec quelques exemples simples et découvrir les principes de base du fonctionnement de R avec SQL Server. Pour l’étape suivante, consultez les liens suivants :

+ [Tutoriel : Exécuter R dans T-SQL](../tutorials/quickstart-r-create-script.md)
+ [Tutoriel : Analytique dans la base de données pour les développeurs R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Pour consulter des exemples d’apprentissage automatique basés sur des scénarios réels, consultez les [Didacticiels d’apprentissage automatique](../tutorials/machine-learning-services-tutorials.md).