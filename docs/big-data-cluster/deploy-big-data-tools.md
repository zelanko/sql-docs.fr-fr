---
title: Installer des outils de Big Data
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer les outils utilisés avec les clusters de données volumineuses de SQL Server 2019 (version préliminaire).
author: rothja
ms.author: jroth
manager: jroth
ms.date: 01/17/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: ffb63e3e7fb2891aeed1b9b26fbc43dddf69c78e
ms.sourcegitcommit: 0a4879dad09c6c42ad1ff717e4512cfea46820e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412967"
---
# <a name="install-sql-server-2019-big-data-tools"></a>Installer les outils de données volumineuses de SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit les outils clients qui doivent être installés pour la création, la gestion, et à l’aide de SQL Server 2019 données volumineuses de clusters (version préliminaire). La section suivante fournit une liste des outils et des liens vers des instructions d’installation. Avant de déployer un cluster de données volumineux, configurez les outils marqué comme requis sur Windows ou Linux.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>Outils de cluster Big data

Le tableau suivant répertorie les outils de cluster big data courants et comment les installer :

| Tool | Requis | Description | Installation |
|---|---|---|---|
| **mssqlctl** | Oui | Outil de ligne de commande pour installer et gérer un cluster de données volumineux. | [Installer](deploy-install-mssqlctl.md) |
| **kubectl**<sup>1</sup> | Oui | Outil de ligne de commande pour l’analyse du cluster Kuberentes sous-jacent ([plus d’informations](https://kubernetes.io/docs/tasks/tools/install-kubectl/)). | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management) |
| **Azure Data Studio (insiders)** | Oui | Outil graphique multiplateforme pour l’interrogation de SQL Server ([plus d’informations](https://docs.microsoft.com/sql/azure-data-studio/what-is?view=sql-server-ver15)). | [Installer](https://aka.ms/azdata-insiders) |
| **Extension de SQL Server 2019** | Oui | Extension pour Azure Data Studio qui prend en charge la connexion au cluster big data. Fournit également un Assistant de virtualisation des données. | [Installer](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure CLI**<sup>2</sup> | Pour AKS | Interface de ligne de commande moderne pour la gestion des services Azure. Utilisé avec les déploiements de cluster AKS big data ([plus d’informations](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)). | [Installer](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | Ce paramètre est facultatif | Interface de ligne de commande moderne pour l’interrogation de SQL Server ([plus d’informations](https://github.com/dbcli/mssql-cli/blob/master/README.rst)). | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | Pour certains scripts | Outil de ligne de commande hérité pour l’interrogation de SQL Server ([plus d’informations](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15)). | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **curl** <sup>3</sup> | Pour certains scripts | Outil de ligne de commande pour transférer des données avec des URL. | [Windows](https://curl.haxx.se/windows/) \| Linux : package d’installation de curl |

<sup>1</sup> vous devez utiliser kubectl 1,10 ou version ultérieure. En outre, la version de kubectl doit être plus ou moins une version secondaire de votre cluster Kubernetes. Si vous souhaitez installer une version spécifique sur le client kubectl, consultez [installer kubectl binaire via curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl) (sur Windows 10, utilisez cmd.exe, pas Windows PowerShell pour exécuter la commande curl). 

> [!TIP]
> Pour utiliser kubectl avec un cluster précédemment déployé sur Azure Kubernetes Service (AKS), vous devez définir le contexte de cluster avec la commande Azure CLI suivante :
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

<sup>2</sup> , vous devez utiliser Azure CLI version 2.0.4 ou version ultérieure. Exécutez `az --version` pour trouver la version, si nécessaire.

<sup>3</sup> si vous exécutez sur Windows 10, **curl** est déjà dans votre chemin d’accès lors de l’exécution à partir d’une invite de commande. Pour les autres versions de Windows, téléchargez **curl** en utilisant le lien et placez-le dans votre chemin d’accès.

## <a name="which-tools-are-required"></a>Quels outils sont nécessaires ?

Le tableau précédent fournit tous les outils courants qui sont utilisés avec les clusters de données volumineuses. Quels outils sont requis dépend de votre scénario. Mais en général, les outils suivants sont plus importantes pour la gestion, la connexion à et l’interrogé le cluster :

- **mssqlctl**
- **kubectl**
- **Azure Data Studio**
- **Extension de SQL Server 2019**

Les autres outils sont uniquement requises dans certains scénarios. **Azure CLI** peut être utilisé pour gérer des services Azure associés au déploiement de AKS. **MSSQL-cli** est un outil facultatif mais utile qui vous permet de se connecter à l’instance principale de SQL Server dans le cluster et exécuter des requêtes à partir de la ligne de commande. Et **sqlcmd** et **curl** sont requises si vous prévoyez d’installer des exemples de données avec le script de GitHub.

## <a name="next-steps"></a>Étapes suivantes

Après avoir configuré les outils, déployer un cluster de données volumineuses de SQL Server 2019 sur Kubernetes dans le nuage ou sur site. Pour plus d’informations, consultez les articles de déploiement suivants :

- [Démarrage rapide : Déployer le cluster de données volumineux de SQL Server sur Azure Kubernetes Service (AKS)](quickstart-big-data-cluster-deploy.md)
- [Comment déployer des clusters de données volumineuses de SQL Server sur Kubernetes](deployment-guidance.md)

Pour plus d’informations sur les clusters de données volumineuses, consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).
