---
title: Installer azdata avec yum
titleSuffix: ''
description: Découvrez comment installer l’outil azdata avec yum.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7f2f06c22b56e2afbe7c51198efbbfe1eecbc8c4
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725270"
---
# <a name="install-azdata-with-yum"></a>Installer `azdata` avec yum

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

Pour les distributions Linux avec `yum` il existe un package pour le `azdata-cli`. Le package CLI a été testé sur des versions Linux qui utilisent `yum` :

- RHEL 7, RHEL 8

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-yum"></a>Installer avec yum

>[!IMPORTANT]
> Le package RPM de `azdata-cli` dépend du package python3. Sur votre système, il doit s’agir d’une version Python antérieure à l’exigence de *Python 3.6.x*. Si cela vous pose un problème, recherchez un remplacement au package python3 ou suivez les instructions d’installation manuelle qui utilisent [`pip`](../install/deploy-install-azdata-pip.md).

1. Installez les dépendances nécessaires pour installer `azdata-cli`.

   ```bash
   sudo yum install -y curl
   ```

1. Importez la clé de référentiel Microsoft.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

1. Créez des informations de dépôt local.

   Pour un client RHEL 7, exécutez :

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```
  
   Pour un client RHEL 8, exécutez :

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/8/prod.repo
   ```

1. Installez `azdata-cli`.

   ```bash
   sudo yum install azdata-cli
   ```

## <a name="verify-install"></a>Vérifier l’installation

```bash
azdata
azdata --version
```

## <a name="update"></a>Update

Mettez à jour le `azdata-cli` avec la commande `yum update`.

```bash
sudo yum update azdata-cli
```

## <a name="uninstall"></a>Désinstaller l’interface

1. Supprimez le package de votre système.

   ```bash
   sudo yum remove azdata-cli
   ```

1. Supprimez les informations relatives au dépôt si vous ne prévoyez pas de réinstaller `azdata-cli`.

   ```bash
   sudo rm /etc/yum.repos.d/azdata-cli.repo
   ```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)] ?](../../big-data-cluster/big-data-cluster-overview.md).

Utiliser azdata avec les [services de données dotés d’Azure Arc](/azure/azure-arc/data/)
