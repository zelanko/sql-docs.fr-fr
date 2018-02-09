---
title: Installer SQL Server 2017 sur Linux | Documents Microsoft
description: "Installer, mettre à jour et désinstaller SQL Server sur Linux. Cette rubrique couvre les scénarios en ligne, hors connexion et sans assistance."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/21/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.workload: Active
ms.openlocfilehash: 924542a970ac63df74e7bb725b4f7a171f74e95a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Aide à l’installation de SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cette rubrique explique comment installer, mettre à jour et désinstaller 2017 du serveur SQL sur Linux. SQL Server 2017 est pris en charge sur Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) et Ubuntu. Il est également disponible sous une image Docker qui peut s’exécuter sur le moteur Docker sur Linux ou Docker pour Windows/Mac.

> [!TIP]
> Pour démarrer rapidement, passez à un des Démarrages rapides pour [RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), [Ubuntu](quickstart-install-connect-ubuntu.md), ou [Docker](quickstart-install-connect-docker.md).

## <a id="supportedplatforms"></a>Plateformes prises en charge

SQL Server 2017 est pris en charge sur les plateformes Linux suivantes :

| Plateforme | Versions prises en charge | Obtenir
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 ou 7.4 | [Obtenir RHEL 7.4](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | v12 SP2 | [Obtenir SLES v12 SP2](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Obtenir Ubuntu 16.04](http://www.ubuntu.com/download/server)
| **Moteur docker** | 1.8+ | [Obtenir Docker](http://www.docker.com/products/overview)

Microsoft prend en charge le déploiement et la gestion des conteneurs de SQL Server à l’aide de OpenShift et Kubernetes.

Pour la dernière stratégie de prise en charge pour SQL Server 2017, consultez [politique de support technique pour Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a id="system"></a>Configuration système requise

SQL Server 2017 requise est la suivante pour Linux :

|||
|-----|-----|
| **Mémoire** | 2 Go |
| **Système de fichiers** | **XFS** ou **EXT4** (autres systèmes de fichiers, tel que **BTRFS**, non pris en charge) |
| **Espace disque** | 6 GO |
| **Vitesse du processeur** | 2 GHz |
| **Cœurs de processeur** | 2 cœurs |
| **Type de processeur** | x64 compatibles uniquement |

Si vous utilisez **système NFS (Network File)** partages distants en production, notez les exigences de prise en charge suivantes :

- Utiliser la version NFS **4.2 ou ultérieure**. Les versions antérieures de NFS ne gèrent pas les fonctionnalités requises, telles que fallocate et la création du fichier partiellement alloué, commune aux systèmes de fichiers modernes.
- Recherchez uniquement les **/var/opt/mssql** répertoires sur le montage NFS. Autres fichiers, tels que les fichiers binaires du système SQL Server, ne sont pas pris en charge.
- Assurez-vous que les clients NFS utilisent l’option 'nolock' lorsque vous montez le partage distant.

## <a id="platforms"></a> Installation de SQL Server

Vous pouvez installer SQL Server sur Linux à partir de la ligne de commande. Pour obtenir des instructions, consultez les Démarrages rapides suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-docker.md)
- [Approvisionner une machine virtuelle SQL dans Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

## <a id="repositories"></a>Configurer des référentiels de code source

Lorsque vous installez ou mettez à niveau de SQL Server, vous obtenez la dernière version de SQL Server 2017 à partir de votre référentiel de Microsoft. Les Démarrages rapides utilisent le **mise à jour Cumulative (CU)** référentiel. Mais vous pouvez configurer à la place la **GDR** référentiel. Pour plus d’informations sur les référentiels et comment les configurer, consultez [configurer des référentiels pour SQL Server sur Linux](sql-server-linux-change-repo.md).

> [!IMPORTANT]
> Si vous avez installé précédemment la version RC de SQL Server 2017 de CTP, vous devez supprimer le référentiel d’aperçu et inscrire une disponibilité générale un. Pour plus d’informations, consultez [configurer des référentiels pour SQL Server sur Linux](sql-server-linux-change-repo.md).

## <a id="upgrade"></a>Mettre à jour de SQL Server

Pour mettre à jour le **mssql-serveur** vers la dernière version du package, utilisez une des commandes suivantes en fonction de votre plateforme :

| Plateforme | Commandes de mise à jour de package |
|-----|-----|
| RHEL | `sudo yum update mssql-server` |
| SLES | `sudo zypper update mssql-server` |
| Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server` |

Ces commandes télécharger le package les plus récents et remplacer les fichiers binaires situés sous `/opt/mssql/`. Bases de données généré par l’utilisateur et les bases de données système ne sont pas affectés par cette opération.

## <a id="rollback"></a>Restauration SQL Server

Pour restaurer ou rétrograder SQL Server vers une version précédente, procédez comme suit :

1. Identifiez le numéro de version pour le package de SQL Server que vous souhaitez rétrograder. Pour obtenir la liste de nombres de package, consultez la [notes de publication](sql-server-linux-release-notes.md).

1. Passer à une version antérieure de SQL Server. Dans les commandes suivantes, remplacez `<version_number>` avec le numéro de version SQL Server que vous avez identifié à l’étape 1.

   | Plateforme | Commandes de mise à jour de package |
   |-----|-----|
   | RHEL | `sudo yum downgrade mssql-server-<version_number>.x86_64` |
   | SLES | `sudo zypper install --oldpackage mssql-server=<version_number>` |
   | Ubuntu | `sudo apt-get install mssql-server=<version_number>`<br/>`sudo systemctl start mssql-server` |

> [!NOTE]
> Il est uniquement pris en charge pour mettre à niveau vers une version au sein de la même version principale, telles que SQL Server 2017.

## <a id="versioncheck"></a>Vérifiez la version installée de SQL Server

Pour vérifier votre version actuelle et l’édition de SQL Server sur Linux, utilisez la procédure suivante :

1. Si pas déjà installé, installez le [les outils de ligne de SQL Server](sql-server-linux-setup-tools.md).

1. Utilisez **sqlcmd** pour exécuter une commande Transact-SQL qui affiche la version de SQL Server et l’édition.

   ```bash
   sqlcmd -S localhost -U SA -Q 'select @@VERSION'
   ```

## <a id="uninstall"></a>Désinstaller SQL Server

Pour supprimer la **mssql-serveur** package sous Linux, utilisez une des commandes suivantes en fonction de votre plateforme :

| Plateforme | Commandes de suppression de package |
|-----|-----|
| RHEL | `sudo yum remove mssql-server` |
| SLES | `sudo zypper remove mssql-server` |
| Ubuntu | `sudo apt-get remove mssql-server` |

La suppression du package ne supprime pas les fichiers de base de données générée. Si vous souhaitez supprimer les fichiers de base de données, utilisez la commande suivante :

```bash
sudo rm -rf /var/opt/mssql/
```

## <a id="unattended"></a>Installation sans assistance

Vous pouvez effectuer une installation sans assistance de la manière suivante :

- Suivez les étapes initial dans le [Démarrages rapides](#platforms) pour inscrire les référentiels, installez SQL Server.
- Lorsque vous exécutez `mssql-conf setup`, définissez [variables d’environnement](sql-server-linux-configure-environment-variables.md) et utiliser le `-n` (sans invite) option.

L’exemple suivant configure l’Édition Developer de SQL Server avec le **MSSQL_PID** variable d’environnement. Elle accepte également le CLUF (**ACCEPT_EULA**) et définit le mot de passe SA (**MSSQL_SA_PASSWORD**). Le `-n` paramètre effectue une installation exemple où les valeurs de configuration sont extraites les variables d’environnement.

```bash
sudo MSSQL_PID=Developer ACCEPT_EULA=Y MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' /opt/mssql/bin/mssql-conf -n setup
```

Vous pouvez également créer un script qui exécute d’autres actions. Par exemple, vous pouvez installer d’autres packages SQL Server.

Pour un exemple de script plus détaillée, consultez les exemples suivants :

- [Red Hat script d’installation sans assistance](sample-unattended-install-redhat.md)
- [SUSE script d’installation sans assistance](sample-unattended-install-suse.md)
- [Ubuntu script d’installation sans assistance](sample-unattended-install-ubuntu.md)

## <a id="offline"></a>Installation hors connexion

Si l’ordinateur Linux n’a pas d’accès pour les référentiels en ligne utilisés dans le [Démarrages rapides](#platforms), vous pouvez télécharger directement les fichiers du package. Ces packages se trouvent dans le référentiel Microsoft, [https://packages.microsoft.com](https://packages.microsoft.com).

> [!TIP]
> Si vous avez installé avec succès avec les étapes décrites dans le démarrage rapide, il est inutile télécharger ou installer manuellement le package (s) ci-dessous. Cette section concerne uniquement le scénario hors connexion.

1. **Télécharger le package de moteur de base de données pour votre plateforme**. Rechercher des liens de téléchargement de package dans la section des détails du package le [Notes de publication](sql-server-linux-release-notes.md).

1. **Déplacer le package téléchargé sur votre ordinateur Linux**. Si vous avez utilisé un autre ordinateur pour télécharger les packages, un pour déplacer les packages à l’ordinateur Linux est la **scp** commande.

1. **Installer le package de moteur de base de données**. Utilisez une des commandes suivantes en fonction de votre plateforme. Remplacez le nom du fichier de package dans cet exemple par le nom exact que vous avez téléchargé.

   | Plateforme | Commande de suppression d’un package |
   |-----|-----|
   | RHEL | `sudo yum localinstall mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `sudo zypper install mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `sudo dpkg -i mssql-server_versionnumber_amd64.deb` |

    > [!NOTE]
    > Vous pouvez également installer les packages RPM (RHEL et SLES) avec le `rpm -ivh` commande, mais les commandes dans le tableau précédent automatiquement installent des dépendances si disponibles à partir d’approuvée référentiels.

1. **Résoudre les dépendances manquantes**: vous pouvez avoir des dépendances manquantes à ce stade. Si ce n’est pas le cas, vous pouvez ignorer cette étape. Sur Ubuntu, si vous avez accès à des référentiels approuvées contenant ces dépendances, la solution la plus simple consiste à utiliser le `apt-get -f install` commande. Cette commande termine également l’installation de SQL Server. Pour examiner les dépendances manuellement, utilisez les commandes suivantes :

   | Plateforme | Commande de dépendances de liste |
   |-----|-----|
   | RHEL | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `dpkg -I mssql-server_versionnumber_amd64.deb` |

   Après avoir résolu les dépendances manquantes, essayez d’installer le package serveur mssql à nouveau.

1. **Terminer l’installation de SQL Server**. Utilisez **mssql-conf** pour terminer l’installation de SQL Server :

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

## <a name="next-steps"></a>Étapes suivantes

Après l’installation, vous pouvez également installer d’autres packages facultatifs de SQL Server.

- [Outils de ligne de commande de SQL Server](sql-server-linux-setup-tools.md)
- [SQL Server Agent](sql-server-linux-setup-sql-agent.md)
- [Recherche en texte intégral SQL Server](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services (Ubuntu)](sql-server-linux-setup-ssis.md)

Se connecter à votre instance de SQL Server pour commencer la création et la gestion des bases de données. Pour commencer, consultez les Démarrages rapides :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-ubuntu.md)
