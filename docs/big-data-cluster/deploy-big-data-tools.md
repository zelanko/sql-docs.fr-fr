---
title: Installer des outils de Big Data
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer les outils utilisés avec [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (version préliminaire).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cbb34d5cd209281a5c97d819c7741503d234ad2d
ms.sourcegitcommit: c4875c097e3aae1b76233777d15e0a0ec8e0d681
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342022"
---
# <a name="install-sql-server-2019-big-data-tools"></a>Installer les outils de Big Data SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit les outils clients qui doivent être installés pour la création, la gestion et l’utilisation de [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (version préliminaire). La section suivante fournit une liste d’outils et de liens vers les instructions d’installation. Avant de déployer un cluster Big Data, configurez les outils marqués comme requis sur Windows ou Linux.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>Outils de cluster Big Data

Le tableau suivant liste les outils de cluster Big Data courants et explique comment les installer :

| Tool | Requis | Description | Installation |
|---|---|---|---|
| **python** | Oui | Python est un langage de programmation de haut niveau, orienté objet, interprété et doté d’une sémantique dynamique. De nombreuses parties des clusters Big Data pour SQL Server utilisent Python. | [Installer python](#python)|
| **azdata** | Oui | Outil en ligne de commande pour l’installation et la gestion d’un cluster Big Data. | [Installer](deploy-install-azdata.md) |
| **kubectl**<sup>1</sup> | Oui | Outil en ligne de commande permettant de superviser le cluster Kuberentes sous-jacent ([plus d’informations](https://kubernetes.io/docs/tasks/tools/install-kubectl/)). | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-using-native-package-management) |
| **Azure Data Studio-SQL Server version Release candidate 2019 (RC)** | Oui | Outil graphique multiplateforme pour l’interrogation de SQL Server. | [Installer](#download-and-install-azure-data-studio-sql-server-2019-release-candidate-rc) |
| **Extension SQL Server 2019** | Oui | Extension pour Azure Data Studio qui prend en charge la connexion au cluster Big Data. Fournit également un assistant Virtualisation de données. | [Installer](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure CLI**<sup>2</sup> | Pour AKS | Interface de ligne de commande moderne pour la gestion des services Azure. Utilisée avec les déploiements de cluster Big Data AKS ([plus d’informations](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)). | [Installer](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | Ce paramètre est facultatif | Interface de ligne de commande moderne permettant d’interroger SQL Server ([plus d’informations](https://github.com/dbcli/mssql-cli/blob/master/README.rst)). | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | Pour certains scripts | Outil en ligne de commande hérité permettant d’interroger SQL Server ([plus d’informations](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15)). | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **curl** <sup>3</sup> | Pour certains scripts | Outil en ligne de commande pour transférer des données avec des URL. | [Windows](https://curl.haxx.se/windows/) \| Linux : installer le package d’installation |

<sup>1</sup> vous devez utiliser kubectl version 1,13 ou ultérieure. En outre, la version de kubectl doit être une version mineure plus une ou moins une de votre cluster Kubernetes. Si vous souhaitez installer une version spécifique sur le client kubectl, consultez [Installer le binaire kubectl via curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl) (sur Windows 10, utilisez cmd.exe et non Windows PowerShell pour exécuter curl).

> [!TIP]
> Pour utiliser kubectl avec un cluster déployé sur AKS (Azure Kubernetes Service), vous devez définir le contexte de cluster à l’aide de la commande Azure CLI suivante :
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

<sup>2</sup> Vous devez utiliser Azure CLI version 2.0.4 ou ultérieure. Exécutez `az --version` pour trouver la version, si nécessaire.

<sup>3</sup> Sur Windows 10, **curl** est déjà dans le chemin d’accès (PATH) quand vous effectuez l’exécution à partir d’une invite cmd. Pour les autres versions de Windows, téléchargez **curl** en utilisant le lien et placez-le dans votre chemin (PATH).

## <a name="which-tools-are-required"></a>Quels sont les outils requis ?

Le tableau précédent indique tous les outils courants qui sont utilisés avec les clusters Big Data. Les outils requis varient en fonction de votre scénario. Mais, en général, les outils suivants sont les plus importants pour gérer le cluster, s’y connecter et l’interroger :

- **azdata**
- **kubectl**
- **Azure Data Studio**
- **Extension SQL Server 2019**

Les autres outils sont requis uniquement dans certains scénarios. **Azure CLI** peut être utilisé pour gérer les services Azure associés aux déploiements AKS. **mssql-cli** est un outil facultatif mais utile qui vous permet de vous connecter à l’instance maître SQL Server dans le cluster et d’exécuter des requêtes à partir de la ligne de commande. Pour leur part, **sqlcmd** et **curl** sont nécessaires si vous envisagez d’installer des exemples de données avec le script GitHub.

### <a id="python"></a> Installer Python en mode hors connexion

1. Sur une machine disposant d’un accès à Internet, téléchargez l’un des fichiers compressés suivants contenant Python :

   | Système d’exploitation | Télécharger |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. Copiez le fichier compressé sur la machine cible et extrayez-le dans un dossier de votre choix.

1. Pour Windows uniquement, exécutez `installLocalPythonPackages.bat` à partir de ce dossier en indiquant comme paramètre le chemin complet au dossier.

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

## <a name="download-and-install-azure-data-studio-sql-server-2019-release-candidate-rc"></a>Télécharger et installer Azure Data Studio SQL Server version Release candidate 2019 (RC)

Azure Data Studio SQL Server 2019 RC offre des fonctionnalités et des fonctionnalités spécifiquement pour SQL Server 2019 RC.

Pour les versions de production normales de Azure Data Studio, suivez les instructions de la procédure de [téléchargement et d’installation Azure Data Studio](../azure-data-studio/download.md).

|Plateforme|Télécharger|Date de publication| Version |
|:---|:---|:---|:---|
|Windows|[Programme d’installation utilisateur (recommandé)](https://go.microsoft.com/fwlink/?linkid=2102435)<br>[Programme d’installation système](https://go.microsoft.com/fwlink/?linkid=2102523)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2102524)|27 août 2019 |RC 1.11.0-Insiders|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=2102436)|27 août 2019 |RC 1.11.0-Insiders|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=2102526)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2102437)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2102525)|27 août 2019 |RC 1.11.0-Insiders|

Pour plus d’informations sur la dernière version, consultez les [notes de publication](../big-data-cluster/release-notes-big-data-cluster.md).

### <a name="get-azure-data-studio-for-windows"></a>Obtenir Azure Data Studio pour Windows

Cette version de [!INCLUDE[name-sos](../includes/name-sos-short.md)] comprend une expérience du programme d’installation Windows standard et un fichier .zip.

Le *programme d'installation utilisateur* est recommandé, car il ne nécessite pas de privilèges administrateur, ce qui simplifie les installations et les mises à niveau. Le programme d’installation utilisateur ne requiert pas de privilèges administrateur, car il se trouve sous votre dossier utilisateur local AppData (LOCALAPPDATA). Le programme d’installation utilisateur fournit également une expérience de mise à jour en arrière-plan plus fluide. Pour plus d’informations, consultez [Configuration utilisateur pour Windows](https://code.visualstudio.com/updates/v1_26#_user-setup-for-windows).

**Programme d' installation utilisateur** (recommandé)

1. Téléchargez et exécutez le [[!INCLUDE[name-sos](../includes/name-sos-short.md)]programme d’installation *utilisateur* pour Windows](https://go.microsoft.com/fwlink/?linkid=2102435).
2. Démarrez l’application [!INCLUDE[name-sos-short](../includes/name-sos-short.md)].

**Programme d’installation système**

1. Téléchargez et exécutez le [[!INCLUDE[name-sos](../includes/name-sos-short.md)]programme d’installation *système* pour Windows](https://go.microsoft.com/fwlink/?linkid=2102523).
2. Démarrez l’application [!INCLUDE[name-sos-short](../includes/name-sos-short.md)].

**Fichier zip**

1. Téléchargez [[!INCLUDE[name-sos](../includes/name-sos-short.md)].zip pour Windows](https://go.microsoft.com/fwlink/?linkid=2102524).
2. Accédez au fichier téléchargé et extrayez-le.
3. Exécutez `\azuredatastudio-windows\azuredatastudio.exe`

### <a name="get-azure-data-studio-for-macos"></a>Obtenir Azure Data Studio pour macOS

1. Téléchargez [[!INCLUDE[name-sos](../includes/name-sos-short.md)] pour macOS](https://go.microsoft.com/fwlink/?linkid=2102436).
2. Pour développer le contenu du fichier zip, double-cliquez dessus.
3. Pour rendre [!INCLUDE[name-sos](../includes/name-sos-short.md)] disponible dans le *Launchpad*, faites glisser *Azure Data Studio.app* vers le dossier *Applications*.

### <a name="get-azure-data-studio-for-linux"></a>Obtenir Azure Data Studio pour Linux

1. Téléchargez [!INCLUDE[name-sos](../includes/name-sos-short.md)] à l’aide d’un des programmes d’installation ou de l’archive tar.gz :
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2102526)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2102437)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2102525)
1. Pour extraire le fichier et lancer [!INCLUDE[name-sos](../includes/name-sos-short.md)], ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   **Installation Debian :**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb

   azuredatastudio
   ```

   **Installation rpm :**
   ```bash
   cd ~
   yum install ./Downloads/azuredatastudio-linux-<version string>.rpm

   azuredatastudio
   ```

   **Installation tar.gz :**
   ```bash 
   cd ~ 
   cp ~/Downloads/azuredatastudio-linux-<version string>.tar.gz ~ 
   tar -xvf ~/azuredatastudio-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/azuredatastudio-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   azuredatastudio 
   ``` 

   > [!NOTE]
   > Sur Debian, Red Hat et Ubuntu, vous pouvez avoir des dépendances manquantes. Utilisez les commandes suivantes pour installer ces dépendances selon votre version de Linux :
   

   **Debian :** 
   ```bash
   sudo apt-get install libunwind8
   ```

   **Redhat :** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu :** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```

### <a name="supported-operating-systems"></a>Systèmes d'exploitation pris en charge

[!INCLUDE[name-sos](../includes/name-sos-short.md)] s’exécute sur Windows, macOS et Linux et est pris en charge sur les plateformes suivantes :

#### <a name="windows"></a>Windows

- Windows 10 (64 bits)
- Windows 8.1 (64 bits)
- Windows 8 (64 bits)
- Windows 7 (SP1) (64 bits) - Nécessite [KB2533623](https://www.microsoft.com/download/details.aspx?id=26767)
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2 (64 bits)
- Windows Server 2012 (64 bits)
- Windows Server 2008 R2 (64 bits)

#### <a name="macos"></a>macOS

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

#### <a name="linux"></a>Linux

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="next-steps"></a>Étapes suivantes

Après avoir configuré les outils, déployez un cluster Big Data SQL Server 2019 sur Kubernetes dans le cloud ou localement. Pour plus d’informations, consultez les articles suivants consacrés au déploiement :

- [Démarrage rapide : déployer un cluster Big Data SQL Server sur AKS (Azure Kubernetes Service)](quickstart-big-data-cluster-deploy.md)
- [Procédure de déploiement [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] sur Kubernetes](deployment-guidance.md)

Pour plus d’informations sur les clusters Big Data, voir [qu’est-ce que [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ?](big-data-cluster-overview.md).
