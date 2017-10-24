---
title: Notes de publication pour 2017 du serveur SQL sur Linux | Documents Microsoft
description: "Cette rubrique contient les notes de publication et les fonctionnalités prises en charge pour SQL Server 2017 est en cours d’exécution sur Linux. Notes de publication sont inclus dans la version la plus récente et plusieurs versions précédentes."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/04/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.translationtype: MT
ms.sourcegitcommit: 2f28400200105e8e63f787cbcda58c183ba00da5
ms.openlocfilehash: f9315ca5b46a0dc45a0f8171fa6eea67cd2f4337
ms.contentlocale: fr-fr
ms.lasthandoff: 10/18/2017

---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Notes de publication pour 2017 du serveur SQL sur Linux

Les notes suivantes s’appliquent à SQL Server 2017 est en cours d’exécution sur Linux. Cette version prend en charge la plupart des fonctionnalités du moteur de base de données SQL Server pour Linux. La rubrique ci-dessous est divisée en sections pour chaque version, en commençant par la plus récente générale (GA) version et les versions précédentes de deux. Consultez les informations contenues dans chaque section pour les plateformes prises en charge, les outils, les fonctionnalités et les problèmes connus.

Le tableau suivant répertorie l’historique de publication pour SQL Server 2017.

| Version | Version | Date de publication |
|-----|-----|-----|
| [DISPONIBILITÉ GÉNÉRALE](#GA) | 14.0.1000.169 | 10-2017 |
| [RC2](#RC2) | 14.0.900.75 | 8-2017 |
| [RC1](#RC1) | 14.0.800.90 | 7-2017 |
| CTP 2.1 | 14.0.600.250 | 5-2017 |
| CTP 2.0 | 14.0.500.272 | 4-2017 |
| CTP 1.4 | 14.0.405.198 | 3-2017 |
| CTP 1.3 | 14.0.304.138 | 2-2017 |
| CTP 1.2 | 14.0.200.24 | 1-2017 |
| CTP 1.1 | 14.0.100.187 | 12-2016 |
| CTP 1.0 | 14.0.1.246 | 11-2016 |

## <a id="GA"></a>GA (octobre 2017)

Il s’agit de la version de la disponibilité générale de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.1000.169.

### <a name="supported-platforms"></a>Plateformes prises en charge

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Bureau, serveur et station de travail Red Hat Enterprise Linux 7.3 ou 7.4 | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| Serveur Linux SUSE Enterprise SP2 v12 | EXT4 | [Guide d’installation](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Moteur docker 1.8 + sur Windows, Mac ou Linux | Néant | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!NOTE]
> Vous devez au moins 3,25 Go de mémoire pour exécuter SQL Server sur Linux.

### <a name="package-details"></a>Détails du package

Détails du package et les emplacements de téléchargement pour les packages RPM et Debian sont répertoriés dans le tableau suivant. Notez que vous n’avez pas besoin de télécharger ces packages directement si vous utilisez les étapes dans les guides d’installation suivantes :

- [Installer le package SQL Server](sql-server-linux-setup.md)
- [Installer le package de la recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
- [Installer le package de l’Agent SQL Server](sql-server-linux-setup-sql-agent.md)

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Rpm de Red Hat | 14.0.1000.169-2 | [Moteur le package RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.1000.169-2 | [package RPM du moteur de serveur MSSQL](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Package de Debian Ubuntu 16.04 | 14.0.1000.169-2 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[Ensemble de SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

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
| &nbsp; | Filetable, FILESTREAM |
| &nbsp; | Définir des assemblys CLR avec l’autorisation EXTERNAL_ACCESS ou UNSAFE |
| &nbsp; | Extension du pool de mémoires tampons |
| **Agent SQL Server** |  Sous-systèmes : CmdExec, PowerShell, lecteur de file d’attente, SSIS, SSAS, SSRS |
| &nbsp; | Alertes |
| &nbsp; | l'Agent de lecture du journal ; |
| &nbsp; | Capture de données modifiées |
| &nbsp; | Sauvegarde managée |
| **Haute disponibilité** | Mise en miroir de bases de données  |
| **Sécurité** | Gestion de clés extensible |
| &nbsp; | Authentification d’Active Directory pour les serveurs liés | 
| &nbsp; | Authentification d’Active Directory pour les groupes de disponibilité (groupes de disponibilité) | 
| &nbsp; | outils tiers AD 3e (Centrify, Vintela, Powerbroker) | 
| **Services** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus avec la version de la disponibilité de genres (GA) de SQL Server 2017 sur Linux.

#### <a name="general"></a>Général

- Mises à niveau vers la version GA de SQL Server 2017 sont pris en charge uniquement à partir de CTP 2.1 ou version ultérieure. 

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
      tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

         >[!NOTE]
         >In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.  

      1. Redémarrez SQL Server avec la commande suivante.

      ```bash
      sudo systemctl restart mssql-server
      ```

- Bases de données SQL Server 2014 sur Windows qui utilisent OLTP en mémoire ne peut pas être restaurées sur 2017 du serveur SQL sur Linux. Pour restaurer une base de données SQL Server 2014 qui utilise l’OLTP en mémoire, tout d’abord mettre à niveau les bases de données vers SQL Server 2016 ou 2017 du serveur SQL sur Windows avant de les déplacer vers SQL Server sur Linux via la sauvegarde/restauration ou de détachement et d’attachement.

- Autorisation de l’utilisateur **ADMINISTER BULK OPERATIONS** n’est pas pris en charge sous Linux pour l’instant.

#### <a name="networking"></a>Réseau

Fonctionnalités qui impliquent des connexions TCP sortantes à partir du processus sqlservr, tels que des serveurs liés ou des groupes de disponibilité peut ne pas fonctionnent si les deux conditions suivantes sont remplies :

1. Le serveur cible est spécifié comme un nom d’hôte et non une adresse IP.

1. L’instance source a IPv6 désactivée dans le noyau. Pour vérifier si votre système IPv6 est activé dans le noyau, tous les tests suivants doivent passer :

   - `cat /proc/cmdline`Imprime la ligne de commande de démarrage du noyau actuel. La sortie ne doit pas contenir `ipv6.disable=1`.
   - La table/proc/sys/net/ipv6/répertoire doit exister.
   - Un programme C qui appelle `socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)` doit réussir - la syscall doit retourner un fd ! = -1 et n’échoue pas avec EAFNOSUPPORT.

L’erreur exacte dépend de la fonctionnalité. Pour les serveurs liés, cela se manifeste en tant qu’une erreur de délai d’attente de connexion. Pour les groupes de disponibilité, le `ALTER AVAILABILITY GROUP JOIN` DDL sur le serveur secondaire échoue après 5 minutes avec une erreur de délai d’attente de configuration de téléchargement.

Pour contourner ce problème, effectuez l’une des opérations suivantes :

1. Utiliser des adresses IP au lieu des noms d’hôtes pour spécifier la cible de la connexion TCP.

1. Activation du protocole IPv6 dans le noyau en supprimant `ipv6.disable=1` à partir de la ligne de commande de démarrage. La façon de procéder dépend de la distribution de Linux et le chargeur de démarrage, tels que grub. Si vous ne souhaitez pas IPv6 doit être désactivée, vous pouvez le désactiver en définissant `net.ipv6.conf.all.disable_ipv6 = 1` dans les `sysctl` configuration (par exemple, `/etc/sysctl.conf`). Cela sera toujours empêcher l’obtention d’une adresse IPv6 de carte de réseau du système, mais vous pouvez autoriser les fonctionnement de fonctionnalités sqlservr.

#### <a name="network-file-system-nfs"></a>Système de fichiers réseau (NFS)
Si vous utilisez **système NFS (Network File)** partages distants en production, notez les exigences de prise en charge suivantes :

- Utiliser la version NFS **4.2 ou ultérieure**. Les versions antérieures de NFS ne gèrent pas les fonctionnalités requises, telles que fallocate et la création du fichier partiellement alloué, commune aux systèmes de fichiers modernes.
- Recherchez uniquement les **/var/opt/mssql** répertoires sur le montage NFS. Autres fichiers, tels que les fichiers binaires du système SQL Server, ne sont pas pris en charge.
- Assurez-vous que les clients NFS utilisent l’option 'nolock' lorsque vous montez le partage distant.

#### <a name="localization"></a>Localisation

- Si vos paramètres régionaux n’est pas anglais (fr_FR) lors de l’installation, vous devez utiliser l’encodage UTF-8 dans votre session d’interpréteur de commandes/terminal. Si vous utilisez l’encodage ASCII, vous pouvez voir une erreur semblable au suivant :

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Si vous ne pouvez pas utiliser le codage UTF-8, exécutez le programme d’installation à l’aide de la variable d’environnement MSSQL_LCID pour spécifier votre choix de la langue.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- Lorsque mssql-conf le programme d’installation en cours d’exécution et effectuez une installation non anglaise de SQL Server, incorrect des caractères étendus sont affichés après le texte localisé, « Configuration de SQL Server... ». Ou, pour les installations de base non Latin, la phrase peut être manquante complètement. La phrase manquante doit afficher la chaîne localisée suivante : « le PID de licence a été traité correctement.  La nouvelle édition est [<Name> édition] ». Cette chaîne est de sortie à titre d’information uniquement et prochaine mise à jour Cumulative SQL Server résoudre ce problème pour toutes les langues. Cela n’affecte pas la réussite de l’installation de SQL Server en aucune façon. 

#### <a name="full-text-search"></a>Recherche en texte intégral

- Pas de tous les filtres sont disponibles avec cette version, notamment les filtres pour les documents Office. Pour obtenir la liste de filtres pris en charge, consultez [installer de recherche de texte intégral SQL Server sur Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a id="ssis"></a> SQL Server Integration Services (SSIS)

- Le **mssql server est** package n’est pas pris en charge sur SUSE dans cette version. Il est actuellement pris en charge sur Ubuntu sur Red Hat Enterprise Linux (RHEL).

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

Pour obtenir la liste de composants SSIS intégrés qui sont actuellement pas en charge, ou qui sont pris en charge avec les limitations, consultez [Limitations et problèmes connus pour SSIS sur Linux](sql-server-linux-ssis-known-issues.md#components).

Pour plus d’informations sur SSIS sur Linux, consultez les articles suivants :
-   [Annonce de billet de blog SSIS prise en charge de Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
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

### <a name="unsupported-features-and-services"></a>Services et les fonctionnalités non prises en charge

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
   
      ```bash
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

