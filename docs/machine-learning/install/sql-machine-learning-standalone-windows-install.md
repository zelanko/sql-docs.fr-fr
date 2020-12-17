---
title: Installer Machine Learning Server (autonome)
description: Configurez un serveur machine learning autonome pour Python et R. Un serveur autonome installé par le biais du programme d’installation de SQL Server est fonctionnellement équivalent aux versions non-SQL de Microsoft Machine Learning Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 01/03/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016'
ms.openlocfilehash: d446416076160642f86c035082481d318479d594
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97471180"
---
# <a name="install-machine-learning-server-standalone-or-r-server-standalone-using-sql-server-setup"></a>Installer Machine Learning Server (autonome) ou R Server (autonome) en utilisant le programme d’installation de SQL Server
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

::: moniker range=">=sql-server-2017"
Le programme d’installation de SQL Server comprend une option de **fonctionnalité partagée** permettant d’installer un serveur machine learning autonome qui s’exécute en dehors de SQL Server. Ce serveur appelé **Machine Learning Server (autonome)** inclut Python et R. 
::: moniker-end
::: moniker range="=sql-server-2016"
Le programme d’installation de SQL Server comprend une option de **fonctionnalité partagée** permettant d’installer un serveur machine learning autonome qui s’exécute en dehors de SQL Server. Dans SQL Server 2016, cette fonctionnalité est appelée **R Server (autonome)** .  
::: moniker-end

Un serveur autonome installé par le biais du programme d’installation de SQL Server est fonctionnellement équivalent aux versions non-SQL de [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server) et prend en charge les mêmes cas d’utilisation et scénarios, notamment :

+ Exécution à distance avec basculement entre les sessions locales et distantes dans la même console
+ Opérationnalisation avec des nœuds web et des nœuds de calcul
+ Déploiement de service web : possibilité d’empaqueter des scripts R et Python dans des services web
+ Collection complète de bibliothèques de fonctions R et Python

En tant que serveur indépendant découplé de SQL Server, l’environnement R et Python est configuré, sécurisé et accessible à l’aide du système d’exploitation sous-jacent et des outils fournis par le serveur autonome et non SQL Server.

En tant que complément de SQL Server, un serveur autonome se révèle utile si vous avez besoin de développer des solutions de machine learning hautes performances pouvant utiliser des contextes de calcul à distance sur toute la gamme de plateformes de données prises en charge. Vous pouvez transférer l’exécution du serveur local vers une instance Machine Learning Server distante sur un cluster Spark ou sur une autre instance SQL Server.

<a name="bkmk_prereqs"> </a>

## <a name="pre-install-checklist"></a>Liste de contrôle avant l’installation

Si vous avez installé une version antérieure, par exemple SQL Server 2016 R Server (autonome) ou Microsoft R Server, désinstallez-la avant de continuer.

D’une manière générale, nous vous recommandons de traiter le serveur autonome et les installations dépendantes des instances du moteur de base de données comme s’excluant mutuellement pour éviter les conflits de ressources. Toutefois, si vous disposez de ressources suffisantes, il n’est pas proscrit d’installer les deux sur le même ordinateur physique.

Vous ne pouvez avoir qu’un serveur autonome sur l’ordinateur : SQL Server Machine Learning Server (autonome) ou SQL Server R Server (autonome). Veillez à désinstaller la version existante avant d’en ajouter une nouvelle.

::: moniker range="=sql-server-2016"
<a name="bkmk_ga_instalpatch"></a> 

 ###  <a name="install-patch-requirement"></a>Installer le correctif obligatoire 

Pour SQL Server 2016 uniquement : Microsoft a identifié un problème avec la version spécifique des fichiers binaires Microsoft VC++ 2013 Runtime qui sont installés en tant que composants requis par SQL Server. Si cette mise à jour des fichiers binaires du runtime VC n’est pas installée, SQL Server risque de rencontrer des problèmes de stabilité dans certains scénarios. Avant d’installer SQL Server, suivez les instructions données dans [Notes de publication de SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) pour voir si votre ordinateur nécessite un correctif pour les fichiers binaires du runtime VC.  
::: moniker-end

## <a name="get-the-installation-media"></a>Obtenir le média d’installation

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

