---
title: Installer azdata à l’aide du programme d’installation sur Linux
titleSuffix: ''
description: Découvrez comment installer l’outil azdata avec le programme d’installation (Linux).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2dc1c3d58ee5f7b6ea032a2e41f7c18431229881
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90914969"
---
# <a name="install-azdata-with-apt"></a>Installer `azdata` avec apt

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/azdata.md)]

Cet article explique comment installer `azdata` sur Linux. Avant que ces gestionnaires de package soient disponibles, l’installation de `azdata` nécessitait `pip`.

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-azdata-for-linux"></a><a id="linux"></a>Installer `azdata` pour Linux

Le package d’installation `azdata` est disponible pour Ubuntu avec `apt`.

### <a name="install-azdata-with-apt-ubuntu"></a><a id="azdata-apt"></a>Installer `azdata` avec apt (Ubuntu)

>[!NOTE]
>Le package `azdata` n’utilise pas l’interpréteur Python du système, mais installe son propre interpréteur Python.

1. Obtenez les packages nécessaires pour le processus d’installation :

    ```bash
    sudo apt-get update
    sudo apt-get install gnupg ca-certificates curl wget software-properties-common apt-transport-https lsb-release -y
    ```

2. Téléchargez et installez la clé de signature :

    ```bash
    curl -sL https://packages.microsoft.com/keys/microsoft.asc |
    gpg --dearmor |
    sudo tee /etc/apt/trusted.gpg.d/microsoft.asc.gpg > /dev/null
    ```

3. Ajoutez les informations sur le référentiel `azdata`.

   Pour le client Ubuntu 16.04, exécutez :
    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/prod.list)"
    ```

   Pour le client Ubuntu 18.04, exécutez :
    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/18.04/prod.list)"
    ```

4. Mettez à jour les informations de référentiel et installez `azdata` :

    ```bash
    sudo apt-get update
    sudo apt-get install -y azdata-cli
    ```

5. Vérifiez l’installation :

    ```bash
    azdata --version
    ```

### <a name="update"></a>Update

Mettez à niveau `azdata` uniquement :

```bash
sudo apt-get update && sudo apt-get install --only-upgrade -y azdata-cli
```

### <a name="uninstall"></a>Désinstaller l’interface

1. Désinstallez avec apt-get remove :

    ```bash
    sudo apt-get remove -y azdata-cli
    ```

2. Supprimez les informations de référentiel `azdata` :

    >[!NOTE]
    >Cette étape n’est pas nécessaire si vous envisagez d’installer `azdata` à l’avenir

    ```bash
    sudo rm /etc/apt/sources.list.d/azdata-cli.list
    ```

3. Supprimez la clé de signature :

    ```bash
    sudo rm /etc/apt/trusted.gpg.d/dpgswdist.v1.asc.gpg
    ```

4. Supprimez toutes les dépendances inutiles qui ont été installées avec l’interface de ligne de commande Azdata :

    ```bash
    sudo apt autoremove
    ```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)] ?](../../big-data-cluster/big-data-cluster-overview.md).

Utiliser azdata avec les [services de données dotés d’Azure Arc](/azure/azure-arc/data/)