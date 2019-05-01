---
title: Déployer en mode hors connexion
titleSuffix: SQL Server big data clusters
description: Découvrez comment effectuer un déploiement hors connexion d’un cluster de données volumineuses de SQL Server.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: afd7c0e3b8fcf92721e95231175cb33d81c6775e
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63759146"
---
# <a name="perform-an-offline-deployment-of-a-sql-server-big-data-cluster"></a>Effectuer un déploiement hors connexion d’un cluster de données volumineuses de SQL Server

Cet article décrit comment effectuer un déploiement hors connexion d’un cluster de données volumineuses de SQL Server 2019 (version préliminaire). Les clusters de données volumineuses doivent avoir accès à un référentiel de Docker à partir de laquelle pour extraire des images de conteneur. Une installation hors connexion est un endroit où les images nécessaires sont placés dans un référentiel Docker privé. Ce référentiel privé est ensuite utilisé comme la source de l’image d’un nouveau déploiement.

## <a name="prerequisites"></a>Prérequis

- Moteur de docker 1.8 + sur n’importe quelle distribution de Linux prise en charge ou Docker pour Mac et Windows. Pour plus d’informations, consultez [Installer Docker](https://docs.docker.com/engine/installation/).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="load-images-into-a-private-repository"></a>Charger des images dans un référentiel privé

Les étapes suivantes décrivent comment extraire des images de conteneur du cluster de données volumineux à partir du référentiel Microsoft et les placer dans votre référentiel privé.

> [!TIP]
> Les étapes suivantes expliquent le processus. Toutefois, pour simplifier la tâche, vous pouvez utiliser la [script automatisé](#automated) au lieu d’exécuter manuellement ces commandes.

1. Tout d’abord, ouvrez une session le Registre de Microsoft Docker avec le **connexion docker** commande. Utilisez le nom d’utilisateur et le mot de passe que vous fournie dans le cadre du programme d’Adoption anticipée de Microsoft.

   ```PowerShell
   docker login private-repo.microsoft.com -u  <SOURCE_DOCKER_USERNAME> -p <SOURCE_DOCKER_PASSWORD>
   ```

   > [!TIP]
   > Ces commandes utilisent PowerShell par exemple, mais vous pouvez les exécuter à partir de cmd, bash ou n’importe quel interface de commande qui peut s’exécuter docker. Sur Linux, ajoutez `sudo` à chaque commande.

1. Extraire des images de conteneur du cluster de données volumineux en répétant la commande suivante. Remplacez `<SOURCE_IMAGE_NAME>` avec chaque [nom de l’image](#images). Remplacez `<SOURCE_DOCKER_TAG>` avec la balise pour les données volumineuses de cluster version, tel que **ctp2.5**.  

   ```PowerShell
   docker pull private-repo.microsoft.com/mssql-private-preview/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG>
   ```

1. Ouvrez une session le privé cible Registre Docker.

   ```PowerShell
   docker login <TARGET_DOCKER_REGISTRY> -u <TARGET_DOCKER_USERNAME> -p <TARGET_DOCKER_PASSWORD>
   ```

1. Marquer les images locales avec la commande suivante pour chaque image :

   ```PowerShell
   docker tag private-repo.microsoft.com/mssql-private-preview/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG> <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

1. Envoyer les images locales vers le référentiel Docker privé :

   ```PowerShell
   docker push <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

### <a id="images"></a> Images de conteneur du cluster Big data

Les images de conteneur de cluster big data suivantes sont requises pour une installation hors connexion :

 - **mssql-appdeploy-init**
 - **mssql-monitor-fluentbit**
 - **mssql-monitor-collectd**
 - **mssql-server-data**
 - **mssql-hadoop**
 - **mssql-java**
 - **mssql-mlservices-pythonserver**
 - **mssql-mlservices-rserver**
 - **mssql-monitor-elasticsearch**
 - **mssql-monitor-influxdb**
 - **mssql-security-knox**
 - **mssql-mlserver-r-runtime**
 - **mssql-mlserver-py-runtime**
 - **mssql-controller**
 - **mssql-portal**
 - **mssql-server-controller**
 - **mssql-monitor-grafana**
 - **mssql-monitor-kibana**
 - **mssql-service-proxy**
 - **mssql-app-service-proxy**
 - **mssql-ssis-app-runtime**
 - **mssql-monitor-telegraf**

## <a id="automated"></a> Script automatisé

Vous pouvez utiliser un script python automatisés qui sera automatiquement extraire toutes les images de conteneur requis et les placer dans un référentiel privé.

> [!NOTE]
> Python est un prérequis pour utiliser le script. Pour plus d’informations sur l’installation de Python, consultez le [documentation Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. À partir de bash ou PowerShell, téléchargez le script avec **curl**:

   ```PowerShell
   curl -o push-bdc-images-to-custom-private-repo.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/offline/push-bdc-images-to-custom-private-repo.py"
   ```

1. Puis exécutez le script avec l’une des commandes suivantes :

   **Windows :**

   ```PowerShell
   python deploy-sql-big-data-aks.py
   ```

   **Linux :**

   ```bash
   sudo python deploy-sql-big-data-aks.py
   ```

1. Suivez les invites pour entrer le référentiel Microsoft et vos informations de référentiel privé. Une fois le script terminé, tous les requis images doivent se trouver dans votre référentiel privé.

## <a name="install-tools-offline"></a>Installer les outils en mode hors connexion

Déploiements de cluster Big data requièrent plusieurs outils, y compris **Python**, **mssqlctl**, et **kubectl**. Utilisez les étapes suivantes pour installer ces outils sur un serveur en mode hors connexion.

### <a id="python"></a> Installer python en mode hors connexion

1. Sur un ordinateur connecté à internet, téléchargez un des fichiers compressés suivantes contenant les Python :

   | Système d'exploitation | Télécharger |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. Copiez le fichier compressé sur l’ordinateur cible et extrayez-le dans un dossier de votre choix.

1. Pour Windows uniquement, exécutez `installLocalPythonPackages.bat` à partir de ce dossier et le passage du chemin d’accès complet dans le même dossier en tant que paramètre.

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

### <a id="mssqlctl"></a> Installer mssqlctl hors connexion

1. Sur un ordinateur connecté à internet et [Python](https://wiki.python.org/moin/BeginnersGuide/Download), exécutez la commande suivante pour télécharger tous les désactiver le **mssqlctl** packages dans le dossier actif.

   ```PowerShell
   pip download -r https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt
   ```

1. Téléchargez le **requirements.txt** fichier.

   ```PowerShell
   curl -o requirements.txt "https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt"
   ```

1. Copiez les packages téléchargés et le **requirements.txt** fichier sur l’ordinateur cible.

1. Exécutez la commande suivante sur l’ordinateur cible, en spécifiant le dossier que vous avez copié les fichiers précédents dans.

   ```PowerShell
   pip install --no-index --find-links <path-to-packages> -r <path-to-requirements.txt>
   ```

### <a id="kubectl"></a> Installer kubectl hors connexion

Pour installer **kubectl** à un ordinateur hors connexion, procédez comme suit.

1. Utilisez **curl** télécharger **kubectl** dans un dossier de votre choix. Pour plus d’informations, consultez [installer binaire kubectl à l’aide de curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl).

1. Copiez le dossier sur l’ordinateur cible.

## <a name="deploy-with-from-repository"></a>Déployer avec à partir du référentiel

Pour déployer à partir du référentiel privé, utilisez les étapes décrites dans le [guide de déploiement](deployment-guidance.md), mais personnaliser les variables d’environnement suivantes pour correspondre à votre référentiel Docker privé.

- **DOCKER_REGISTRY**  
- **DOCKER_REPOSITORY**
- **DOCKER_USERNAME**
- **DOCKER_PASSWORD**  
- **DOCKER_EMAIL**
- **DOCKER_IMAGE_TAG**

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les déploiements de cluster big data, consultez [comment déployer des données volumineuses de SQL Server clusters sur Kubernetes](deployment-guidance.md).
