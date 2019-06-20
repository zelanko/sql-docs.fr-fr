---
title: Installer R Server ou Machine Learning Server (autonome) à l’aide du programme d’installation de SQL Server - SQL Server Machine Learning
description: Configurer un serveur d’apprentissage autonome non-instance-prenant en charge pour le développement R et Python à l’aide de revoscalepy, RevoScaleR, MicrosoftML et autres packages.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/28/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 911086beaaaeb28a036a764e066402d7ba6f1da7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62747071"
---
# <a name="install-machine-learning-server-standalone-or-r-server-standalone-using-sql-server-setup"></a>Installer Machine Learning Server (autonome) ou R Server (autonome) à l’aide du programme d’installation de SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Le programme d’installation de SQL Server inclut un **fonctionnalité partagée** option pour installer une instance prenant, autonome machine learning serveur qui s’exécute en dehors de SQL Server. Dans SQL Server 2016, cette fonctionnalité est appelée **R Server (autonome)** . Dans SQL Server 2017, elle est appelée **Machine Learning Server (autonome)** et inclut R et Python. 

Un serveur autonome, telle qu’installée par le programme d’installation de SQL Server est fonctionnellement équivalent pour les versions non SQL personnalisée de [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), prenant en charge les mêmes cas d’usage et scénarios, notamment :

+ Exécution à distance, la commutation entre les sessions locales et distantes dans la même console
+ Opérationnalisation avec les nœuds de site web et les nœuds de calcul
+ Déploiement de service Web : la possibilité de package de script R et Python dans des services web
+ Collection complète de bibliothèques de fonctions R et Python

Comme un serveur indépendant découplé à partir de SQL Server, l’environnement R et Python est configuré, sécurisées et accessibles en utilisant le système d’exploitation sous-jacent et les outils fournis dans le serveur autonome, pas de SQL Server.

En outre à SQL Server, un serveur autonome est utile si vous avez besoin pour développer des solutions qui peuvent utiliser des contextes de calcul à distance à la gamme complète des plateformes de données pris en charge d’apprentissage hautes performances. Vous pouvez décaler l’exécution à partir du serveur local à une Machine Learning Server à distance sur un cluster Spark ou sur une autre instance de SQL Server.

<a name="bkmk_prereqs"> </a>

## <a name="pre-install-checklist"></a>Liste de vérification de préinstallation

Si vous avez installé une version antérieure, telles que SQL Server 2016 R Server (autonome) ou Microsoft R Server, désinstallez l’installation existante avant de continuer.

En règle générale, nous recommandons que vous traiter autonome installations de serveur et base de données du moteur dépendant des instances en tant que mutuellement exclusives afin d’éviter les conflits de ressources, mais si vous avez suffisamment de ressources, il n’existe aucune interdiction par rapport à l’installation de tous les deux sur le même ordinateur physique.

Vous ne pouvez avoir qu’un serveur autonome sur l’ordinateur : SQL Server 2017 Machine Learning Server ou SQL Server 2016 R Server (autonome). Veillez à désinstaller une version avant d’ajouter un nouveau.

::: moniker range="=sql-server-2016"
<a name="bkmk_ga_instalpatch"></a> 

 ###  <a name="install-patch-requirement"></a>Installer le correctif obligatoire 

Pour SQL Server 2016 uniquement : Microsoft a identifié un problème avec la version spécifique des fichiers binaires Microsoft VC++ 2013 Runtime qui sont installés en tant que composants requis par SQL Server. Si cette mise à jour des fichiers binaires du runtime VC n’est pas installée, SQL Server risque de rencontrer des problèmes de stabilité dans certains scénarios. Avant d’installer SQL Server, suivez les instructions données dans [Notes de publication de SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) pour voir si votre ordinateur nécessite un correctif pour les fichiers binaires du runtime VC.  
::: moniker-end

