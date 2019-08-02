---
title: Installer R Server ou Machine Learning Server (autonome) à l’aide du programme d’installation de SQL Server
description: Configurez un serveur de Machine Learning autonome ne prenant pas en charge les instances pour le développement R et Python à l’aide de RevoScaleR, revoscalepy, MicrosoftML et d’autres packages.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/28/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 94ca7b3646b9005e11b3ee4968cbfaaa65d42264
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715846"
---
# <a name="install-machine-learning-server-standalone-or-r-server-standalone-using-sql-server-setup"></a>Installer Machine Learning Server (autonome) ou R Server (autonome) à l’aide du programme d’installation de SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
SQL Server installation comprend une option de **fonctionnalité partagée** pour l’installation d’un serveur de machine learning autonome qui ne prend pas en charge les instances et qui s’exécute en dehors de SQL Server. Elle est appelée **machine learning Server (autonome)** et comprend R et Python. 
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
SQL Server installation comprend une option de **fonctionnalité partagée** pour l’installation d’un serveur de machine learning autonome qui ne prend pas en charge les instances et qui s’exécute en dehors de SQL Server. Dans SQL Server 2016, cette fonctionnalité est appelée **R Server (autonome)** .  
::: moniker-end

Un serveur autonome installé par SQL Server installation est fonctionnellement équivalent aux versions non-SQL de [Microsoft machine learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), prenant en charge les mêmes cas d’usage et scénarios, notamment:

+ Exécution à distance, basculement entre les sessions locales et distantes dans la même console
+ Fonctionnement avec les nœuds Web et les nœuds de calcul
+ Déploiement du service Web: possibilité d’empaqueter le script R et Python dans des services Web
+ Collection complète de bibliothèques de fonctions R et Python

En tant que serveur indépendant découplé de SQL Server, l’environnement R et Python est configuré, sécurisé et accessible à l’aide du système d’exploitation sous-jacent et des outils fournis sur le serveur autonome, et non SQL Server.

Comme complément à SQL Server, un serveur autonome est utile si vous avez besoin de développer des solutions de Machine Learning à hautes performances qui peuvent utiliser des contextes de calcul à distance pour toute la gamme de plateformes de données prises en charge. Vous pouvez déplacer l’exécution du serveur local vers une Machine Learning Server distante sur un cluster Spark ou sur une autre instance SQL Server.

<a name="bkmk_prereqs"> </a>

## <a name="pre-install-checklist"></a>Liste de vérification préalable à l’installation

Si vous avez installé une version antérieure, par exemple SQL Server 2016 R Server (autonome) ou Microsoft R Server, désinstallez l’installation existante avant de continuer.

En règle générale, nous vous recommandons de traiter les installations autonomes prenant en charge les instances de moteur de base de données et de serveur comme s’excluant mutuellement pour éviter les conflits de ressources. Toutefois, si vous disposez de ressources suffisantes, il n’y a aucune interdiction pour les installer à la fois sur le même ordinateur physique.

Vous ne pouvez avoir qu’un seul serveur autonome sur l’ordinateur: SQL Server Machine Learning Server (autonome) ou SQL Server R Server (autonome). Veillez à désinstaller une version avant d’en ajouter une nouvelle.

::: moniker range="=sql-server-2016"
<a name="bkmk_ga_instalpatch"></a> 

 ###  <a name="install-patch-requirement"></a>Installer les correctifs requis 

Pour SQL Server 2016 uniquement: Microsoft a identifié un problème avec la version spécifique des fichiers binaires Microsoft VC++ 2013 Runtime qui sont installés en tant que composants requis par SQL Server. Si cette mise à jour des fichiers binaires du runtime VC n’est pas installée, SQL Server risque de rencontrer des problèmes de stabilité dans certains scénarios. Avant d’installer SQL Server, suivez les instructions données dans [Notes de publication de SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) pour voir si votre ordinateur nécessite un correctif pour les fichiers binaires du runtime VC.  
::: moniker-end

