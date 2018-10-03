---
title: SQL Server sur Linux FAQ | Microsoft Docs
description: Cet article fournit des réponses aux questions fréquemment posées sur SQL Server en cours d’exécution sur Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/24/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 6725f986a66020d0560c4e3f17be5da12a2cd3f1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745747"
---
# <a name="sql-server-on-linux-frequently-asked-questions-faq"></a>SQL Server sur Linux Forum aux Questions (FAQ)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Les sections suivantes fournissent des questions et réponses pour SQL Server s’exécutant sur Linux.

## <a name="general-questions"></a>Questions générales

1. **Quelles plateformes Linux sont prises en charge ?**

   SQL Server est actuellement pris en charge sur Red Hat Enterprise Server, SUSE Linux Enterprise Server et Ubuntu. Il est également possible d’en cours d’exécution dans un conteneur avec Docker. Pour obtenir les dernières informations sur les versions prises en charge, consultez [plateformes prises en charge](sql-server-linux-setup.md#supportedplatforms).

1. **SQL Server sur Linux ne fonctionnera sur d’autres plateformes**?

   SQL Server est testé et pris en charge sur Linux pour les distributions répertoriées précédemment. Autres distributions de Linux sont étroitement liées et peut être en mesure d’exécuter SQL Server (par exemple, CentOS est étroitement liée à Red Hat Enterprise Server). Mais si vous choisissez d’installer SQL Server sur un système d’exploitation non pris en charge, passez en revue la **politique de Support** section de la [politique de support technique pour Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server) pour comprendre la prise en charge implications. Notez également que certains-gérées par la communautéent distributions Linux n’ont pas de moyen formel pour recevoir un support si le système d’exploitation sous-jacent est le problème.

1. **Comment fonctionnent les licences sur Linux ?**

   SQL Server est concédé sous licence de la même façon pour Windows et Linux. En fait, la licence de SQL Server et puis vous pouvez choisir d’utiliser cette licence sur la plateforme de votre choix. Pour plus d’informations, consultez [comment la licence SQL Server](https://www.microsoft.com/sql-server/sql-server-2017-pricing).

1. **Est SQL Server sur Linux dans le même que sur Windows ?**

   Le moteur de base de données pour SQL Server core est le même sur Linux, car il est sur Windows. Toutefois, certaines fonctionnalités sont actuellement pas pris en charge sur Linux. Pour obtenir la liste des fonctionnalités qui ne sont pas pris en charge sur Linux, consultez le [non pris en charge des fonctionnalités et services](sql-server-linux-release-notes.md#Unsupported). Examinez également le [problèmes connus](sql-server-linux-release-notes.md#known-issues). Sauf indication contraire dans ces listes, autres fonctionnalités SQL Server et les services sont pris en charge sur Linux.

1. **Qu’est la stratégie de prise en charge pour SQL Server ?**

   Pour comprendre la politique de support, consultez le [politique d’assistance pour SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

1. **Je suis provenant d’un arrière-plan de Windows SQL Server. Existe-t-il des ressources pour aider à apprendre à utiliser SQL Server sur Linux ?**

   Le [Démarrages rapides](sql-server-linux-setup.md#platforms) fournissent des instructions détaillées sur la façon d’installer SQL Server sur Linux et exécuter des requêtes Transact-SQL. Autres didacticiels fournissent des instructions supplémentaires sur l’utilisation de SQL Server sur Linux. Pour une liste de fournisseurs tiers de conseils, consultez le [liste MSSQLTIPS de SQL Server sur Linux conseils](https://www.mssqltips.com/sql-server-tip-category/226/sql-server-on-linux/).

## <a name="installation"></a>Installation

1. **Comment obtenir SQL Server installée sur mes serveurs Linux ?**

   Microsoft tient à jour des référentiels de packages pour l’installation de SQL Server et prend en charge l’installation par le biais de gestionnaires de packages natifs tels qu’yum, zypper et apt. Pour installer rapidement, consultez une de la [Démarrages rapides](sql-server-linux-setup.md#platforms).

1. **Puis-je installer SQL Server sur le sous-système de Linux pour Windows 10 ?**

   Non. Linux s’exécutant sur Windows 10 n’est actuellement pas une plateforme prise en charge pour SQL Server et les outils associés.

1. **Les systèmes de fichiers Linux SQL Server peut utiliser pour les fichiers de données ?**

   SQL Server sur Linux prend en charge ext4 et XFS. Prise en charge d’autres systèmes de fichiers est ajouté en fonction des besoins à l’avenir.

1. **Puis-je télécharger les packages d’installation pour installer SQL Server en mode hors connexion ?**

   Oui. Pour plus d’informations, consultez le package télécharger les liens dans le [notes de version](sql-server-linux-release-notes.md). En outre, passez en revue la [obtenir des instructions pour les installations hors connexion](sql-server-linux-setup.md#offline).

1. **Puis-je effectuer une installation sans assistance de SQL Server sur Linux ?**

   Oui. Pour une présentation de l’installation sans assistance, consultez [consignes d’Installation pour SQL Server sur Linux](sql-server-linux-setup.md#unattended). Consultez les exemples de scripts pour [Red Hat](sample-unattended-install-redhat.md), [SUSE Linux Enterprise Server](sample-unattended-install-suse.md), et [Ubuntu](sample-unattended-install-ubuntu.md). Vous pouvez également consulter [cet exemple de script](https://blogs.msdn.microsoft.com/sqlcat/2017/10/03/unattended-install-and-configuration-for-sql-server-2017-on-linux/) créé par l’équipe de conseil clientèle SQL Server.

## <a name="tools"></a>Outils

1. **Puis-je utiliser le client de SQL Server Management Studio sur Windows pour accéder à SQL Server sur Linux ?**

   Oui, vous pouvez utiliser tous vos outils existants qui s’exécutent sur Windows pour accéder à SQL Server sur Linux. Ceux-ci incluent les outils de Microsoft telles que SQL Server Management Studio (SSMS), SQL Server Data Tools (SSDT) et systèmes d’exploitation et des outils tiers.

1. **Existe-t-il un outil tel que SSMS qui s’exécute sur Linux ?**

   Le nouveau Studio de données Azure (version préliminaire) est un outil multiplateforme pour la gestion de SQL Server. Pour plus d’informations, consultez [What ' s Studio de données Azure (aperçu)](../azure-data-studio/what-is.md).

1. **Commandes telles que sqlcmd et bcp sont disponibles sur Linux ?**

   Oui, [sqlcmd et bcp](sql-server-linux-setup-tools.md) sont disponibles en mode natif sur Linux, macOS et Windows. En outre, utilisez la nouvelle [mssql-scripter](https://github.com/Microsoft/mssql-scripter) outil de ligne de commande sur Linux, macOS ou Windows pour générer des scripts T-SQL pour votre base de données SQL en cours d’exécution en tout lieu. En outre, consultez la version d’évaluation de mise à jour pour [mssql-cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/).

1. **Il est possible d’afficher le moniteur d’activité lorsque connecté via SSMS sur Windows pour une instance s’exécute sur Linux ?**

   Oui, vous pouvez utiliser SSMS sur Windows pour se connecter à distance et utilisez outils / fonctionnalités telles que les commandes de moniteur d’activité sur une instance de Linux.

1. **Quels outils sont disponibles pour surveiller les performances de SQL Server sur Linux ?**

   Vous pouvez utiliser [vues de gestion dynamique (DMV) système](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) pour collecter différents types d’informations sur SQL Server, y compris les informations de processus Linux. Vous pouvez utiliser [requête Store](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md) pour améliorer les performances de requête. Autres outils, tels que le compte [tableau de bord performances](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-performance-dashboard-built-in/), travaillez à distance dans SQL Server Management Studio (SSMS) à partir de Windows.

   > [!TIP]
   > Un pour améliorer les performances consiste à configurer correctement votre système d’exploitation Linux et l’insance de SQL Server. Pour plus d’informations, consultez [performances meilleures pratiques et des instructions de configuration de SQL Server sur Linux](sql-server-linux-performance-best-practices.md).

## <a name="administration"></a>Administration

1. **Microsoft a créé d’une application, comme le Gestionnaire de Configuration SQL Server sur Linux ?**

   Oui, il existe un outil de configuration pour SQL Server sur Linux : [mssql-conf](sql-server-linux-configure-mssql-conf.md).

1. **SQL Server sur Linux prend-il en charge plusieurs instances sur le même hôte ?**

   Nous vous recommandons d’exécuter plusieurs conteneurs sur un ordinateur hôte d’avoir plusieurs instances distinctes. Chaque conteneur doit écouter sur un port différent. Pour plus d’informations, consultez [exécuter plusieurs conteneurs de SQL Server](sql-server-linux-configure-docker.md#run-multiple-sql-server-containers).

1. **Authentification Active Directory est prise en charge sur Linux ?**

   Oui. Pour plus d’informations, consultez [l’authentification Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md).

1. **Always On et gestion de clusters prises en charge dans Linux ?**

   Clustering de basculement et de haute disponibilité sur Linux sont réalisés avec Pacemaker sur Linux. Pour plus d’informations, consultez [Business continuité des activités et la base de données de récupération - SQL Server sur Linux](sql-server-linux-business-continuity-dr.md).

1. **Est-il possible de configurer la réplication à partir de Linux vers Windows et vice versa ?**

   Les réplicas en lecture à l’échelle peuvent servir pour la réplication de données unidirectionnelle entre Windows et Linux.

1. **Est-il possible de migrer des bases de données existantes dans les versions antérieures de SQL Server à partir de Windows vers Linux ?**

   Oui, il existe [plusieurs méthodes](sql-server-linux-migrate-overview.md) de réaliser cela.

1. **Puis-je migrer mes données d’Oracle et d’autres moteurs de base de données vers SQL Server sur Linux ?**

   Oui. SSMA prend en charge la migration à partir de plusieurs types de moteurs de base de données : Microsoft Access, DB2, MySQL, Oracle et SAP ASE (anciennement SAP Sybase ASE). Pour obtenir un exemple montrant comment utiliser SSMA, consultez [migrer un schéma d’Oracle vers SQL Server sur Linux avec l’Assistant Migration SQL Server](../ssma/oracle/sql-server-linux-convert-from-oracle.md?toc=%2fsql%2flinux%2ftoc.json).

1. **Quelles sont les autorisations requises pour les fichiers SQL Server ?**

   Tous les fichiers dans le `/var/opt/mssql` dossier de fichiers doit être possédé par le **mssql** utilisateur et appartiennent à la **mssql** groupe. Les deux le **mssql** utilisateur et groupe doivent disposer des autorisations en lecture-écriture de tous les fichiers et répertoires. Notez les scénarios suivants spéciaux, impliquant des autorisations de fichier et répertoire :

   * Autorisations pour le propriétaire de mssql et de groupe sont requises pour les partages réseau montés qui sont utilisés pour stocker les fichiers de SQL Server.
   * Si vous trouvez des sauvegardes ou des fichiers de base de données dans un répertoire non définis par défaut, vous devez également définir des autorisations pour ce répertoire.
   * Si vous modifiez l’umask de racine par défaut à partir de 0022, configuration de SQL Server échoue après l’installation. Vous devez ensuite appliquer manuellement les autorisations requises au compte de démarrage de SQL Server.

1. **Puis-je modifier la propriété de répertoires et fichiers de SQL Server dans le compte de mssql installés et le groupe ?**

   Nous ne gérons pas la modification de la propriété du répertoire de SQL Server et les fichiers à partir de l’installation par défaut. Le compte de mssql et le groupe est utilisée spécifiquement pour SQL Server et n’a pas accès à une connexion interactive.

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]
