---
title: Installer SQL Server Machine Learning Services (Python, R) sur Windows
titleSuffix: ''
description: Cet article explique comment installer SQL Server Machine Learning Services sur Windows. Vous pouvez utiliser Machine Learning Services pour exécuter des scripts Python et R dans la base de données.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: bdd1a9e20379ae66335baa7d3c415cf68e570d47
ms.sourcegitcommit: 2f56848ec422845ee81fb84ed321a716c677aa0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71271919"
---
# <a name="install-sql-server-machine-learning-services-python-and-r-on-windows"></a>Installer SQL Server Machine Learning Services (Python et R) sur Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment installer SQL Server Machine Learning Services sur Windows. Vous pouvez utiliser Machine Learning Services pour exécuter des scripts Python et R dans la base de données.

## <a name="bkmk_prereqs"></a> Liste de vérification préalable à l’installation

+ L’installation de SQL Server 2017 (ou version ultérieure) est requise si vous souhaitez installer Machine Learning Services avec la prise en charge du langage R ou python. Si, à la place, vous disposez d’un support d’installation SQL Server 2016, vous pouvez installer [SQL Server R services (dans la base de données)](sql-r-services-windows-install.md) pour obtenir la prise en charge du langage R.

+ Une instance du moteur de base de données est requise. Vous ne pouvez pas installer uniquement les fonctionnalités R ou python, même si vous pouvez les ajouter de façon incrémentielle à une instance existante.

+ Pour la continuité des activités, les [groupes de disponibilité Always on](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server) sont pris en charge pour les machine learning services. Vous devez installer Machine Learning Services et configurer des packages sur chaque nœud.

+ L’installation de Machine Learning Services n’est *pas prise en charge* sur un cluster de basculement dans SQL Server 2017. Toutefois, il *est pris en charge* avec SQL Server 2019. 
 
+ N’installez pas Machine Learning Services sur un contrôleur de domaine. La partie Machine Learning Services du programme d’installation échoue.

+ N’installez pas de **fonctionnalités** > partagées**machine learning Server (autonomes)** sur le même ordinateur exécutant une instance de dans la base de données. Un serveur autonome est en concurrence pour les mêmes ressources, ce qui permet de sous-utiliser les performances des deux installations.

+ L’installation côte à côte avec d’autres versions de R et Python est prise en charge, mais n’est pas recommandée. Il est pris en charge, car SQL Server instance utilise ses propres copies des distributions R et Anaconda Open source. Mais cela n’est pas recommandé, car l’exécution de code qui utilise R et Python sur l’ordinateur SQL Server en dehors de SQL Server peut entraîner divers problèmes:
    
  + Vous utilisez une autre bibliothèque et un autre fichier exécutable, et vous pouvez obtenir des résultats différents, que lorsque vous exécutez dans SQL Server.
  + Les scripts R et Python exécutés dans les bibliothèques externes ne peuvent pas être gérés par SQL Server, ce qui entraîne une contention des ressources.
  
> [!IMPORTANT]
> Une fois l’installation terminée, veillez à suivre les étapes de la suite de la configuration décrites dans cet article. Ces étapes incluent l’activation de SQL Server pour utiliser des scripts externes et l’ajout de comptes requis pour SQL Server pour exécuter des travaux R et Python en votre nom. Les modifications de configuration nécessitent généralement un redémarrage de l’instance ou un redémarrage du service launchpad.

## <a name="get-the-installation-media"></a>Obtenir le média d’installation

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="run-setup"></a>Exécuter le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrez l’Assistant Installation de SQL Server 2017. 
  
2. Sous l’onglet **installation** , sélectionnez **nouvelle SQL Server installation autonome ou ajout de fonctionnalités à une installation existante**.

   ![Nouvelle installation SQL Server autonome](media/2017setup-installation-page-mlsvcs.PNG)
   
3. Dans la page **Sélection de fonctionnalités** , sélectionnez les options suivantes :
  
    -   **Services Moteur de base de données**
  
         Pour utiliser R et Python avec SQL Server, vous devez installer une instance du moteur de base de données. Vous pouvez utiliser une instance par défaut ou une instance nommée.
  
    -   **Machine Learning Services (dans la base de données)**
  
         Cette option installe les services de base de données qui prennent en charge l’exécution de scripts R et Python.

    -   **R**

        Cochez cette option pour ajouter les packages Microsoft R, l’interpréteur et le R Open source. 

    -   **Python**

        Cochez cette option pour ajouter les packages Microsoft Python, l’exécutable Python 3,5, puis sélectionnez les bibliothèques à partir de la distribution Anaconda.
        
        ![Options de fonctionnalité pour R et Python](media/2017setup-features-page-mls-rpy.png "Options d’installation pour Python")

        > [!NOTE]
        > 
        > Ne sélectionnez pas l’option pour **machine learning Server (autonome)** . L’option d’installation de Machine Learning Server sous **fonctionnalités partagées** est destinée à être utilisée sur un ordinateur distinct.