::: moniker range=">=sql-server-2017"
## <a name="run-setup"></a>Exécuter le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrez l’Assistant Installation.

2. Cliquez sur l’onglet **Installation**, puis sélectionnez **Nouvelle installation de Machine Learning Server (autonome)** .
    
   ::: moniker-end
   ::: moniker range="=sql-server-2017"
   ![Installer Machine Learning Server (autonome)](media/2017setup-installation-page-mlsvr.png "Commencer l’installation de Machine Learning Server (autonome)")
   ::: moniker-end
   ::: moniker range="=sql-server-ver15"
   ![Installer Machine Learning Server (autonome)](media/2019setup-installation-page-mlsvr.png "Commencer l’installation de Machine Learning Server (autonome)")
   ::: moniker-end
   ::: moniker range=">=sql-server-2017"

3. Une fois la vérification des règles terminée, acceptez les termes du contrat de licence SQL Server et sélectionnez une nouvelle installation.

4. Dans la page **Sélection de fonctionnalités**, les options suivantes doivent déjà être sélectionnées :

    - **Machine Learning Server (autonome)**

    - Les langages **R** et **Python** sont tous les deux sélectionnés par défaut. Vous pouvez les désélectionner, mais nous vous recommandons d’installer au moins l’un des langages pris en charge.

   ::: moniker-end
   ::: moniker range="=sql-server-2017"
   ![Choisir les fonctionnalités R ou Python](media/2017setup-features-page-mlsvr-rpy.png "Commencer l’installation de Machine Learning Server (autonome)")
   ::: moniker-end
   ::: moniker range="=sql-server-ver15"
   ![Choisir les fonctionnalités R ou Python](media/2019setup-features-page-mlsvr-rpy.png "Commencer l’installation de Machine Learning Server (autonome)")
   ::: moniker-end
   ::: moniker range=">=sql-server-2017"
    
   Toutes les autres options peuvent être ignorées. 
    
   > [!NOTE]
   > Évitez d’installer les **fonctionnalités partagées** si Machine Learning Services est déjà installé sur l’ordinateur pour l’analytique en base de données SQL Server. Ceci créerait des bibliothèques dupliquées.
   > 
   > De plus, si les scripts R ou Python s’exécutant dans SQL Server sont gérés par SQL Server pour éviter tout conflit de mémoire avec les autres services du moteur de base de données, le serveur machine learning autonome n’est pas soumis à ces contraintes et peut interférer avec d’autres opérations de base de données. Enfin, l’accès à distance par session RDP, souvent utilisé pour l’opérationnalisation, est généralement bloqué par les administrateurs de base de données.
   > 
   > C’est pourquoi nous recommandons généralement d’installer Machine Learning Server (autonome) sur un ordinateur distinct de SQL Server Machine Learning Services.

5. Acceptez les termes du contrat de licence pour télécharger et installer les distributions de langage de base. Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**. 

6. Sur la page **Prêt pour l’installation** , vérifiez vos sélections, et cliquez sur **Installer**.
::: moniker-end

::: moniker range="=sql-server-2016"
## <a name="run-setup"></a>Exécuter le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrez l’Assistant Installation.

2. Dans l’onglet **Installation**, cliquez sur **Nouvelle installation de R Server (autonome)** .
    
   ![Commencer l’installation de R Server (autonome)](media/2016-setup-installation-rsvr.png "Commencer l’installation de R Server (autonome)")

3. Une fois la vérification des règles terminée, acceptez les termes du contrat de licence SQL Server et sélectionnez une nouvelle installation.

4. Dans la page **Sélection de fonctionnalités** , l’option suivante doit déjà être sélectionnée :
    
   - **R Server (autonome)**  
    
   ![Sélection des fonctionnalités pour R Server (autonome)](media/2016setup-rserver-features.png "Sélection des fonctionnalités pour R Server (autonome)")
    
   Toutes les autres options peuvent être ignorées. 
    
   > [!NOTE]
   > Évitez d’installer les **fonctionnalités partagées** si vous exécutez l’installation sur un ordinateur sur lequel R Services est déjà installé pour l’analytique en base de données SQL Server. Ceci créerait des bibliothèques dupliquées.
   > 
   > Si les scripts R s’exécutant dans SQL Server sont gérés par SQL Server pour éviter tout conflit de mémoire avec les autres services du moteur de base de données, le serveur R autonome n’est pas soumis à ces contraintes et peut interférer avec d’autres opérations de base de données.
   > 
   > Nous recommandons généralement d’installer R Server (autonome) sur un ordinateur distinct de SQL Server R Services (en base de données).

