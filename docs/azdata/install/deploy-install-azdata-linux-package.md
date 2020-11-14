---
title: Installer Azure Data CLI (azdata) avec apt
description: Découvrez comment installer l’outil azdata (Azure Data CLI) avec apt.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4508db56c0246f181f9244fe0a3b853a3e91eb24
ms.sourcegitcommit: 4b7ecc080795c5f90322d60df5c0550884f48140
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334448"
---
# <a name="install-azure-data-cli-azdata-with-apt"></a>Installer [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] avec apt

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

Pour les distributions Linux avec `apt` il existe un package pour le `azdata-cli`. Le package CLI a été testé sur des versions Linux qui utilisent `apt` :

- Ubuntu 16.04, Ubuntu 18.04

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-apt"></a>Installer avec apt

>[!IMPORTANT]
> Le package RPM de `azdata-cli` dépend du package python3. Sur votre système, il doit s’agir d’une version Python antérieure à l’exigence de *Python 3.6.x*. Si cela vous pose un problème, recherchez un remplacement au package python3 ou suivez les instructions d’installation manuelle qui utilisent [`pip`](../install/deploy-install-azdata-pip.md).

1. Installez les dépendances nécessaires pour installer `azdata-cli`.

   ```bash
   sudo apt-get update
   sudo apt-get install gnupg ca-certificates curl wget software-properties-common apt-transport-https lsb-release -y
   ```

2. Importez la clé de référentiel Microsoft.

   ```bash
   curl -sL https://packages.microsoft.com/keys/microsoft.asc |
   gpg --dearmor |
   sudo tee /etc/apt/trusted.gpg.d/microsoft.asc.gpg > /dev/null
   ```

3. Créez des informations de dépôt local.

   Pour le client Ubuntu 16.04, exécutez :

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/prod.list)"
    ```

   Pour le client Ubuntu 18.04, exécutez :

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/18.04/prod.list)"
    ```

   Pour le client Ubuntu 20.04, exécutez :

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/20.04/prod.list)"
    ```

4. Installez `azdata-cli`.

   ```bash
   sudo apt-get update
   sudo apt-get install -y azdata-cli
   ```

## <a name="verify-install"></a>Vérifier l’installation

```bash
azdata
azdata --version
```

## <a name="update"></a>Update

Mettez à jour `azdata-cli` avec les commandes `apt-get update` et `apt-get install`.

```bash
sudo apt-get update && sudo apt-get install --only-upgrade -y azdata-cli
```

## <a name="uninstall"></a>Désinstaller l’interface

1. Supprimez le package de votre système.

   ```bash
   sudo apt-get remove -y azdata-cli
   ```

2. Supprimez les informations relatives au dépôt si vous ne prévoyez pas de réinstaller `azdata-cli`.

   ```bash
   sudo rm /etc/apt/sources.list.d/azdata-cli.list
   ```

3. Supprimez la clé de dépôt.

   ```bash
   sudo rm /etc/apt/trusted.gpg.d/dpgswdist.v1.asc.gpg
   ```

4. Supprimez les dépendances qui ne sont plus nécessaires.

   ```bash
   sudo apt autoremove
   ```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)] ?](../../big-data-cluster/big-data-cluster-overview.md).

Utiliser azdata avec les [services de données dotés d’Azure Arc](/azure/azure-arc/data/)
