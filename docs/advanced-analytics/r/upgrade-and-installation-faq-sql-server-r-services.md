---
title: "FAQ d’installation et de mise à niveau (SQL Server R Services) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 001e66b9-6c3f-41b3-81b7-46541e15f9ea
caps.latest.revision: 59
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: 395554af6b9d014d560d8b6520d032966630c5b2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/08/2017

---
# <a name="upgrade-and-installation-faq-sql-server-r-services"></a>FAQ d’installation et de mise à niveau (SQL Server R Services)

Cette rubrique fournit des réponses aux questions courantes sur l’installation de l’apprentissage des fonctionnalités de SQL Server. Elle traite également des questions courantes sur les mises à niveau. Certains problèmes se produisent uniquement avec les mises à niveau à partir de versions préliminaires. Par conséquent, nous vous recommandons d’identifier votre version et l’édition de la première et mise à niveau vers la version la plus récente ou une version de service dès que possible.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage Services (de-de base de données)

## <a name="performing-setup-for-the-first-time"></a>Exécuter le programme d’installation pour la première fois

Suivez les procédures de configuration de [ ! INCLUDEssCurrent] et les composants R, comme décrit ici : 

+ [Configurer SQL Server R Services ou Machine Learning Services de bases de données](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)
+ [Configurer 2017 du serveur SQL avec Python](../python/setup-python-machine-learning-services.md)
+ [Créer un serveur R autonome](create-a-standalone-r-server.md)

Après avoir installé SQL Server, pour utiliser des scripts R ou Python externes, vous devez effectuer des configurations supplémentaires. C’est parce que la fonctionnalité d’exécution de script externe n’est pas activée par défaut.

> [!NOTE]
> N’utilisez pas les instructions de configuration qui ont été publiées avant la publication de SQL Server 2016. Le processus d’installation complètement changé entre les premières versions et la version officielle. 

### <a name="requirements-and-restrictions"></a>Exigences et restrictions

La génération de R Services, vous installez, certaines des limitations suivantes peuvent s’appliquer :

- Dans les versions antérieures de SQL Server 2016 R Services, modèle 8.3 notation était nécessaire sur le lecteur qui contient le répertoire de travail. Si vous avez installé une version préliminaire, la mise à niveau vers SQL Server 2016 Service Pack 1 doit supprimer cette exigence.

- Vous ne pouvez pas installer [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sur un cluster de basculement. 

- Sur une machine virtuelle Azure, une configuration supplémentaire peut être nécessaire. Par exemple, vous devrez peut-être créer une exception de pare-feu pour prendre en charge l’accès à distance.

- Installation côte à côte avec une autre version de R, ou avec d’autres versions de Revolution Analytique, n’est pas pris en charge.

- Les nouvelles installations de versions préliminaires de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] ne sont plus prises en charge. Si vous utilisez une version préliminaire, mettez à niveau dès que possible.

- Désactiver l’analyse antivirus, avant de commencer l’installation. Une fois le programme d’installation est terminée, nous vous recommandons d’interruption analyse antivirus sur les dossiers utilisés par SQL Server (de préférence, l’arborescence entière).

### <a name="licensing-agreements-for-unattended-installs"></a>Contrats de licence pour les installations sans assistance

Si vous utilisez la ligne de commande pour mettre à niveau une instance de SQL Server, assurez-vous que la ligne de commande inclut le nouveau paramètre de contrat de licence, */IACCEPTROPENLICENSEAGREEMENT*. Le programme d’installation peut échouer si vous n’utilisez pas ce paramètre.

### <a name="offline-installation-of-r-components-for-a-localized-version-of-sql-server"></a>Installation hors connexion des composants R pour une version localisée de SQL Server

Lorsque vous installez R Services sur un ordinateur qui n’a pas accès à internet, vous devez prendre deux étapes supplémentaires. Téléchargez le programme d’installation du composant de R dans un dossier local avant d’exécuter le programme d’installation de SQL Server et modifiez le fichier de programme d’installation pour vous assurer que la bonne langue est installée.

L’identificateur de langue utilisée pour les composants R doit être identique à la langue d’installation de SQL Server, ou le **suivant** bouton est désactivé et vous ne pouvez pas terminer l’installation.

Pour plus d’informations, consultez [l’installation des composants R sans accès à internet](../../advanced-analytics/r-services/installing-ml-components-without-internet-access.md).

## <a name="post-installation-configuration"></a>Configuration de post-installation