5. Acceptez les termes du contrat de licence pour télécharger et installer les distributions de langage de base. Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**. 

6. Sur la page **Prêt pour l’installation** , vérifiez vos sélections, et cliquez sur **Installer**.
::: moniker-end

## <a name="set-environment-variables"></a>Définir des variables d’environnement

Pour l’intégration de fonctionnalités R uniquement, vous devez définir la variable d’environnement **MKL_CBWR** pour [garantir la cohérence de la sortie](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) des calculs d’Intel Math Kernel Library (MKL).

1. Dans le Panneau de configuration, cliquez sur **Système et sécurité** > **Système** > **Paramètres système avancés** > **Variables d’environnement**.

2. Créez une variable Utilisateur ou Système. 

  + Nommez la variable `MKL_CBWR`.
  + Définissez la valeur de la variable sur `AUTO`.

3. Redémarrez le serveur.

<a name="install-path"></a>

### <a name="default-installation-folders"></a>Dossiers d’installation par défaut

Pour le développement R et Python, il est courant de disposer de plusieurs versions sur le même ordinateur. Avec le programme d’installation de SQL Server, la distribution de base est installée dans un dossier associé à la version de SQL Server que vous avez utilisée pour l’installation.

Le tableau suivant liste les chemins pour les distributions R et Python, créés par les programmes d’installation Microsoft. À des fins d’exhaustivité, ce tableau comprend les chemins générés par le programme d’installation de SQL Server et le programme d’installation de Microsoft Machine Learning Server en mode autonome.

