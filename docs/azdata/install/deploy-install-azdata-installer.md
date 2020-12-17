---
title: Installer Azure Data CLI (azdata) avec Windows Installer
titleSuffix: ''
description: Découvrez comment installer l’outil azdata (Azure Data CLI) avec le programme d’installation.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c5b190c50dbbeebef94cdd15314539e5ce501160
ms.sourcegitcommit: 3bd188e652102f3703812af53ba877cce94b44a9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97489639"
---
# <a name="install-azure-data-cli-azdata-with-windows-installer"></a>Installer [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] avec Windows Installer

[!INCLUDE [azdata](../../includes/applies-to-version/azdata.md)]

Cet article explique comment installer `azdata` sur Windows avec un programme d’installation. Utilisez `azdata` pour gérer les clusters Big Data SQL Server ou les services de données avec Azure Arc.

## <a name="steps-to-install-azdata-with-the-microsoft-windows-installer"></a>Étapes à effectuer pour installer `azdata` avec Microsoft Windows Installer

Pour installer `azdata` avec Microsoft Windows Installer :

1. Supprimez `azdata`, s’il a été installé à l’aide de `pip`. Si `azdata` a été installé à l’aide de Windows Installer, passez à l’étape suivante.
1. Installez `azdata` à l’aide de [Windows Installer](https://aka.ms/azdata-msi).

### <a name="uninstall-azdata-with-windows-installer"></a>Désinstaller `azdata`avec Windows Installer

Pour désinstaller `azdata` avec Windows Installer, suivez les instructions correspondant au système d’exploitation approprié.

| Plateforme      | Instructions                                           |
| ------------- |--------------------------------------------------------|
| Windows 10| Démarrer > Paramètres > Applications                                |
| Windows 8     | Démarrer > Panneau de configuration > Programmes > Désinstaller un programme |

Le programme à désinstaller s’appelle `Azure Data CLI`. Sélectionnez cette application, puis cliquez sur le bouton `Uninstall`.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)] ?](../../big-data-cluster/big-data-cluster-overview.md)

Utiliser `azdata` avec les [services de données activés pour Azure Arc](/azure/azure-arc/data/)
