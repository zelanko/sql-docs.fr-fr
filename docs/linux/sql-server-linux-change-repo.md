---
title: Configurer des référentiels de Linux pour SQL Server 2017 et 2019 | Microsoft Docs
description: Vérifiez et configurez des référentiels de code source pour SQL Server 2019 et SQL Server 2017 sur Linux. Le référentiel source a une incidence sur la version de SQL Server qui est appliqué pendant l’installation et mise à niveau.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/11/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
zone_pivot_groups: ld2-linux-distribution
ms.openlocfilehash: 2cc95a36a83307667b3f3678ccd19f7712dc54b3
ms.sourcegitcommit: 009bee6f66142c48477849ee03d5177bcc3b6380
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56230986"
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>Configurer des référentiels pour l’installation et la mise à niveau de SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

::: zone pivot="ld2-rhel"
Cet article décrit comment configurer le référentiel approprié pour les mises à niveau et les installations de SQL Server 2017 et SQL Server 2019 sur Linux. En haut, votre sélection actuelle est **avait Red (RHEL)**.
::: zone-end

::: zone pivot="ld2-sles"
Cet article décrit comment configurer le référentiel approprié pour les mises à niveau et les installations de SQL Server 2017 et SQL Server 2019 sur Linux. En haut, votre sélection actuelle est **SUSE (SLES)**.
::: zone-end

::: zone pivot="ld2-ubuntu"
Cet article décrit comment configurer le référentiel approprié pour les mises à niveau et les installations de SQL Server 2017 et SQL Server 2019 sur Linux. En haut, votre sélection actuelle est **Ubuntu**.
::: zone-end

> [!TIP]
> SQL Server 2019 preview est désormais disponible ! Pour l’essayer, utilisez cet article pour configurer le nouveau **mssql-server-preview** référentiel. Puis installer en suivant les instructions dans le [guide d’installation](sql-server-linux-setup.md).

## <a id="repositories"></a>Référentiels

Lorsque vous installez SQL Server sur Linux, vous devez configurer un référentiel Microsoft. Ce référentiel est utilisé pour acquérir le package de moteur de base de données, **mssql-server**et les packages SQL Server. Il existe actuellement trois référentiels principales :

| Référentiel | Créer une vue d’abonnement | Description |
|---|---|---|
| **Version préliminaire (2017)** | **mssql-server** | Référentiel SQL Server 2017 CTP et RC (supprimée). |
| **Version préliminaire (2019)** | **mssql-server-preview** | Version préliminaire de SQL Server 2019 et référentiel RC. |
| **CU** | **mssql-server-2017** | Référentiel de SQL Server 2017 Cumulative Update (CU). |
| **GDR** | **mssql-server-2017-gdr** | Référentiel de SQL Server 2017 GDR pour les mises à jour critiques uniquement. |

## <a id="cuversusgdr"></a> Mise à jour cumulative et GDR

Il est important de noter qu’il existe deux types principaux de référentiel pour chaque distribution :

- **Mises à jour cumulatives (CU)**: Le référentiel de mise à jour Cumulative (CU) contient des packages pour la version de SQL Server de base et tous les correctifs de bogues ou améliorations depuis cette version. Mises à jour cumulatives sont spécifiques à une version release, telles que SQL Server 2017. Elles sont publiées régulièrement.

- **GDR**: Le référentiel GDR contient les packages de mise en production de base SQL Server et uniquement les correctifs critiques et mises à jour de sécurité depuis cette version. Ces mises à jour sont également ajoutés à la prochaine version CU.

