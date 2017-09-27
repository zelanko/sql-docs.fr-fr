---
title: Notes de publication pour 2017 du serveur SQL sur Linux | Documents Microsoft
description: "Cette rubrique contient les notes de publication et les fonctionnalités prises en charge pour SQL Server 2017 est en cours d’exécution sur Linux. Notes de publication sont incluses pour RC2 et les versions antérieures."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/07/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.translationtype: MT
ms.sourcegitcommit: dbe6f832d4af55ddd15e12fba17a4da490fe19ae
ms.openlocfilehash: 14277304baaaf6aa40fe279af407c7ce915eaa60
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Notes de publication pour 2017 du serveur SQL sur Linux

Les notes suivantes s’appliquent à SQL Server 2017 est en cours d’exécution sur Linux. Cette version prend en charge la plupart des fonctionnalités du moteur de base de données SQL Server pour Linux. La rubrique ci-dessous est divisée en sections pour chaque version, à partir de la version la plus récente, RC2. Consultez les informations contenues dans chaque section pour les plateformes prises en charge, les outils, les fonctionnalités et les problèmes connus.

Le tableau suivant répertorie les versions de SQL Server 2017 est abordées dans cette rubrique.

| Version | Version | Date de publication |
|-----|-----|-----|
| [RC2](#RC2) | 14.0.900.75 | 8-2017 |
| [RC1](#RC1) | 14.0.800.90 | 7-2017 |
| [CTP 2.1](#ctp21) | 14.0.600.250 | 5-2017 |
| [CTP 2.0](#ctp20) | 14.0.500.272 | 4-2017 |
| [CTP 1.4](#ctp14) | 14.0.405.198 | 3-2017 |
| [CTP 1.3](#ctp13) | 14.0.304.138 | 2-2017 |
| [CTP 1.2](#ctp12) | 14.0.200.24 | 1-2017 |
| [CTP 1.1](#ctp11) | 14.0.100.187 | 12-2016 |
| [CTP 1.0](#ctp10) | 14.0.1.246 | 11-2016 |

## <a id="RC2"></a>RC2 (2017 août)

La version du moteur SQL Server pour cette version est 14.0.900.75.

### <a name="supported-platforms"></a>Plateformes prises en charge

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Bureau, serveur et station de travail Red Hat Enterprise Linux 7.3 | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| Serveur Linux SUSE Enterprise SP2 v12 | EXT4 | [Guide d’installation](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Moteur docker 1.8 + sur Windows, Mac ou Linux | Néant | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!NOTE]
> Vous devez au moins 3,25 Go de mémoire pour exécuter SQL Server sur Linux.
> Moteur SQL Server a été testé jusqu'à 1,5 To de mémoire pour l’instant.

### <a name="package-details"></a>Détails du package

Détails du package et les emplacements de téléchargement pour les packages RPM et Debian sont répertoriés dans le tableau suivant. Notez que vous n’avez pas besoin de télécharger ces packages directement si vous utilisez les étapes dans les guides d’installation suivantes :

- [Installer le package SQL Server](sql-server-linux-setup.md)
- [Installer le package de la recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
- [Installer le package de l’Agent SQL Server](sql-server-linux-setup-sql-agent.md)

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Rpm de Red Hat | 14.0.900.75-1 | [Moteur le package RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.900.75-1 | [package RPM du moteur de serveur MSSQL](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) | 
| Package de Debian Ubuntu 16.04 | 14.0.900.75-1 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.900.75-1_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.900.75-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.900.75-1_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.900.75-1_amd64.deb) |

### <a name="supported-client-tools"></a>Outils clients pris en charge

| Outil | Version minimale |
|-----|-----|
| [SQL Server Management Studio (SSMS) pour Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools pour Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Code Visual Studio](https://code.visualstudio.com) avec la [mssql extension](https://aka.ms/mssql-marketplace) | dernière |

### <a name="Unsupported"></a>Services et les fonctionnalités non prises en charge

Les fonctionnalités et les services suivants ne sont pas disponibles sur Linux pour l’instant. La prise en charge de ces fonctionnalités est plus activé lors de la cadence mensuelle de mises à jour le programme d’évaluation.

| Domaine | Fonctionnalité non prise en charge ou un service |
|-----|-----|
| **Moteur de base de données** | Réplication transactionnelle |
| &nbsp; | Réplication de fusion |
| &nbsp; | Étendre la base de données |
| &nbsp; | Polybase |
| &nbsp; | Requête distribuée avec des connexions 3ème partie |
| &nbsp; | Procédures système stockées étendues (XP_CMDSHELL, etc.). |
| &nbsp; | Filetable |
| &nbsp; | Définir des assemblys CLR avec l’autorisation EXTERNAL_ACCESS ou UNSAFE |
| &nbsp; | Extension du pool de mémoires tampons |
| **Agent SQL Server** |  Sous-systèmes : CmdExec, PowerShell, lecteur de file d’attente, SSIS, SSAS, SSRS |
| &nbsp; | Alertes |
| &nbsp; | l'Agent de lecture du journal ; |
| &nbsp; | Capture de données modifiées |
| &nbsp; | Sauvegarde managée |
| **Haute disponibilité** | Mise en miroir de bases de données  |
| **Sécurité** | Gestion de clés extensible |
| **Services** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus avec cette version de SQL Server 2017 RC2 sur Linux.

#### <a name="general"></a>Général

- La longueur du nom d’hôte sur lequel SQL Server est installé a besoin pour être de 15 caractères ou moins. 

    - **Résolution**: Remplacez le nom d’hôte/etc/quelque chose de 15 caractères ou plus.

- Définition manuelle de l’heure système vers l’arrière dans le temps entraîne SQL Server arrêter la mise à jour de l’heure système interne dans SQL Server.

    - **Résolution**: redémarrez SQL Server.

- Seules les installations d’instance unique sont pris en charge.

    - **Résolution**: Si vous souhaitez disposer de plusieurs instances sur un hôte donné, envisagez d’utiliser des machines virtuelles ou des conteneurs Docker. 

- Gestionnaire de Configuration SQL Server ne peut pas se connecter à SQL Server sur Linux.

- La langue par défaut de la **sa** connexion est l’anglaise.

    - **Résolution**: modifier la langue de la **sa** connexion avec le **ALTER LOGIN** instruction.

#### <a name="databases"></a>Bases de données

- Impossible de déplacer la base de données master avec l’utilitaire mssql-conf. Autres bases de données système peuvent être déplacés avec mssql-conf.

- Lorsque vous restaurez une base de données a été sauvegardée sur SQL Server sur Windows, vous devez utiliser le **WITH MOVE** clause dans l’instruction Transact-SQL.

- Nécessiter que le service Microsoft Distributed Transaction Coordinator les transactions distribuées ne sont pas pris en charge sur SQL Server est en cours d’exécution sur Linux. SQL Server vers SQL Server, les transactions distribuées sont prises en charge.

- Certains algorithmes (suites de chiffrement) et de sécurité TLS (Transport Layer) ne fonctionnent pas correctement avec SQL Server sur Linux. Cela entraîne des échecs de connexion lorsque vous tentez de vous connecter à SQL Server, ainsi que des problèmes pour établir des connexions entre les réplicas des groupes de disponibilité de.

   - **Résolution**: modifier le **mssql.conf** un script de configuration pour SQL Server sur Linux pour désactiver les suites de chiffrement problématique, en procédant comme suit :

      1. Ajoutez le code suivant /var/opt/mssql/mssql.conf.

      ```
      [network]
      tlsciphers=ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

      1. Redémarrez SQL Server avec la commande suivante.
   
      ```
      sudo systemctl restart mssql-server
      ```

- Bases de données SQL Server 2014 sur Windows qui utilisent OLTP en mémoire ne peut pas être restaurées sur 2017 du serveur SQL sur Linux. Pour restaurer une base de données SQL Server 2014 qui utilise l’OLTP en mémoire, tout d’abord mettre à niveau les bases de données vers SQL Server 2016 ou 2017 du serveur SQL sur Windows avant de les déplacer vers SQL Server sur Linux via la sauvegarde/restauration ou de détachement et d’attachement.

#### <a name="remote-database-files"></a>Fichiers de base de données distante

- Qui héberge les fichiers de base de données sur un serveur NFS n’est pas pris en charge dans cette version. Cela inclut l’utilisation de NFS pour le disque partagé clustering de basculement, ainsi que des bases de données sur les instances non cluster. Nous travaillons sur l’activation de prise en charge du serveur NFS dans les versions à venir.

#### <a name="localization"></a>Localisation

- Si vos paramètres régionaux n’est pas anglais (fr_FR) lors de l’installation, vous devez utiliser l’encodage UTF-8 dans votre session d’interpréteur de commandes/terminal. Si vous utilisez l’encodage ASCII, vous pouvez voir une erreur semblable au suivant :

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Si vous ne pouvez pas utiliser le codage UTF-8, exécutez le programme d’installation à l’aide de la variable d’environnement MSSQL_LCID pour spécifier votre choix de la langue.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

#### <a name="full-text-search"></a>Recherche en texte intégral
- Pas de tous les filtres sont disponibles avec cette version, notamment les filtres pour les documents Office. Pour obtenir la liste de filtres pris en charge, consultez [installer de recherche de texte intégral SQL Server sur Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
Vous pouvez exécuter des packages SSIS sur Linux. Pour plus d’informations, consultez les articles suivants :
-   [Annonce de billet de blog SSIS prise en charge de Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Installer SQL Server Integration Services (SSIS) sur Linux](sql-server-linux-setup-ssis.md)
-   [Extraire, transformer et charger des données sur Linux avec SSIS](sql-server-linux-migrate-ssis.md)

Veuillez noter les problèmes connus suivants avec cette version.

- Le **mssql server est** package est pris en charge sur Ubuntu et Red Hat Enterprise Linux (RHEL) dans cette version.

- SSIS lors de l’actualisation de Linux CTP 2.1 et versions ultérieures, les packages SSIS permet les connexions ODBC sur Linux. Cette fonctionnalité a été testée avec les pilotes ODBC MySQL sur le serveur SQL Server, mais il est également prévue pour fonctionner avec n’importe quel pilote ODBC Unicode qui respecte la spécification ODBC. Au moment du design, vous pouvez fournir une source de données ou une chaîne de connexion pour se connecter aux données ODBC ; Vous pouvez également utiliser l’authentification Windows. Pour plus d’informations, consultez la [blog de l’annonce prise en charge d’ODBC sur Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- Les fonctionnalités suivantes ne sont pas pris en charge dans cette version lorsque vous exécutez des packages SSIS sur Linux :
  - Base de données du catalogue SSIS
  - Exécution du package planifiés par l’Agent SQL
  - Authentification Windows
  - Les composants tiers
  - Capture de données modifiées (CDC)
  - Avec montée en puissance SSIS
  - Azure Feature Pack pour SSIS
  - Prise en charge de Hadoop et HDFS
  - Microsoft Connector pour SAP BW

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Les limitations suivantes s’appliquent à SSMS sur Windows connectés à SQL Server sur Linux.

- Plans de maintenance ne sont pas pris en charge.

- L’entrepôt de données de gestion (MDW) et le collecteur de données dans SSMS ne sont pas pris en charge. 

- Les composants SSMS UI disposant de l’authentification Windows ou les options du journal des événements Windows ne fonctionnent pas avec Linux. Vous pouvez toujours utiliser ces fonctionnalités avec d’autres options, telles que des connexions SQL. 

- Impossible de modifier le nombre de fichiers journaux à conserver.

### <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez les didacticiels de démarrage rapide suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Graphique de barre de séparation](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="RC1"></a>RC1 (juillet 2017)
La version du moteur SQL Server pour cette version est 14.0.800.90.

### <a name="supported-platforms"></a>Plateformes prises en charge 

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Bureau, serveur et station de travail Red Hat Enterprise Linux 7.3 | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| Serveur Linux SUSE Enterprise SP2 v12 | EXT4 | [Guide d’installation](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Moteur docker 1.8 + sur Windows, Mac ou Linux | Néant | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!NOTE]
> Vous devez au moins 3,25 Go de mémoire pour exécuter SQL Server sur Linux.
> Moteur SQL Server a été testé jusqu'à 1 To de mémoire pour l’instant.

### <a name="package-details"></a>Détails du package
Détails du package et les emplacements de téléchargement pour les packages RPM et Debian sont répertoriés dans le tableau suivant. Notez que vous n’avez pas besoin de télécharger ces packages directement si vous utilisez les étapes dans les guides d’installation suivantes :

- [Installer le package SQL Server](sql-server-linux-setup.md)
- [Installer le package de la recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
- [Installer le package de l’Agent SQL Server](sql-server-linux-setup-sql-agent.md)

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Rpm de Red Hat | 14.0.800.90-2 | [Moteur le package RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.800.90-2.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.800.90-2.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.800.90-2.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.800.90-2.x86_64.rpm) | 
| Package RPM de SLES | 14.0.800.90-2 | [package RPM du moteur de serveur MSSQL](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.800.90-2.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.800.90-2.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.800.90-2.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.800.90-2.x86_64.rpm) | 
| Package de Debian Ubuntu 16.04 | 14.0.800.90-2 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.800.90-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.800.90-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.800.90-2_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.800.90-2_amd64.deb) |

### <a name="supported-client-tools"></a>Outils clients pris en charge

| Outil | Version minimale |
|-----|-----|
| [SQL Server Management Studio (SSMS) pour Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools pour Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Code Visual Studio](https://code.visualstudio.com) avec la [mssql extension](https://aka.ms/mssql-marketplace) | dernière |

### <a name="unsupported-features-and-services"></a>Services et les fonctionnalités non prises en charge
Les fonctionnalités et les services suivants ne sont pas disponibles sur Linux pour l’instant. La prise en charge de ces fonctionnalités est plus activé lors de la cadence mensuelle de mises à jour le programme d’évaluation.

| Domaine | Fonctionnalité non prise en charge ou un service |
|-----|-----|
| **Moteur de base de données** | Réplication transactionnelle |
| &nbsp; | Réplication de fusion |
| &nbsp; | Étendre la base de données |
| &nbsp; | Polybase |
| &nbsp; | Requête distribuée |
| &nbsp; | Services d’apprentissage |
| &nbsp; | Procédures système stockées étendues (XP_CMDSHELL, etc.). |
| &nbsp; | Filetable |
| &nbsp; | Définir des assemblys CLR avec l’autorisation EXTERNAL_ACCESS ou UNSAFE |
| **Agent SQL Server** |  Sous-systèmes : CmdExec, PowerShell, lecteur de file d’attente, SSIS, SSAS, SSRS |
| &nbsp; | Alertes |
| &nbsp; | l'Agent de lecture du journal ; |
| &nbsp; | Capture de données modifiées |
| &nbsp; | Sauvegarde managée |
| **Haute disponibilité** | Mise en miroir de bases de données  |
| &nbsp; | Mise à niveau propagée du groupe de disponibilité |
| **Sécurité** | Gestion de clés extensible |
| **Services** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problèmes connus
Les sections suivantes décrivent les problèmes connus avec cette version de SQL Server 2017 RC1 sur Linux.

#### <a name="general"></a>Général
- La longueur du nom d’hôte sur lequel SQL Server est installé a besoin pour être de 15 caractères ou moins. 

    - **Résolution**: Remplacez le nom d’hôte/etc/quelque chose de 15 caractères ou plus.

- Définition manuelle de l’heure système vers l’arrière dans le temps entraîne SQL Server arrêter la mise à jour de l’heure système interne dans SQL Server.

    - **Résolution**: redémarrez SQL Server.

- Seules les installations d’instance unique sont pris en charge.

    - **Résolution**: Si vous souhaitez disposer de plusieurs instances sur un hôte donné, envisagez d’utiliser des machines virtuelles ou des conteneurs Docker. 

- Gestionnaire de Configuration SQL Server ne peut pas se connecter à SQL Server sur Linux.

- La langue par défaut de la **sa** connexion est l’anglaise.

    - **Résolution**: modifier la langue de la **sa** connexion avec le **ALTER LOGIN** instruction.

#### <a name="databases"></a>Bases de données

- Impossible de déplacer les bases de données système avec l’utilitaire mssql-conf.

- Lorsque vous restaurez une base de données a été sauvegardée sur SQL Server sur Windows, vous devez utiliser le **WITH MOVE** clause dans l’instruction Transact-SQL.

- Nécessiter que le service Microsoft Distributed Transaction Coordinator les transactions distribuées ne sont pas pris en charge sur SQL Server est en cours d’exécution sur Linux. SQL Server vers SQL Server, les transactions distribuées sont prises en charge.

#### <a name="remote-database-files"></a>Fichiers de base de données distante

- Qui héberge les fichiers de base de données sur un serveur NFS n’est pas pris en charge dans cette version. Cela inclut l’utilisation de NFS pour le disque partagé clustering de basculement, ainsi que des bases de données sur les instances non cluster. Nous travaillons sur l’activation de prise en charge du serveur NFS dans les versions à venir.

#### <a name="cross-platform-availability-groups-and-distributed-availability-groups"></a>Groupes de disponibilité inter-plateformes et des groupes de disponibilité distribués

- En raison d’un problème connu, la création de groupes de disponibilité avec des réplicas sur les instances hébergées sur Windows et Linux ne fonctionne pas dans cette version. Cela inclut les groupes de disponibilité distribués. Le correctif sera disponible dans la prochaine version release candidate. 

#### <a name="server-collation"></a>Classement du serveur

- Lorsque à l’aide de la MSSQL_COLLATION remplacer, ou lorsque vous effectuez une installation (non anglaise) localisée, il est possible de SQL Server sera atteint un blocage lors de la tentative de définir le classement du serveur, ce qui génère un fichier de vidage. Le programme d’installation ne termine avec succès, cependant le classement du serveur ne doit pas être défini. La solution de contournement consiste à exécuter. / classement mssql-conf ensemble et entrez le nom du classement souhaité quand vous y êtes invité (le nom de classement sont accessibles dans le journal des erreurs au niveau de la ligne : « Tente de modifier le classement par défaut pour... »). 
 
#### <a name="localization"></a>Localisation

- Si vos paramètres régionaux n’est pas anglais (fr_FR) lors de l’installation, vous devez utiliser l’encodage UTF-8 dans votre session d’interpréteur de commandes/terminal. Si vous utilisez l’encodage ASCII, vous pouvez voir une erreur semblable au suivant :

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Si vous ne pouvez pas utiliser le codage UTF-8, exécutez le programme d’installation à l’aide de la variable d’environnement MSSQL_LCID pour spécifier votre choix de la langue.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

#### <a name = "fci"></a>Partagé de mise à niveau instance cluster de disque

Dans la version RC1 l’agent de ressource de cluster définit le nom du serveur virtuel comme elle le fait dans une Instance de Cluster de basculement sous Windows. Avant RC1 `@@servername` sur un disque partagé cluster a retourné le nœud spécifique, nom après le basculement `@@servername` a retourné une valeur différente. Dans la version RC1 le nom du serveur de l’instance de cluster de disque partagé est mis à jour avec le nom de ressource lorsque la ressource est ajoutée au cluster. Pour cette raison, le cluster sera obligé de redémarrer le serveur SQL Server après le basculement manuel pendant la mise à niveau - comme dans les étapes suivantes :

1. Mise à niveau de nœud de cluster (passif) secondaire tout d’abord.
   - Mise à niveau **mssql-serveur** package.
   - Mise à niveau **mssql-server-ha** package.
1. Basculez manuellement vers le nœud mis à niveau.
   `pcs resource move <resourceName>`
   - Ressource échoue car l’agent de ressource vérifie le nom de serveur réel et prévu. Le nom de serveur attendu sera différente.
   - Cluster va redémarrer la ressource SQL Server sur le même nœud. Met à jour le nom du serveur.
1. Mise à niveau de l’autre nœud. 
   - Mise à niveau **mssql-serveur** package.
   - Mise à niveau **mssql-server-ha** package.
1. Supprimez la contrainte ajoutée par le déplacement manuel des ressources. Consultez [manuellement de cluster de basculement](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md#failManual).
2. Si vous le souhaitez, restauré sur le nœud principal d’origine. 

#### <a name="availability-group"></a>Groupe de disponibilité

Mise à niveau de SQL Server 2017 CTP 2.1 de propagée vers la version RC1 sur Linux, n’est pas pris en charge. Une fois que vous mettez à niveau le réplica secondaire, il sera déconnecté du réplica principal jusqu'à ce que le réplica principal est mis à niveau. Microsoft prévoit de résoudre ce problème avant la prochaine version.

#### <a name="full-text-search"></a>Recherche en texte intégral
- Pas de tous les filtres sont disponibles avec cette version, notamment les filtres pour les documents Office. Pour obtenir la liste de filtres pris en charge, consultez [installer de recherche de texte intégral SQL Server sur Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)

- Le **mssql server est** package n’est pas pris en charge sur SUSE dans cette version. Il est actuellement pris en charge sur Ubuntu sur Red Hat Enterprise Linux (RHEL).

- Les fonctionnalités suivantes ne sont pas pris en charge dans cette version lorsque vous exécutez des packages SSIS sur Linux :
  - Base de données du catalogue SSIS
  - Exécution du package planifiés par l’Agent SQL
  - Authentification Windows
  - Les composants tiers
  - Capture de données modifiées (CDC)
  - Avec montée en puissance SSIS
  - Azure Feature Pack pour SSIS
  - Prise en charge de Hadoop et HDFS
  - Microsoft Connector pour SAP BW

Pour plus d’informations sur SSIS sur Linux, consultez les articles suivants :
-   [Installer SQL Server Integration Services (SSIS) sur Linux](sql-server-linux-setup-ssis.md)
-   [Extraire, transformer et charger des données sur Linux avec SSIS](sql-server-linux-migrate-ssis.md)

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Les limitations suivantes s’appliquent à SSMS sur Windows connectés à SQL Server sur Linux.

- Plans de maintenance ne sont pas pris en charge.

- L’entrepôt de données de gestion (MDW) et le collecteur de données dans SSMS ne sont pas pris en charge. 

- Les composants SSMS UI disposant de l’authentification Windows ou les options du journal des événements Windows ne fonctionnent pas avec Linux. Vous pouvez toujours utiliser ces fonctionnalités avec d’autres options, telles que des connexions SQL. 

- Impossible de modifier le nombre de fichiers journaux à conserver.

### <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez les didacticiels de démarrage rapide suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Graphique de barre de séparation](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp21"></a>CTP 2.1 (mai 2017)
La version du moteur SQL Server pour cette version est 14.0.600.250.

### <a name="supported-platforms"></a>Plateformes prises en charge 

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Bureau, serveur et station de travail Red Hat Enterprise Linux 7.3 | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| Serveur Linux SUSE Enterprise SP2 v12 | EXT4 | [Guide d’installation](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Moteur docker 1.8 + sur Windows, Mac ou Linux | Néant | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!NOTE]
> Vous devez au moins 3,25 Go de mémoire pour exécuter SQL Server sur Linux.
> Moteur SQL Server a été testé jusqu'à 1 To de mémoire pour l’instant.

### <a name="package-details"></a>Détails du package
Détails du package et les emplacements de téléchargement pour les packages RPM et Debian sont répertoriés dans le tableau suivant. Vous n’avez pas besoin télécharger ces packages directement si vous utilisez les étapes dans les guides d’installation suivantes :

- [Installer le package SQL Server](sql-server-linux-setup.md)
- [Installer le package de la recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
- [Installer le package de l’Agent SQL Server](sql-server-linux-setup-sql-agent.md)

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Rpm de Red Hat | 14.0.600.250-2 | [Moteur le package RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.600.250-2.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.600.250-2.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.600.250-2.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.600.250-2.x86_64.rpm) | 
| Package RPM de SLES | 14.0.600.250-2 | [package RPM du moteur de serveur MSSQL](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.600.250-2.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.600.250-2.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.600.250-2.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.600.250-2.x86_64.rpm) | 
| Package de Debian Ubuntu 16.04 | 14.0.600.250-2 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.600.250-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.600.250-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.600.250-2_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.600.250-2_amd64.deb) |

### <a name="supported-client-tools"></a>Outils clients pris en charge

| Outil | Version minimale |
|-----|-----|
| [SQL Server Management Studio (SSMS) pour Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools pour Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Code Visual Studio](https://code.visualstudio.com) avec la [mssql extension](https://aka.ms/mssql-marketplace) | Plus récente (1.12) |

### <a name="unsupported-features-and-services"></a>Services et les fonctionnalités non prises en charge
Les fonctionnalités et les services suivants ne sont pas disponibles sur Linux pour l’instant. La prise en charge de ces fonctionnalités est plus activé lors de la cadence mensuelle de mises à jour le programme d’évaluation.

| Domaine | Fonctionnalité non prise en charge ou un service |
|-----|-----|
| **Moteur de base de données** | Réplication |
| &nbsp; | Étendre la base de données |
| &nbsp; | Polybase |
| &nbsp; | Requête distribuée |
| &nbsp; | Procédures système stockées étendues (XP_CMDSHELL, etc.). |
| &nbsp; | Filetable |
| &nbsp; | Définir des assemblys CLR avec l’autorisation EXTERNAL_ACCESS ou UNSAFE |
| **Haute disponibilité** | Mise en miroir de bases de données  |
| **Sécurité** | Authentification Active Directory |
| &nbsp; | Authentification Windows |
| &nbsp; | Gestion de clés extensible |
| &nbsp; | Utilisation du certificat fourni par l’utilisateur pour les protocoles SSL ou TLS |
| **Services** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problèmes connus
Les sections suivantes décrivent les problèmes connus avec cette version de SQL Server 2017 CTP 2.1 sur Linux.

#### <a name="general"></a>Général
- La longueur du nom d’hôte sur lequel SQL Server est installé a besoin pour être de 15 caractères ou moins. 

    - **Résolution**: Remplacez le nom d’hôte/etc/quelque chose de 15 caractères ou plus.

- Définition manuelle de l’heure système vers l’arrière dans le temps entraîne SQL Server arrêter la mise à jour de l’heure système interne dans SQL Server.

    - **Résolution**: redémarrez SQL Server.

- Seules les installations d’instance unique sont pris en charge.

    - **Résolution**: Si vous souhaitez disposer de plusieurs instances sur un hôte donné, envisagez d’utiliser des machines virtuelles ou des conteneurs Docker. 

- Gestionnaire de Configuration SQL Server ne peut pas se connecter à SQL Server sur Linux.

- La langue par défaut de la **sa** connexion est l’anglaise.

    - **Résolution**: modifier la langue de la **sa** connexion avec le **ALTER LOGIN** instruction.

#### <a name="databases"></a>Bases de données
- Impossible de déplacer les bases de données système avec l’utilitaire mssql-conf.

- Lorsque vous restaurez une base de données a été sauvegardée sur SQL Server sur Windows, vous devez utiliser le **WITH MOVE** clause dans l’instruction Transact-SQL.

- Nécessiter que le service Microsoft Distributed Transaction Coordinator les transactions distribuées ne sont pas pris en charge sur SQL Server est en cours d’exécution sur Linux. SQL Server vers SQL Server, les transactions distribuées sont prises en charge.

#### <a name="always-on-availability-group"></a>Toujours sur le groupe de disponibilité
- `sys.fn_hadr_backup_is_preffered_replica`ne fonctionne pas pour `CLUSTER_TYPE=NONE` ou `CLUSTER_TYPE=EXTERNAL` , car il s’appuie sur le Registre de cluster de réplication WSFC de clé qui est non disponible. Nous travaillons sur la fourniture d’une fonctionnalité similaire à une autre fonction. 

#### <a name="full-text-search"></a>Recherche en texte intégral
- Pas de tous les filtres sont disponibles avec cette version, notamment les filtres pour les documents Office. Pour obtenir la liste de filtres pris en charge, consultez [installer de recherche de texte intégral SQL Server sur Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a name="sql-agent"></a>Agent SQL
- Les composants et les sous-systèmes de travaux de l’Agent SQL suivants ne sont pas actuellement pris en charge sous Linux :

    - Sous-systèmes : CmdExec, PowerShell, serveur de distribution de réplication, instantanés, fusion, lecteur de file d’attente, SSIS, SSAS, SSRS
    - Alertes
    - Messagerie de base de données
    - l'Agent de lecture du journal ; 
    - Capture de données modifiées

#### <a name="sqlpackage"></a>SqlPackage
- À l’aide de SqlPackage, vous devez spécifier un chemin d’accès absolu pour les fichiers. À l’aide de chemins d’accès relatifs mappera les fichiers sous la « / tmp/sqlpackage. \<code \> /système/system32 « dossier. 

  - **Résolution**: utiliser des chemins d’accès absolus.

- SqlPackage indique l’emplacement des fichiers avec un « C:\\« préfixe.

#### <a name="ssis"></a> SQL Server Integration Services (SSIS)
Vous pouvez exécuter des packages SSIS sur Linux. Pour plus d’informations, consultez la [annonce de billet de blog SSIS prise en charge de Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/). Veuillez noter les problèmes connus suivants avec cette version.

- Le **mssql server est** package est uniquement pris en charge sur Ubuntu pour l’instant.

- Les fonctionnalités suivantes ne sont pas prises en charge lors de l’exécution des packages SSIS sur Linux :
  - Catalogue SSIS DB
  - Planifier l’exécution de Packages par l’Agent SQL
  - Authentification Windows
  - Les composants tiers
  - Pilotes ODBC de tiers
  - Gestionnaire de connexions ODBC, Source et Destination (pris en charge avec SSIS lors de l’actualisation de Linux CTP 2.1)
  - Capture de données modifiées (CDC)
  - Montée en puissance parallèle
  - Feature Pack Azure
  - Hadoop et HDFS Support
  - Microsoft Connector pour SAP BW

SSIS lors de l’actualisation de Linux CTP 2.1, vos packages SSIS permet les connexions ODBC sur Linux. Pour plus d’informations, consultez la [blog de l’annonce prise en charge d’ODBC sur Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Les limitations suivantes s’appliquent à SSMS sur Windows connectés à SQL Server sur Linux.

- Plans de maintenance ne sont pas pris en charge.

- L’entrepôt de données de gestion (MDW) et le collecteur de données dans SSMS ne sont pas pris en charge. 

- Les composants SSMS UI disposant de l’authentification Windows ou les options du journal des événements Windows ne fonctionnent pas avec Linux. Vous pouvez toujours utiliser ces fonctionnalités avec d’autres options, telles que des connexions SQL. 

- Impossible de modifier le nombre de fichiers journaux à conserver.

### <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez les didacticiels de démarrage rapide suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Graphique de barre de séparation](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp20"></a>CTP 2.0 (avril 2017)
La version du moteur SQL Server pour cette version est 14.0.500.272.

### <a name="supported-platforms"></a>Plateformes prises en charge 

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Bureau, serveur et station de travail Red Hat Enterprise Linux 7.3 | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| Serveur Linux SUSE Enterprise SP2 v12 | EXT4 | [Guide d’installation](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS et 16.10 | EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Moteur docker 1.8 + sur Windows, Mac ou Linux | Néant | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Vous devez au moins 3,25 Go de mémoire pour exécuter SQL Server sur Linux.
> Moteur SQL Server a été testé jusqu'à 1 To de mémoire pour l’instant.

### <a name="package-details"></a>Détails du package
Détails du package et les emplacements de téléchargement pour les packages RPM et Debian sont répertoriés dans le tableau suivant. Notez que vous n’avez pas besoin de télécharger ces packages directement si vous utilisez les étapes dans les guides d’installation suivantes :

- [Installer le package SQL Server](sql-server-linux-setup.md)
- [Installer le package de la recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
- [Installer le package de l’Agent SQL Server](sql-server-linux-setup-sql-agent.md)

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Rpm de Red Hat | 14.0.500.272-2 | [Moteur le package RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.500.272-2.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.500.272-2.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.500.272-2.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.500.272-2.x86_64.rpm) | 
| Package RPM de SLES | 14.0.500.272-2 | [package RPM du moteur de serveur MSSQL](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.500.272-2.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.500.272-2.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.500.272-2.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.500.272-2.x86_64.rpm) | 
| Package de Debian Ubuntu 16.04 | 14.0.500.272-2 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.500.272-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.500.272-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.500.272-2_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.500.272-2_amd64.deb) |
| Package de Debian Ubuntu 16.10 | 14.0.500.272-2 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.500.272-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.500.272-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.500.272-2_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.500.272-2_amd64.deb) |

### <a name="supported-client-tools"></a>Outils clients pris en charge

| Outil | Version minimale |
|-----|-----|
| [SQL Server Management Studio (SSMS) pour Windows - version Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools pour Visual Studio - version Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Code Visual Studio](https://code.visualstudio.com) avec la [mssql extension](https://aka.ms/mssql-marketplace) | Plus récente (0.2.1) |

> [!NOTE] 
> Les versions de SQL Server Management Studio et SQL Server Data Tools spécifiées ci-dessus sont des candidats de mise en production, par conséquent, ne pas recommandé pour une utilisation en production.

### <a name="unsupported-features-and-services"></a>Services et les fonctionnalités non prises en charge
Les fonctionnalités et les services suivants ne sont pas disponibles sur Linux pour l’instant. La prise en charge de ces fonctionnalités est plus activé lors de la cadence mensuelle de mises à jour le programme d’évaluation.

| Domaine | Fonctionnalité non prise en charge ou un service |
|-----|-----|
| **Moteur de base de données** | Réplication |
| &nbsp; | Étendre la base de données |
| &nbsp; | Polybase |
| &nbsp; | Requête distribuée |
| &nbsp; | Procédures système stockées étendues (XP_CMDSHELL, etc.). |
| &nbsp; | Filetable |
| &nbsp; | Définir des assemblys CLR avec l’autorisation EXTERNAL_ACCESS ou UNSAFE |
| **Haute disponibilité** | Mise en miroir de bases de données  |
| **Sécurité** | Authentification Active Directory |
| &nbsp; | Authentification Windows |
| &nbsp; | Gestion de clés extensible |
| &nbsp; | Utilisation du certificat fourni par l’utilisateur pour les protocoles SSL ou TLS |
| **Services** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problèmes connus
Les sections suivantes décrivent les problèmes connus avec cette version de SQL Server 2017 CTP 2.0 sur Linux.

#### <a name="general"></a>Général
- La longueur du nom d’hôte sur lequel SQL Server est installé a besoin pour être de 15 caractères ou moins. 

    - **Résolution**: Remplacez le nom d’hôte/etc/quelque chose de 15 caractères ou plus.

- Définition manuelle de l’heure système vers l’arrière dans le temps entraîne SQL Server arrêter la mise à jour de l’heure système interne dans SQL Server.

    - **Résolution**: redémarrez SQL Server.

- Seules les installations d’instance unique sont pris en charge.

    - **Résolution**: Si vous souhaitez disposer de plusieurs instances sur un hôte donné, envisagez d’utiliser des machines virtuelles ou des conteneurs Docker. 

- Gestionnaire de Configuration SQL Server ne peut pas se connecter à SQL Server sur Linux.

- La langue par défaut de la **sa** connexion est l’anglaise.

    - **Résolution**: modifier la langue de la **sa** connexion avec le **ALTER LOGIN** instruction.

#### <a name="databases"></a>Bases de données
- Impossible de déplacer les bases de données système avec l’utilitaire mssql-conf.

- Lorsque vous restaurez une base de données a été sauvegardée sur SQL Server sur Windows, vous devez utiliser le **WITH MOVE** clause dans l’instruction Transact-SQL.

- Nécessiter que le service Microsoft Distributed Transaction Coordinator les transactions distribuées ne sont pas pris en charge sur SQL Server est en cours d’exécution sur Linux. SQL Server vers SQL Server, les transactions distribuées sont prises en charge.

#### <a name="always-on-availability-group"></a>Toujours sur le groupe de disponibilité
- Toutes les configurations de haute disponibilité - ce qui signifie que le groupe de disponibilité est ajouté en tant que ressource à un cluster STIMULATEUR - créé avec les versions antérieures CTP2.0 packages ne sont pas une compatibilité descendante avec le nouveau package. Supprimer toutes les ressources de cluster précédemment configurés et créer des groupes de disponibilité avec `CLUSTER_TYPE=EXTERNAL`. Consultez [configurer toujours sur le groupe de disponibilité pour SQL Server sur Linux](sql-server-linux-availability-group-configure-ha.md).
- Groupes de disponibilité créés avec `CLUSTER_TYPE=NONE` et non ajoutés comme ressources dans le cluster de continuer à utiliser après la mise à niveau. À utiliser pour les scénarios en lecture à l’échelle. Consultez [groupe de disponibilité de l’échelle de la lecture de configurer pour SQL Server sur Linux](sql-server-linux-availability-group-configure-rs.md).
- `sys.fn_hadr_backup_is_preffered_replica`ne fonctionne pas pour `CLUSTER_TYPE=NONE` ou `CLUSTER_TYPE=EXTERNAL` , car il s’appuie sur le Registre de cluster de réplication WSFC de clé qui est non disponible. Nous travaillons sur la fourniture d’une fonctionnalité similaire à une autre fonction. 

#### <a name="full-text-search"></a>Recherche en texte intégral
- Pas de tous les filtres sont disponibles avec cette version, notamment les filtres pour les documents Office. Pour obtenir la liste de filtres pris en charge, consultez [installer de recherche de texte intégral SQL Server sur Linux](sql-server-linux-setup-full-text-search.md#filters).

- L’analyseur lexical coréen prend quelques secondes pour charger et génère une erreur lors de la première utilisation. Après cette erreur initiale, il doit fonctionner normalement.

#### <a name="sql-agent"></a>Agent SQL
- Les composants et les sous-systèmes de travaux de l’Agent SQL suivants ne sont pas actuellement pris en charge sous Linux :

    - Sous-systèmes : CmdExec, PowerShell, serveur de distribution de réplication, instantanés, fusion, lecteur de file d’attente, SSIS, SSAS, SSRS
    - Alertes
    - Messagerie de base de données
    - l'Agent de lecture du journal ; 
    - Capture de données modifiées

#### <a name="sqlpackage"></a>SqlPackage
- À l’aide de SqlPackage, vous devez spécifier un chemin d’accès absolu pour les fichiers. À l’aide de chemins d’accès relatifs mappera les fichiers sous la « / tmp/sqlpackage. \<code \> /système/system32 « dossier. 

    - **Résolution**: utiliser des chemins d’accès absolus.

- SqlPackage indique l’emplacement des fichiers avec un « C:\\« préfixe.

    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Les limitations suivantes s’appliquent à SSMS sur Windows connectés à SQL Server sur Linux.

- Plans de maintenance ne sont pas pris en charge.

- L’entrepôt de données de gestion (MDW) et le collecteur de données dans SSMS ne sont pas pris en charge. 

- Les composants SSMS UI disposant de l’authentification Windows ou les options du journal des événements Windows ne fonctionnent pas avec Linux. Vous pouvez toujours utiliser ces fonctionnalités avec d’autres options, telles que des connexions SQL. 

- Impossible de modifier le nombre de fichiers journaux à conserver.

### <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez les didacticiels de démarrage rapide suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Graphique de barre de séparation](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp14"></a>CTP 1.4 (mars 2017)
La version du moteur SQL Server pour cette version est 14.0.405.198.

### <a name="supported-platforms"></a>Plateformes prises en charge 

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Bureau, serveur et station de travail Red Hat Enterprise Linux 7.3 | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| Serveur Linux SUSE Enterprise SP2 v12 | EXT4 | [Guide d’installation](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS et 16.10 | EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Moteur docker 1.8 + sur Windows, Mac ou Linux | Néant | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Vous devez au moins 3,25 Go de mémoire pour exécuter SQL Server sur Linux.
> Moteur SQL Server a été testé jusqu'à 1 To de mémoire pour l’instant.

### <a name="package-details"></a>Détails du package
Détails du package et les emplacements de téléchargement pour les packages RPM et Debian sont répertoriés dans le tableau suivant. Notez que vous n’avez pas besoin de télécharger ces packages directement si vous utilisez les étapes dans les guides d’installation ci-dessous
-   [Installer le package SQL Server](sql-server-linux-setup.md)
-   [Installer le package de la recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
-   [Installer le package de l’Agent SQL Server](sql-server-linux-setup-sql-agent.md)

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Rpm de Red Hat | 14.0.405.200-1 | [Moteur le package RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.405.200-1.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.405.200-1.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.405.200-1.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.405.200-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.405.200-1 | [package RPM du moteur de serveur MSSQL](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.405.200-1.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.405.200-1.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.405.200-1.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.405.200-1.x86_64.rpm) | 
| Package de Debian Ubuntu 16.04 | 14.0.405.200-1 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.405.200-1_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.405.200-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.405.200-1_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.405.200-1_amd64.deb) |
| Package de Debian Ubuntu 16.10 | 14.0.405.200-1 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.405.200-1_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.405.200-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.405.200-1_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.405.200-1_amd64.deb) |

### <a name="supported-client-tools"></a>Outils clients pris en charge

| Outil | Version minimale |
|-----|-----|
| [SQL Server Management Studio (SSMS) pour Windows - version Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools pour Visual Studio - version Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Code Visual Studio](https://code.visualstudio.com) avec la [mssql extension](https://aka.ms/mssql-marketplace) | Plus récente (0.2.1) |

> [!NOTE] 
> Les versions de SQL Server Management Studio et SQL Server Data Tools spécifiées ci-dessus sont des candidats de mise en production, par conséquent, ne pas recommandé pour une utilisation en production.

### <a name="unsupported-features-and-services"></a>Services et les fonctionnalités non prises en charge
Les fonctionnalités et les services suivants ne sont pas disponibles sur Linux pour l’instant. La prise en charge de ces fonctionnalités est plus activé lors de la cadence mensuelle de mises à jour le programme d’évaluation.

| Domaine | Fonctionnalité non prise en charge ou un service |
|-----|-----|
| **Moteur de base de données** | Réplication |
| &nbsp; | Étendre la base de données |
| &nbsp; | Polybase |
| &nbsp; | Requête distribuée |
| &nbsp; | Procédures système stockées étendues (XP_CMDSHELL, etc.). |
| &nbsp; | Filetable |
| &nbsp; | Définir des assemblys CLR avec l’autorisation EXTERNAL_ACCESS ou UNSAFE |
| **Haute disponibilité** | Mise en miroir de bases de données  |
| **Sécurité** | Authentification Active Directory |
| &nbsp; | Authentification Windows |
| &nbsp; | Gestion de clés extensible |
| &nbsp; | Utilisation du certificat fourni par l’utilisateur pour les protocoles SSL ou TLS |
| **Services** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problèmes connus
Les sections suivantes décrivent les problèmes connus avec cette version de SQL Server 2017 CTP 1.4 sur Linux.

#### <a name="general"></a>Général
- La longueur du nom d’hôte sur lequel SQL Server est installé a besoin pour être de 15 caractères ou moins. 

    - **Résolution**: Remplacez le nom d’hôte/etc/quelque chose de 15 caractères ou plus.

- N’exécutez pas la commande `ALTER SERVICE MASTER KEY REGENERATE`. Il existe un bogue connu qui fait que SQL Server dans un état instable. Si vous avez besoin régénérer la clé principale du Service, vous devez sauvegarder vos fichiers de base de données, désinstallez puis réinstallez SQL Server et restaurer les fichiers de base de données à nouveau.

- Définition manuelle de l’heure système vers l’arrière dans le temps entraîne SQL Server arrêter la mise à jour de l’heure système interne dans SQL Server.

    - **Résolution**: redémarrez SQL Server.

- Certains noms de fuseau horaire dans Linux ne sont pas exactement aux noms de fuseau horaire Windows.

    - **Résolution**: utiliser des noms de fuseau horaire à partir de la colonne TZID le ' mappage pour : table de section de Windows sur le [page de documentation Unicode.org](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- Moteur SQL Server attend des lignes dans les fichiers texte à se terminer avec CRLF (Windows-style ligne mise en forme).

- Seules les installations d’instance unique sont pris en charge.

    - **Résolution**: Si vous souhaitez disposer de plusieurs instances sur un hôte donné, envisagez d’utiliser des machines virtuelles ou des conteneurs Docker. 

- Tous les fichiers journaux et les journaux d’erreurs sont encodés en UTF-16.

- Gestionnaire de Configuration SQL Server ne peut pas se connecter à SQL Server sur Linux.

- **CREATE ASSEMBLY** ne fonctionne pas lorsque vous tentez d’utiliser un fichier. Utilisez le **FROM \<bits\> ** méthode à la place pour l’instant. 

#### <a name="databases"></a>Bases de données
- Impossible de déplacer les bases de données système avec l’utilitaire mssql-conf.

- Lorsque vous restaurez une base de données a été sauvegardée sur SQL Server sur Windows, vous devez utiliser le **WITH MOVE** clause dans l’instruction Transact-SQL.

- Nécessiter que le service Microsoft Distributed Transaction Coordinator les transactions distribuées ne sont pas pris en charge sur SQL Server est en cours d’exécution sur Linux. SQL Server vers SQL Server, les transactions distribuées sont prises en charge.

#### <a name="always-on-availability-group"></a>Toujours sur le groupe de disponibilité
- Groupe de disponibilité AlwaysOn des ressources en cluster sur Linux qui ont été créées avec CTP 1.3 échoue une fois que vous mettez à niveau le package à haute disponibilité (mssql-server-ha). 

   - **Résolution**: mettre à niveau le package de haute disponibilité, définissez le paramètre de ressource de cluster `notify=true`. 
   
      - L’exemple suivant définit le paramètre de ressource de cluster sur une ressource nommée **ag1** sur RHEL ou Ubuntu : 

      ```bash
      sudo pcs resource update ag1-master notify=true
      ```

      - Pour SLES, mettre à jour de configuration pour ajouter la ressource de groupe de disponibilité `notify=true`.  

      ```bash
      crm configure edit ms-ag_cluster 
      ```

      Ajouter `notify=true` et enregistrer la configuration de la ressource.

- Groupes de disponibilité AlwaysOn dans Linux peuvent être soumis à une perte de données si les réplicas sont en mode de validation synchrone. Afficher les détails en fonction de votre distribution Linux. 

   - [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   - [SLES](sql-server-linux-availability-group-cluster-sles.md)
   - [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

#### <a name="full-text-search"></a>Recherche en texte intégral
- Pas de tous les filtres sont disponibles avec cette version, notamment les filtres pour les documents Office. Pour obtenir la liste de filtres pris en charge, consultez [installer de recherche de texte intégral SQL Server sur Linux](sql-server-linux-setup-full-text-search.md#filters).

- L’analyseur lexical coréen prend quelques secondes pour charger et génère une erreur lors de la première utilisation. Après cette erreur initiale, il doit fonctionner normalement.

#### <a name="sql-agent"></a>Agent SQL
- Les composants et les sous-systèmes de travaux de l’Agent SQL suivants ne sont pas actuellement pris en charge sous Linux :
    - Sous-systèmes : CmdExec, PowerShell, serveur de distribution de réplication, instantanés, fusion, lecteur de file d’attente, SSIS, SSAS, SSRS
    - Alertes
    - Messagerie de base de données
    - Copie des journaux de transaction
    - l'Agent de lecture du journal ; 
    - Capture de données modifiées

#### <a name="in-memory-oltp"></a>OLTP en mémoire
- Bases de données OLTP en mémoire peuvent être créés uniquement dans le répertoire /var/opt/mssql. Pour plus d’informations, visitez le [In-memory OLTP rubrique](sql-server-linux-performance-get-started.md#use-in-memory-oltp).

#### <a name="sqlpackage"></a>SqlPackage
- À l’aide de SqlPackage, vous devez spécifier un chemin d’accès absolu pour les fichiers. À l’aide de chemins d’accès relatifs mappera les fichiers sous la « / tmp/sqlpackage. \<code \> /système/system32 « dossier. 

    - **Résolution**: utiliser des chemins d’accès absolus.

- SqlPackage indique l’emplacement des fichiers avec un « C:\\« préfixe.

    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Les limitations suivantes s’appliquent à SSMS sur Windows connectés à SQL Server sur Linux.

- Plans de maintenance ne sont pas pris en charge.

- L’entrepôt de données de gestion (MDW) et le collecteur de données dans SSMS n’est pas pris en charge. 

- Les composants SSMS UI disposant de l’authentification Windows ou les options du journal des événements Windows ne fonctionnent pas avec Linux. Vous pouvez toujours utiliser ces fonctionnalités avec d’autres options, telles que des connexions SQL. 

- L’Explorateur de fichiers est limité à la « C:\\« étendue, qui est résolue en/var/opt/mssql/sur Linux. Pour utiliser les autres chemins d’accès, générer des scripts de l’opération de l’interface utilisateur et remplacez le lecteur C:\\ chemins d’accès des chemins d’accès de Linux. Puis exécutez manuellement le script dans SSMS.

- Impossible de modifier le nombre de fichiers journaux à conserver.

### <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez les didacticiels de démarrage rapide suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Graphique de barre de séparation](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp13"></a>CTP 1.3 (février 2017)
La version du moteur SQL Server pour cette version est 14.0.304.138.

### <a name="supported-platforms"></a>Plateformes prises en charge 

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Bureau, serveur et station de travail Red Hat Enterprise Linux 7.3 | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| Serveur Linux SUSE Enterprise SP2 v12 | EXT4 | [Guide d’installation](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS et 16.10 | EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Moteur docker 1.8 + sur Windows, Mac ou Linux | Néant | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Vous devez au moins 3,25 Go de mémoire pour exécuter SQL Server sur Linux.
> Moteur SQL Server a été testé jusqu'à 1 To de mémoire pour l’instant.

### <a name="package-details"></a>Détails du package
Détails du package et les emplacements de téléchargement pour les packages RPM et Debian sont répertoriés dans le tableau suivant. Notez que vous n’avez pas besoin de télécharger ces packages directement si vous utilisez les étapes décrites dans le [guides d’installation](sql-server-linux-setup.md).

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Rpm de Red Hat | 14.0.304.138-1 | [package RPM du moteur de serveur MSSQL](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.304.138-1.x86_64.rpm)</br>[package MSSQL-server-ha tr/min de haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.304.138-1.x86_64.rpm)</br>[package RPM de recherche en texte intégral de FTP du serveur MSSQL](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.304.138-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.304.138-1 | [package RPM du moteur de serveur MSSQL](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.304.138-1.x86_64.rpm)</br>[package MSSQL-server-ha tr/min de haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.304.138-1.x86_64.rpm)</br>[package RPM de recherche en texte intégral de FTP du serveur MSSQL](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.304.138-1.x86_64.rpm) | 
| Package de Debian Ubuntu 16.04 | 14.0.304.138-1 | [MSSQL-serveur moteur Debian le package](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.304.138-1_amd64.deb)</br>[MSSQL-server-ha haute disponibilité Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.304.138-1_amd64.deb)</br>[package Debian de recherche en texte intégral FTP du serveur MSSQL](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.304.138-1_amd64.deb) |
| Package de Debian Ubuntu 16.10 | 14.0.304.138-1 | [MSSQL-serveur moteur Debian le package](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.304.138-1_amd64.deb)</br>[MSSQL-server-ha haute disponibilité Debian package](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.304.138-1_amd64.deb)</br>[package Debian de recherche en texte intégral FTP du serveur MSSQL](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.304.138-1_amd64.deb) |

### <a name="supported-client-tools"></a>Outils clients pris en charge

| Outil | Version minimale |
|-----|-----|
| [SQL Server Management Studio (SSMS) pour Windows - version Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools pour Visual Studio - version Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Code Visual Studio](https://code.visualstudio.com) avec la [mssql extension](https://aka.ms/mssql-marketplace) | Plus récente (0.2.1) |

> [!NOTE] 
> Les versions de SQL Server Management Studio et SQL Server Data Tools spécifiées ci-dessus sont des candidats de mise en production, par conséquent, ne pas recommandé pour une utilisation en production.

### <a name="unsupported-features-and-services"></a>Services et les fonctionnalités non prises en charge
Les fonctionnalités et les services suivants ne sont pas disponibles sur Linux pour l’instant. La prise en charge de ces fonctionnalités est plus activé lors de la cadence mensuelle de mises à jour le programme d’évaluation.

| Domaine | Fonctionnalité non prise en charge ou un service |
|-----|-----|
| **Moteur de base de données** | Réplication |
| &nbsp; | Étendre la base de données |
| &nbsp; | Polybase |
| &nbsp; | Requête distribuée |
| &nbsp; | Procédures système stockées étendues (XP_CMDSHELL, etc.). |
| &nbsp; | Filetable |
| &nbsp; | Définir des assemblys CLR avec l’autorisation EXTERNAL_ACCESS ou UNSAFE |
| **Haute disponibilité** | Mise en miroir de bases de données  |
| **Sécurité** | Authentification Active Directory |
| &nbsp; | Authentification Windows |
| &nbsp; | Gestion de clés extensible |
| &nbsp; | Utilisation du certificat fourni par l’utilisateur pour les protocoles SSL ou TLS |
| **Services** | SQL Server Agent |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problèmes connus
Les sections suivantes décrivent les problèmes connus avec cette version de SQL Server 2017 CTP 1.3 sur Linux.

#### <a name="general"></a>Général
- La longueur du nom d’hôte sur lequel SQL Server est installé a besoin pour être de 15 caractères ou moins. 

    - **Résolution**: Remplacez le nom d’hôte/etc/quelque chose de 15 caractères ou plus.

- N’exécutez pas la commande `ALTER SERVICE MASTER KEY REGENERATE`. Il existe un bogue connu qui fait que SQL Server dans un état instable. Si vous avez besoin régénérer la clé principale du Service, vous devez sauvegarder vos fichiers de base de données, désinstallez puis réinstallez SQL Server et restaurer les fichiers de base de données à nouveau.

- Définition manuelle de l’heure système vers l’arrière dans le temps entraîne SQL Server arrêter la mise à jour de l’heure système interne dans SQL Server.

    - **Résolution**: redémarrez SQL Server.

- Certains noms de fuseau horaire dans Linux ne sont pas exactement aux noms de fuseau horaire Windows.

    - **Résolution**: utiliser des noms de fuseau horaire à partir de la colonne TZID le ' mappage pour : table de section de Windows sur le [page de documentation Unicode.org](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- Moteur SQL Server attend des lignes dans les fichiers texte à se terminer avec CRLF (Windows-style ligne mise en forme).

- Seules les installations d’instance unique sont pris en charge.

    - **Résolution**: Si vous souhaitez disposer de plusieurs instances sur un hôte donné, envisagez d’utiliser des machines virtuelles ou des conteneurs Docker. 

- Tous les fichiers journaux et les journaux d’erreurs sont encodés en UTF-16.

- Gestionnaire de Configuration SQL Server ne peut pas se connecter à SQL Server sur Linux.

- **CREATE ASSEMBLY** ne fonctionne pas lorsque vous tentez d’utiliser un fichier. Utilisez le **FROM \<bits\> ** méthode à la place pour l’instant. 

#### <a name="databases"></a>Bases de données
- Modification des emplacements de fichiers de données et les journaux de TempDB n’est pas pris en charge.

- Impossible de déplacer les bases de données système avec l’utilitaire mssql-conf.

- Lorsque vous restaurez une base de données a été sauvegardée sur SQL Server sur Windows, vous devez utiliser le **WITH MOVE** clause dans l’instruction Transact-SQL.

- Nécessiter que le service Microsoft Distributed Transaction Coordinator les transactions distribuées ne sont pas pris en charge sur SQL Server est en cours d’exécution sur Linux. SQL Server vers SQL Server, les transactions distribuées sont prises en charge.

- Groupes de disponibilité AlwaysOn dans Linux peuvent être soumis à une perte de données si les réplicas sont en mode de validation synchrone. Consultez 
 
   - [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   - [SLES](sql-server-linux-availability-group-cluster-sles.md)
   - [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   
#### <a name="full-text-search"></a>Recherche en texte intégral
- Pas de tous les filtres sont disponibles avec cette version, notamment les filtres pour les documents Office. Pour obtenir la liste de filtres pris en charge, consultez [installer de recherche de texte intégral SQL Server sur Linux](sql-server-linux-setup-full-text-search.md#filters).

- L’analyseur lexical coréen prend quelques secondes pour charger et génère une erreur lors de la première utilisation. Après cette erreur initiale, il doit fonctionner normalement.

#### <a name="in-memory-oltp"></a>OLTP en mémoire
- Bases de données OLTP en mémoire peuvent être créés uniquement dans le répertoire /var/opt/mssql. Pour plus d’informations, visitez le [In-memory OLTP rubrique](sql-server-linux-performance-get-started.md#use-in-memory-oltp).  

#### <a name="sqlpackage"></a>SqlPackage
- À l’aide de SqlPackage, vous devez spécifier un chemin d’accès absolu pour les fichiers. À l’aide de chemins d’accès relatifs mappera les fichiers sous la « /tmp/sqlpackage./ <code/> /système/system32 « dossier. 

    - **Résolution**: utiliser des chemins d’accès absolus.

- SqlPackage indique l’emplacement des fichiers avec un « C:\\« préfixe.

#### <a name="sqlcmdbcp--odbc"></a>SQLCMD/BCP et ODBC 
- Outils de ligne de commande SQL Server (mssql-tools) et le pilote ODBC (msodbcsql) dépend d’un gestionnaire de pilotes unixODBC de personnalisé. Cela provoque des conflits si vous disposez d’un gestionnaire de pilotes unixODBC de précédemment installé. 

    - **Résolution**: sur Ubuntu, le conflit sera résolu automatiquement. Lorsque vous y êtes invité si vous souhaitez désinstaller le Gestionnaire de pilotes unixODBC existant, tapez « o » et poursuivre l’installation. Sur Red Hat, vous devrez supprimer manuellement les Gestionnaire de pilotes unixODBC existant à l’aide de `yum remove unixODBC`. Nous travaillons sur la résolution de cette limitation pour RHEL et SUSE et que vous doit avoir une mise à jour pour vous plus rapidement.  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Les limitations suivantes s’appliquent à SSMS sur Windows connectés à SQL Server sur Linux.

- Plans de maintenance ne sont pas pris en charge.

- L’entrepôt de données de gestion (MDW) et le collecteur de données dans SSMS n’est pas pris en charge. 

- Les composants SSMS UI disposant de l’authentification Windows ou les options du journal des événements Windows ne fonctionnent pas avec Linux. Vous pouvez toujours utiliser ces fonctionnalités avec d’autres options, telles que des connexions SQL. 

- L’Agent SQL Server n’est pas encore pris en charge. Par conséquent, les fonctionnalités de l’Agent SQL Server dans SSMS ne fonctionnent pas sur Linux pour le moment.

- L’Explorateur de fichiers est limité à la « C:\\« étendue, qui est résolue en/var/opt/mssql/sur Linux. Pour utiliser les autres chemins d’accès, générer des scripts de l’opération de l’interface utilisateur et remplacez le lecteur C:\\ chemins d’accès des chemins d’accès de Linux. Puis exécutez manuellement le script dans SSMS.

- Impossible de modifier le nombre de fichiers journaux à conserver.

### <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez les didacticiels de démarrage rapide suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Graphique de barre de séparation](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp12-ctp-12-january-2017"></a><a id="ctp12">CTP 1.2 (janvier 2017)
La version du moteur SQL Server pour cette version est 14.0.200.24.

### <a name="supported-platforms"></a>Plateformes prises en charge 

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Bureau, serveur et station de travail Red Hat Enterprise Linux 7.3 | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| Serveur Linux SUSE Enterprise SP2 v12 | EXT4 | [Guide d’installation](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS et 16.10 | EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Moteur docker 1.8 + sur Windows, Mac ou Linux | Néant | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Vous devez au moins 3,25 Go de mémoire pour exécuter SQL Server sur Linux.
> Moteur SQL Server n’a pas été testé jusqu'à 256 Go de mémoire pour l’instant.

### <a name="package-details"></a>Détails du package
Détails du package et les emplacements de téléchargement pour les packages RPM et Debian sont répertoriés dans le tableau suivant. Notez que vous n’avez pas besoin de télécharger ces packages directement si vous utilisez les étapes décrites dans le [guides d’installation](sql-server-linux-setup.md).

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Package RPM | 14.0.200.24-2 | [package de moteur 14.0.200.24-2 MSSQL-serveur](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.200.24-2.x86_64.rpm)</br>[package de haute disponibilité RPM 14.0.200.24-2 MSSQL-serveur](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.200.24-2.x86_64.rpm) | 
| Package Debian | 14.0.200.24-2 | [MSSQL-serveur 14.0.200.24-2 moteur Debian le package](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.200.24-2_amd64.deb) |

### <a name="supported-client-tools"></a>Outils clients pris en charge

| Outil | Version minimale |
|-----|-----|
| [SQL Server Management Studio (SSMS) pour Windows - version Release Candidate 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools pour Visual Studio - version Release Candidate 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Code Visual Studio](https://code.visualstudio.com) avec la [mssql extension](https://aka.ms/mssql-marketplace) | Plus récente (0,2) |

> [!NOTE] 
> Les versions de SQL Server Management Studio et SQL Server Data Tools spécifiées ci-dessus sont des candidats de mise en production, par conséquent, ne pas recommandé pour une utilisation en production.

### <a name="unsupported-features-and-services"></a>Services et les fonctionnalités non prises en charge
Les fonctionnalités et les services suivants ne sont pas disponibles sur Linux pour l’instant. La prise en charge de ces fonctionnalités est plus activé lors de la cadence mensuelle de mises à jour le programme d’évaluation.

| Domaine | Fonctionnalité non prise en charge ou un service |
|-----|-----|
| **Moteur de base de données** | Recherche en texte intégral |
| &nbsp; | Réplication |
| &nbsp; | Étendre la base de données |
| &nbsp; | Polybase |
| &nbsp; | Requête distribuée |
| &nbsp; | Procédures système stockées étendues (XP_CMDSHELL, etc.). |
| &nbsp; | Filetable |
| &nbsp; | Définir des assemblys CLR avec l’autorisation EXTERNAL_ACCESS ou UNSAFE |
| **Haute disponibilité** | Groupes de disponibilité AlwaysOn |
| &nbsp; | Mise en miroir de bases de données  |
| **Sécurité** | Authentification Active Directory |
| &nbsp; | Authentification Windows |
| &nbsp; | Gestion de clés extensible |
| &nbsp; | Utilisation du certificat fourni par l’utilisateur pour les protocoles SSL ou TLS |
| **Services** | SQL Server Agent |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problèmes connus
Les sections suivantes décrivent les problèmes connus avec cette version de SQL Server 2017 CTP 1.2 sur Linux.

#### <a name="general"></a>Général
- La longueur du nom d’hôte sur lequel SQL Server est installé a besoin pour être de 15 caractères ou moins. 

    - **Résolution**: Remplacez le nom d’hôte/etc/quelque chose de 15 caractères ou plus.

- N’exécutez pas la commande `ALTER SERVICE MASTER KEY REGENERATE`. Il existe un bogue connu qui fait que SQL Server dans un état instable. Si vous avez besoin régénérer la clé principale du Service, vous devez sauvegarder vos fichiers de base de données, désinstallez puis réinstallez SQL Server et restaurer les fichiers de base de données à nouveau.

- Nom de ressource pour la ressource SQL a été remplacée par ocf:sql:fci à ocf:mssql:fci. Plus d’informations sur la configuration d’un cluster de basculement de disque partagé que vous pouvez trouver [ici](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-shared-disk-cluster-red-hat-7-configure).

- Définition manuelle de l’heure système vers l’arrière dans le temps entraîne SQL Server arrêter la mise à jour de l’heure système interne dans SQL Server.

    - **Résolution**: redémarrez SQL Server.

- Certains noms de fuseau horaire dans Linux ne sont pas exactement aux noms de fuseau horaire Windows.

    - **Résolution**: utiliser des noms de fuseau horaire à partir de la colonne TZID le ' mappage pour : table de section de Windows sur le [page de documentation Unicode.org](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- Moteur SQL Server attend des lignes dans les fichiers texte à se terminer avec CRLF (Windows-style ligne mise en forme).

- Seules les installations d’instance unique sont pris en charge.

    - **Résolution**: Si vous souhaitez disposer de plusieurs instances sur un hôte donné, envisagez d’utiliser des machines virtuelles ou des conteneurs Docker. 

- Tous les fichiers journaux et les journaux d’erreurs sont encodés en UTF-16.

- Gestionnaire de Configuration SQL Server ne peut pas se connecter à SQL Server sur Linux.

- **CREATE ASSEMBLY** ne fonctionne pas lorsque vous tentez d’utiliser un fichier. Utilisez le **FROM \<bits\> ** méthode à la place pour l’instant. 

#### <a name="databases"></a>Bases de données
- Modification des emplacements de fichiers de données et les journaux de TempDB n’est pas pris en charge.

- Impossible de déplacer les bases de données système avec l’utilitaire mssql-conf.

- Lorsque vous restaurez une base de données a été sauvegardée sur SQL Server sur Windows, vous devez utiliser le **WITH MOVE** clause dans l’instruction Transact-SQL.

- Nécessiter que le service Microsoft Distributed Transaction Coordinator les transactions distribuées ne sont pas pris en charge sur SQL Server est en cours d’exécution sur Linux. SQL Server vers SQL Server, les transactions distribuées sont prises en charge.

#### <a name="in-memory-oltp"></a>OLTP en mémoire
- Bases de données OLTP en mémoire peuvent être créés uniquement dans le répertoire /var/opt/mssql. Ces bases de données doivent également avoir le « C:\\« notation de référencé. Pour plus d’informations, visitez le [In-memory OLTP rubrique](sql-server-linux-performance-get-started.md#use-in-memory-oltp).  

#### <a name="sqlpackage"></a>SqlPackage
- À l’aide de SqlPackage, vous devez spécifier un chemin d’accès absolu pour les fichiers. À l’aide de chemins d’accès relatifs mappera les fichiers sous la « / tmp/sqlpackage. \<code \> /système/system32 « dossier. 

    - **Résolution**: utiliser des chemins d’accès absolus.

- SqlPackage indique l’emplacement des fichiers avec un « C:\\« préfixe.

#### <a name="sqlcmdbcp--odbc"></a>SQLCMD/BCP et ODBC 
- Si vous avez une version antérieure des outils de ligne de commande SQL Server (mssql-outils) et le pilote ODBC (msodbcsql), vous avez peut-être installé un unixODBC personnalisé du Gestionnaire de pilotes (unixODBC-utf16). Cela peut entraîner un conflit potentiel que nous ne plus utiliser un gestionnaire de pilote personnalisé. 

    - **Résolution**: sur Ubuntu et SLES, le conflit sera résolu automatiquement. Lorsque vous y êtes invité si vous souhaitez désinstaller le Gestionnaire de pilotes unixODBC existant, tapez « o » et poursuivre l’installation. Sur Red Hat, vous devrez supprimer manuellement les Gestionnaire de pilotes unixODBC existant à l’aide de `yum remove unixODBC-utf16 unixODBC-utf16-devel` et recommencez l’installation.
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Les limitations suivantes s’appliquent à SSMS sur Windows connectés à SQL Server sur Linux.

- Plans de maintenance ne sont pas pris en charge.

- L’entrepôt de données de gestion (MDW) et le collecteur de données dans SSMS n’est pas pris en charge. 

- Les composants SSMS UI disposant de l’authentification Windows ou les options du journal des événements Windows ne fonctionnent pas avec Linux. Vous pouvez toujours utiliser ces fonctionnalités avec d’autres options, telles que des connexions SQL. 

- L’Agent SQL Server n’est pas encore pris en charge. Par conséquent, les fonctionnalités de l’Agent SQL Server dans SSMS ne fonctionnent pas sur Linux pour le moment.

- L’Explorateur de fichiers est limité à la « C:\\« étendue, qui est résolue en/var/opt/mssql/sur Linux. Pour utiliser les autres chemins d’accès, générer des scripts de l’opération de l’interface utilisateur et remplacez le lecteur C:\\ chemins d’accès des chemins d’accès de Linux. Puis exécutez manuellement le script dans SSMS.

### <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez les didacticiels de démarrage rapide suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Graphique de barre de séparation](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp11-ctp-11-december-2016"></a><a id="ctp11">CTP 1.1 (décembre 2016)
La version du moteur SQL Server pour cette version est 14.0.100.187.

### <a name="supported-platforms"></a>Plateformes prises en charge 

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Bureau, serveur et station de travail Red Hat Enterprise Linux | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| Ubuntu 16.04LTS et 16.10 | EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Moteur docker 1.8 + sur Windows, Mac ou Linux | Néant | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Vous devez au moins 3,25 Go de mémoire pour exécuter SQL Server sur Linux.
> Moteur SQL Server n’a pas été testé jusqu'à 256 Go de mémoire pour l’instant.

### <a name="package-details"></a>Détails du package
Détails du package et les emplacements de téléchargement pour les packages RPM et Debian sont répertoriés dans le tableau suivant. Notez que vous n’avez pas besoin de télécharger ces packages directement si vous utilisez les étapes décrites dans le [guides d’installation](sql-server-linux-setup.md).

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Package RPM | 14.0.100.187-1 | [package de moteur 14.0.100.187-1 MSSQL-serveur](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.100.187-1.x86_64.rpm)</br>[package de haute disponibilité RPM 14.0.100.187-1 MSSQL-serveur](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.100.187-1.x86_64.rpm) | 
| Package Debian | 14.0.100.187-1 | [MSSQL-serveur 14.0.100.187-1 moteur Debian le package](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.100.187-1_amd64.deb) |

### <a name="supported-client-tools"></a>Outils clients pris en charge

| Outil | Version minimale |
|-----|-----|
| [SQL Server Management Studio (SSMS) pour Windows - version Release Candidate 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools pour Visual Studio - version Release Candidate 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Code Visual Studio](https://code.visualstudio.com) avec la [mssql extension](https://aka.ms/mssql-marketplace) | Plus récente (0,2) |

> [!NOTE] 
> Les versions de SQL Server Management Studio et SQL Server Data Tools spécifiées ci-dessus sont des candidats de mise en production, par conséquent, ne pas recommandé pour une utilisation en production.

### <a name="unsupported-features-and-services"></a>Services et les fonctionnalités non prises en charge
Les fonctionnalités et les services suivants ne sont pas disponibles sur Linux pour l’instant. La prise en charge de ces fonctionnalités est plus activé lors de la cadence mensuelle de mises à jour le programme d’évaluation.

| Domaine | Fonctionnalité non prise en charge ou un service |
|-----|-----|
| **Moteur de base de données** | Recherche en texte intégral |
| &nbsp; | Réplication |
| &nbsp; | Étendre la base de données |
| &nbsp; | Polybase |
| &nbsp; | Requête distribuée |
| &nbsp; | Procédures système stockées étendues (XP_CMDSHELL, etc.). |
| &nbsp; | Filetable |
| &nbsp; | Définir des assemblys CLR avec l’autorisation EXTERNAL_ACCESS ou UNSAFE |
| **Haute disponibilité** | Groupes de disponibilité AlwaysOn |
| &nbsp; | Mise en miroir de bases de données  |
| **Sécurité** | Authentification Active Directory |
| &nbsp; | Authentification Windows |
| &nbsp; | Gestion de clés extensible |
| &nbsp; | Utilisation du certificat fourni par l’utilisateur pour les protocoles SSL ou TLS |
| **Services** | SQL Server Agent |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problèmes connus
Les sections suivantes décrivent les problèmes connus avec cette version de SQL Server 2017 CTP 1.1 sur Linux.

#### <a name="general"></a>Général
- La longueur du nom d’hôte sur lequel SQL Server est installé a besoin pour être de 15 caractères ou moins. 

    - **Résolution**: Remplacez le nom d’hôte/etc/quelque chose de 15 caractères ou plus.

- N’exécutez pas la commande `ALTER SERVICE MASTER KEY REGENERATE`. Il existe un bogue connu qui fait que SQL Server dans un état instable. Si vous avez besoin régénérer la clé principale du Service, vous devez sauvegarder vos fichiers de base de données, désinstallez puis réinstallez SQL Server et restaurer les fichiers de base de données à nouveau.

- Nom de ressource pour la ressource SQL a été remplacée par ocf:sql:fci à ocf:mssql:fci. Plus d’informations sur la configuration d’un cluster de basculement de disque partagé que vous pouvez trouver [ici](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-shared-disk-cluster-red-hat-7-configure).

- Définition manuelle de l’heure système vers l’arrière dans le temps entraîne SQL Server arrêter la mise à jour de l’heure système interne dans SQL Server.

    - **Résolution**: redémarrez SQL Server.

- Certains noms de fuseau horaire dans Linux ne sont pas exactement aux noms de fuseau horaire Windows.

    - **Résolution**: utiliser des noms de fuseau horaire à partir de la colonne TZID le ' mappage pour : table de section de Windows sur le [page de documentation Unicode.org](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- Moteur SQL Server attend des lignes dans les fichiers texte à se terminer avec CRLF (Windows-style ligne mise en forme).

- Seules les installations d’instance unique sont pris en charge.

    - **Résolution**: Si vous souhaitez disposer de plusieurs instances sur un hôte donné, envisagez d’utiliser des machines virtuelles ou des conteneurs Docker. 

- Tous les fichiers journaux et les journaux d’erreurs sont encodés en UTF-16.

- Gestionnaire de Configuration SQL Server ne peut pas se connecter à SQL Server sur Linux.

- **CREATE ASSEMBLY** ne fonctionne pas lorsque vous tentez d’utiliser un fichier. Utilisez le **FROM \<bits\> ** méthode à la place pour l’instant. 

#### <a name="databases"></a>Bases de données
- Modification des emplacements de fichiers de données et les journaux de TempDB n’est pas pris en charge.

- Impossible de déplacer les bases de données système avec l’utilitaire mssql-conf.

- Lorsque vous restaurez une base de données a été sauvegardée sur SQL Server sur Windows, vous devez utiliser le **WITH MOVE** clause dans l’instruction Transact-SQL.

- Nécessiter que le service Microsoft Distributed Transaction Coordinator les transactions distribuées ne sont pas pris en charge sur SQL Server est en cours d’exécution sur Linux. SQL Server vers SQL Server, les transactions distribuées sont prises en charge.

#### <a name="in-memory-oltp"></a>OLTP en mémoire
- Bases de données OLTP en mémoire peuvent être créés uniquement dans le répertoire /var/opt/mssql. Ces bases de données doivent également avoir le « C:\" notation visés. Pour plus d’informations, visitez le [In-memory OLTP rubrique](sql-server-linux-performance-get-started.md#use-in-memory-oltp).  

#### <a name="sqlpackage"></a>SqlPackage
- À l’aide de SqlPackage, vous devez spécifier un chemin d’accès absolu pour les fichiers. À l’aide de chemins d’accès relatifs mappera les fichiers sous la « / tmp/sqlpackage. \<code \> /système/system32 « dossier. 

    - **Résolution**: utiliser des chemins d’accès absolus.

- SqlPackage indique l’emplacement des fichiers avec un « C:\\« préfixe.

#### <a name="sqlcmdbcp--odbc"></a>SQLCMD/BCP et ODBC 
- Outils de ligne de commande SQL Server (mssql-tools) et le pilote ODBC (msodbcsql) dépend d’un gestionnaire de pilotes unixODBC de personnalisé. Cela provoque des conflits si vous disposez d’un gestionnaire de pilotes unixODBC de précédemment installé. 

    - **Résolution**: sur Ubuntu, le conflit sera résolu automatiquement. Lorsque vous y êtes invité si vous souhaitez désinstaller le Gestionnaire de pilotes unixODBC existant, tapez « o » et poursuivre l’installation. Sur Red Hat, vous devrez supprimer manuellement les Gestionnaire de pilotes unixODBC existant à l’aide de `yum remove unixODBC`. Nous travaillons sur la résolution de cette limitation pour RHEL et SUSE et que vous doit avoir une mise à jour pour vous plus rapidement.  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Les limitations suivantes s’appliquent à SSMS sur Windows connectés à SQL Server sur Linux.

- Plans de maintenance ne sont pas pris en charge.

- L’entrepôt de données de gestion (MDW) et le collecteur de données dans SSMS n’est pas pris en charge. 

- Les composants SSMS UI disposant de l’authentification Windows ou les options du journal des événements Windows ne fonctionnent pas avec Linux. Vous pouvez toujours utiliser ces fonctionnalités avec d’autres options, telles que des connexions SQL. 

- L’Agent SQL Server n’est pas encore pris en charge. Par conséquent, les fonctionnalités de l’Agent SQL Server dans SSMS ne fonctionnent pas sur Linux pour le moment.

- L’Explorateur de fichiers est limité à la « C:\\« étendue, qui est résolue en/var/opt/mssql/sur Linux. Pour utiliser les autres chemins d’accès, générer des scripts de l’opération de l’interface utilisateur et remplacez le lecteur C:\\ chemins d’accès des chemins d’accès de Linux. Puis exécutez manuellement le script dans SSMS.

v

![Graphique de barre de séparation](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp10-ctp-10-november-2016"></a><a id="ctp10">CTP 1.0 (novembre 2016)
La version du moteur SQL Server pour cette version est 14.0.1.246.

### <a name="supported-platforms"></a>Plateformes prises en charge 

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Bureau, serveur et station de travail Red Hat Enterprise Linux 7.2 | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| Ubuntu 16.04LTS | EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Moteur docker 1.8 + sur Windows, Mac ou Linux | Néant | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Vous devez au moins 3,25 Go de mémoire pour exécuter SQL Server sur Linux.
> Moteur SQL Server n’a pas été testé jusqu'à 256 Go de mémoire pour l’instant.

### <a name="package-details"></a>Détails du package
Détails du package et les emplacements de téléchargement pour les packages RPM et Debian sont répertoriés dans le tableau suivant. Notez que vous n’avez pas besoin de télécharger ces packages directement si vous utilisez les étapes décrites dans le [guides d’installation](sql-server-linux-setup.md).

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Package RPM | 14.0.1.246-6 | [package de moteur 14.0.1.246-6 MSSQL-serveur](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.1.246-6.x86_64.rpm)</br>[package de haute disponibilité RPM 14.0.1.246-6 MSSQL-serveur](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.1.246-6.x86_64.rpm) | 
| Package Debian | 14.0.1.246-6 | [MSSQL-serveur 14.0.1.246-6 moteur Debian le package](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.1.246-6_amd64.deb) |

### <a name="supported-client-tools"></a>Outils clients pris en charge

| Outil | Version minimale |
|-----|-----|
| [SQL Server Management Studio (SSMS) pour Windows - version Release Candidate 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools pour Visual Studio - version Release Candidate 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Code Visual Studio](https://code.visualstudio.com) avec la [mssql extension](https://aka.ms/mssql-marketplace) | Plus récente (0.1.5) |

> [!NOTE] 
> Les versions de SQL Server Management Studio et SQL Server Data Tools spécifiées ci-dessus sont des candidats de mise en production, par conséquent, ne pas recommandé pour une utilisation en production.

### <a name="unsupported-features-and-services"></a>Services et les fonctionnalités non prises en charge
Les fonctionnalités et les services suivants ne sont pas disponibles sur Linux pour l’instant. La prise en charge de ces fonctionnalités est plus activé lors de la cadence mensuelle de mises à jour le programme d’évaluation.

| Domaine | Fonctionnalité non prise en charge ou un service |
|-----|-----|
| **Moteur de base de données** | Recherche en texte intégral |
| &nbsp; | Réplication |
| &nbsp; | Étendre la base de données |
| &nbsp; | Polybase |
| &nbsp; | Requête distribuée |
| &nbsp; | Procédures système stockées étendues (XP_CMDSHELL, etc.). |
| &nbsp; | Filetable |
| &nbsp; | Définir des assemblys CLR avec l’autorisation EXTERNAL_ACCESS ou UNSAFE |
| **Haute disponibilité** | Groupes de disponibilité AlwaysOn |
| &nbsp; | Mise en miroir de bases de données  |
| **Sécurité** | Authentification Active Directory |
| &nbsp; | Authentification Windows |
| &nbsp; | Gestion de clés extensible |
| &nbsp; | Utilisation du certificat fourni par l’utilisateur pour les protocoles SSL ou TLS |
| **Services** | SQL Server Agent |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problèmes connus
Les sections suivantes décrivent les problèmes connus avec cette version de SQL Server 2017 CTP1 sur Linux.

#### <a name="general"></a>Général
- La longueur du nom d’hôte sur lequel SQL Server est installé a besoin pour être de 15 caractères ou moins. 

    - **Résolution**: Remplacez le nom d’hôte/etc/quelque chose de 15 caractères ou plus.

- Définition manuelle de l’heure système vers l’arrière dans le temps entraîne SQL Server arrêter la mise à jour de l’heure système interne dans SQL Server.

    - **Résolution**: redémarrez SQL Server.

- Certains noms de fuseau horaire dans Linux ne sont pas exactement aux noms de fuseau horaire Windows.

    - **Résolution**: utiliser des noms de fuseau horaire à partir de la colonne TZID le ' mappage pour : table de section de Windows sur le [page de documentation Unicode.org](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- Moteur SQL Server attend des lignes dans les fichiers texte à se terminer avec CRLF (Windows-style ligne mise en forme).

- Seules les installations d’instance unique sont pris en charge.

    - **Résolution**: Si vous souhaitez disposer de plusieurs instances sur un hôte donné, envisagez d’utiliser des machines virtuelles ou des conteneurs Docker. 

- Tous les fichiers journaux et les journaux d’erreurs sont encodés en UTF-16.

- Gestionnaire de Configuration SQL Server ne peut pas se connecter à SQL Server sur Linux.

- **CREATE ASSEMBLY** ne fonctionne pas lorsque vous tentez d’utiliser un fichier. Utilisez le **FROM \<bits\> ** méthode à la place pour l’instant.

#### <a name="databases"></a>Bases de données
- Modification des emplacements de fichiers de données et les journaux de TempDB n’est pas pris en charge.

- Impossible de déplacer les bases de données système avec l’utilitaire mssql-conf.

- Lorsque vous restaurez une base de données a été sauvegardée sur SQL Server sur Windows, vous devez utiliser le **WITH MOVE** clause dans l’instruction Transact-SQL.

- Nécessiter que le service Microsoft Distributed Transaction Coordinator les transactions distribuées ne sont pas pris en charge sur SQL Server est en cours d’exécution sur Linux. SQL Server vers SQL Server, les transactions distribuées sont prises en charge.

#### <a name="in-memory-oltp"></a>OLTP en mémoire
- Bases de données OLTP en mémoire peuvent être créés uniquement dans le répertoire /var/opt/mssql. Ces bases de données doivent également avoir le « C:\\« notation de référencé. Pour plus d’informations, visitez le [In-memory OLTP rubrique](sql-server-linux-performance-get-started.md#use-in-memory-oltp).  

#### <a name="sqlpackage"></a>SqlPackage
- À l’aide de SqlPackage nécessite de spécifier un chemin d’accès absolu pour les fichiers. À l’aide de chemins d’accès relatifs mappera les fichiers sous la « / tmp/sqlpackage. \<code \> /système/system32 « dossier. 

    - **Résolution**: utiliser des chemins d’accès absolus.

- SqlPackage indique l’emplacement des fichiers avec un « C:\\« préfixe.

#### <a name="sqlcmdbcp--odbc"></a>SQLCMD/BCP et ODBC 
- Outils de ligne de commande SQL Server (mssql-tools) et le pilote ODBC (msodbcsql) dépend d’un gestionnaire de pilotes unixODBC de personnalisé. Cela provoque des conflits si vous disposez d’un gestionnaire de pilotes unixODBC de précédemment installé. 

    - **Résolution**: sur Ubuntu, le conflit sera résolu automatiquement. Lorsque vous y êtes invité si vous souhaitez désinstaller le Gestionnaire de pilotes unixODBC existant, tapez « o » et poursuivre l’installation. Sur Red Hat, vous devrez supprimer manuellement les Gestionnaire de pilotes unixODBC existant à l’aide de `yum remove unixODBC`. Nous travaillons sur la résolution de cette limitation pour RHEL et SUSE et que vous doit avoir une mise à jour pour vous plus rapidement.  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Les limitations suivantes s’appliquent à SSMS sur Windows connectés à SQL Server sur Linux.

- Plans de maintenance ne sont pas pris en charge.

- L’entrepôt de données de gestion (MDW) et le collecteur de données dans SSMS n’est pas pris en charge. 

- Les composants SSMS UI disposant de l’authentification Windows ou les options du journal des événements Windows ne fonctionnent pas avec Linux. Vous pouvez toujours utiliser ces fonctionnalités avec d’autres options, telles que des connexions SQL. 

- L’Agent SQL Server n’est pas encore pris en charge. Par conséquent, les fonctionnalités de l’Agent SQL Server dans SSMS ne fonctionnent pas sur Linux pour le moment.

- L’Explorateur de fichiers est limité à la « C:\\« étendue, qui est résolue en/var/opt/mssql/sur Linux. Pour utiliser les autres chemins d’accès, générer des scripts de l’opération de l’interface utilisateur et remplacez le lecteur C:\\ chemins d’accès des chemins d’accès de Linux. Puis exécutez manuellement le script dans SSMS.

### <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez les didacticiels de démarrage rapide suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