## <a name="get-the-installation-media"></a>Obtenir le média d’installation

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="run-setup"></a>Exécutez le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrer l’Assistant installation.

2. Cliquez sur le **Installation** et sélectionnez **installation de la nouvelle Machine Learning Server (autonome)** .
    
     ![Installer Machine Learning Server (autonome)](media/2017setup-installation-page-mlsvr.png "démarrer l’installation de Machine Learning Server (autonome)")

3. Une fois la vérification des règles terminée, acceptez les termes du contrat de licence de SQL Server, puis sélectionnez une nouvelle installation.

4. Sur le **sélection des fonctionnalités** page, ce qui suit options doivent déjà être sélectionnées :

    - Microsoft Machine Learning Server (autonome)

    - R et Python est sélectionnées par défaut. Vous pouvez désélectionner les deux langues, mais nous vous recommandons d’installer au moins une des langues prises en charge.

     ![Choisissez les fonctionnalités de R ou Python](media/2017setup-features-page-mlsvr-rpy.png "démarrer l’installation de Machine Learning Server (autonome)")
    
    Toutes les autres options peuvent être ignorées. 
    
    > [!NOTE]
    > Évitez d’installer le **fonctionnalités partagées** si l’ordinateur a déjà installé pour l’analytique en base de données de SQL Server Machine Learning Services. Cela crée des bibliothèques en double.
    > 
    > En outre, tandis que les scripts R ou Python en cours d’exécution dans SQL Server sont gérés par SQL Server pour autant en conflit avec la mémoire utilisée par d’autres services de moteur de base de données, serveur autonome machine learning ne comporte aucune contrainte de ce type et peut interférer avec d’autres opérations de base de données . Enfin, l’accès à distance via une session RDP, ce qui est souvent utilisée pour l’Opérationnalisation, est généralement bloqué par les administrateurs de base de données.
    > 
    > Pour ces raisons, nous recommandons généralement que vous installez Machine Learning Server (autonome) sur un ordinateur distinct à partir de SQL Server Machine Learning Services.

5.  Acceptez les termes du contrat de licence pour télécharger et installer des distributions de langue de base. Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**. 

     ![Contrat de licence Python](media/2017setup-python-license.png "contrat de licence de Python")

6.  Sur la page **Prêt pour l’installation** , vérifiez vos sélections, et cliquez sur **Installer**.

Lors de l’installation terminée, consultez [rapports personnalisés pour SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md) pour avec des erreurs ou avertissements, consultez [mise à niveau et installation FAQ - Services Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md).
::: moniker-end

::: moniker range="=sql-server-2016"
## <a name="run-setup"></a>Exécutez le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrer l’Assistant installation.

2. Sur le **Installation** , cliquez sur **installation nouvelle R Server (autonome)** .
    
     ![Démarrer le programme d’installation de R Server (autonome)](media/2016-setup-installation-rsvr.png "démarrer le programme d’installation de R Server (autonome)")

3. Une fois la vérification des règles terminée, acceptez les termes du contrat de licence de SQL Server, puis sélectionnez une nouvelle installation.

4.  Dans la page **Sélection de fonctionnalités** , l’option suivante doit déjà être sélectionnée :
    
    **R Server (autonome)**  
    
    ![Sélections pour R Server (autonome) de fonctionnalités](media/2016setup-rserver-features.png "fonctionnalité sélections pour R Server (autonome)")
    
    Toutes les autres options peuvent être ignorées. 
    
    > [!NOTE]
    > Évitez d’installer le **fonctionnalités partagées** si vous exécutez le programme d’installation sur un ordinateur où R Services a déjà été installé pour l’analytique en base de données de SQL Server. Cela crée des bibliothèques en double.
    > 
    > Tandis que les scripts R en cours d’exécution dans SQL Server sont gérés par SQL Server pour autant en conflit avec la mémoire utilisée par d’autres services de moteur de base de données, R Server autonome ne comporte aucune contrainte de ce type et peut interférer avec d’autres opérations de base de données.
    > 
    > Nous recommandons généralement que vous installez R Server (autonome) sur un ordinateur distinct à partir de SQL Server R Services (en base de données).

