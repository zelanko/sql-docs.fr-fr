---
title: "FAQ d’installation et de mise à niveau pour l’apprentissage de SQL Server | Documents Microsoft"
ms.date: 10/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 001e66b9-6c3f-41b3-81b7-46541e15f9ea
caps.latest.revision: "59"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 3c4fb79f04daeff6d98856b521fa1602a2334cdd
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="upgrade-and-installation-faq-for-sql-server-machine-learning"></a>FAQ d’installation et de mise à niveau pour l’apprentissage de SQL Server

Cette rubrique fournit des réponses aux questions courantes sur l’installation de l’apprentissage des fonctionnalités de SQL Server. Elle traite également des questions courantes sur les mises à niveau.

+ Certains problèmes se produisent uniquement avec les mises à niveau à partir de versions préliminaires. Par conséquent, nous vous recommandons d’identifier votre version et l’édition tout d’abord avant de lire ces notes.
+ Mettre à niveau vers la version de service dès que possible, ou d’une version la plus récente pour résoudre les problèmes qui ont été résolus dans les versions récentes.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage Services (de-de base de données)

## <a name="performing-setup-for-the-first-time"></a>Exécuter le programme d’installation pour la première fois

Suivez les procédures de configuration [!INCLUDE[sscurrent_md](../../includes/sscurrent_md.md)] et des composants R, comme décrit ici : 

+ [Configurer SQL Server R Services ou Machine Learning Services de bases de données](../r/set-up-sql-server-r-services-in-database.md)
+ [Configurer 2017 du serveur SQL avec Python](../python/setup-python-machine-learning-services.md)
+ [Créer un serveur R autonome](../r/create-a-standalone-r-server.md)

> [!IMPORTANT]
> 
> Après avoir installé SQL Server et apprentissage des fonctionnalités, avant de pouvoir utiliser des scripts R ou Python, vous devez effectuer certaines étapes de configuration supplémentaires. C’est parce que la fonctionnalité d’exécution de script externe n’est pas activée par défaut.

### <a name="requirements-and-restrictions"></a>Exigences et restrictions

La version de SQL Server que vous installez, certaines des limitations suivantes peuvent s’appliquer :

- Dans les versions antérieures de SQL Server 2016 R Services, modèle 8.3 notation était nécessaire sur le lecteur qui contient le répertoire de travail. Si vous avez installé une version préliminaire, la mise à niveau vers SQL Server 2016 Service Pack 1 doit résoudre ce problème. Cette exigence ne s’applique pas aux versions après le SP1.

- Actuellement, vous ne pouvez pas installer [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sur un cluster de basculement. 

- Sur une machine virtuelle Azure, une configuration supplémentaire peut être nécessaire. Par exemple, vous devrez peut-être créer une exception de pare-feu pour prendre en charge l’accès à distance.

- Installation côte à côte avec une autre version de R, ou avec d’autres versions de Revolution Analytique, n’est pas pris en charge.

- Les nouvelles installations de versions préliminaires de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] ne sont plus prises en charge. Si vous utilisez une version préliminaire, mettez à niveau dès que possible.

- Désactiver l’analyse antivirus, avant de commencer l’installation. Une fois le programme d’installation est terminée, nous vous recommandons d’interruption analyse antivirus sur les dossiers utilisés par [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]. De préférence, suspendre l’analyse sur l’ensemble du [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)] arborescence.

### <a name="licensing-agreements-for-unattended-installs"></a>Contrats de licence pour les installations sans assistance

Si vous utilisez la ligne de commande pour mettre à niveau une instance de SQL Server, assurez-vous que la ligne de commande comprend à la fois le [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)] paramètre de contrat et les nouveaux paramètres de contrat de licence de licence pour R et Python.

### <a name="offline-installation-of-machine-learning-components-for-a-localized-version-of-sql-server"></a>Installation hors connexion des composants d’apprentissage machine pour une version localisée de SQL Server

Lorsque vous installez [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)] composants learning d’ordinateurs sur un ordinateur qui n’a pas accès à internet, vous devez prendre quelques étapes supplémentaires :

+ Télécharger les programmes d’installation de composants de R ou Python vers un dossier local avant d’exécuter le programme d’installation de SQL Server.
+ Dans certains cas, vous devrez peut-être modifier le fichier de programme d’installation pour vous assurer que la bonne langue est installée.
+ L’identificateur de langue utilisé pour les composants d’apprentissage automatique doit être identique à la langue d’installation de SQL Server, ou vous ne pouvez pas terminer l’installation.