Pour utiliser l’apprentissage automatique avec R ou Python, une configuration supplémentaire est requise après avoir exécuté le programme d’installation de SQL Server. Étapes supplémentaires peuvent être requises selon le niveau de sécurité du serveur et de votre instance de SQL Server et les bases de données. Passez en revue ces étapes à partir de la documentation de configuration pour déterminer si aucune configuration supplémentaire peut être nécessaire.

[Définir la configuration SQL Server R Services dans-base de données](set-up-sql-server-r-services-in-database.md)

- La fonctionnalité qui prend en charge l’exécution de scripts externes, tels que R ou Python, est désactivée par défaut pour la sécurité de la base de données et doit être activée.

- Assurez-vous que les comptes de travail qui sont utilisés par le Launchpad pour exécuter R ou Python ont accès à l’instance.

- Vous devrez peut-être activer l’accès à distance sur le serveur, ou créer une règle de pare-feu autorisant les communications entrantes avec SQL Server.

- En fonction de la charge de travail planifié, vous devrez peut-être optimiser le serveur pour les tâches d’apprentissage. 

## <a name="upgrades-or-uninstallation"></a>Mises à niveau ou la désinstallation

Cette section contient des instructions détaillées pour les scénarios de mise à niveau spécifiques.

Mises à niveau à partir d’une version préliminaire de SQL Server 2016 R Services ne sont plus prises en charge. Nous vous recommandons de désinstaller la version préliminaire puis installez une version release dès que possible.

### <a name="support-for-slipstream-upgrades"></a>Prise en charge des mises à niveau de l’installation intégrée

Une installation intégrée renvoie à la possibilité d’appliquer un correctif ou une mise à jour à une installation d’instance défaillante dans le but de corriger les problèmes existants. L’avantage de cette méthode est que SQL Server est mis à jour en même temps à exécuter le programme d’installation, pour éviter un redémarrage distinct ultérieurement.

Si le serveur n’a pas accès à internet, veillez à télécharger le programme d’installation de SQL Server. Vous devez aussi télécharger les versions correspondantes des programmes d’installation des composants R séparément *avant* de lancer le processus de mise à jour. 

Pour les emplacements de téléchargement, consultez [des composants de l’installation de R sans accès à internet](installing-ml-components-without-internet-access.md).

Une fois que tous les fichiers d’installation sont copiés dans un répertoire local, démarrez l’utilitaire d’installation en tapant SETUP. EXE à partir de la ligne de commande.

- Utilisez le */UpdateSource* argument pour spécifier l’emplacement d’un fichier local qui contient la mise à jour de SQL Server, tel qu’une mise à jour cumulative ou la version service pack.

- Utilisez le */MRCACHEDIRECTORY* argument pour spécifier le dossier qui contient les fichiers CAB des composants R.

Pour plus d’informations, consultez le blog par l’équipe de support : [déploiement R Services sur des ordinateurs sans accès à internet](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/).

### <a name="upgrade-r-components-offline"></a>Mettre à niveau les composants de R en mode hors connexion

Si vous installez ou mettez à niveau les serveurs qui ne sont pas connectés à internet, vous devez télécharger une version mise à jour des composants R manuellement avant de commencer l’actualisation. Pour plus d’informations, consultez [des composants de l’installation de R sans accès à internet](../../advanced-analytics/r-services/installing-ml-components-without-internet-access.md).

### <a name="schedule-for-update-of-r-components"></a>Planification de la mise à jour des composants R

Comme les correctifs logiciels ou des améliorations apportées à SQL Server 2016 sont libérées, les composants R sont également mis à niveau ou actualisées, si votre instance comprend déjà la fonctionnalité Services de R.

Si vous utilisez SQL Server 2017, mises à niveau vers les composants R sont installés automatiquement.

À compter de décembre 2016, vous pouvez mettre à niveau les composants de R à un rythme plus rapide que le cycle de publication SQL Server. Pour ce faire *liaison* une instance de R Services à la stratégie de cycle de vie des logiciels modernes. Actuellement prise en charge est fournie uniquement pour la mise à niveau des instances de 2016. Quand une nouvelle version de R Server est publiée, vous ne pourrez pas mettre à niveau vers des instances 2017 ainsi.

Pour plus d’informations, consultez [SqlBindR utilisé pour mettre à niveau une instance de SQL Server R Services](../../advanced-analytics/r-services/use-sqlbindr-exe-to-upgrade-an-instance-of-r-services.md).

### <a name="upgrade-from-a-pre-release-version-of-sql-server-2016"></a>Mise à niveau à partir d’une version préliminaire de SQL Server 2016

En général, les mises à niveau sur place ne sont pas pris en charge pour les versions préliminaires.

