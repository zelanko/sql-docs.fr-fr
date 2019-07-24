---
title: Installer des outils de Big Data
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer les outils utilisés avec les clusters SQL Server 2019 Big Data (version préliminaire).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 757209ff89fd40dcc737b65d3b19f2a7d4ef247b
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419454"
---
# <a name="install-sql-server-2019-big-data-tools"></a>Installer les outils de Big Data SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit les outils clients qui doivent être installés pour la création, la gestion et l’utilisation des clusters SQL Server 2019 Big Data (version préliminaire). La section suivante fournit une liste d’outils et des liens vers les instructions d’installation. Avant de déployer un cluster Big Data, configurez les outils marqués comme requis sur Windows ou Linux.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>Outils de cluster Big Data

Le tableau suivant répertorie les outils courants de cluster Big Data et explique comment les installer:

| Tool | Obligatoire | Description | Installation |
|---|---|---|---|
| **Software** | Oui | Python est un langage de programmation de haut niveau, orienté objet et interprété avec une sémantique dynamique. De nombreuses parties de Big Data clusters pour SQL Server utilisent Python. | [Installer python](#python)|
| **azdata** | Oui | Outil en ligne de commande pour l’installation et la gestion d’un cluster Big Data. | [Installer](deploy-install-azdata.md) |
| **kubectl**<sup>1</sup> | Oui | Outil en ligne de commande permettant de surveiller le cluster Kuberentes sous-jacent ([plus d’informations](https://kubernetes.io/docs/tasks/tools/install-kubectl/)). | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management) |
| **Azure Data Studio (Insiders)** | Oui | Outil graphique multiplateforme pour l’interrogation des SQL Server ([plus d’informations](https://docs.microsoft.com/sql/azure-data-studio/what-is?view=sql-server-ver15)). | [Installer](https://aka.ms/azdata-insiders) |
| **SQL Server extension 2019** | Oui | Extension pour Azure Data Studio qui prend en charge la connexion au cluster Big Data. Fournit également un assistant de virtualisation des données. | [Installer](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure CLI** <sup>2</sup> | Pour AKS | Interface de ligne de commande moderne pour la gestion des services Azure. Utilisé avec AKS Big Data les déploiements de cluster ([plus d’informations](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)). | [Installer](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | Facultatif | Interface de ligne de commande moderne pour l’interrogation des SQL Server ([plus d’informations](https://github.com/dbcli/mssql-cli/blob/master/README.rst)). | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | Pour certains scripts | Outil en ligne de commande hérité pour l’interrogation de SQL Server ([plus d’informations](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15)). | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **curl** <sup>3</sup> | Pour certains scripts | Outil en ligne de commande pour transférer des données avec des URL. | [Windows](https://curl.haxx.se/windows/) \| Linux: installer le package bouclé |

<sup>1</sup> vous devez utiliser kubectl version 1,10 ou ultérieure. En outre, la version de kubectl doit être plus ou moins une version mineure de votre cluster Kubernetes. Si vous souhaitez installer une version spécifique sur le client kubectl, consultez [installer kubectl binaire via la boucle](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl) (sur Windows 10, utilisez cmd. exe et non Windows PowerShell pour exécuter la boucle). 

> [!TIP]
> Pour utiliser kubectl avec un cluster précédemment déployé sur le service Azure Kubernetes (AKS), vous devez définir le contexte de cluster à l’aide de la commande Azure CLI suivante:
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

<sup>2</sup> vous devez utiliser Azure CLI version 2.0.4 ou ultérieure. Exécutez `az --version` pour trouver la version si nécessaire.

<sup>3</sup> si vous exécutez sur Windows 10, la **boucle** est déjà dans votre chemin d’accès lorsque vous exécutez à partir d’une invite de commandes. Pour les autres versions de Windows, téléchargez la **boucle** en utilisant le lien et placez-le dans votre chemin d’accès.

## <a name="which-tools-are-required"></a>Quels sont les outils requis?

Le tableau précédent fournit tous les outils courants qui sont utilisés avec les clusters Big Data. Les outils requis varient en fonction de votre scénario. Mais en général, les outils suivants sont les plus importants pour la gestion, la connexion et l’interrogation du cluster:

- **azdata**
- **kubectl**
- **Azure Data Studio**
- **SQL Server extension 2019**

Les autres outils sont requis uniquement dans certains scénarios. **Azure CLI** peut être utilisé pour gérer les services Azure associés aux déploiements AKS. **MSSQL-CLI** est un outil facultatif mais utile qui vous permet de vous connecter à l’instance SQL Server Master dans le cluster et d’exécuter des requêtes à partir de la ligne de commande. Et **sqlcmd** et **roulage** sont nécessaires si vous envisagez d’installer des exemples de données avec le script github.

### <a id="python"></a>Installer Python en mode hors connexion

1. Sur un ordinateur disposant d’un accès à Internet, téléchargez l’un des fichiers compressés suivants contenant Python:

   | Système d’exploitation | Télécharger |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. Copiez le fichier compressé sur l’ordinateur cible et extrayez-le dans un dossier de votre choix.

1. Pour Windows uniquement, exécutez `installLocalPythonPackages.bat` à partir de ce dossier et transmettez le chemin d’accès complet au même dossier qu’un paramètre.

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

## <a name="next-steps"></a>Étapes suivantes

Après avoir configuré les outils, déployez un cluster SQL Server 2019 Big Data vers Kubernetes dans le Cloud ou localement. Pour plus d’informations, consultez les articles suivants sur le déploiement:

- [Démarrage rapide : Déployer SQL Server Cluster Big Data sur Azure Kubernetes service (AKS)](quickstart-big-data-cluster-deploy.md)
- [Comment déployer des clusters de Big Data SQL Server sur Kubernetes](deployment-guidance.md)

Pour plus d’informations sur les clusters Big Data, consultez [que sont SQL Server les clusters Big Data 2019?](big-data-cluster-overview.md).