## <a name="get-the-installation-media"></a>Obtenir le média d’installation

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="run-setup"></a>Exécuter le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrez l’Assistant Installation de.

2. Cliquez sur l’onglet **installation** , puis sélectionnez **nouvelle installation machine learning Server (autonome)** .
    
     ![Installer machine learning Server autonome](media/2017setup-installation-page-mlsvr.png "Démarrer l’installation de machine learning Server autonome")

3. Une fois la vérification des règles terminée, acceptez SQL Server termes du contrat de licence et sélectionnez une nouvelle installation.

4. Dans la page **sélection de fonctionnalités** , les options suivantes doivent déjà être sélectionnées:

    - Microsoft Machine Learning Server (autonome)

    - R et Python sont tous les deux sélectionnés par défaut. Vous pouvez désélectionner l’une ou l’autre langue, mais nous vous recommandons d’installer au moins l’une des langues prises en charge.

     ![Choisir les fonctionnalités R ou python](media/2017setup-features-page-mlsvr-rpy.png "Démarrer l’installation de machine learning Server autonome")
    
    Toutes les autres options peuvent être ignorées. 
    
    > [!NOTE]
    > Évitez d’installer les **fonctionnalités partagées** si l’ordinateur a déjà machine learning services installé pour SQL Server analytique dans la base de données. Cela crée des bibliothèques dupliquées.
    > 
    > En outre, les scripts R ou python s’exécutant dans SQL Server sont gérés par SQL Server afin de ne pas entrer en conflit avec la mémoire utilisée par d’autres services du moteur de base de données, le serveur Machine Learning autonome n’a pas de telles contraintes et peut interférer avec d’autres opérations de base de données. . Enfin, l’accès à distance via une session RDP, qui est souvent utilisée pour la désexploitation, est généralement bloqué par les administrateurs de base de données.
    > 
    > Pour ces raisons, nous vous recommandons généralement d’installer Machine Learning Server (autonome) sur un ordinateur distinct à partir de SQL Server Machine Learning Services.

5.  Acceptez les termes du contrat de licence pour télécharger et installer les distributions de la langue de base. Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**. 

     ![Contrat de licence python](media/2017setup-python-license.png "Contrat de licence python")

6.  Sur la page **Prêt pour l’installation** , vérifiez vos sélections, et cliquez sur **Installer**.

Une fois l’installation terminée, consultez [rapports personnalisés pour SQL Server R services](../r/monitor-r-services-using-custom-reports-in-management-studio.md) pour obtenir de l’aide sur les erreurs ou les avertissements, consultez [FAQ sur la mise à niveau et l’installation-machine learning services](../r/upgrade-and-installation-faq-sql-server-r-services.md).
::: moniker-end

::: moniker range="=sql-server-2016"
## <a name="run-setup"></a>Exécuter le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrez l’Assistant Installation de.

2. Dans l’onglet **installation** , cliquez sur **nouvelle installation R Server (autonome)** .
    
     ![Démarrer l’installation de R Server autonome](media/2016-setup-installation-rsvr.png "Démarrer l’installation de R Server autonome")

3. Une fois la vérification des règles terminée, acceptez SQL Server termes du contrat de licence et sélectionnez une nouvelle installation.

4.  Dans la page **Sélection de fonctionnalités** , l’option suivante doit déjà être sélectionnée :
    
    **R Server (autonome)**  
    
    ![Sélection de fonctionnalités pour R Server autonome](media/2016setup-rserver-features.png "Sélection de fonctionnalités pour R Server autonome")
    
    Toutes les autres options peuvent être ignorées. 
    
    > [!NOTE]
    > Évitez d’installer les **fonctionnalités partagées** si vous exécutez le programme d’installation sur un ordinateur où R services a déjà été installé pour SQL Server analytique dans la base de données. Cela crée des bibliothèques dupliquées.
    > 
    > Tandis que les scripts R s’exécutant dans SQL Server sont gérés par SQL Server afin de ne pas entrer en conflit avec la mémoire utilisée par d’autres services du moteur de base de données, le R Server autonome n’a pas de telles contraintes et peut interférer avec d’autres opérations de base de données.
    > 
    > Nous vous recommandons généralement d’installer R Server (autonome) sur un ordinateur distinct de SQL Server R Services (dans la base de données).

