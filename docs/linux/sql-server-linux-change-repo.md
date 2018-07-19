---
title: Configurer des référentiels pour SQL Server sur Linux | Microsoft Docs
description: Vérifiez et configurez des référentiels de code source pour SQL Server 2017 sur Linux. Le référentiel source a une incidence sur la version de SQL Server qui est appliqué pendant l’installation et mise à niveau.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/14/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 63cb2f56852a668bc48aa85cd31a72a2b583463b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38006081"
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>Configurer des référentiels pour l’installation et la mise à niveau de SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article décrit comment configurer le référentiel approprié pour les mises à niveau et les installations de SQL Server 2017 sur Linux.

> [!IMPORTANT]
> Si vous avez installé précédemment un CTP ou la version RC de SQL Server 2017, vous devez utiliser les étapes décrites dans cet article pour inscrire un référentiel de la disponibilité générale (GA) et mettre à niveau ou réinstaller. Les versions préliminaires de SQL Server 2017 ne sont pas prises en charge et va expirer.

## <a id="repositories"></a>Référentiels

Lorsque vous installez SQL Server sur Linux, vous devez configurer un référentiel Microsoft. Ce référentiel est utilisé pour acquérir le package de moteur de base de données, **mssql-server**et les packages SQL Server. Il existe actuellement trois référentiels principales :

| Référentiel | Nom    | Description |
|---|---|---|
| **Aperçu** | **mssql-server** | Référentiel de version préliminaire pour les versions CTP et RC de SQL Server. Ce dépôt n’est pas pris en charge pour SQL Server 2017. |
| **CU** | **mssql-server-2017** | Référentiel de SQL Server 2017 Cumulative Update (CU). |
| **GDR** | **mssql-server-2017-gdr** | Référentiel de SQL Server 2017 GDR pour les mises à jour critiques uniquement. |

## <a id="cuversusgdr"></a> Mise à jour cumulative et GDR

Il est important de noter qu’il existe deux types principaux de référentiel pour chaque distribution :

- **Mises à jour cumulative (CU)**: référentiel de la mise à jour Cumulative (CU) contient des packages pour la version de SQL Server de base et tous les correctifs de bogues ou améliorations depuis cette version. Mises à jour cumulatives sont spécifiques à une version release, telles que SQL Server 2017. Elles sont publiées régulièrement.

- **GDR**: référentiel du GDR contient les packages de mise en production de base SQL Server et uniquement les correctifs critiques et mises à jour de sécurité depuis cette version. Ces mises à jour sont également ajoutés à la prochaine version CU.

