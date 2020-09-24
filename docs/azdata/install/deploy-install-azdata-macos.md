---
title: Installer azdata pour macOS
titleSuffix: ''
description: Découvrez comment installer l’outil azdata sur macOS.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c812600394546cba8adb0eacab59fa450b7c4bd2
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90914904"
---
# <a name="install-azdata-on-macos"></a>Installer `azdata` sur macOS

Pour la plateforme macOS, vous pouvez installer `azdata-cli` avec le gestionnaire de package Homebrew. Le package CLI a été testé sur macOS versions : 
* 10.13 High Sierra
* 10.14 Mojave
* 10.15 Catalina

## <a name="install-with-homebrew"></a>Installer avec Homebrew

```bash
brew tap microsoft/azdata-cli-release
brew update
brew install azdata-cli
```

>[!IMPORTANT]
>`azdata-cli` a une dépendance sur les packages `python3`, `freetds`, `unixodbc`, `zeromq` Homebrew et les installe. `azdata-cli` offre la garantie d’être compatible avec la dernière version de ces dépendances publiées sur Homebrew.

## <a name="verify-install"></a>Vérifier l’installation

```bash
azdata
azdata --version
```

## <a name="update"></a>Update

Mettez à jour vos informations de référentiel local, puis mettez à niveau le package `azdata-cli`.

```bash
brew tap microsoft/azdata-cli-release
brew update
brew upgrade azdata-cli
```

## <a name="uninstall"></a>Désinstaller l’interface

Utilisez homebrew pour désinstaller le package `azdata-cli`.

```bash
brew uninstall azdata-cli
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)] ?](../../big-data-cluster/big-data-cluster-overview.md).

Utiliser azdata avec les [services de données dotés d’Azure Arc](/azure/azure-arc/data/)