Pour installer les Services de R avec succès, vous devez désinstaller toute version antérieure de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] et ses composants R associés. Cela inclut SQL Server 2016 CTP3, CTP3.1, CTP3.2, RC0 ou RC1.

Désinstallation d’une version préliminaire permettre être complexes et nécessitent l’exécution d’un script spécial. Contactez le support technique pour obtenir de l'aide.

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

Si vous avez un doute sur la version que vous utilisez, exécutez `@@VERSION` à partir de SQL Server Management Studio.

### <a name="problems-with-setup-of-r-server-standalone"></a>Problèmes avec le programme d’installation de R Server (autonome)

Cette section décrit les problèmes propres aux installations de Microsoft R Server (autonome) qui utilisent le programme d’installation de SQL Server 2016. Pour les problèmes liés aux mises à niveau du serveur R plus générales, consultez [Microsoft R Server](https://msdn.microsoft.com/microsoft-r/) sur MSDN.

#### <a name="failure-to-install-localized-versions"></a>Si l’installation des versions localisées

Lorsque vous installez R Server en mode hors connexion, les versions préliminaires ne vous permettent pas d’utiliser des langues localisées.

En règle générale, lorsque le serveur n’a pas accès à internet, avant d’exécuter le programme d’installation vous devez télécharger tous les packages d’installation pour R Server. Puis, vous spécifiez l’emplacement des fichiers pendant l’installation.

Toutefois, si l’identificateur de langue associé au package de programme d’installation n’est pas identique à la langue d’installation de SQL Server, un problème se produit. Lorsque vous atteignez la page pour l’installation des composants R, le **suivant** bouton est désactivé et vous ne pouvez pas poursuivre l’installation. Pour résoudre ce problème, vous pouvez renommer le package pour utiliser un identificateur correspondant.

Par exemple, le nom des packages d’installation peut être `SRO_3.2.2.0_1031.cab`.
Pour installer la langue 104 sur SQL Server, renommez le fichier `SRO_3.2.2.0_1041.cab`.

#### <a name="installing-r-services-and-r-server-standalone-on-the-same-computer"></a>Installation de R Services et R Server autonome sur le même ordinateur

En règle générale, vous n’installez pas R Services (de-de base de données) et R Server (autonome) sur le même ordinateur. Toutefois, si le serveur possède une capacité suffisante, R serveur autonome peut être utile en tant qu’un outil de développement. Vous devrez peut-être également utiliser les fonctionnalités à l’Opérationnalisation du serveur de R et l’accès aux données SQL Server à partir de R Server sans le déplacement des données.

Notez que si vous installez le serveur R et R Services sur le même ordinateur, deux ensembles distincts des mêmes bibliothèques R sont installés. Un pour une utilisation par l’instance de SQL Server, et l’autre pour le développement, utilisez ou par R Server.

Dans les versions antérieures de SQL Server 2016, l’installation de R Server (autonome) et R Services (de-de base de données) en même temps peut entraîner le programme d’installation échoue avec un message « accès refusé ». Ce problème a été résolu dans le Service Pack 1 pour SQL Server 2016.

Si vous a rencontré cette erreur et que vous devez mettre à niveau ces fonctionnalités, effectuez une installation intégrée de SQL Server 2016 avec SP1. Il existe deux façons de résoudre le problème, qui nécessitent le désinstaller et réinstaller.

1. Désinstaller les Services de R (de-de base de données) et assurez-vous que les comptes d’utilisateurs SQLRUserGroup sont supprimés.

2. Redémarrez le serveur, puis réinstallez R Server (autonome).

3. Exécuter SQL Server le programme d’installation une fois plus d’informations, et cette fois, sélectionnez **ajouter des fonctionnalités à SQL Server existant**.

4. Choisissez l’instance, puis sélectionnez le **R Services (de-de base de données)** option à ajouter.

Dans certains cas, cette procédure ne parvient pas à résoudre le problème. Essayez la solution de contournement suivante :

1. Désinstallez R Services (de-de base de données) et R Server (autonome) en même temps.

2. Supprimer les comptes d’utilisateur local (SQLRUserGroup).

3. Redémarrez le serveur.

4. Exécutez le programme d’installation de SQL Server et ajouter la fonctionnalité de R Services (de-de base de données) uniquement. Ne sélectionnez pas **R Server (autonome)**.

## <a name="see-also"></a>Voir aussi

 [Prise en main de SQL Server R Services](../r/getting-started-with-sql-server-r-services.md)

 [Prise en main de Microsoft R Server autonome](../r/getting-started-with-microsoft-r-server-standalone.md)