Chaque version de l’unité de capacité et GDR contient le package complet de SQL Server et toutes les mises à jour précédentes pour ce référentiel. La mise à jour à partir d’une version de correctif logiciel grand public à une version CU est pris en charge en modifiant votre référentiel configuré pour SQL Server. Vous pouvez également [rétrograder](sql-server-linux-setup.md#rollback) à n’importe quelle version au sein de votre version principale (ex : 2017).

> [!NOTE]
> Vous pouvez mettre à jour à partir d’une version GDR CU release à tout moment en modifiant les référentiels. La mise à jour à partir d’une unité de capacité mise en production vers une version de correctif logiciel grand public n’est pas pris en charge. 

## <a id="configure"></a> Configurer un référentiel

Les sections suivantes décrivent comment vérifier et configurer un référentiel pour les plateformes prises en charge suivantes :

- [Red Hat Enterprise Server](#rhel)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#sles)

## <a id="rhel"></a> Configurer des référentiels RHEL
Utilisez les étapes suivantes pour configurer les référentiels sur Red Hat Enterprise Server (RHEL).

### <a name="check-for-previously-configured-repositories-rhel"></a>Recherchez les référentiels configurées précédemment (RHEL)
Tout d’abord vérifier si vous avez déjà enregistré un référentiel SQL Server.

1. Afficher les fichiers dans le **/etc/yum.repos.d** répertoire avec la commande suivante :

   ```bash
   sudo ls /etc/yum.repos.d
   ```

2. Recherchez le fichier qui configure le répertoire de SQL Server, tels que **mssql-server.repo**.

3. Imprimer le contenu du fichier.

   ```bash
   sudo cat /etc/yum.repos.d/mssql-server.repo
   ```

4. La propriété **name** est le réertoire configuré. Vous pouvez l’identifier la table dans le [référentiels](#repositories) section de cet article.

### <a name="remove-old-repository-rhel"></a>Supprimer l’ancien référentiel (RHEL)
Si nécessaire, supprimez l’ancien référentiel avec la commande suivante.

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Cette commande suppose que le fichier identifié dans la section précédente a été nommé **mssql-server.repo**.

### <a name="configure-new-repository-rhel"></a>Configurer le nouveau référentiel (RHEL)
Configurer le nouveau référentiel à utiliser pour les mises à niveau et les installations de SQL Server. Utilisez une des commandes suivantes pour configurer le référentiel de votre choix.

| Référentiel | Command |
|---|---|
| **CU** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

## <a id="sles"></a> Configurer des référentiels SLES
Utilisez les étapes suivantes pour configurer des référentiels sur SLES.

### <a name="check-for-previously-configured-repositories-sles"></a>Recherchez les référentiels configurées précédemment (SLES)
Tout d’abord vérifier si vous avez déjà enregistré un référentiel SQL Server.

1. Utilisez **zypper info** pour obtenir des informations sur n’importe quel référentiel précédemment configuré.

   ```bash
   sudo zypper info mssql-server
   ```

2. Le **référentiel** propriété est le référentiel configuré. Vous pouvez l’identifier la table dans le [référentiels](#repositories) section de cet article.

### <a name="remove-old-repository-sles"></a>Supprimer l’ancien référentiel (SLES)
Si nécessaire, supprimez l’ancien référentiel. Utilisez une des commandes suivantes en fonction du type de référentiel précédemment configuré.

| Référentiel | Commande à supprimer |
|---|---|
| **Aperçu** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

### <a name="configure-new-repository-sles"></a>Configurer le nouveau référentiel (SLES)
Configurer le nouveau référentiel à utiliser pour les mises à niveau et les installations de SQL Server. Utilisez une des commandes suivantes pour configurer le référentiel de votre choix.

| Référentiel | Command |
|---|---|
| **CU** | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

## <a id="ubuntu"></a> Configurer les référentiels d’Ubuntu
Utilisez les étapes suivantes pour configurer des référentiels sur Ubuntu.

### <a name="check-for-previously-configured-repositories-ubuntu"></a>Recherchez les référentiels configurées précédemment (Ubuntu)
Tout d’abord vérifier si vous avez déjà enregistré un référentiel SQL Server.

1. Afficher le contenu de la **/etc/apt/sources.list** fichier.

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Examinez l’URL de package pour mssql-server. Vous pouvez l’identifier la table dans le [référentiels](#repositories) section de cet article.

### <a name="remove-old-repository-ubuntu"></a>Supprimer l’ancien référentiel (Ubuntu)
Si nécessaire, supprimez l’ancien référentiel. Utilisez une des commandes suivantes en fonction du type de référentiel précédemment configuré.

| Référentiel | Commande à supprimer |
|---|---|
| **Aperçu** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` 
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

### <a name="configure-new-repository-ubuntu"></a>Configurer le nouveau référentiel (Ubuntu)
Configurer le nouveau référentiel à utiliser pour les mises à niveau et les installations de SQL Server.

1. Importez les clés publiques GPG de référentiel.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Utilisez une des commandes suivantes pour configurer le référentiel de votre choix.

   | Référentiel | Command |
   |---|---|
   | **CU** | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **GDR** | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. Exécutez **apt-get mise à jour**.

   ```bash
   sudo apt-get update
   ```

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez configuré le référentiel approprié, vous pouvez passer à [installer](sql-server-linux-setup.md#platforms) ou [mettre à jour](sql-server-linux-setup.md#upgrade) SQL Server et tous liés packages à partir du référentiel de nouveau.

> [!IMPORTANT]
> À ce stade, si vous choisissez d’utiliser un des articles de l’installation, tels que le [Démarrages rapides](sql-server-linux-setup.md#platforms), n’oubliez pas que vous avez déjà configuré le référentiel cible. Ne répétez pas cette étape dans les didacticiels. Cela est particulièrement vrai si vous configurez le référentiel GDR, étant donné que les Démarrages rapides utilisent le référentiel CU.

Pour plus d’informations sur l’installation de SQL Server 2017 sur Linux, consultez [consignes d’Installation pour SQL Server sur Linux](sql-server-linux-setup.md).