5.  Acceptez les termes du contrat de licence pour télécharger et installer les distributions de la langue de base. Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**. 

6.  Sur la page **Prêt pour l’installation** , vérifiez vos sélections, et cliquez sur **Installer**.

Une fois l’installation terminée, consultez [rapports personnalisés pour SQL Server R services](../r/monitor-r-services-using-custom-reports-in-management-studio.md) pour obtenir de l’aide sur les erreurs ou les avertissements, consultez [FAQ sur la mise à niveau et l’installation-machine learning services](../r/upgrade-and-installation-faq-sql-server-r-services.md).
::: moniker-end

## <a name="set-environment-variables"></a>Définition des variables d'environnement

Pour l’intégration de fonctionnalités R uniquement, vous devez définir la variable d’environnement **MKL_CBWR** pour [garantir la cohérence](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) de la sortie des calculs d’Intel Math Kernel Library (MKL).

1. Dans le panneau de configuration, cliquez sur système **et sécurité** >  > **paramètres** > système avancés**variables d’environnement**.

2. Créez un utilisateur ou une variable système. 

  + Définir le nom de la variable sur`MKL_CBWR`
  + Affectez à la variable la valeur`AUTO`

3. Redémarrez le serveur.

<a name="install-path"></a>

### <a name="default-installation-folders"></a>Dossiers d’installation par défaut

Pour le développement R et Python, il est courant d’avoir plusieurs versions sur le même ordinateur. Comme installé par SQL Server installation, la distribution de base est installée dans un dossier associé à la version SQL Server que vous avez utilisée pour le programme d’installation.

Le tableau suivant répertorie les chemins d’accès pour les distributions R et Python créées par les programmes d’installation Microsoft. À des fins d’exhaustivité, la table comprend les chemins d’accès générés par le programme d’installation de SQL Server ainsi que le programme d’installation autonome pour les Microsoft Machine Learning Server.

