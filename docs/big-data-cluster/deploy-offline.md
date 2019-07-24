---
title: Déployer hors connexion
titleSuffix: SQL Server big data clusters
description: Découvrez comment effectuer un déploiement hors connexion d’un cluster SQL Server Big Data.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cd8b3128fc11037a5ade494813611d473c995f8f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419367"
---
# <a name="perform-an-offline-deployment-of-a-sql-server-big-data-cluster"></a>Effectuer un déploiement hors connexion d’un cluster SQL Server Big Data

Cet article explique comment effectuer un déploiement hors connexion d’un cluster SQL Server 2019 Big Data (version préliminaire). Les clusters Big Data doivent avoir accès à un référentiel d’ancrage à partir duquel extraire les images de conteneur. Une installation hors connexion est une installation où les images requises sont placées dans un référentiel d’ancrage privé. Ce dépôt privé est ensuite utilisé comme source d’image pour un nouveau déploiement.

## <a name="prerequisites"></a>Prérequis

- Moteur de docker 1.8 + sur n’importe quelle distribution de Linux prise en charge ou Docker pour Mac et Windows. Pour plus d’informations, consultez [Installer Docker](https://docs.docker.com/engine/installation/).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="load-images-into-a-private-repository"></a>Charger des images dans un dépôt privé

Les étapes suivantes décrivent comment extraire les images de conteneur du cluster Big Data du référentiel Microsoft, puis les transmettre dans votre dépôt privé.

> [!TIP]
> Les étapes suivantes expliquent le processus. Toutefois, pour simplifier la tâche, vous pouvez utiliser le [script automatisé](#automated) plutôt que d’exécuter manuellement ces commandes.

1. Tirez les images du conteneur du cluster Big Data en répétant la commande suivante. Remplacez `<SOURCE_IMAGE_NAME>` par chaque [nom d’image](#images). Remplacez `<SOURCE_DOCKER_TAG>` par la balise de la Big Data version de cluster, par exemple **2019-CTP 3.2-Ubuntu**.  

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/bdc/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG>
   ```

1. Connectez-vous au registre de l’ancrage privé cible.

   ```PowerShell
   docker login <TARGET_DOCKER_REGISTRY> -u <TARGET_DOCKER_USERNAME> -p <TARGET_DOCKER_PASSWORD>
   ```

1. Baliser les images locales à l’aide de la commande suivante pour chaque image:

   ```PowerShell
   docker tag mcr.microsoft.com/mssql/bdc/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG> <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

1. Transmettent les images locales dans le référentiel de la station d’accueil privée:

   ```PowerShell
   docker push <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

### <a id="images"></a>Images de conteneur de cluster Big Data

Les images de conteneur de cluster Big Data suivantes sont requises pour une installation hors connexion:

 - **mssql-appdeploy-init**
 - **mssql-monitor-fluentbit**
 - **mssql-monitor-collectd**
 - **mssql-server-data**
 - **mssql-hadoop**
 - **mssql-monitor-elasticsearch**
 - **mssql-monitor-influxdb**
 - **mssql-security-knox**
 - **mssql-mlserver-r-runtime**
 - **mssql-mlserver-py-runtime**
 - **mssql-controller**
 - **mssql-server-controller**
 - **mssql-monitor-grafana**
 - **mssql-monitor-kibana**
 - **mssql-service-proxy**
 - **mssql-app-service-proxy**
 - **mssql-ssis-app-runtime**
 - **mssql-monitor-telegraf**
 - **mssql-mleap-serving-runtime**
 - **MSSQL-sécurité-support**

## <a id="automated"></a>Script automatisé

Vous pouvez utiliser un script Python automatisé qui extrait automatiquement toutes les images de conteneur requises et les transmet dans un dépôt privé.

> [!NOTE]
> Python est un composant requis pour l’utilisation du script. Pour plus d’informations sur l’installation de Python, consultez la [documentation python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. À partir de bash ou de PowerShell, téléchargez le script à l’aide de la **boucle**:

   ```PowerShell
   curl -o push-bdc-images-to-custom-private-repo.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/offline/push-bdc-images-to-custom-private-repo.py"
   ```

1. Exécutez ensuite le script avec l’une des commandes suivantes:

   **Windows**

   ```PowerShell
   python deploy-sql-big-data-aks.py
   ```

   **Linux**

   ```bash
   sudo python deploy-sql-big-data-aks.py
   ```

1. Suivez les invites pour entrer le référentiel Microsoft et vos informations de référentiel privées. Une fois le script terminé, toutes les images requises doivent se trouver dans votre dépôt privé.

## <a name="install-tools-offline"></a>Installer les outils hors connexion

Les déploiements de cluster Big Data requièrent plusieurs outils, notamment **python**, **azdata**et **kubectl**. Procédez comme suit pour installer ces outils sur un serveur hors connexion.

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

### <a id="azdata"></a>Installer azdata hors connexion

1. Sur un ordinateur disposant d’un accès à Internet et de [python](https://wiki.python.org/moin/BeginnersGuide/Download), exécutez la commande suivante pour télécharger tous les packages **azdata** dans le dossier actif.

   ```PowerShell
   pip download -r https://aka.ms/azdata
   ```

1. Copiez les packages téléchargés et le fichier **Requirements. txt** sur l’ordinateur cible.

1. Exécutez la commande suivante sur l’ordinateur cible, en spécifiant le dossier dans lequel vous avez copié les fichiers précédents.

   ```PowerShell
   pip install --no-index --find-links <path-to-packages> -r <path-to-requirements.txt>
   ```

### <a id="kubectl"></a>Installer kubectl hors connexion

Pour installer **kubectl** sur un ordinateur hors connexion, procédez comme suit.

1. Utilisez la **boucle** pour télécharger **kubectl** dans un dossier de votre choix. Pour plus d’informations, consultez [installer kubectl binaire à l’aide](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl)de la boucle.

1. Copiez le dossier sur l’ordinateur cible.

## <a name="deploy-from-private-repository"></a>Déployer à partir d’un dépôt privé

Pour effectuer un déploiement à partir du dépôt privé, utilisez les étapes décrites dans le [Guide de déploiement](deployment-guidance.md), mais utilisez un fichier de configuration de déploiement personnalisé qui spécifie les informations de votre référentiel d’ancrage privé. Les commandes **azdata** suivantes montrent comment modifier les paramètres de l’ancrage dans un fichier de configuration de déploiement personnalisé nommé **Control. JSON**:

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.repository=<your-docker-repository>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.registry=<your-docker-registry>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.imageTag=<your-docker-image-tag>"
```

Le déploiement vous invite à entrer le nom d’utilisateur et le mot de passe de l’ancrage, ou vous pouvez les spécifier dans les variables d’environnement **DOCKER_USERNAME** et **DOCKER_PASSWORD** .

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les déploiements de cluster Big Data, consultez [comment déployer des clusters Big Data SQL Server sur Kubernetes](deployment-guidance.md).
