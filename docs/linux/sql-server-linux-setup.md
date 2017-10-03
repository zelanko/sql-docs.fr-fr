---
title: Installer SQL Server 2017 sur Linux | Documents Microsoft
description: "Installer, mettre à jour et désinstaller SQL Server sur Linux. Cette rubrique couvre les scénarios en ligne, hors connexion et sans assistance."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 0220ef0349acac274567bb75bcb0e8b38a3126ce
ms.contentlocale: fr-fr
ms.lasthandoff: 10/02/2017

---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Aide à l’installation de SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Cette rubrique explique comment installer, mettre à jour et désinstaller 2017 du serveur SQL sur Linux. SQL Server 2017 est pris en charge sur Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) et Ubuntu. Il est également disponible sous une image Docker qui peut s’exécuter sur le moteur Docker sur Linux ou Docker pour Windows/Mac.

> [!TIP]
> Pour démarrer rapidement, passez à un des didacticiels de démarrage rapide pour [RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), [Ubuntu](quickstart-install-connect-ubuntu.md), ou [Docker](quickstart-install-connect-docker.md).

## <a id="supportedplatforms"></a>Plateformes prises en charge

SQL Server 2017 est pris en charge sur les plateformes Linux suivantes :

| Plateforme | Versions prises en charge | Obtenir
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 | [Obtenir RHEL 7.3](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | v12 SP2 | [Obtenir SLES v12 SP2](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Obtenir Ubuntu 16.04](http://www.ubuntu.com/download/server)
| **Moteur docker** | 1.8+ | [Obtenir Docker](http://www.docker.com/products/overview)

## <a id="system"></a>Configuration système requise

SQL Server 2017 requise est la suivante pour Linux :

|||
|-----|-----|
| **Mémoire** | 3,25 GO |
| **File System** | **XFS** ou **EXT4** (autres systèmes de fichiers, tel que **BTRFS**, non pris en charge) |
| **Espace disque** | 6 GO |
| **Vitesse du processeur** | 2 GHz |
| **Cœurs de processeur** | 2 cœurs |
| **Type de processeur** | x64 compatibles uniquement |

> [!NOTE]
> Moteur SQL Server a été testé jusqu'à 1 To de mémoire pour l’instant.

Si vous utilisez **système NFS (Network File)** partages distants en production, notez les exigences de prise en charge suivantes :

- Utiliser la version NFS **4.2 ou ultérieure**. Les versions antérieures de NFS ne gèrent pas les fonctionnalités requises, telles que fallocate et la création du fichier partiellement alloué, commune aux systèmes de fichiers modernes.
- Recherchez uniquement les **/var/opt/mssql** répertoires sur le montage NFS. Autres fichiers, tels que les fichiers binaires du système SQL Server, ne sont pas pris en charge.
- Assurez-vous que les clients NFS utilisent l’option 'nolock' lorsque vous montez le partage distant.

## <a id="platforms"></a> Installation de SQL Server

Vous pouvez installer SQL Server sur Linux à partir de la ligne de commande. Pour obtenir des instructions, consultez les didacticiels de démarrage rapide suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-docker.md)

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

> [!IMPORTANT]
> Vers une version antérieure est uniquement prise en charge entre RC1, RC2 et RTM pour l’instant.

## <a id="repositories"></a>Modifier les référentiels sources

Lorsque vous installez ou mettez à niveau de SQL Server, vous obtenez la dernière version de SQL Server à partir de votre référentiel de Microsoft. Il est important de noter qu’il existe deux principaux types de référentiels pour chaque point de distribution :

- **Les mises à jour cumulative (CU)**: référentiel de la mise à jour Cumulative (CU) contient des packages pour la version de SQL Server de base et tous les correctifs de bogues ou améliorations apportées depuis cette version. Mises à jour cumulatives sont spécifiques à une version release, telles que SQL Server 2017. Ils sont publiés sur une cadence régulière.

- **GDR**: référentiel du GDR contient des packages pour la base version de SQL Server et uniquement les correctifs critiques et les mises à jour de sécurité depuis cette version. Ces mises à jour sont également ajoutés à la prochaine version CU.

Chaque version de CU et correctif logiciel grand public contient le package SQL Server complète et toutes les mises à jour précédentes pour ce référentiel. Mise à jour à partir d’une version GDR vers une version CU prend en charge la modification de votre référentiel configuré pour SQL Server. Vous pouvez également [rétrograder](#rollback) à n’importe quelle version dans votre version principale (ex : 2017).

> [!NOTE]
> Mise à jour à partir d’une CU version à une version de correctif logiciel grand public n’est pas pris en charge.

Pour modifier à partir du référentiel GDR vers le référentiel CU procédez comme suit :

1. Supprimer le référentiel d’aperçu précédemment configurés.

   | Plateforme | Commande de suppression de référentiel |
   |-----|-----|
   | RHEL | `sudo rm -rf /etc/yum.repos.d/mssql-server.repo` |
   | SLES | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
   | Ubuntu | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` |

1. Configurez le nouveau référentiel.

   | Plateforme | Référentiel | Command |
   |-----|-----|-----|
   | RHEL | CU | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
   | RHEL | GDR | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |
   | SLES | CU  | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
   | SLES | GDR | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |
   | Ubuntu | CU | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | Ubuntu | GDR | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

1. Mettre à jour votre système.

   | Plateforme | Commande UPDATE |
   |-----|-----|
   | RHEL | `sudo yum update` |
   | SLES | `sudo zypper --gpg-auto-import-keys refresh` |
   | Ubuntu | `sudo apt-get update` |


1. [Installer](#platforms) ou [mettre à jour](#upgrade) SQL Server à partir du référentiel de nouveau.

   > [!IMPORTANT]
   > À ce stade, si vous choisissez d’effectuer une installation complète à l’aide de la [didacticiels de démarrage rapide](#platforms), souvenez-vous que vous venez de configurer le référentiel cible. Ne répétez pas cette étape dans les didacticiels. Cela est particulièrement vrai si vous configurez le référentiel GDR, étant donné que les didacticiels de démarrage rapide utilisent le référentiel CU.

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

- Suivez les étapes initial dans le [didacticiels de démarrage rapide](#platforms) pour inscrire les référentiels, installez SQL Server.
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
- [Agent SQL Server](sql-server-linux-setup-sql-agent.md)
- [Recherche en texte intégral SQL Server](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services (Ubuntu)](sql-server-linux-setup-ssis.md)

Se connecter à votre instance de SQL Server pour commencer la création et la gestion des bases de données. Pour commencer, consultez les didacticiels de démarrage rapide :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-ubuntu.md)