Pour plus d’informations, consultez [l’installation des composants d’apprentissage machine sans accès à internet](../r/installing-ml-components-without-internet-access.md).

## <a name="post-installation-configuration"></a>Configuration de post-installation

Pour utiliser l’apprentissage automatique avec R ou Python, une configuration supplémentaire est requise après avoir exécuté le programme d’installation de SQL Server. Les étapes précises requises varient selon le niveau de sécurité du serveur et la manière dont vous avez configuré votre instance de SQL Server et les bases de données.

Passez en revue toutes les options dans la liste d’instructions de post-installation pour voir les étapes supplémentaires peuvent être requises dans votre environnement.

+ [Configurer l’ordinateur SQL Server dans la base de données d’apprentissage](set-up-sql-server-r-services-in-database.md) 

## <a name="upgrades-or-uninstallation"></a>Mises à niveau ou la désinstallation

Cette section contient des instructions détaillées pour les scénarios de mise à niveau spécifiques.

### <a name="how-to-upgrade-sql-server"></a>La mise à niveau de SQL Server

Vous pouvez mettre à niveau votre version de SQL Server en réexécutant l’Assistant installation.

+ [Mise à niveau vers SQL Server](../../database-engine/install-windows/upgrade-sql-server.md)
+ [Mise à niveau SQL Server à l’aide de l’Assistant Installation](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)