5.  Acceptez les termes du contrat de licence pour télécharger et installer des distributions de langue de base. Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**. 

6.  Sur la page **Prêt pour l’installation** , vérifiez vos sélections, et cliquez sur **Installer**.

Lors de l’installation terminée, consultez [rapports personnalisés pour SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md) pour avec des erreurs ou avertissements, consultez [mise à niveau et installation FAQ - Services Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md).
::: moniker-end

## <a name="set-environment-variables"></a>Jeu de variables d’environnement

Pour R fonctionnalité d’intégration uniquement, vous devez définir le **MKL_CBWR** variable d’environnement [résultat homogène](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) des calculs d’Intel Math Kernel Library (MKL).

1. Dans le panneau de configuration, cliquez sur **système et sécurité** > **système** > **paramètres système avancés**  >   **Variables d’environnement**.

2. Créer une nouvelle variable utilisateur ou système. 

  + Nom de variable du jeu `MKL_CBWR`
  + La valeur est la valeur de variable `AUTO`

3. Redémarrez le serveur.

<a name="install-path"></a>

### <a name="default-installation-folders"></a>Dossiers d’installation par défaut

Pour le développement R et Python, il est courant d’avoir plusieurs versions sur le même ordinateur. Installé par le programme d’installation de SQL Server, la distribution de base est installée dans un dossier associé à la version de SQL Server que vous avez utilisé pour le programme d’installation.

Le tableau suivant répertorie les chemins d’accès pour les distributions de R et Python créées par les programmes d’installation de Microsoft. Par souci d’exhaustivité, la table inclut des chemins d’accès générés par le programme d’installation de SQL Server, ainsi que le programme d’installation autonome de Microsoft Machine Learning Server.