4. Sur la page **consentement pour installer R** , sélectionnez **accepter**. Ce contrat de licence couvre Microsoft R Open, qui comprend une distribution des packages de base et des outils R Open source, ainsi que des packages R et des fournisseurs de connectivité améliorés de l’équipe de développement Microsoft.

5. Sur la page **consentement pour installer python** , sélectionnez **accepter**. Le contrat de licence Open source Python couvre également Anaconda et les outils associés, ainsi que quelques nouvelles bibliothèques python de l’équipe de développement Microsoft.
     
     ![Contrat de licence python](media/2017setup-python-license.png "Contrat de licence pour Python")
  
    > [!NOTE]
    >  Si l’ordinateur que vous utilisez n’a pas accès à Internet, vous pouvez suspendre le programme d’installation à ce stade pour télécharger les programmes d’installation séparément. Pour plus d’informations, consultez [installer des composants machine learning sans accès à Internet](../install/sql-ml-component-install-without-internet-access.md).
  
     Sélectionnez **accepter**, attendez que le bouton **suivant** devienne actif, puis sélectionnez **suivant**.
  
6. Sur la page **prêt pour l’installation** , vérifiez que ces sélections sont incluses, puis sélectionnez **installer**.
  
    + Services Moteur de base de données
    + Machine Learning Services (en base de données)
    + R ou python, ou les deux

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

## <a name="enable-script-execution"></a>Activer l’exécution du script

1. Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > Vous pouvez télécharger et installer la version appropriée à partir de cette page: [Téléchargez SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > Vous pouvez également utiliser [Azure Data Studio](../../azure-data-studio/what-is.md), qui prend en charge les tâches administratives et les requêtes sur SQL Server.
  
2. Connectez-vous à l’instance où vous avez installé Machine Learning Services, cliquez sur **nouvelle requête** pour ouvrir une fenêtre de requête, puis exécutez la commande suivante:

    ```sql
    sp_configure
    ```

    La propriété `external scripts enabled` a normalement la valeur **0** à ce stade. Cela est dû au fait que la fonctionnalité est désactivée par défaut. Pour que vous puissiez exécuter des scripts R ou python, la fonctionnalité doit être activée de manière explicite par un administrateur.
    
3.  Pour activer la fonctionnalité de script externe, exécutez l’instruction suivante:
    
    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    Si vous avez déjà activé la fonctionnalité pour le langage R, n’exécutez pas reconfigure une deuxième fois pour Python. La plateforme d’extensibilité sous-jacente prend en charge les deux langages.

## <a name="restart-the-service"></a>Redémarrez le service.

Une fois l’installation terminée, redémarrez le moteur de base de données avant de passer à la suivante, en activant l’exécution du script.

Le redémarrage du service redémarre également automatiquement le service associé [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] .

Vous pouvez redémarrer le service à l’aide de la commande de redémarrage du bouton droit de l’instance dans SSMS, ou à l’aide du panneau **services** du panneau de configuration, ou à l’aide de [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Vérifier l'installation

Vérifiez l’état d’installation de l’instance dans les [rapports personnalisés](../r/monitor-r-services-using-custom-reports-in-management-studio.md) ou les journaux d’installation.

Procédez comme suit pour vérifier que tous les composants utilisés pour lancer le script externe sont en cours d’exécution.

1. Dans SQL Server Management Studio, ouvrez une nouvelle fenêtre de requête, puis exécutez la commande suivante:
    
    ```sql
    EXEC sp_configure  'external scripts enabled'
    ```

    La valeur **run_value** doit maintenant être définie sur 1.
    
2. Ouvrez le panneau **services** ou gestionnaire de configuration SQL Server, puis vérifiez **SQL Server Launchpad service** est en cours d’exécution. Vous devez disposer d’un service pour chaque instance du moteur de base de données sur laquelle R ou python est installé. Pour plus d’informations sur le service, consultez [extensibilité Framework](../concepts/extensibility-framework.md). 
   
3. Si Launchpad est en cours d’exécution, vous devez être en mesure d’exécuter des scripts R et Python simples pour vérifier que les runtimes de script externes peuvent communiquer avec SQL Server.

   Ouvrez une nouvelle fenêtre de requête [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]dans, puis exécutez un script tel que le suivant:
    
    + Pour R
    
    ```sql
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    + Pour Python
    
    ```sql
    EXEC sp_execute_external_script  @language =N'Python',
    @script=N'
    OutputDataSet = InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    **Résultats**

    L’exécution du script peut prendre un peu de temps, la première fois que l’exécution du script externe est chargée. Les résultats doivent ressembler à ceci:

    | hello |
    |----|
    | 1|

> [!NOTE]
> Les colonnes ou les en-têtes utilisés dans le script Python ne sont pas retournés, par conception. Pour ajouter des noms de colonnes à votre sortie, vous devez spécifier le schéma pour le jeu de données de retour. POUR ce faire, utilisez le paramètre WITH RESULTs de la procédure stockée, en nommant les colonnes et en spécifiant le type de données SQL.
> 
> Par exemple, vous pouvez ajouter la ligne suivante pour générer un nom de colonne arbitraire:`WITH RESULT SETS ((Col1 AS int))`

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Appliquer les mises à jour

Nous vous recommandons d’appliquer la dernière mise à jour cumulative au moteur de base de données et aux composants de Machine Learning.

Sur les appareils connectés à Internet, les mises à jour cumulatives sont généralement appliquées par le biais de Windows Update, mais vous pouvez également suivre les étapes ci-dessous pour contrôler les mises à jour. Lorsque vous appliquez la mise à jour du moteur de base de données, le programme d’installation extrait les mises à jour cumulatives pour toutes les fonctionnalités R ou python que vous avez installées sur la même instance. 

Sur les serveurs déconnectés, des étapes supplémentaires sont requises. Pour plus d’informations, consultez [installer sur des ordinateurs sans accès internet > appliquer des mises à jour cumulatives](sql-ml-component-install-without-internet-access.md#apply-cu).

1. Démarrer avec une instance de ligne de base déjà installée: Version initiale de SQL Server 2017

2. Accédez à la liste des mises à jour cumulatives: [Mises à jour de SQL Server 2017](https://sqlserverupdates.com/sql-server-2017-updates/)

3. Sélectionnez la dernière mise à jour cumulative. Un fichier exécutable est téléchargé et extrait automatiquement.

4. Exécutez le programme d'installation. Acceptez les termes du contrat de licence et, dans la page sélection de fonctionnalités, passez en revue les fonctionnalités pour lesquelles des mises à jour cumulatives sont appliquées. Vous devez voir toutes les fonctionnalités installées pour l’instance actuelle, y compris les fonctionnalités de Machine Learning. Le programme d’installation télécharge les fichiers CAB nécessaires à la mise à jour de toutes les fonctionnalités.

  ![Résumé des fonctionnalités installées](media/cumulative-update-feature-selection.png)

5. Poursuivez avec l’Assistant, en acceptant les termes du contrat de licence pour les distributions R et Python. 

## <a name="additional-configuration"></a>Configuration supplémentaire

Si l’étape de vérification du script externe a réussi, vous pouvez exécuter des commandes R ou python à partir de SQL Server Management Studio, Visual Studio Code ou tout autre client qui peut envoyer des instructions T-SQL au serveur.

Si vous avez rencontré une erreur lors de l’exécution de la commande, passez en revue les étapes de configuration supplémentaires de cette section. Vous devrez peut-être apporter des configurations appropriées supplémentaires au service ou à la base de données.

Au niveau de l’instance, une configuration supplémentaire peut inclure:

* [Configuration du pare-feu pour SQL Server Machine Learning Services](../../advanced-analytics/security/firewall-configuration.md)
* [Activer les protocoles réseau supplémentaires](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Activer les connexions à distance](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Créer une connexion pour SQLRUserGroup](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md)
* [Gérer les quotas de disque](https://docs.microsoft.com/windows/desktop/fileio/managing-disk-quotas) pour éviter les scripts externes exécutant des tâches qui épuisent l’espace disque

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
Dans SQL Server 2019 sur Windows, le mécanisme d’isolation a changé. Cela affecte les **SQLRUserGroup**, les règles de pare-feu, l’autorisation de fichier et l’authentification implicite. Pour plus d’informations, consultez [modifications de l’isolation pour machine learning services](sql-server-machine-learning-services-2019.md).
::: moniker-end

<a name="bkmk_configureAccounts"></a> 
<a name="permissions-external-script"></a> 

Sur la base de données, vous pouvez avoir besoin des mises à jour de configuration suivantes:

* [Accorder aux utilisateurs l’autorisation d’SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md)

> [!NOTE]
> La nécessité d’une configuration supplémentaire dépend de votre schéma de sécurité, de l’emplacement où vous avez installé SQL Server et de la façon dont vous vous attendez à ce que les utilisateurs se connectent à la base de données et exécutent des scripts externes.

## <a name="suggested-optimizations"></a>Optimisations suggérées

Maintenant que tout fonctionne, vous souhaiterez peut-être également optimiser le serveur pour prendre en charge Machine Learning ou installer des modèles préformés.

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
### <a name="add-more-worker-accounts"></a>Ajouter d’autres comptes de travail

Si vous prévoyez que de nombreux utilisateurs exécutent des scripts simultanément, vous pouvez augmenter le nombre de comptes de travail affectés au service launchpad. Pour plus d’informations, consultez [modifier le pool de comptes d’utilisateurs pour SQL Server machine learning services](../administration/modify-user-account-pool.md).
::: moniker-end

### <a name="optimize-the-server-for-script-execution"></a>Optimiser le serveur pour l’exécution du script

Les paramètres par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le programme d’installation de sont destinés à optimiser l’équilibre du serveur pour divers services pris en charge par le moteur de base de données, qui peuvent inclure des processus d’extraction, de transformation et de chargement (ETL), de création de rapports, d’audit et applications qui utilisent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des données. Par conséquent, dans les paramètres par défaut, vous constaterez peut-être que les ressources pour Machine Learning sont parfois limitées ou limitées, en particulier dans les opérations gourmandes en mémoire.

Pour vous assurer que les travaux de Machine Learning sont classés par ordre de priorité et resourcement appropriés, nous vous recommandons d’utiliser SQL Server Resource Governor pour configurer un pool de ressources externes. Vous pouvez également modifier la quantité de mémoire allouée au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur de base de données ou augmenter le nombre de comptes qui s’exécutent sous le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service.

- Pour configurer un pool de ressources pour la gestion des ressources externes, consultez [créer un pool de ressources externes](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Pour modifier la quantité de mémoire réservée pour la base de données, consultez Options de configuration de la [mémoire du serveur](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Pour modifier le nombre de comptes R qui peuvent être démarrés [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]par, consultez [modifier le pool de comptes d’utilisateur pour machine learning](../administration/modify-user-account-pool.md).

Si vous utilisez l’édition standard et que vous n’avez pas Resource Governor, vous pouvez utiliser les vues de gestion dynamique (DMV) et les événements étendus, ainsi que l’analyse des événements Windows, pour faciliter la gestion des ressources du serveur. Pour plus d’informations, consultez [Monitoring and Managing R services](../r/managing-and-monitoring-r-solutions.md) et [Monitoring and Managing python services](../python/managing-and-monitoring-python-solutions.md).

### <a name="install-additional-r-packages"></a>Installer des packages R supplémentaires

Les solutions R que vous créez pour SQL Server peuvent appeler des fonctions R de base, des fonctions des packages propriétaires installés avec SQL Server et des packages R tiers compatibles avec la version de R Open source installée par SQL Server.

Installez les packages que vous souhaitez utiliser à partir de SQL Server dans la bibliothèque par défaut qui est utilisée par l’instance. Si vous disposez d’une installation distincte de R sur l’ordinateur, ou si vous avez installé des packages dans les bibliothèques utilisateur, vous ne pourrez pas utiliser ces packages à partir de T-SQL.

Pour installer et gérer des packages R, vous pouvez configurer des groupes d’utilisateurs pour partager des packages au niveau de chaque base de données ou configurer des rôles de base de données pour permettre aux utilisateurs d’installer leurs propres packages. Pour plus d’informations, consultez [installer de nouveaux packages R dans SQL Server](../r/install-additional-r-packages-on-sql-server.md).

## <a name="next-steps"></a>Étapes suivantes

Les développeurs peuvent démarrer avec quelques exemples simples et découvrir les principes de base du fonctionnement de R avec SQL Server. Pour l’étape suivante, consultez les liens suivants :

+ [Tutoriel : Exécuter R dans T-SQL](../tutorials/quickstart-r-create-script.md)
+ [Tutoriel : Analytique dans la base de données pour les développeurs R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Les développeurs Python peuvent apprendre à utiliser Python avec SQL Server en effectuant les didacticiels suivants :

+ [Tutoriel : Exécuter Python dans T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Tutoriel : Analytique dans la base de données pour les développeurs Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Pour consulter des exemples d’apprentissage automatique basés sur des scénarios réels, consultez les [Didacticiels d’apprentissage automatique](../tutorials/machine-learning-services-tutorials.md).
