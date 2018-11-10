---
title: Comment déployer des données volumineuses de SQL Server clusters sur Kubernetes | Microsoft Docs
description: Découvrez comment déployer des clusters de données volumineuses de SQL Server 2019 (version préliminaire) sur Kubernetes.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 70d8b07caf618cb5f1629fc80f0ca1db8b73ad3c
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269862"
---
# <a name="how-to-deploy-sql-server-big-data-cluster-on-kubernetes"></a>Comment déployer SQL Server du cluster big data sur Kubernetes

Cluster de données volumineux de SQL Server peut être déployé en tant que conteneurs docker sur un cluster Kubernetes. Il s’agit d’une vue d’ensemble des étapes d’installation et de configuration :

- Configurer le cluster Kubernetes sur une machine virtuelle unique, un cluster de machines virtuelles, ou dans Azure Kubernetes Service (ACS).
- Installer l’outil de configuration de cluster **mssqlctl** sur votre ordinateur client.
- Déployer un cluster de données volumineux de SQL Server dans un cluster Kubernetes.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="prereqs"></a> Prérequis du cluster Kubernetes

Cluster de données volumineux de SQL Server requiert une version 1.10 d’edgeos minimale pour Kubernetes, pour le serveur et client. Pour installer une version spécifique sur le client kubectl, consultez [installer kubectl binaire via curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). Dernières versions de minikube et AKS sont au moins 1.10. Pour AKS, vous devez utiliser `--kubernetes-version` paramètre pour spécifier une version différente de celle par défaut.