Chaque version de l’unité de capacité et GDR contient le package complet de SQL Server et toutes les mises à jour précédentes pour ce référentiel. La mise à jour à partir d’une version de correctif logiciel grand public à une version CU est pris en charge en modifiant votre référentiel configuré pour SQL Server. Vous pouvez également [rétrograder](sql-server-linux-setup.md#rollback) à n’importe quelle version au sein de votre version principale (ex : 2017).

> [!NOTE]
> Vous pouvez mettre à jour à partir d’une version GDR CU release à tout moment en modifiant les référentiels. La mise à jour à partir d’une unité de capacité mise en production vers une version de correctif logiciel grand public n’est pas pris en charge.

## <a name="configure-repositories"></a>Configurer les référentiels

::: zone pivot="ld2-rhel"
Procédez comme indiqué dans les sections suivantes pour configurer des référentiels sur Red Hat Enterprise Server (RHEL).
::: zone-end

::: zone pivot="ld2-sles"
Procédez comme indiqué dans les sections suivantes pour configurer des référentiels sur SUSE Linux Enterprise Server (SLES).
::: zone-end

::: zone pivot="ld2-ubuntu"
Utilisez les étapes décrites dans les sections suivantes pour configurer des référentiels sur Ubuntu.
::: zone-end

## <a name="check-for-previously-configured-repositories"></a>Recherchez des référentiels précédemment configurés

<!--RHEL-->
::: zone pivot="ld2-rhel"
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

::: zone-end

<!--SLES-->
::: zone pivot="ld2-sles"
Tout d’abord vérifier si vous avez déjà enregistré un référentiel SQL Server.

1. Utilisez **zypper info** pour obtenir des informations sur n’importe quel référentiel précédemment configuré.

   ```bash
   sudo zypper info mssql-server
   ```

2. Le **référentiel** propriété est le référentiel configuré. Vous pouvez l’identifier la table dans le [référentiels](#repositories) section de cet article.

::: zone-end

<!--Ubuntu-->
::: zone pivot="ld2-ubuntu"
Tout d’abord vérifier si vous avez déjà enregistré un référentiel SQL Server.

1. Afficher le contenu de la **/etc/apt/sources.list** fichier.

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Examinez l’URL de package pour mssql-server. Vous pouvez l’identifier la table dans le [référentiels](#repositories) section de cet article.

::: zone-end

## <a name="remove-old-repository"></a>Supprimer l’ancien référentiel

<!--RHEL-->
::: zone pivot="ld2-rhel"
Si nécessaire, supprimez l’ancien référentiel avec la commande suivante.

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Cette commande suppose que le fichier identifié dans la section précédente a été nommé **mssql-server.repo**.

::: zone-end

<!--SLES-->
::: zone pivot="ld2-sles"
Si nécessaire, supprimez l’ancien référentiel. Utilisez une des commandes suivantes en fonction du type de référentiel précédemment configuré.

| Référentiel | Commande à supprimer |
|---|---|
| **Version préliminaire (2017)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **Version préliminaire (2019)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-preview'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

::: zone-end

<!--Ubuntu-->
::: zone pivot="ld2-ubuntu"
Si nécessaire, supprimez l’ancien référentiel. Utilisez une des commandes suivantes en fonction du type de référentiel précédemment configuré.

| Référentiel | Commande à supprimer |
|---|---|
| **Version préliminaire (2017)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` |
| **Version préliminaire (2019)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview xenial main'` |
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

::: zone-end

## <a name="configure-new-repository"></a>Configurer le nouveau référentiel

<!--RHEL-->
::: zone pivot="ld2-rhel"
Configurer le nouveau référentiel à utiliser pour les mises à niveau et les installations de SQL Server. Utilisez une des commandes suivantes pour configurer le référentiel de votre choix.

| Référentiel | Version | Command |
|---|---|---|
| **Version préliminaire (2019)** | 2019 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

::: zone-end

<!--SLES-->
::: zone pivot="ld2-sles"
Configurer le nouveau référentiel à utiliser pour les mises à niveau et les installations de SQL Server. Utilisez une des commandes suivantes pour configurer le référentiel de votre choix.

| Référentiel | Version | Command |
|---|---|---|
| **Version préliminaire (2019)** | 2019 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

::: zone-end

<!--Ubuntu-->
::: zone pivot="ld2-ubuntu"
Configurer le nouveau référentiel à utiliser pour les mises à niveau et les installations de SQL Server.

1. Importez les clés publiques GPG de référentiel.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Utilisez une des commandes suivantes pour configurer le référentiel de votre choix.

   | Référentiel | Version | Command |
   |---|---|---|
   | **Version préliminaire (2019)** | 2019 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"` |
   | **CU** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **GDR** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. Exécutez **apt-get mise à jour**.

   ```bash
   sudo apt-get update
   ```

::: zone-end

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez configuré le référentiel approprié, vous pouvez passer à [installer](sql-server-linux-setup.md#platforms) ou [mettre à jour](sql-server-linux-setup.md#upgrade) SQL Server et tous liés packages à partir du référentiel de nouveau.

::: zone pivot="ld2-rhel"
> [!IMPORTANT]
> À ce stade, si vous choisissez d’utiliser le [RHEL quickstart](quickstart-install-connect-red-hat.md), n’oubliez pas que vous avez déjà configuré le référentiel cible. Ne répétez pas cette étape dans les didacticiels. Cela est particulièrement vrai si vous configurez le référentiel GDR, étant donné que le démarrage rapide utilise le référentiel CU.
::: zone-end

::: zone pivot="ld2-sles"
> [!IMPORTANT]
> À ce stade, si vous choisissez d’utiliser le [SLES quickstart](quickstart-install-connect-suse.md), n’oubliez pas que vous avez déjà configuré le référentiel cible. Ne répétez pas cette étape dans les didacticiels. Cela est particulièrement vrai si vous configurez le référentiel GDR, étant donné que le démarrage rapide utilise le référentiel CU.
::: zone-end

::: zone pivot="ld2-ubuntu"
> [!IMPORTANT]
> À ce stade, si vous choisissez d’utiliser le [Guide de démarrage rapide Ubuntu](quickstart-install-connect-ubuntu.md), n’oubliez pas que vous avez déjà configuré le référentiel cible. Ne répétez pas cette étape dans les didacticiels. Cela est particulièrement vrai si vous configurez le référentiel GDR, étant donné que le démarrage rapide utilise le référentiel CU.
::: zone-end

Pour plus d’informations sur l’installation de SQL Server 2017 sur Linux, consultez [consignes d’Installation pour SQL Server sur Linux](sql-server-linux-setup.md).
