---
title: Notes de publication pour 2017 de SQL Server sur Linux | Documents Microsoft
description: "Cette rubrique contient les notes de publication et les fonctionnalités prises en charge pour SQL Server 2017 fonctionnant sous Linux. Les notes de publication sont incluses dans la version la plus récente et plusieurs versions précédentes."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 11/28/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.workload: Active
ms.openlocfilehash: f625cbf53c25dd097efb6619a47069be7873320f
ms.sourcegitcommit: d122a41cc953ba3e269c8709a18aa84f7c17982c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2017
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Notes de publication pour 2017 de SQL Server sur Linux

Les notes de publication suivantes s’appliquent à SQL Server 2017 s'exécutant sous Linux. La rubrique ci-dessous est divisée en sections pour chaque version. La version GA a une prise en charge détaillée et les problèmes connus sont répertoriés. Chaque version de mise à jour Cumulative (CU) a un lien vers une rubrique d’aide qui décrit les modifications du CU ainsi que des liens vers les téléchargements de packages Linux.

## <a name="supported-platforms"></a>Plateformes prises en charge

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 ou 7.4 Workstation, Server, et Desktop | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| Serveur Linux SUSE Enterprise SP2 v12 | EXT4 | [Guide d’installation](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Moteur docker 1.8+ sur Windows, Mac ou Linux | Néant | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!TIP]
> Examinez le [prérequis système](sql-server-linux-setup.md#system) pour SQL Server sur Linux.

## <a name="supported-client-tools"></a>Outils clients pris en charge

| Outil | Version minimale |
|-----|-----|
| [SQL Server Management Studio (SSMS) pour Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools pour Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Code Visual Studio](https://code.visualstudio.com) avec la [mssql extension](https://aka.ms/mssql-marketplace) | dernière |

## <a name="release-history"></a>Historique des versions

Le tableau suivant répertorie l’historique des versions pour SQL Server 2017.

| Version | Version | Date de publication |
|-----|-----|-----|
| [CU2](#CU2) | 14.0.3008.27 | 11-2017 |
| [CU1](#CU1) | 14.0.3006.16 | 10-2017 |
| [DISPONIBILITÉ GÉNÉRALE](#GA) | 14.0.1000.169 | 10-2017 |

## <a name="how-to-install-cumulative-updates"></a>Comment installer les mises à jour cumulatives

Si vous avez configuré le référentiel de mise à jour cumulative, vous obtiendrez la mise à jour cumulative la plus récente de packages SQL Server lorsque vous effectuerez de nouvelles installations. Le référentiel de mise à jour cumulative est la valeur par défaut pour tous les articles concernant l’installation de package pour SQL Server sur Linux. Pour plus d’informations sur la configuration du référentiel, consultez [Source référentiels](sql-server-linux-setup.md#repositories).

Si vous mettez à jour des packages SQL Server existants, exécutez la commande de mise à jour appropriée pour chaque package obtenir la dernière mise à jour cumulative. Pour obtenir des instructions de mise à jour spécifique pour chaque package, consultez les guides d’installation suivants :

- [Installer le package SQL Server](sql-server-linux-setup.md#upgrade)
- [Installer le package de la recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
- [Installer le package de l’Agent SQL Server](sql-server-linux-setup-sql-agent.md)
- [Installer SQL Server Integration Services](sql-server-linux-setup-ssis.md)

## <A id="CU2"></a>Mise à jour cumulative 2 (2017 novembre)

Il s’agit de la version de Cumulative Update 2 (CU2) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3008.27. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [https://support.microsoft.com/help/4052574](https://support.microsoft.com/help/4052574).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Rpm de Red Hat | 14.0.3008.27-1 | [Moteur le package RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3008.27-1 | [package RPM du moteur de serveur MSSQL](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Package de Debian Ubuntu 16.04 | 14.0.3008.27-1 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <A id="CU1"></a>Mise à jour cumulative 1 (octobre 2017)

Il s’agit de la version à jour Cumulative 1 (CU1) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3006.16. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [https://support.microsoft.com/help/4038634](https://support.microsoft.com/help/4038634).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Rpm de Red Hat | 14.0.3006.16-3 | [Moteur le package RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3006.16-3 | [package RPM du moteur de serveur MSSQL](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Package de Debian Ubuntu 16.04 | 14.0.3006.16-3 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a>GA (octobre 2017)

Il s’agit de la version de disponibilité générale de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.1000.169.

### <a name="package-details"></a>Détails du package

Les détails du package et les emplacements de téléchargement pour les packages RPM et Debian sont répertoriés dans le tableau suivant. Notez que vous n’avez pas besoin de télécharger ces packages directement si vous utilisez les étapes des guides d’installation suivants :

- [Installer le package SQL Server](sql-server-linux-setup.md)
- [Installer le package de la recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
- [Installer le package de l’Agent SQL Server](sql-server-linux-setup-sql-agent.md)
- [Installer SQL Server Integration Services](sql-server-linux-setup-ssis.md)

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Rpm de Red Hat | 14.0.1000.169-2 | [Package RPM du Moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de SQL Server Agent](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.1000.169-2 | [Package RPM du moteur de serveur MSSQL](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de SQL Server Agent](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Package de Debian Ubuntu 16.04 | 14.0.1000.169-2 | [Package de moteur Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

### <a name="Unsupported"></a>Services et fonctionnalités non prises en charge

Les fonctionnalités et les services suivants ne sont pas disponibles sur Linux pour l’instant. La prise en charge de ces fonctionnalités sera activée au fil du temps.

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

Les sections suivantes décrivent les problèmes connus avec la version de la disponibilité générale (GA) de SQL Server 2017 sous Linux.

#### <a name="general"></a>Général

- Les mises à niveau vers la version GA de SQL Server 2017 sont pris en charge uniquement à partir de CTP 2.1 ou version ultérieure. 

- Le nom d’hôte de l'ordinateur sur lequel SQL Server est installé doit avoir 15 caractères ou moins. 

    - **Résolution**: Remplacez le nom d’hôte dans /etc/hostname avec un nom de 15 caractères ou moins.

- Reculer manuellement l’heure système entraîne l'arrêt de la mise à jour de l’heure système interne dans SQL Server.

    - **Résolution**: redémarrez SQL Server.

- Seules les installations d’instance unique sont prises en charge.

    - **Résolution**: Si vous souhaitez disposer de plusieurs instances sur un hôte donné, envisagez d’utiliser des machines virtuelles ou des conteneurs Docker. 

- Le gestionnaire de Configuration SQL Server ne peut pas se connecter à SQL Server sur Linux.

- La langue par défaut de la connexion **sa** est l’anglais.

    - **Résolution**: modifier la langue de la connexion **sa** avec l'instruction **ALTER LOGIN** 

#### <a name="databases"></a>Bases de données

- Impossible de déplacer la base de données master avec l’utilitaire mssql-conf. Les autres bases de données système peuvent être déplacées avec mssql-conf.

- Lorsque vous restaurez une base de données qui a été sauvegardée sur SQL Server sur Windows, vous devez utiliser la clause **WITH MOVE** dans l’instruction Transact-SQL.

- Les transactions distribuées qui nécessitent le service Microsoft Distributed Transaction Coordinator ne sont pas pris en charge sur SQL Server sous Linux. Les serveurs liés vers SQL Server sont pris en charge sauf si des transactions distribuées sont utilisées.

- Certains algorithmes (suites de chiffrement) et de sécurité TLS (Transport Layer) ne fonctionnent pas correctement avec SQL Server sur Linux. Cela entraîne des échecs lorsque vous tentez de vous connecter à SQL Server, ainsi que des problèmes pour établir des connexions entre les réplicas des groupes de disponibilité.

   - **Résolution**: modifier le script de configuration **mssql.conf** de SQL Server sur Linux pour désactiver les suites de chiffrement problématiques, en procédant comme suit :

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

- Les bases de données SQL Server 2014 sous Windows qui utilisent OLTP en mémoire ne peuvent pas être restaurées sur SQL 2017 sous Linux. Pour restaurer une base de données SQL Server 2014 qui utilise l’OLTP en mémoire, tout d’abord mettre à niveau les bases de données vers SQL Server 2016 ou 2017 avec un serveur SQL sous Windows avant de les déplacer vers SQL Server sous Linux via la sauvegarde/restauration ou le détachement et attachement.

- L'autorisation de l’utilisateur **ADMINISTER BULK OPERATIONS** n’est pas pris en charge sous Linux pour l’instant.

#### <a name="networking"></a>Réseau

Les fonctionnalités qui impliquent des connexions TCP sortantes à partir du processus sqlservr, tels que des serveurs liés ou des groupes de disponibilité peuvent ne pas fonctionnent si les deux conditions suivantes sont remplies :

1. Le serveur cible est spécifié comme un nom d’hôte et non une adresse IP.

1. L’instance source a IPv6 désactivée dans le noyau. Pour vérifier si votre système a IPv6 activé dans le noyau, les tests suivants doivent être validés :

   - `cat /proc/cmdline`Imprime la ligne de commande de démarrage du noyau actuel. La sortie ne doit pas contenir `ipv6.disable=1`.
   - Le répertoire /proc/sys/net/ipv6/ doit exister.
   - Un programme C qui appelle `socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)` doit fonctionner - syscall doit retourner un fd ! = -1 et n’échoue pas avec EAFNOSUPPORT.

L’erreur exacte dépend de la fonctionnalité. Pour les serveurs liés, cela se manifeste en tant qu’une erreur de délai d’attente de connexion. Pour les groupes de disponibilité, le DDL `ALTER AVAILABILITY GROUP JOIN` sur le serveur secondaire échoue après 5 minutes avec une erreur de délai d’attente de téléchargement de la configuration.

Pour contourner ce problème, effectuez l’une des opérations suivantes :

1. Utiliser des adresses IP au lieu des noms d’hôtes pour spécifier la cible de la connexion TCP.

1. Activez le protocole IPv6 dans le noyau en supprimant `ipv6.disable=1` à partir de la ligne de commande de démarrage. La façon de procéder dépend de la distribution de Linux et le chargeur de démarrage, tels que grub. Si vous ne souhaitez pas que IPv6 soit désactivée, vous pouvez le désactiver en définissant `net.ipv6.conf.all.disable_ipv6 = 1` dans la configuration `sysctl` (par exemple, `/etc/sysctl.conf`). Cela empêchera la carte réseau du système d'obtenir une adresse IPv6, mais permet le fonctionnement de fonctionnalités de sqlservr.

#### <a name="network-file-system-nfs"></a>Network File System (NFS)
Si vous utilisez les partages distants **Network File System (NFS)** en production, notez les exigences de prise en charge suivantes :

- Utiliser la version NFS **4.2 ou ultérieure**. Les versions antérieures de NFS ne gèrent pas les fonctionnalités requises, telles que fallocate et la création de fichier sparse, courantes avec les systèmes de fichiers modernes.
- Positionnez uniquement les répertoires **/var/opt/mssql**  sur le montage NFS. Les autres fichiers, tels que les fichiers binaires du système SQL Server, ne sont pas pris en charge.
- Assurez-vous que les clients NFS utilisent l’option 'nolock' lorsque qu'ils montent le partage distant.

#### <a name="localization"></a>Localisation

- Si vos paramètres régionaux ne sont pas anglais (fr_FR) lors de l’installation, vous devez utiliser l’encodage UTF-8 dans votre session d’interpréteur de commandes/terminal. Si vous utilisez l’encodage ASCII, vous pouvez voir une erreur comme ci-après :

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Si vous ne pouvez pas utiliser le codage UTF-8, exécutez le programme d’installation à l’aide de la variable d’environnement MSSQL_LCID pour spécifier votre choix de la langue.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- Lors de l’exécution du programme d’installation mssql-conf et d'une installation non anglaise de SQL Server, des caractères incorrects étendus sont affichés après le texte localisé, « Configuration de SQL Server... ». Ou, pour les installations basées sur des jeux non Latin, le texte peut être totalement manquant. La phrase manquante doit afficher la chaîne localisée suivante : « le PID de licence a été traité correctement.  La nouvelle édition est [\<nom\> édition] ». Cette chaîne est affichée à titre d’information uniquement et la prochaine mise à jour Cumulative SQL Server résoudra ce problème pour toutes les langues. Cela n’affecte en aucune façon la réussite de l’installation de SQL Server. 

#### <a name="full-text-search"></a>Recherche en texte intégral

- Tous les filtres sont pas disponibles avec cette version, notamment les filtres pour les documents Office. Pour obtenir la liste de filtres pris en charge, consultez [installer de recherche de texte intégral SQL Server sur Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a id="ssis"></a> SQL Server Integration Services (SSIS)

- Le package **mssql-server-is** n’est pas pris en charge sur SUSE dans cette version. Il est actuellement pris en charge sur Ubuntu sur Red Hat Enterprise Linux (RHEL).

- Avec SSIS sur Linux CTP 2.1 Refresh et versions ultérieures, les packages SSIS permettent les connexions ODBC sur Linux. Cette fonctionnalité a été testée avec les pilotes ODBC MySQL sur le serveur SQL Server, mais elle est également prévue pour fonctionner avec n’importe quel pilote ODBC Unicode qui respecte la spécification ODBC. Au moment du design, vous pouvez fournir une source de données ou une chaîne de connexion pour se connecter aux données ODBC ; Vous pouvez également utiliser l’authentification Windows. Pour plus d’informations, consultez la [blog de l’annonce prise en charge d’ODBC sur Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- Les fonctionnalités suivantes ne sont pas pris en charge dans cette version lorsque vous exécutez des packages SSIS sur Linux :
  - Base de données du catalogue SSIS
  - Exécution de package planifié par l’Agent SQL
  - Authentification Windows
  - Composants tiers
  - Capture de données modifiées (CDC)
  - SSIS Scale Out
  - Azure Feature Pack pour SSIS
  - Prise en charge de Hadoop et HDFS
  - Microsoft Connector pour SAP BW

Pour obtenir la liste de composants SSIS intégrés qui sont actuellement pas en charge, ou qui sont pris en charge avec des limitations, consultez [Limitations et problèmes connus pour SSIS sur Linux](sql-server-linux-ssis-known-issues.md#components).

Pour plus d’informations sur SSIS sur Linux, consultez les articles suivants :
-   [Billet de blog annonçant la prise en charge de SSIS sur Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Installer SQL Server Integration Services (SSIS) sur Linux](sql-server-linux-setup-ssis.md)
-   [Extraire, transformer et charger des données sur Linux avec SSIS](sql-server-linux-migrate-ssis.md)

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)

Les limitations suivantes s’appliquent à SSMS sur Windows connectés à SQL Server sur Linux.

- Les plans de maintenance ne sont pas pris en charge.

- L’entrepôt de données de gestion (MDW) et la collecte de données (Data Collector) dans SSMS ne sont pas pris en charge. 

- Les composants de SSMS qui utilisent l’authentification Windows ou les options du journal des événements Windows ne fonctionnent pas avec Linux. Vous pouvez toujours utiliser ces fonctionnalités avec d’autres options, telles que des connexions SQL. 

- Impossible de modifier le nombre de fichiers journaux à conserver.

### <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez les didacticiels de démarrage rapide suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-ubuntu.md)