> [!NOTE]
> Notez que les versions Kubernetes client et le serveur doivent être de version mineure + 1 ou -1. Pour plus d’informations, consultez [Kubernetes pris en charge les versions et composant de décalage](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

## <a id="kubernetes"></a> Configuration du cluster Kubernetes

Si vous avez déjà un cluster Kubernetes répondant aux critères ci-dessus les conditions préalables, vous pouvez passer directement à la [étape de déploiement](#deploy). Cette section suppose une compréhension élémentaire des concepts de Kubernetes.  Pour plus d’informations sur Kubernetes, consultez le [documentation Kubernetes](https://kubernetes.io/docs/home).

Vous pouvez choisir de déployer Kubernetes dans une des trois manières :

| Déploiement Kubernetes sur : | Description |
|---|---|
| **Minikube** | Un cluster Kubernetes à nœud unique dans une machine virtuelle. |
| **Services de Azure Kubernetes (AKS)** | Un service de conteneur Kubernetes géré dans Azure. |
| **Plusieurs ordinateurs** | Un cluster Kubernetes déployé sur des ordinateurs physiques ou virtuels à l’aide de **kubeadm** |

Pour obtenir des conseils sur la configuration d’une de ces options de cluster Kubernetes pour un cluster de données volumineuses de SQL Server, consultez les articles suivants :

   - [Configurer Minikube](deploy-on-minikube.md)
   - [Configurer Kubernetes sur Azure Kubernetes Service](deploy-on-aks.md)
   - [Configurer Kubernetes sur plusieurs ordinateurs avec kubeadm](deploy-with-kubeadm.md)
   
> [!TIP]
> Pour un exemple de script python qui déploie le cluster de données volumineux AKS et SQL Server, consultez [déployer un serveur SQL Server sur Azure Kubernetes Service (ACS) de cluster de données volumineuses](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a id="deploy"></a> Déployer le cluster de données volumineux de SQL Server

Une fois que vous avez configuré votre cluster Kubernetes, vous pouvez poursuivre le déploiement de cluster de données volumineux de SQL Server. 

> [!NOTE]
> Si vous mettez à niveau à partir d’une version antérieure, veuillez consulter la [mise à niveau de la section de cet article](#upgrade).

Pour déployer un cluster de données volumineuses dans Azure avec toutes les configurations par défaut pour un environnement de développement/test, suivez les instructions de cet article :

[Démarrage rapide : Déployer le cluster de données volumineux de SQL Server sur Kubernetes](quickstart-big-data-cluster-deploy.md)

Si vous souhaitez personnaliser votre configuration de cluster de données volumineuses en fonction des besoins de votre charge de travail, suivez l’ensemble suivant d’instructions.

## <a name="verify-kubernetes-configuration"></a>Vérifier la configuration de kubernetes

Exécutez le **kubectl** commande pour afficher la configuration du cluster. Assurez-vous que kubectl pointe vers le contexte de cluster correct.

```bash
kubectl config view
```

## <a id="mssqlctl"></a> Installer mssqlctl

**mssqlctl** est un utilitaire de ligne de commande écrit dans Python que permet aux administrateurs de démarrer et de gérer le cluster de données volumineuses via les API REST de cluster. La version de Python minimale requise est v3.5. Vous devez également avoir `pip` qui est utilisé pour télécharger et installer **mssqlctl** outil. 

> [!IMPORTANT]
> Si vous avez installé une version antérieure, vous devez supprimer le cluster *avant* la mise à niveau **mssqlctl** et l’installation de la nouvelle version. Pour plus d’informations, consultez [mise à niveau vers une nouvelle version](deployment-guidance.md#upgrade).

### <a name="windows-mssqlctl-installation"></a>Installation de mssqlctl Windows

1. Sur un client Windows, téléchargez le package Python nécessaire [ https://www.python.org/downloads/ ](https://www.python.org/downloads/). Pour python3.5.3 et versions ultérieures, pip3 est également installé lorsque vous installez Python. 

   > [!TIP] 
   > Lorsque vous installez Python3, sélectionnez cette option pour ajouter Python à votre chemin d’accès. Si vous ne le faites pas, vous pouvez êtes amené à constater où se trouve pip3 et l’ajouter manuellement à votre chemin d’accès.

1. Assurez-vous que vous disposez de la dernière version **demandes** package.

   ```cmd
   python -m pip install requests
   python -m pip install requests --upgrade
   ```

1. Installer **mssqlctl** avec la commande suivante :

   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.1 mssqlctl
   ```

### <a name="linux-mssqlctl-installation"></a>Installation de mssqlctl Linux

Sur Linux, vous devez installer le **python3** et **python3-pip** packages, puis exécutez `sudo pip3 install --upgrade pip`. Cette opération installe la dernière version 3.5 de Python et pip. L’exemple suivant montre le fonctionnement de ces commandes pour Ubuntu (si vous utilisez une autre plateforme, modifier les commandes pour votre gestionnaire de package) :

1. Installer les packages Python nécessaires :

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip && /
   sudo -H pip3 install --upgrade pip
   ```

1. Installer **mssqlctl** avec la commande suivante :

   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.1 mssqlctl
   ```

## <a name="define-environment-variables"></a>Définir des variables d’environnement

La configuration du cluster peut être personnalisée à l’aide d’un ensemble de variables d’environnement qui sont passés à la `mssqlctl create cluster` commande. La plupart des variables d’environnement est facultatif avec les valeurs par défaut comme indiqué ci-dessous. Notez qu’il n’y a des variables d’environnement telles que des informations d’identification qui exigent une entrée utilisateur.

| Variable d'environnement | Requis | Valeur par défaut | Description |
|---|---|---|---|
| **ACCEPT_EULA** | Oui | Néant | Acceptez le contrat de licence de SQL Server (par exemple, « Y »).  |
| **NOM_CLUSTER** | Oui | Néant | Le nom de l’espace de noms Kubernetes pour déployer SQLServer regrouper les données volumineuses en. |
| **CLUSTER_PLATFORM** | Oui | Néant | La plateforme du cluster Kubernetes est déployée. Peut être `aks`, `minikube`, `kubernetes`|
| **CLUSTER_COMPUTE_POOL_REPLICAS** | non | 1 | Le nombre de réplicas de pool de calcul à créer. Dans CTP2.0 uniquement à la valeur autorisée est 1. |
| **CLUSTER_DATA_POOL_REPLICAS** | non | 2 | Le nombre de données du pool pour créer les réplicas. |
| **CLUSTER_STORAGE_POOL_REPLICAS** | non | 2 | Le nombre de réplicas de pool de stockage à créer. |
| **DOCKER_REGISTRY** | Oui | TBD | Le Registre privé où sont stockées les images utilisées pour déployer le cluster. |
| **DOCKER_REPOSITORY** | Oui | TBD | Le dépôt privé au sein de la sous-clé de Registre ci-dessus où les images sont stockées.  Il est nécessaire pour la durée de la préversion publique contrôlée. |
| **DOCKER_USERNAME** | Oui | Néant | Le nom d’utilisateur pour accéder aux images de conteneur dans le cas où ils sont stockés dans un référentiel privé. Il est nécessaire pour la durée de la préversion publique contrôlée. |
| **DOCKER_PASSWORD** | Oui | Néant | Le mot de passe pour accéder au référentiel privé ci-dessus. Il est nécessaire pour la durée de la préversion publique contrôlée.|
| **DOCKER_EMAIL** | Oui | Néant | Adresse de messagerie associé au référentiel privé ci-dessus. Il est nécessaire pour la durée de la version préliminaire privée contrôlée. |
| **DOCKER_IMAGE_TAG** | non | Dernière | L’étiquette utilisée pour marquer les images. |
| **DOCKER_IMAGE_POLICY** | non | Always | Toujours forcer une opération d’extraction des images.  |
| **DOCKER_PRIVATE_REGISTRY** | Oui | 1 | Pour la période de la préversion publique contrôlée, cette valeur doit être définie sur 1. |
| **CONTROLLER_USERNAME** | Oui | Néant | Le nom d’utilisateur pour l’administrateur de cluster. |
| **CONTROLLER_PASSWORD** | Oui | Néant | Le mot de passe pour l’administrateur de cluster. |
| **KNOX_PASSWORD** | Oui | Néant | Le mot de passe utilisateur de Knox. |
| **MSSQL_SA_PASSWORD** | Oui | Néant | Le mot de passe de l’utilisateur d’association de sécurité pour l’instance principale de SQL. |
| **USE_PERSISTENT_VOLUME** | non | true | `true` Pour utiliser les revendications de Volume persistant Kubernetes pour le stockage de pod.  `false` Pour utiliser le stockage éphémère hôte pour le stockage de pod. Consultez le [persistance des données](concept-data-persistence.md) article pour plus d’informations. Si vous déployez SQL Server du cluster big data sur minikube et USE_PERSISTENT_VOLUME = true, vous devez définir la valeur de `STORAGE_CLASS_NAME=standard`. |
| **STORAGE_CLASS_NAME** | non | par défaut | Si `USE_PERSISTENT_VOLUME` est `true` cela indique le nom de la classe de stockage Kubernetes à utiliser. Consultez le [persistance des données](concept-data-persistence.md) article pour plus d’informations. Si vous déployez des données volumineuses de cluster sur minikube de SQL Server, le nom de classe de stockage par défaut est différent et vous devez le remplacer en définissant `STORAGE_CLASS_NAME=standard`. |
| **MASTER_SQL_PORT** | non | 31433 | Port TCP/IP utilisé par l’instance SQL principale est à l’écoute sur le réseau public. |
| **KNOX_PORT** | non | 30443 | Le port TCP/IP que Apache Knox écoute sur le réseau public. |
| **GRAFANA_PORT** | non | 30888 | Le port TCP/IP que l’application de surveillance de Grafana écoute sur le réseau public. |
| **KIBANA_PORT** | non | 30999 | Port TCP/IP utilisé par l’application de recherche de journal Kibana écoute sur le réseau public. |

> [!IMPORTANT]
>1. Pendant la durée de la préversion privée limitée, les informations d’identification du Registre Docker privé vous être fournies lors de triage votre [l’inscription EAP](https://aka.ms/eapsignup).
>1. Pour un cluster local intégrée **kubeadm**, la valeur de variable d’environnement `CLUSTER_PLATFORM` est `kubernetes`. Également, lorsque `USE_PERSISTENT_VOLUME=true`, vous devez préconfigurer une classe de stockage Kubernetes et passer d’à l’aide de la `STORAGE_CLASS_NAME`.
>1. Assurez-vous que vous encapsulez les mots de passe entre guillemets s’il contient des caractères spéciaux. Vous pouvez définir le MSSQL_SA_PASSWORD sur comme vous le souhaitez, mais assurez-vous qu’ils sont suffisamment complexes et n’utilisent pas le `!`, `&` ou `‘` caractères. Notez que les délimiteurs de guillemets doubles ne fonctionnent que dans les commandes bash.
>1. Le nom de votre cluster doit être uniquement alphanumériques minuscules, sans espaces. Tous les artefacts de Kubernetes (conteneurs, pods, les jeux avec état, services) pour le cluster seront créées dans un espace de noms avec le même nom que le cluster de nom spécifié.
>1. Le **SA** compte est un administrateur système sur l’instance principale de SQL Server qui est créé pendant l’installation. Après que la création de votre conteneur de SQL Server, la variable d’environnement MSSQL_SA_PASSWORD que vous avez spécifié est détectable en exécutant l’écho MSSQL_SA_PASSWORD $ dans le conteneur. Pour des raisons de sécurité, modifier votre mot de passe SA conformément aux bonnes pratiques documentées [ici](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Définition des variables d’environnement requises pour le déploiement d’un cluster de données volumineux diffère selon que vous utilisez un client Windows ou Linux.  Choisissez les étapes ci-dessous, selon le système d’exploitation que vous utilisez.

Initialiser les variables d’environnement, ils sont requis pour déployer le cluster :

### <a name="windows"></a>Windows

À l’aide d’une fenêtre CMD (pas PowerShell), configurer les variables d’environnement suivantes. N’utilisez pas les valeurs entre guillemets.

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=<minikube or aks or kubernetes>

SET CONTROLLER_USERNAME=<controller_admin_name – can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

SET DOCKER_REGISTRY=private-repo.microsoft.com
SET DOCKER_REPOSITORY=mssql-private-preview
SET DOCKER_USERNAME=<your username, credentials provided by Microsoft>
SET DOCKER_PASSWORD=<your password, credentials provided by Microsoft>
SET DOCKER_EMAIL=<your Docker email, use the username provided by Microsoft>
SET DOCKER_PRIVATE_REGISTRY="1"
```

### <a name="linux"></a>Linux

Initialiser les variables d’environnement suivantes. Dans l’interpréteur de commandes, vous pouvez utiliser des guillemets autour de chaque valeur.

```bash
export ACCEPT_EULA=Y
export CLUSTER_PLATFORM=<minikube or aks or kubernetes>

export CONTROLLER_USERNAME="<controller_admin_name – can be anything>"
export CONTROLLER_PASSWORD="<controller_admin_password – can be anything, password complexity compliant>"
export KNOX_PASSWORD="<knox_password – can be anything, password complexity compliant>"
export MSSQL_SA_PASSWORD="<sa_password_of_master_sql_instance, password complexity compliant>"

export DOCKER_REGISTRY="private-repo.microsoft.com"
export DOCKER_REPOSITORY="mssql-private-preview"
export DOCKER_USERNAME="<your username, credentials provided by Microsoft>"
export DOCKER_PASSWORD="<your password, credentials provided by Microsoft>"
export DOCKER_EMAIL="<your Docker email, use the username provided by Microsoft>"
export DOCKER_PRIVATE_REGISTRY="1"
```

### <a name="minikube-settings"></a>Paramètres de Minikube

Si vous déployez sur minikube et `USE_PERSISTENT_VOLUME=true` (valeur par défaut), vous devez également substituer la valeur par défaut `STORAGE_CLASS_NAME` variable d’environnement.

Utilisez la commande suivante sur Windows pour les déploiements de minikube :

```cmd
SET STORAGE_CLASS_NAME=standard
```

Utilisez la commande suivante sur Linux pour les déploiements de minikube :

```bash
export STORAGE_CLASS_NAME=standard
```

Ou bien, vous pouvez supprimer à l’aide de volumes persistants sur minikube en définissant `USE_PERSISTENT_VOLUME=false`.

### <a name="kubadm-settings"></a>Paramètres de Kubadm

Si vous déployez avec kubeadm sur vos propres ordinateurs physiques ou virtuels, vous devez préconfigurer une classe de stockage Kubernetes et passer d’à l’aide de la `STORAGE_CLASS_NAME`. Ou bien, vous pouvez supprimer à l’aide de volumes persistants en définissant `USE_PERSISTENT_VOLUME=false`. Pour plus d’informations sur le stockage persistant, consultez [persistance des données avec SQL Server du cluster big data sur Kubernetes](concept-data-persistence.md).

## <a name="deploy-sql-server-big-data-cluster"></a>Déployer le cluster Big Data de SQL Server

L’API de création de cluster est utilisé pour initialiser l’espace de noms Kubernetes et de déployer tous les pods d’application dans l’espace de noms. Pour déployer un cluster de données volumineux de SQL Server sur votre cluster Kubernetes, exécutez la commande suivante :

```bash
mssqlctl create cluster <name of your cluster>
```

Pendant l’amorçage de cluster, la fenêtre de commande client affiche l’état du déploiement. Vous pouvez également vérifier l’état du déploiement en exécutant ces commandes dans une fenêtre cmd différents :

```bash
kubectl get all -n <name of your cluster>
kubectl get pods -n <name of your cluster>
kubectl get svc -n <name of your cluster>
```

Vous pouvez voir un état et configuration pour chaque pod plus granulaire en exécutant :
```bash
kubectl describe pod <pod name> -n <name of your cluster>
```

Une fois que le pod de contrôleur est en cours d’exécution, vous pouvez utiliser l’onglet déploiement dans le portail d’Administration de Cluster pour surveiller le déploiement.

## <a id="masterip"></a> Obtenir l’instance de SQL Server Master et les adresses IP de cluster de données SQL Server

Une fois le script de déploiement terminée, vous pouvez obtenir l’adresse IP de l’instance principale de SQL Server à l’aide de la procédure décrite ci-dessous. Vous utiliserez cette adresse IP et port numéro 31433 pour se connecter à l’instance principale de SQL Server (par exemple :  **\<ip-address\>, 31433**). De même, les données de SQL Server big IP du cluster. Tous les points de terminaison de cluster sont décrites dans l’onglet points de terminaison de Service dans le portail d’Administration du Cluster ainsi. Vous pouvez utiliser le portail d’Administration de Cluster pour surveiller le déploiement. Vous pouvez accéder au portail à l’aide de l’externe IP adresse et numéro de port pour le `service-proxy-lb` (par exemple : **https://\<ip-address\>: 30777**). Informations d’identification pour accéder au portail d’administration est les valeurs de `CONTROLLER_USERNAME` et `CONTROLLER_PASSWORD` variables d’environnement fournis ci-dessus.

### <a name="aks"></a>AKS

Si vous utilisez AKS, Azure fournit le service de l’équilibreur de charge Azure. Exécutez la commande suivante :

```bash
kubectl get svc service-master-pool-lb -n <name of your cluster>
kubectl get svc service-security-lb -n <name of your cluster>
kubectl get svc service-proxy-lb -n <name of your cluster>
```

Recherchez le **External-IP** valeur affectée au service. Ensuite, connectez-vous à l’instance principale de SQL Server à l’aide de l’adresse IP sur le port 31433 (Ex :  **\<ip-address\>, 31433**) et au point de terminaison cluster de données SQL Server à l’aide de l’IP externe pour `service-security-lb` service. 

### <a name="minikube"></a>Minikube

Si vous utilisez Minikube, vous devez exécuter la commande suivante pour obtenir l’adresse IP, que vous devez vous connecter à. En plus de l’adresse IP, spécifiez le port pour le point de terminaison que vous avez besoin pour vous connecter à. Pour obtenir tous les points de terminaison de service pour 

```bash
minikube ip
```

Quelle que soit la plateforme vous s’exécutent votre cluster Kubernetes, pour obtenir tous les points de terminaison service déployés pour le cluster, exécutez la commande suivante :
```bash
kubectl get svc -n <name of your cluster>
```

## <a id="upgrade"></a> Mise à niveau vers une nouvelle version

Actuellement, la seule façon de mettre à niveau un cluster de données volumineux vers une nouvelle version consiste à supprimer et recréer le cluster manuellement. Chaque version comporte une version unique de **mssqlctl** qui n’est pas compatible avec la version précédente. En outre, si un cluster plus anciens avait télécharger une image sur un nouveau nœud, la dernière image peut-être pas compatible avec les anciennes images sur le cluster. Pour mettre à niveau vers la dernière version, procédez comme suit :

1. Avant de supprimer l’ancien cluster, sauvegardez les données sur l’instance principale de SQL Server et sur HDFS. Pour l’instance principale de SQL Server, vous pouvez utiliser [sauvegarde et restauration SQL Server](data-ingestion-restore-databse.md). Système de fichiers HDFS, vous [peut copier les données avec **curl**](data-ingestion-curl.md).

1. Supprimer l’ancien cluster avec le `mssqlctl delete cluster` commande.

   ```bash
    mssqlctl delete cluster <old-cluster-name>
   ```

1. Installez la dernière version de **mssqlctl**.
   
   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.1 mssqlctl
   ```

   > [!IMPORTANT]
   > Pour chaque version, le chemin d’accès à **mssqlctl** modifications. Même si vous avez installé précédemment **mssqlctl**, vous devez réinstaller à partir du chemin plus récent avant de créer le nouveau cluster.

1. Installer la dernière version en suivant les instructions dans le [déployer section](#deploy) de cet article. 

## <a name="next-steps"></a>Étapes suivantes

Après avoir correctement déployé SQL Server du cluster big data pour Kubernetes, [installer les outils de données volumineuses](deploy-big-data-tools.md) et essayer certaines des nouvelles fonctionnalités et découvrez [comment utiliser des blocs-notes en version préliminaire de SQL Server 2019](notebooks-guidance.md).
