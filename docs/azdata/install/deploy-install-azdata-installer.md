---
title: Installer azdata avec Windows Installer
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer l’outil azdata pour installer et gérer ensuite des clusters Big Data SQL Server à l’aide du programme d’installation.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 60d3b60f98a93cb6b724cd569fb2871adec3f1ce
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733879"
---
# <a name="install-azdata-to-manage-big-data-clusters-2019-with-windows-installer"></a>Installer `azdata` pour gérer [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)] avec Windows Installer

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

Cet article explique comment installer `azdata` pour les clusters Big Data SQL Server 2019 sur Windows. Avant la disponibilité de l’installation de Windows, l’installation d’`azdata` nécessitait `pip`.

>Pour Linux (Ubuntu), consultez les informations relatives à l’[installation d’`azdata` à l’aide du programme d’installation](./deploy-install-azdata-linux-package.md).

Actuellement, il n’existe aucun gestionnaire de package permettant d’installer `azdata` sur d’autres systèmes d’exploitation ou distributions. Pour ces plateformes, consultez les informations relatives à l’[installation d’`azdata` sans gestionnaire de package](./deploy-install-azdata.md).

## <a name="install-azdata-with-the-microsoft-windows-installer"></a>Installer `azdata` avec Microsoft Windows Installer

Pour installer `azdata` avec Microsoft Windows Installer :

1. Supprimez `azdata`, s’il a été installé à l’aide de `pip`. Si `azdata` a été installé à l’aide de Windows Installer, passez à l’étape suivante.
1. Installez `azdata` à l’aide de Windows Installer.

### <a name="uninstall-if-previous-installation-done-with-pip"></a>Effectuer une désinstallation si l’installation précédente a été effectuée avec `pip`

Si des versions release précédentes d’`azdata` sont déjà installées, il est important de commencer par les désinstaller avant d’installer la dernière version.

   Pour supprimer la version finale (RC) d’`azdata`, exécutez la commande suivante.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

Une fois la suppression effectuée, vous pouvez [installer `azdata` sur Windows](#install-azdata-windows).

>[!NOTE]
>Si votre installation précédente a été effectuée à l’aide de MSI, vous n’avez pas besoin de désinstaller les versions actuelles avant d’utiliser le programme d’installation MSI.

### <a name="install-with-windows-installer"></a><a id="install-azdata-windows"></a>Installer avec Windows Installer

Utilisez Windows Installer pour installer ou mettre à jour `azdata` sur Windows.

[Téléchargez le programme `azdata`Windows Installer](https://aka.ms/azdata-msi).

Quand le programme d’installation vous demande s’il peut apporter des changements à l’ordinateur, cliquez sur `Yes`.

### <a name="uninstall-azdata-with-windows-installer"></a>Désinstaller `azdata`avec Windows Installer

Pour désinstaller `azdata` avec Windows Installer, suivez les instructions correspondant au système d’exploitation approprié.

| Plateforme      | Instructions                                           |
| ------------- |--------------------------------------------------------|
| Windows 10| Démarrer > Paramètres > Applications                                |
| Windows 8     | Démarrer > Panneau de configuration > Programmes > Désinstaller un programme |

Le programme à désinstaller s’appelle `Azdata CLI`. Sélectionnez cette application, puis cliquez sur le bouton `Uninstall`.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)] ?](../../big-data-cluster/big-data-cluster-overview.md)