|Version| Méthode d’installation | Dossier par défaut|
|----|----|----|
|SQL Server 2017 Machine Learning Server (autonome) |  Assistant Installation de SQL Server 2017 |`C:\Program Files\Microsoft SQL Server\140\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Microsoft Machine Learning Server (autonome) |  Programme d’installation autonome de Windows |`C:\Program Files\Microsoft\ML Server\R_SERVER`<br/>`C:\Program Files\Microsoft\ML Server\PYTHON_SERVER`|
|SQL Server Machine Learning Services (dans la base de données) |Assistant Installation de SQL Server 2017, avec l’option de langage R|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
|SQL Server 2016 R Server (autonome) |  Assistant Installation de SQL Server 2016 |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2016 R services (en base de données) |Assistant Installation de SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Appliquer les mises à jour

Nous vous recommandons d’appliquer la dernière mise à jour cumulative au moteur de base de données et aux composants de Machine Learning. Les mises à jour cumulatives sont installées par le biais du programme d’installation de. 

Sur les appareils connectés à Internet, vous pouvez télécharger un fichier exécutable à extraction automatique. L’application d’une mise à jour pour le moteur de base de données extrait automatiquement les mises à jour cumulatives pour les fonctionnalités R et Python existantes. 

Sur les serveurs déconnectés, des étapes supplémentaires sont requises. Vous devez obtenir la mise à jour cumulative pour le moteur de base de données ainsi que les fichiers CAB pour les fonctionnalités de Machine Learning. Tous les fichiers doivent être transférés vers le serveur isolé et appliqués manuellement.

1. Démarrez avec une instance de ligne de base. Vous ne pouvez appliquer des mises à jour cumulatives qu’à des installations existantes:

  + Machine Learning Server (autonome) à partir de SQL Server version initiale de 2017
  + R Server (autonome) à partir de SQL Server version initiale 2016, SQL Server 2016 SP 1 ou SQL Server 2016 SP 2

2. Fermez toutes les sessions R ou python ouvertes et arrêtez les processus en cours d’exécution sur le système.

3. Si vous avez activé l’exécution en tant que nœuds Web et nœuds de calcul pour les déploiements de service Web, sauvegardez le fichier **appSettings. JSON** à titre de précaution. En appliquant SQL Server 2017 CU13 ou une version ultérieure, vous pouvez utiliser une copie de sauvegarde pour conserver la version d’origine.

4. Sur un appareil connecté à Internet, cliquez sur le lien de la mise à jour cumulative pour votre version de SQL Server.

  + [Mises à jour de SQL Server 2017](https://sqlserverupdates.com/sql-server-2017-updates/)
  + [Mises à jour de SQL Server 2016](https://sqlserverupdates.com/sql-server-2016-updates/)

5. Téléchargez la dernière mise à jour cumulative. Il s’agit d’un fichier exécutable.

6. Sur un appareil connecté à Internet, double-cliquez sur le fichier. exe pour exécuter le programme d’installation et suivez les étapes de l’Assistant pour accepter les termes du contrat de licence, passer en revue les fonctionnalités affectées et surveiller la progression jusqu’à la fin de l’opération.

7. Sur un serveur sans connexion Internet:

   + Obtenir les fichiers CAB correspondants pour R et Python. Pour obtenir des liens de téléchargement, consultez la page [téléchargements cab pour les mises à jour cumulatives sur SQL Server instances analytiques dans la base de données](sql-ml-cab-downloads.md).

   + Transférez tous les fichiers, le fichier exécutable principal et les fichiers CAB, dans un dossier sur l’ordinateur hors connexion.

   + Double-cliquez sur le fichier. exe pour exécuter le programme d’installation. Lors de l’installation d’une mise à jour cumulée sur un serveur sans connexion Internet, vous êtes invité à sélectionner l’emplacement des fichiers. cab pour R et Python.

8. Après l’installation, sur un serveur pour lequel vous avez activé la mise en œuvre avec les nœuds de calcul et les nœuds Web, modifiez **appSettings. JSON**en ajoutant une entrée «MMLResourcePath», directement sous «MMLNativePath»:

    ```json
    "ScorerParameters": {
        "MMLNativePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\",
        "MMLResourcePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\"
    }
    ```

9. [Exécutez l’utilitaire CLI de l’administrateur](https://docs.microsoft.com/machine-learning-server/operationalize/configure-admin-cli-launch) pour redémarrer le Web et les nœuds de calcul. Pour connaître les étapes et la syntaxe, consultez [surveiller, démarrer et arrêter des nœuds de calcul et Web](https://docs.microsoft.com/machine-learning-server/operationalize/configure-admin-cli-stop-start).

## <a name="development-tools"></a>Outils de développement

Un environnement de développement intégré n’est pas installé dans le cadre de l’installation de. Pour plus d’informations sur la configuration d’un environnement de développement, consultez [configurer les outils R](../r/set-up-a-data-science-client.md) et [configurer les outils python](../python/setup-python-client-tools-sql.md).

## <a name="next-steps"></a>Étapes suivantes

Les développeurs r peuvent commencer par des exemples simples et découvrir les principes de base du fonctionnement de R avec SQL Server. Pour l’étape suivante, consultez les liens suivants:

+ [Tutoriel : Exécuter R dans T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutoriel : Analyse en base de données pour les développeurs R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Les développeurs python peuvent apprendre à utiliser Python avec SQL Server en suivant les didacticiels suivants:

+ [Tutoriel : Exécuter python dans T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Tutoriel : Analytique en base de données pour les développeurs python](../tutorials/sqldev-in-database-python-for-sql-developers.md)
::: moniker-end

Pour consulter des exemples de Machine Learning basés sur des scénarios réels, consultez didacticiels [machine learning](../tutorials/machine-learning-services-tutorials.md).