Vous pouvez mettre à niveau uniquement d’apprentissage des composants à l’aide d’un processus appelé liaison : 
+ [Utilisez SqlBindR pour mettre à niveau les composants de la machine learning](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

### <a name="end-of-support-for-in-place-upgrades-from-prerelease-versions"></a>Fin de la prise en charge des mises à niveau sur place à partir de versions préliminaires

Mises à niveau à partir de versions préliminaires de SQL Server 2016 ne sont plus prises en charge. Cela inclut SQL Server 2016 CTP3, CTP3.1, CTP3.2, RC0 ou RC1.

Les versions suivantes ont été installées avec les versions préliminaires de SQL Server 2016.

| Version | Build         |
|---------|---------------|
| CTP 3.0 | 13.0.xxx      |
| CTP 3.1 | 13.0.801.12   |
| CTP 3.2 | 13.0.900.73   |
| CTP 3.3 | 13.0.1000.281 |
| RC1     | 13.0.1200.242 |
| RC2     | 13.0.1300.275 |
| RC3     | 13.0.1400.361 |

Si vous avez un doute sur la version que vous utilisez, exécutez `@@VERSION` dans une requête à partir de SQL Server Management Studio.

En règle générale, le processus de mise à niveau est la suivante :

1. Sauvegardez les scripts et données.
2. Désinstallez la version préliminaire.
3. Installez une version release.

Désinstallation d’une version préliminaire de SQL Server learning les composants d’ordinateur peuvent être complexes et peut nécessiter l’exécution d’un script spécial. Contactez le support technique pour obtenir de l'aide.

### <a name="support-for-slipstream-upgrades"></a>Prise en charge des mises à niveau de l’installation intégrée

Une installation intégrée renvoie à la possibilité d’appliquer un correctif ou une mise à jour à une installation d’instance défaillante dans le but de corriger les problèmes existants. L’avantage de cette méthode est que SQL Server est mis à jour en même temps à exécuter le programme d’installation, pour éviter un redémarrage distinct ultérieurement.

Si le serveur n’a pas accès à internet, veillez à télécharger le programme d’installation de SQL Server. Vous devez aussi télécharger les versions correspondantes des programmes d’installation des composants R séparément *avant* de lancer le processus de mise à jour. 

Pour les emplacements de téléchargement, consultez [l’installation des composants d’apprentissage machine sans accès à internet](installing-ml-components-without-internet-access.md).

Une fois que tous les fichiers d’installation sont copiés dans un répertoire local, démarrez l’utilitaire d’installation en tapant SETUP. EXE à partir de la ligne de commande.

- Utilisez le */UpdateSource* argument pour spécifier l’emplacement d’un fichier local qui contient la mise à jour de SQL Server, tel qu’une mise à jour cumulative ou la version service pack.

- Utilisez le */MRCACHEDIRECTORY* argument pour spécifier le dossier qui contient les fichiers CAB des composants R.

Pour plus d’informations, consultez le blog par l’équipe de support : [déploiement R Services sur des ordinateurs sans accès à internet](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/).

### <a name="get-machine-learning-components-for-offline-installs"></a>Obtenir des composants de machine learning pour les installations en mode hors connexion

Si vous installez ou mettez à niveau les serveurs qui ne sont pas connectés à internet, vous devez télécharger une version mise à jour de la machine learning composants manuellement avant de commencer l’actualisation. 

+ [Installation des composants d’apprentissage machine sans accès à internet](../../advanced-analytics/r/installing-ml-components-without-internet-access.md).

### <a name="support-policy-and-schedule-for-update-of-machine-learning-components"></a>Prise en charge de stratégie et la planification de mise à jour des composants de machine learning

Comme les correctifs logiciels ou des améliorations apportées à SQL Server sont libérées, machine learning composants sont automatiquement mis à niveau ou actualisées, si votre instance comprend déjà la fonctionnalité.

À compter de 2016 de décembre, vous pouvez mettre à niveau les composants learning d’ordinateur à un rythme plus rapide que le cycle de publication SQL Server. Pour ce faire, *liaison* une instance de SQL Server à la stratégie de cycle de vie des logiciels modernes. Chaque fois qu’une nouvelle version des outils d’apprentissage est publiée par l’équipe de développement d’apprentissage, vous pouvez télécharger la dernière version et l’appliquer à une instance de SQL Server qui est utilisée pour l’apprentissage.

Pour plus d'informations, consultez :

+ [Chronologie de prise en charge de Microsoft R Server et serveur de Machine Learning](https://docs.microsoft.com/machine-learning-server/resources-servicing-support)
+ [Permet de mettre à niveau une instance de SQL Server SqlBindR](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="r-server-standalone"></a>R Server (autonome)

Cette section décrit les problèmes propres aux installations de Microsoft R Server (autonome) qui utilisent le programme d’installation de SQL Server 2016. 

Pour les problèmes liés aux mises à niveau à partir de R Server pour serveur de Machine Learning, consultez [installer Machine Learning pour Windows Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).

### <a name="problems-when-r-services-and-r-server-standalone-are-installed-on-the-same-computer"></a>Problèmes lors de la R Services et autonome du serveur R sont installés sur le même ordinateur

Dans les versions antérieures de SQL Server 2016, l’installation de R Server (autonome) et R Services (de-de base de données) en même temps parfois a provoqué le programme d’installation échoue avec un message « accès refusé ». Ce problème a été résolu dans le Service Pack 1 pour SQL Server 2016.

Si vous a rencontré cette erreur et que vous devez mettre à niveau ces fonctionnalités, effectuez une installation intégrée de SQL Server 2016 avec SP1. Il existe deux façons de résoudre le problème, qui nécessitent le désinstaller et réinstaller.

1. Désinstaller les Services de R (de-de base de données) et assurez-vous que les comptes d’utilisateurs SQLRUserGroup sont supprimés.

2. Redémarrez le serveur, puis réinstallez R Server (autonome).

3. Exécuter SQL Server le programme d’installation une fois plus d’informations, et cette fois, sélectionnez **ajouter des fonctionnalités à SQL Server existant**.

4. Choisissez l’instance, puis sélectionnez le **R Services (de-de base de données)** option à ajouter.

Si cette procédure ne parvient pas à résoudre le problème, essayez de la solution de contournement suivante :

1. Désinstallez R Services (de-de base de données) et R Server (autonome) en même temps.

2. Supprimer les comptes d’utilisateur local (SQLRUserGroup).

3. Redémarrez le serveur.

4. Exécutez le programme d’installation de SQL Server et ajouter la fonctionnalité de R Services (de-de base de données) uniquement. Ne sélectionnez pas **R Server (autonome)**.

En règle générale, nous vous recommandons de ne pas installer R Services (de-de base de données) et R Server (autonome) sur le même ordinateur. Toutefois, en supposant que le serveur possède une capacité suffisante, vous pouvez trouver que r serveur autonome peut être utile en tant qu’un outil de développement. Un autre scénario possible est que vous devez utiliser les fonctionnalités à l’Opérationnalisation de R Server, mais que vous souhaitez également accéder aux données de SQL Server sans le déplacement des données.

## <a name="see-also"></a>Voir aussi

 [Prise en main de SQL Server R Services](../r/getting-started-with-sql-server-r-services.md)

 [Prise en main de Microsoft R Server autonome](../r/getting-started-with-microsoft-r-server-standalone.md)