|Version| Méthode d’installation | Dossier par défaut|
|----|----|----|
|SQL Server 2017 Machine Learning Server (autonome) |  Assistant d’installation de SQL Server 2017 |`C:\Program Files\Microsoft SQL Server\140\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Microsoft Machine Learning Server (autonome) |  Le programme d’installation de Windows autonome |`C:\Program Files\Microsoft\ML Server\R_SERVER`<br/>`C:\Program Files\Microsoft\ML Server\PYTHON_SERVER`|
|SQL Server 2017 Machine Learning Services (en base de données) |Assistant d’installation de SQL Server 2017, avec l’option de langage R|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
|SQL Server 2016 R Server (autonome) |  Assistant d’installation de SQL Server 2016 |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2016 R Services (en base de données) |Assistant d’installation de SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Appliquer des mises à jour

Nous vous recommandons d’appliquer la mise à jour cumulative la plus récente pour le moteur de base de données et les composants d’apprentissage. Mises à jour cumulatives sont installées via le programme d’installation. 

Sur les appareils connectés à internet, vous pouvez télécharger un exécutable à extraction automatique. Appliquer une mise à jour pour le moteur de base de données automatiquement extrait les mises à jour cumulatives pour les fonctionnalités existantes de R et Python. 

Sur les serveurs hors connexion, des étapes supplémentaires sont nécessaires. Vous devez obtenir la mise à jour cumulative pour le moteur de base de données, ainsi que les fichiers CAB pour les fonctionnalités d’apprentissage automatique. Tous les fichiers doivent être transférés vers le serveur isolé et appliqués manuellement.

1. Démarrez avec une instance de la ligne de base. Vous pouvez uniquement appliquer des mises à jour cumulatives aux installations existantes :

  + Machine Learning Server (autonome) à partir de la version initiale de SQL Server 2017
  + R Server (autonome) à partir de la version initiale de SQL Server 2016, SQL Server 2016 Service Pack 1 ou SQL Server 2016 Service Pack 2

2. Fermez toutes les sessions ouvertes R ou Python et d’arrêter tous les processus en cours d’exécution sur le système.

3. Si vous avez activé Opérationnalisation à exécuter en tant que nœuds de site web et des nœuds de calcul pour les déploiements de service web, sauvegardez le **AppSettings.json** fichier par mesure de précaution. Application SQL Server 2017 CU13 ou versions ultérieures revises ce fichier, vous pouvez donc une copie de sauvegarde pour conserver la version d’origine.

4. Sur un dispositif connecté à internet, cliquez sur le lien de mise à jour cumulative pour votre version de SQL Server.

  + [Mises à jour de SQL Server 2017](https://sqlserverupdates.com/sql-server-2017-updates/)
  + [Mises à jour de SQL Server 2016](https://sqlserverupdates.com/sql-server-2016-updates/)

5. Téléchargez la dernière mise à jour cumulative. C’est un fichier exécutable.

6. Sur un appareil connecté à internet, double-cliquez sur le fichier .exe pour exécuter le programme d’installation et de l’étape de l’Assistant pour accepter les termes du contrat de licence, passez en revue les fonctionnalités concernées et surveiller la progression jusqu'à la fin.

7. Sur un serveur sans connectivité internet :

   + Obtenir les fichiers CAB correspondants pour R et Python. Pour obtenir des liens de téléchargement, consultez [CAB télécharge les mises à jour cumulatives sur analytique en base de données de SQL Server instances](sql-ml-cab-downloads.md).

   + Transférer tous les fichiers, le fichier exécutable principal et les fichiers CAB, dans un dossier sur l’ordinateur hors connexion.

   + Double-cliquez sur le fichier .exe pour exécuter le programme d’installation. Lorsque vous installez une mise à jour cumulatif sur un serveur sans connectivité internet, vous êtes invité à sélectionner l’emplacement des fichiers .cab pour R et Python.

8. Après l’installation, sur un serveur pour lequel vous avez activé Opérationnalisation des nœuds de web et des nœuds de calcul, modifier **AppSettings.json**, ajout d’une entrée « MMLResourcePath », directement sous « MMLNativePath » :

    ```json
    "ScorerParameters": {
        "MMLNativePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\",
        "MMLResourcePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\"
    }
    ```

9. [Exécutez l’utilitaire d’administration CLI](https://docs.microsoft.com/machine-learning-server/operationalize/configure-admin-cli-launch) pour redémarrer le web et de nœuds de calcul. Pour plus d’étapes et la syntaxe, consultez [moniteur, de démarrage et d’arrêt web et de nœuds de calcul](https://docs.microsoft.com/machine-learning-server/operationalize/configure-admin-cli-stop-start).

## <a name="development-tools"></a>Outils de développement

Un IDE de développement n’est pas installé dans le cadre du programme d’installation. Pour plus d’informations sur la configuration d’un environnement de développement, consultez [configurer les outils R](../r/set-up-a-data-science-client.md) et [configurer Python tools](../python/setup-python-client-tools-sql.md).

## <a name="next-steps"></a>Étapes suivantes

Aux développeurs R peuvent démarrer avec des exemples simples et apprendre les bases du fonctionne de R avec SQL Server. Pour votre prochaine étape, consultez les liens suivants :

+ [Tutoriel : Exécuter R dans T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutoriel : Analytique en base de données pour les développeurs R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Les développeurs Python peuvent apprendre à utiliser Python avec SQL Server en suivant ces didacticiels :

+ [Tutoriel : Exécutez le code Python dans T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Tutoriel : Analytique en base de données pour les développeurs Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)
::: moniker-end

Pour afficher des exemples d’apprentissage qui sont basées sur des scénarios réels, consultez [d’apprentissage didacticiels](../tutorials/machine-learning-services-tutorials.md).
