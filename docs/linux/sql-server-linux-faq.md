---
title: SQL Server sur Linux FAQ | Microsoft Docs
description: Cet article fournit des réponses aux questions fréquemment posées sur SQL Server s'exécutant sur Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/25/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: c45203e8524fe2df9301250afd1bef40df37bc3d
ms.sourcegitcommit: 13d98701ecd681f0bce9ca5c6456e593dfd1c471
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49419354"
---
# <a name="sql-server-on-linux-frequently-asked-questions-faq"></a>SQL Server sur Linux Forum aux Questions (FAQ)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Les sections suivantes fournissent des questions et réponses pour SQL Server s’exécutant sur Linux.

## <a name="general-questions"></a>Questions générales

1. **Quelles plateformes Linux sont prises en charge ?**

   SQL Server est actuellement pris en charge sur Red Hat Enterprise Server, SUSE Linux Enterprise Server et Ubuntu. Il est également possible de l'exécuter dans un conteneur avec Docker. Pour obtenir les dernières informations sur les versions prises en charge, consultez [plateformes prises en charge](sql-server-linux-setup.md#supportedplatforms).

1. **SQL Server sur Linux ne fonctionnera sur d’autres plateformes**?

   SQL Server est testé et pris en charge sur Linux pour les distributions répertoriées précédemment. D'autres distributions de Linux sont étroitement liées et peuvent être en mesure d’exécuter SQL Server (par exemple, CentOS est étroitement liée à Red Hat Enterprise Server). Mais si vous choisissez d’installer SQL Server sur un système d’exploitation non pris en charge, passez en revue la **politique de Support** section de la [politique de support technique pour Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server) pour comprendre les implications de cette prise en charge. Notez également que certaines-distributions Linux gérées par la communauté, n’ont pas de moyen formel pour recevoir un support si le système d’exploitation sous-jacent est l'origine du problème.