|Version| Méthode d’installation | Dossier par défaut|
|----|----|----|
|SQL Server 2019 Machine Learning Server (autonome) |  Assistant Installation de SQL Server 2019 |`C:\Program Files\Microsoft SQL Server\150\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\150\PYTHON_SERVER`|
|SQL Server 2017 Machine Learning Server (autonome) |  Assistant Installation de SQL Server 2017 |`C:\Program Files\Microsoft SQL Server\140\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Microsoft Machine Learning Server (autonome) |  Programme d’installation de Windows en mode autonome |`C:\Program Files\Microsoft\ML Server\R_SERVER`<br/>`C:\Program Files\Microsoft\ML Server\PYTHON_SERVER`|
|SQL Server Machine Learning Services (en base de données) |Assistant Installation de SQL Server 2019 avec option de langage R|`C:\Program Files\Microsoft SQL Server\MSSQL15.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL15.<instance_name>\PYTHON_SERVICES` |
|SQL Server Machine Learning Services (en base de données) |Assistant Installation de SQL Server 2017 avec option de langage R|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
|SQL Server 2016 R Server (autonome) |  Assistant Installation de SQL Server 2016 |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2016 R Services (en base de données) |Assistant Installation de SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Appliquer des mises à jour

Nous vous recommandons d’appliquer la mise à jour cumulative la plus récente au moteur de base de données et aux composants de machine learning. Les mises à jour cumulatives sont installées par le biais du programme d’installation. 

Sur les appareils connectés à Internet, vous pouvez télécharger un fichier exécutable à extraction automatique. L’application d’une mise à jour au moteur de base de données extrait automatiquement les mises à jour cumulatives pour les fonctionnalités R et Python existantes. 

Sur les serveurs non connectés, des étapes supplémentaires sont nécessaires. Vous devez obtenir la mise à jour cumulative pour le moteur de base de données ainsi que les fichiers CAB pour les fonctionnalités de machine learning. Tous les fichiers doivent être transférés vers le serveur isolé et appliqués manuellement.

1. Commencez avec une instance de base. Vous pouvez appliquer des mises à jour cumulatives aux installations existantes uniquement :

  + Machine Learning Server (autonome) à partir de la version initiale de SQL Server 2019
  + Machine Learning Server (autonome) à partir de la version initiale de SQL Server 2017
  + R Server (autonome) à partir de la version initiale de SQL Server 2016, SQL Server 2016 SP 1 ou SQL Server 2016 SP 2

2. Fermez toutes les sessions R ou Python ouvertes et arrêtez tous les processus en cours d’exécution sur le système.

3. Si vous avez activé l’exécution de l’opérationnalisation avec des nœuds web et des nœuds de calcul pour les déploiements de service web, sauvegardez le fichier **AppSettings.json** à titre de précaution. L’application de SQL Server 2017 CU13 (ou d’une version ultérieure) met à jour ce fichier. Une copie de sauvegarde vous permettra donc de conserver la version d’origine.

4. Sur une machine connectée à Internet, téléchargez la dernière mise à jour cumulative de votre version à partir de la page [Dernières mises à jour pour Microsoft SQL Server](../../database-engine/install-windows/latest-updates-for-microsoft-sql-server.md).

5. Téléchargez la mise à jour cumulative la plus récente. Il s’agit d’un fichier exécutable.

6. Sur un appareil connecté à Internet, double-cliquez sur le fichier .exe pour exécuter le programme d’installation, puis suivez les étapes de l’Assistant pour accepter les termes du contrat de licence, passer en revue les fonctionnalités affectées et suivre la progression jusqu’à la fin de l’opération.

7. Sur un serveur sans connectivité Internet :

   + Récupérez les fichiers CAB correspondants pour R et Python. Pour obtenir les liens de téléchargement, consultez [Téléchargement des fichiers CAB pour les mises à jour cumulatives sur les instances d’analytique en base de données SQL Server](sql-ml-cab-downloads.md).

   + Transférez tous les fichiers, le fichier exécutable principal et les fichiers CAB, vers un dossier de l’ordinateur hors connexion.

   + Double-cliquez sur le fichier .exe pour exécuter le programme d’installation. Lors de l’installation d’une mise à jour cumulative sur un serveur sans connexion Internet, vous êtes invité à sélectionner l’emplacement des fichiers .cab pour R et Python.

8. Après l’installation, sur un serveur pour lequel vous avez activé le déploiement avec des nœuds web et des nœuds de calcul, modifiez le fichier **AppSettings.json** en ajoutant une entrée « MMLResourcePath » directement sous « MMLNativePath ». Par exemple :

    ```json
    "ScorerParameters": {
        "MMLNativePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\",
        "MMLResourcePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\"
    }
    ```

9. [Exécutez l’utilitaire CLI d’administration](/machine-learning-server/operationalize/configure-admin-cli-launch) pour redémarrer les nœuds web et les nœuds de calcul. Pour connaître les étapes et la syntaxe, consultez [Superviser, démarrer et arrêter des nœuds web et des nœuds de calcul](/machine-learning-server/operationalize/configure-admin-cli-stop-start).

## <a name="development-tools"></a>Outils de développement

Aucun IDE n’est installé dans le cadre de la configuration. Pour plus d’informations sur la configuration d’un environnement de développement, consultez [Configurer des outils R](../r/set-up-a-data-science-client.md) et [Configurer des outils Python](../python/setup-python-client-tools-sql.md).

## <a name="next-steps"></a>Étapes suivantes

Les développeurs peuvent démarrer avec quelques exemples simples et découvrir les principes de base du fonctionnement de R avec SQL Server. Pour l’étape suivante, consultez les liens suivants :

+ [Démarrage rapide : Exécuter R dans T-SQL](../tutorials/quickstart-r-create-script.md)
+ [Tutoriel : Analytique dans la base de données pour les développeurs R](../tutorials/r-taxi-classification-introduction.md)

::: moniker range=">=sql-server-2017"
Les développeurs Python peuvent apprendre à utiliser Python avec SQL Server en effectuant les didacticiels suivants :

+ [Tutoriel Python : Prédire la location de ski avec régression linéaire dans SQL Server Machine Learning Services](../tutorials/python-ski-rental-linear-regression-deploy-model.md)
+ [Tutoriel Python : Catégoriser des clients à l’aide de k-moyennes avec SQL Server Machine Learning Services](../tutorials/python-clustering-model.md)
::: moniker-end