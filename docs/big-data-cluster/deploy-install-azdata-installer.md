---
title: Installer azdata avec Windows Installer
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer l’outil azdata pour installer et gérer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (version préliminaire) avec le programme d’installation.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a8dd5d2c7d0210880a82d774185a3f2a915608ec
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70158144"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-with-windows-installer"></a>Installer `azdata` pour gérer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] avec Windows Installer

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment installer `azdata` pour les clusters de SQL Server 2019 Big Data dans la version Release Candidate sur Windows. Avant la disponibilité de l’installation de Windows, l' `azdata` installation `pip`de est obligatoire.

>Pour Linux (Ubuntu), consultez [installer `azdata` avec le programme d'](./deploy-install-azdata-linux-package.md)installation.

À ce stade, il n’y a aucun gestionnaire de `azdata` package à installer sur d’autres systèmes d’exploitation ou distributions. Pour ces plateformes, [consultez `azdata` installation sans le gestionnaire de package](./deploy-install-azdata.md).

## <a name="install-azdata-with-the-microsoft-windows-installer"></a>Installer `azdata` avec le Microsoft Windows Installer

Pour installer `azdata` sur avec le Microsoft Windows Installer,

1. Supprimez `azdata` s’il a été `pip`installé à l’aide de. Si `azdata` a été installé à l’aide de Windows Installer, passez à l’étape suivante.
1. Installez `azdata` à l’aide de la Windows Installer.

### <a name="uninstall-if-previous-installation-done-with-pip"></a>Désinstaller si l’installation précédente a été effectuée avec`pip`

Si des versions précédentes de **mssqlctl** sont installées, supprimez-les. La commande suivante supprime la version CTP 3,1 de **mssqlctl**.

   ```bash
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

Si vous avez installé des versions antérieures `azdata` de, il est important de le désinstaller avant d’installer la dernière version.

   Pour CTP 3,2, exécutez la commande suivante.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```

Une fois supprimé [, `azdata` installez sur Windows](#install-azdata-windows).

>[!NOTE]
>Si votre installation précédente a été effectuée à l’aide de MSI, vous n’aurez pas besoin de désinstaller les versions actuelles avant d’utiliser le programme d’installation MSI.

### <a id="install-azdata-windows"></a>Installer avec Windows Installer

Utilisez la Windows Installer pour installer ou mettre `azdata` à jour sur Windows.

[Téléchargez le `azdata` Windows Installer](http://aka.ms/azdata-msi).

Quand le programme d’installation vous demande s’il peut apporter des modifications à `Yes`votre ordinateur, cliquez sur.

### <a name="uninstall-azdata-with-windows-installer"></a>Désinstaller `azdata` avec Windows Installer

Pour désinstaller `azdata` avec Windows Installer, suivez les instructions pour le système d’exploitation approprié.

| Plateforme      | Instructions                                           |
| ------------- |--------------------------------------------------------|
| Windows 10    | Démarrer > Paramètres > applications                                |
| Windows 8     | Démarrer > panneau de configuration > programmes > désinstaller un programme |

Le programme à désinstaller est **`Azdata CLI`** appelé. Sélectionnez cette application, puis cliquez sur `Uninstall` le bouton.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]que sont?](big-data-cluster-overview.md).