1. **Comment fonctionnent les licences sur Linux ?**

   SQL Server est concédé sous licence de la même façon pour Windows et Linux. En fait, vous devez obtenir la licence pour SQL Server, ensuite vous pouvez choisir d’utiliser cette licence sur la plateforme de votre choix. Pour plus d’informations, consultez [comment obtenir la licence SQL Server](https://www.microsoft.com/sql-server/sql-server-2017-pricing).

1. **SQL Server sur Linux est-il le même que sur Windows ?**

   Le coeur du moteur de base de données pour SQL Server est le même sur Linux que sur Windows. Toutefois, certaines fonctionnalités ne sont actuellement pas pris en charge sur Linux. Pour obtenir la liste des fonctionnalités qui ne sont pas pris en charge sur Linux, consultez le [fonctionnalités et services non pris en charge](sql-server-linux-release-notes.md#Unsupported). Examinez également les [problèmes connus](sql-server-linux-release-notes.md#known-issues). Sauf indication contraire dans ces listes, les autres fonctionnalités et services de SQL Server sont pris en charge sur Linux.

1. **Quelle est la stratégie de support pour SQL Server ?**

   Pour comprendre la politique de support, consultez la [politique d’assistance pour SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

1. **Je viens du monde SQL Server sous Windows. Existe-t-il des ressources pour aider à apprendre à utiliser SQL Server sur Linux ?**

   Les [Démarrages rapides](sql-server-linux-setup.md#platforms) fournissent des instructions détaillées sur la façon d’installer SQL Server sur Linux et d'exécuter des requêtes Transact-SQL. D'autres didacticiels fournissent des instructions supplémentaires sur l’utilisation de SQL Server sur Linux. Pour une liste de fournisseurs externes de conseils, consultez la [liste MSSQLTIPS de SQL Server sur Linux conseils](https://www.mssqltips.com/sql-server-tip-category/226/sql-server-on-linux/).

## <a name="installation"></a>Installation

1. **Comment obtenir SQL Server installé sur mes serveurs Linux ?**

   Microsoft tient à jour des référentiels de packages pour l’installation de SQL Server et prend en charge l’installation par le biais de gestionnaires de packages natifs tels qu’yum, zypper et apt. Pour installer rapidement, consultez une procédure de [Démarrages rapides](sql-server-linux-setup.md#platforms).

1. **Puis-je installer SQL Server sur le sous-système Linux pour Windows 10 ?**

   Non. Linux s’exécutant sur Windows 10 n’est actuellement pas une plateforme prise en charge pour SQL Server et les outils associés.

1. **Les systèmes de fichiers Linux SQL Server peut utiliser pour les fichiers de données ?**

   SQL Server sur Linux prend en charge ext4 et XFS. Prise en charge d’autres systèmes de fichiers est ajouté en fonction des besoins à l’avenir.

1. **Puis-je télécharger les packages d’installation pour installer SQL Server en mode hors connexion ?**

   Oui. Pour plus d’informations, consultez les liens de téléchargement de packages dans les [notes de version](sql-server-linux-release-notes.md). En outre, passez en revue le lien [obtenir des instructions pour les installations hors connexion](sql-server-linux-setup.md#offline).

1. **Puis-je effectuer une installation sans assistance de SQL Server sur Linux ?**

   Oui. Pour une présentation de l’installation sans assistance, consultez les [consignes d’Installation pour SQL Server sur Linux](sql-server-linux-setup.md#unattended). Consultez les exemples de scripts pour [Red Hat](sample-unattended-install-redhat.md), [SUSE Linux Enterprise Server](sample-unattended-install-suse.md), et [Ubuntu](sample-unattended-install-ubuntu.md). Vous pouvez également consulter [cet exemple de script](https://blogs.msdn.microsoft.com/sqlcat/2017/10/03/unattended-install-and-configuration-for-sql-server-2017-on-linux/) créé par l’équipe des conseillers de clientèle SQL Server.

1. **Quelle édition de SQL Server dois-je utiliser selon ce que j'ai déjà acheté ?**

   Lorsque vous exécutez le programme d’installation de mssql-conf vous les possibilités suivantes :  
   `Choose an edition of SQL Server:` <br>
`     1. Evaluation (free, no production use rights, 180-day limit)` <br>
`     2. Developer (free, no production use rights)` <br>
`     3. Express (free)` <br>
`     4. Web (PAID)` <br>
`     5. Standard (PAID)` <br>
`     6. Enterprise (PAID)` <br>
`     7. Enterprise Core (PAID)` <br>
`     8. I bought a license through a retail sales channel and have a product key to enter.`
     
   Si vous avez obtenu votre licence via la licence en volume dans le cadre d’un accord entreprise ou via votre abonnement MSDN, vous devez sélectionner parmi les choix 4 à 7. Si vous avez acheté une édition Standard via un canal de vente au détail, vous devez sélectionner le choix 8. 


## <a name="tools"></a>Outils

1. **Puis-je utiliser le client de SQL Server Management Studio sur Windows pour accéder à SQL Server sur Linux ?**

   Oui, vous pouvez utiliser tous vos outils existants qui s’exécutent sur Windows pour accéder à SQL Server sur Linux. Ceux-ci incluent les outils de Microsoft tels que SQL Server Management Studio (SSMS), SQL Server Data Tools (SSDT) ainsi que les systèmes d’exploitation et outils tiers.

1. **Existe-t-il un outil tel que SSMS qui s’exécute sur Linux ?**

   Le nouveau Studio de données Azure (version préliminaire) est un outil multiplateforme pour la gestion de SQL Server. Pour plus d’informations, consultez [What ' s Studio de données Azure (aperçu)](../azure-data-studio/what-is.md).

1. **Les commandes telles que sqlcmd et bcp sont-elles disponibles sur Linux ?**

   Oui, [sqlcmd et bcp](sql-server-linux-setup-tools.md) sont disponibles en mode natif sur Linux, macOS et Windows. En outre, vous pouvez utiliser le nouvel [mssql-scripter](https://github.com/Microsoft/mssql-scripter) outil de ligne de commande sur Linux, macOS ou Windows pour générer des scripts T-SQL pour votre base de données SQL en cours d’exécution en tout lieu. En outre, consultez la version d’évaluation de mise à jour pour [mssql-cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/).

1. **Il est possible d’afficher le moniteur d’activité lorsque l'on est connecté via SSMS sur Windows pour une instance s’exécute sur Linux ?**

   Oui, vous pouvez utiliser SSMS sur Windows pour se connecter à distance et utiliser les outils / fonctionnalités tels que les commandes de moniteur d’activité sur une instance de Linux.

1. **Quels outils sont disponibles pour surveiller les performances de SQL Server sur Linux ?**

   Vous pouvez utiliser les [vues de gestion dynamique (DMV) systèmes](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) pour collecter les différents types d’informations sur SQL Server, y compris les informations de processus Linux. Vous pouvez utiliser une[requête Store](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md) pour améliorer les performances de requête. D'autres outils, tels que le compte [tableau de bord performances](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-performance-dashboard-built-in/), fonctionne à distance dans SQL Server Management Studio (SSMS) à partir de Windows.

   > [!TIP]
   > Un moyen d'améliorer les performances consiste à configurer correctement votre système d’exploitation Linux et l’instance SQL Server. Pour plus d’informations, consultez les [performances, meilleures pratiques et des instructions de configuration de SQL Server sur Linux](sql-server-linux-performance-best-practices.md).

## <a name="administration"></a>Administration

1. **Microsoft a t-il créé une application telle le Gestionnaire de Configuration SQL Server sur Linux ?**

   Oui, il existe un outil de configuration pour SQL Server sur Linux : [mssql-conf](sql-server-linux-configure-mssql-conf.md).

1. **SQL Server sur Linux prend-il en charge plusieurs instances sur le même hôte ?**

   Nous vous recommandons d’exécuter plusieurs conteneurs sur un ordinateur hôte afin d’avoir plusieurs instances distinctes. Cela est facile à l’aide de docker, mais chaque conteneur doit écouter sur un port différent. Pour plus d’informations, consultez le lien [exécuter plusieurs conteneurs de SQL Server](sql-server-linux-configure-docker.md#run-multiple-sql-server-containers).

1. **L'authentification Active Directory est-elle prise en charge sur Linux ?**

   Oui. Pour plus d’informations, consultez [l’authentification Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md).

1. **Always On et gestion de clusters sont-ils pris en charge dans Linux ?**

   Le clustering de basculement et la haute disponibilité sur Linux sont réalisés avec Pacemaker sur Linux. Pour plus d’informations, consultez [Business continuité des activités et la base de données de récupération - SQL Server sur Linux](sql-server-linux-business-continuity-dr.md).

1. **Est-il possible de configurer la réplication à partir de Linux vers Windows et vice versa ?**

   Les réplicas en lecture à l’échelle peuvent servir pour la réplication de données unidirectionnelle entre Windows et Linux.

1. **Est-il possible de migrer des bases de données existantes dans les versions antérieures de SQL Server à partir de Windows vers Linux ?**

   Oui, il existe [plusieurs méthodes](sql-server-linux-migrate-overview.md) pour réaliser cela.

1. **Puis-je migrer mes données depuis Oracle et d’autres moteurs de base de données vers SQL Server sur Linux ?**

   Oui. SSMA prend en charge la migration à partir de plusieurs types de moteurs de base de données : Microsoft Access, DB2, MySQL, Oracle et SAP ASE (anciennement SAP Sybase ASE). Pour obtenir un exemple montrant comment utiliser SSMA, consultez [migrer un schéma d’Oracle vers SQL Server sur Linux avec l’Assistant Migration SQL Server](../ssma/oracle/sql-server-linux-convert-from-oracle.md?toc=%2fsql%2flinux%2ftoc.json).

1. **Quelles sont les autorisations requises pour les fichiers SQL Server ?**

   Tous les fichiers dans le dossier `/var/opt/mssql` doivent être possédés par l'utilisateur **mssql** et appartenir au groupe **mssql**. Les deux, **mssql** utilisateur et groupe, doivent disposer des autorisations en lecture-écriture sur tous les fichiers et répertoires. Notez les scénarios spéciaux suivants, impliquant des autorisations de fichier et répertoire :

   * Les autorisations de propriétaire de mssql et de groupe sont requises pour les partages réseau montés qui sont utilisés pour stocker les fichiers de SQL Server.
   * Si vous trouvez des sauvegardes ou des fichiers de base de données dans un répertoire non définis par défaut, vous devez également définir des autorisations pour ce répertoire.
   * Si vous modifiez l’umask de la racine par défaut qui a la valeur 0022, la configuration de SQL Server échoue après l’installation. Vous devez ensuite appliquer manuellement les autorisations requises au compte de démarrage de SQL Server.

1. **Puis-je modifier la propriété de répertoires et fichiers de SQL Server pour le compte et le groupe mssql installés ?**

   Nous ne gérons pas la modification de la propriété du répertoire de SQL Server et les fichiers à partir de l’installation par défaut. Le compte et le groupe mssql sont utilisés spécifiquement pour SQL Server et n’ont pas accès à une connexion interactive.

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]
