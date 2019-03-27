---
title: Comment déployer
titleSuffix: SQL Server 2019 big data clusters
description: Découvrez comment déployer des clusters de données volumineuses de SQL Server 2019 (version préliminaire) sur Kubernetes.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 5efefd5bc94aa8d1842ee244c947e48e90604834
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493731"
---
# <a name="how-to-deploy-sql-server-big-data-clusters-on-kubernetes"></a>Comment déployer des clusters de données volumineuses de SQL Server sur Kubernetes

Cluster de données volumineux de SQL Server peut être déployé en tant que conteneurs docker sur un cluster Kubernetes. Il s’agit d’une vue d’ensemble des étapes d’installation et de configuration :

- Configurer le cluster Kubernetes sur une machine virtuelle unique, un cluster de machines virtuelles, ou dans Azure Kubernetes Service (ACS).
- Installer l’outil de configuration de cluster **mssqlctl** sur votre ordinateur client.
- Déployer un cluster de données volumineux de SQL Server dans un cluster Kubernetes.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="prereqs"></a> Prérequis du cluster Kubernetes

Clusters de données volumineuses de SQL Server nécessitent au minimum Kubernetes d’au moins 1.10 d’edgeos pour le serveur et le client (kubectl).

> [!NOTE]
> Notez que les versions Kubernetes client et le serveur doivent être de version mineure + 1 ou -1. Pour plus d’informations, consultez [Kubernetes pris en charge les versions et composant de décalage](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

## <a id="kubernetes"></a> Configuration du cluster Kubernetes

Si vous avez déjà un cluster Kubernetes répondant aux critères ci-dessus les conditions préalables, vous pouvez passer directement à la [étape de déploiement](#deploy). Cette section suppose une compréhension élémentaire des concepts de Kubernetes.  Pour plus d’informations sur Kubernetes, consultez le [documentation Kubernetes](https://kubernetes.io/docs/home).

Vous pouvez choisir de déployer Kubernetes dans une des trois manières :

| Déploiement Kubernetes sur : | Description | Lien |
|---|---|---|
| **Minikube** | Un cluster Kubernetes à nœud unique dans une machine virtuelle. | [Instructions](deploy-on-minikube.md) |
| **Services de Azure Kubernetes (AKS)** | Un service de conteneur Kubernetes géré dans Azure. | [Instructions](deploy-on-aks.md) |
| **Plusieurs ordinateurs** | Un cluster Kubernetes déployé sur des ordinateurs physiques ou virtuels à l’aide de **kubeadm** | [Instructions](deploy-with-kubeadm.md) |
  
> [!TIP]
> Pour un exemple de script python qui déploie le cluster de données volumineux AKS et SQL Server, consultez [déployer un serveur SQL Server sur Azure Kubernetes Service (ACS) de cluster de données volumineuses](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a name="deploy-sql-server-2019-big-data-tools"></a>Déployer les outils de données volumineuses de SQL Server 2019

Avant de déployer le cluster de données volumineux de SQL Server 2019, tout d’abord [installer les outils de données volumineuses](deploy-big-data-tools.md):
- **mssqlctl**
- **kubectl**
- **Azure Data Studio**
- **Extension de SQL Server 2019**

## <a id="deploy"></a> Déployer le cluster de données volumineux de SQL Server

Une fois que vous avez configuré votre cluster Kubernetes, vous pouvez poursuivre le déploiement de cluster de données volumineux de SQL Server. 

> [!NOTE]
> Si vous mettez à niveau à partir d’une version antérieure, veuillez consulter la [mise à niveau de la section de cet article](#upgrade).

Pour déployer un cluster de données volumineuses dans Azure avec toutes les configurations par défaut pour un environnement de développement/test, suivez les instructions de cet article :

[Démarrage rapide : Déployer le cluster de données volumineux de SQL Server sur Kubernetes](quickstart-big-data-cluster-deploy.md)

Si vous souhaitez personnaliser votre déploiement de cluster de données volumineux en fonction de votre charge de travail a besoin, suivez les instructions dans le reste de cet article.

## <a name="verify-kubernetes-configuration"></a>Vérifier la configuration de kubernetes

Exécutez le **kubectl** commande pour afficher la configuration du cluster. Assurez-vous que kubectl pointe vers le contexte de cluster correct.

```bash
kubectl config view
```

## <a id="env"></a> Définir des variables d’environnement

La configuration du cluster peut être personnalisée à l’aide d’un ensemble de variables d’environnement qui sont passés à la `mssqlctl create cluster` commande. La plupart des variables d’environnement est facultatif avec les valeurs par défaut comme indiqué ci-dessous. Notez qu’il n’y a des variables d’environnement telles que des informations d’identification qui exigent une entrée utilisateur.

| Variable d'environnement | Requis | Valeur par défaut | Description |
|---|---|---|---|
| **ACCEPT_EULA** | Oui | N/A | Acceptez le contrat de licence de SQL Server (par exemple, « Oui »).  |
| **CLUSTER_NAME** | Oui | N/A | Le nom de l’espace de noms Kubernetes pour déployer SQLServer regrouper les données volumineuses en. |
| **CLUSTER_PLATFORM** | Oui | N/A | La plateforme du cluster Kubernetes est déployée. Peut être `aks`, `minikube`, `kubernetes`|
| **CLUSTER_COMPUTE_POOL_REPLICAS** | Non | 1 | Le nombre de réplicas de pool de calcul à créer. Dans CTP 2.4 uniquement à la valeur autorisée est 1. |
| **CLUSTER_DATA_POOL_REPLICAS** | Non | 2 | Le nombre de données du pool pour créer les réplicas. |
| **CLUSTER_STORAGE_POOL_REPLICAS** | Non | 2 | Le nombre de réplicas de pool de stockage à créer. |
| **DOCKER_REGISTRY** | Oui | TBD | Le Registre privé où sont stockées les images utilisées pour déployer le cluster. |
| **DOCKER_REPOSITORY** | Oui | TBD | Le dépôt privé au sein de la sous-clé de Registre ci-dessus où les images sont stockées.  Il est nécessaire pour la durée de la préversion publique contrôlée. |
| **DOCKER_USERNAME** | Oui | N/A | Le nom d’utilisateur pour accéder aux images de conteneur dans le cas où ils sont stockés dans un référentiel privé. Il est nécessaire pour la durée de la préversion publique contrôlée. |
| **DOCKER_PASSWORD** | Oui | N/A | Le mot de passe pour accéder au référentiel privé ci-dessus. Il est nécessaire pour la durée de la préversion publique contrôlée.|
| **DOCKER_EMAIL** | Oui | N/A | Votre adresse de messagerie. |
| **DOCKER_IMAGE_TAG** | Non | Dernière | L’étiquette utilisée pour marquer les images. |
| **DOCKER_IMAGE_POLICY** | Non | Always | Toujours forcer une opération d’extraction des images.  |
| **DOCKER_PRIVATE_REGISTRY** | Oui | N/A | Pour la période de la préversion publique contrôlée, vous devez définir cette valeur sur « 1 ». |
| **CONTROLLER_USERNAME** | Oui | N/A | Le nom d’utilisateur pour l’administrateur de cluster. |
| **CONTROLLER_PASSWORD** | Oui | N/A | Le mot de passe pour l’administrateur de cluster. |
| **KNOX_PASSWORD** | Oui | N/A | Le mot de passe utilisateur de Knox. |
| **MSSQL_SA_PASSWORD** | Oui | N/A | Le mot de passe de l’utilisateur d’association de sécurité pour l’instance principale de SQL. |
| **USE_PERSISTENT_VOLUME** | Non | true | `true` Pour utiliser les revendications de Volume persistant Kubernetes pour le stockage de pod.  `false` Pour utiliser le stockage éphémère hôte pour le stockage de pod. Consultez le [persistance des données](concept-data-persistence.md) article pour plus d’informations. Si vous déployez SQL Server du cluster big data sur minikube et USE_PERSISTENT_VOLUME = true, vous devez définir la valeur de `STORAGE_CLASS_NAME=standard`. |
| **STORAGE_CLASS_NAME** | Non | par défaut | Si `USE_PERSISTENT_VOLUME` est `true` cela indique le nom de la classe de stockage Kubernetes à utiliser. Consultez le [persistance des données](concept-data-persistence.md) article pour plus d’informations. Si vous déployez des données volumineuses de cluster sur minikube de SQL Server, le nom de classe de stockage par défaut est différent et vous devez le remplacer en définissant `STORAGE_CLASS_NAME=standard`. |
| **CONTROLLER_PORT** | Non | 30080 | Port TCP/IP utilisé par le service de contrôleur est à l’écoute sur le réseau public. |
| **MASTER_SQL_PORT** | Non | 31433 | Port TCP/IP utilisé par l’instance SQL principale est à l’écoute sur le réseau public. |
| **KNOX_PORT** | Non | 30443 | Le port TCP/IP que Apache Knox écoute sur le réseau public. |
| **PROXY_PORT** | Non | 30777 | Le port TCP/IP que service proxy écoute sur le réseau public. Il s’agit du port utilisé pour le portail informatique URL. |
| **GRAFANA_PORT** | Non | 30888 | Le port TCP/IP que l’application de surveillance de Grafana écoute sur le réseau public. |
| **KIBANA_PORT** | Non | 30999 | Port TCP/IP utilisé par l’application de recherche de journal Kibana écoute sur le réseau public. |


> [!IMPORTANT]
>1. Pendant la durée de la préversion privée limitée, les informations d’identification du Registre Docker privé vous être fournies lors de triage votre [l’inscription EAP](https://aka.ms/eapsignup).
>1. Pour un cluster local intégrée **kubeadm**, la valeur de variable d’environnement `CLUSTER_PLATFORM` est `kubernetes`. Également, lorsque `USE_PERSISTENT_VOLUME=true`, vous devez préconfigurer une classe de stockage Kubernetes et passer d’à l’aide de la `STORAGE_CLASS_NAME`.
>1. Assurez-vous que vous encapsulez les mots de passe entre guillemets s’il contient des caractères spéciaux. Vous pouvez définir le MSSQL_SA_PASSWORD sur comme vous le souhaitez, mais assurez-vous qu’ils sont suffisamment complexes et n’utilisent pas le `!`, `&` ou `'` caractères. Notez que les délimiteurs de guillemets doubles ne fonctionnent que dans les commandes bash.
>1. Le nom de votre cluster doit être uniquement alphanumériques minuscules, sans espaces. Tous les artefacts de Kubernetes (conteneurs, pods, les jeux avec état, services) pour le cluster seront créées dans un espace de noms avec le même nom que le cluster de nom spécifié.
>1. Le **SA** compte est un administrateur système sur l’instance principale de SQL Server qui est créé pendant l’installation. Après que la création de votre conteneur de SQL Server, la variable d’environnement MSSQL_SA_PASSWORD que vous avez spécifié est détectable en exécutant l’écho MSSQL_SA_PASSWORD $ dans le conteneur. Pour des raisons de sécurité, modifier votre mot de passe SA conformément aux bonnes pratiques documentées [ici](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Définition des variables d’environnement requises pour le déploiement d’un cluster de données volumineux diffère selon que vous utilisez un client Windows ou Linux.  Choisissez les étapes ci-dessous, selon le système d’exploitation que vous utilisez.

Initialiser les variables d’environnement, ils sont requis pour déployer le cluster :

### <a name="windows"></a>Windows

À l’aide d’une fenêtre CMD (pas PowerShell), configurer les variables d’environnement suivantes. N’utilisez pas les valeurs entre guillemets.

```cmd
SET ACCEPT_EULA=yes
SET CLUSTER_PLATFORM=<minikube or aks or kubernetes>

SET CONTROLLER_USERNAME=<controller_admin_name - can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password - can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password - can be anything, password complexity compliant>
SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

SET DOCKER_REGISTRY=private-repo.microsoft.com
SET DOCKER_REPOSITORY=mssql-private-preview
SET DOCKER_USERNAME=<your username, credentials provided by Microsoft>
SET DOCKER_PASSWORD=<your password, credentials provided by Microsoft>
SET DOCKER_EMAIL=<your email address>
SET DOCKER_PRIVATE_REGISTRY=1
```

### <a name="linux"></a>Linux

Initialiser les variables d’environnement suivantes. Dans l’interpréteur de commandes, vous pouvez utiliser des guillemets autour de chaque valeur.

```bash
export ACCEPT_EULA="yes"
export CLUSTER_PLATFORM="<minikube or aks or kubernetes>"

export CONTROLLER_USERNAME="<controller_admin_name - can be anything>"
export CONTROLLER_PASSWORD="<controller_admin_password - can be anything, password complexity compliant>"
export KNOX_PASSWORD="<knox_password - can be anything, password complexity compliant>"
export MSSQL_SA_PASSWORD="<sa_password_of_master_sql_instance, password complexity compliant>"

export DOCKER_REGISTRY="private-repo.microsoft.com"
export DOCKER_REPOSITORY="mssql-private-preview"
export DOCKER_USERNAME="<your username, credentials provided by Microsoft>"
export DOCKER_PASSWORD="<your password, credentials provided by Microsoft>"
export DOCKER_EMAIL="<your email address>"
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
mssqlctl cluster create --name <your-cluster-name>
```

Pendant l’amorçage de cluster, la fenêtre de commande client affiche l’état du déploiement. Pendant le processus de déploiement, vous devez voir une série de messages où il attend que le pod de contrôleur :

```output
2018-11-15 15:42:02.0209 UTC | INFO | Waiting for controller pod to be up...
```

Au bout de 10 à 20 minutes, vous devez averti que le pod de contrôleur est en cours d’exécution :

```output
2018-11-15 15:50:50.0300 UTC | INFO | Controller pod is running.
2018-11-15 15:50:50.0585 UTC | INFO | Controller Endpoint: https://111.111.111.111:30080
```

> [!IMPORTANT]
> La totalité du déploiement peut prendre beaucoup de temps en raison du temps nécessaire pour télécharger les images de conteneur pour les composants du cluster de données volumineuses. Toutefois, il ne doit pas prendre plusieurs heures. Si vous rencontrez des problèmes avec votre déploiement, consultez le [dépannage](#troubleshoot) section de cet article pour apprendre à surveiller et d’inspecter le déploiement.

Une fois le déploiement terminé, la sortie vous informe de réussite :

```output
2018-11-15 16:10:25.0583 UTC | INFO | Cluster state: Ready
2018-11-15 16:10:25.0583 UTC | INFO | Cluster deployed successfully.
```

## <a id="masterip"></a> Obtenir les points de terminaison de cluster big data

Une fois le script de déploiement terminée, vous pouvez obtenir l’adresse IP de l’instance principale de SQL Server à l’aide de la procédure décrite ci-dessous. Vous utiliserez cette adresse IP et port numéro 31433 pour se connecter à l’instance principale de SQL Server (par exemple :  **\<ip-address-of-endpoint-master-pool\>, 31433**). De même, vous pouvez vous connecter à l’adresse IP de cluster (passerelle HDFS/Spark) de données volumineuses associée de SQL Server le **-security du point de terminaison** service.

Les commandes de kubectl suivantes récupèrent des points de terminaison communs pour le cluster de données volumineuses :

```bash
kubectl get svc endpoint-master-pool -n <your-cluster-name>
kubectl get svc endpoint-security -n <your-cluster-name>
kubectl get svc endpoint-service-proxy -n <your-cluster-name>
```

Recherchez le **External-IP** valeur est assignée à chaque service.

Tous les points de terminaison de cluster sont également présentées dans le **points de terminaison de Service** onglet dans le portail d’Administration de Cluster. Vous pouvez accéder au portail à l’aide de l’externe IP adresse et numéro de port pour le `endpoint-service-proxy` (par exemple : **https://\<ip-address-of-endpoint-service-proxy\>: 30777/portail**). Informations d’identification pour accéder au portail d’administration est les valeurs de `CONTROLLER_USERNAME` et `CONTROLLER_PASSWORD` variables d’environnement fournis ci-dessus. Vous pouvez également utiliser le portail d’Administration de Cluster pour surveiller le déploiement.

Pour plus d’informations sur la façon de se connecter, consultez [se connecter à SQL Server cluster big data avec Azure Data Studio](connect-to-big-data-cluster.md).

### <a name="minikube"></a>Minikube

Si vous utilisez Minikube, vous devez exécuter la commande suivante pour obtenir l’adresse IP, que vous devez vous connecter à. En plus de l’adresse IP, spécifiez le port pour le point de terminaison que vous avez besoin pour vous connecter à. Pour obtenir tous les points de terminaison de service pour 

```bash
minikube ip
```

Quelle que soit la plateforme vous s’exécutent votre cluster Kubernetes, pour obtenir tous les points de terminaison service déployés pour le cluster, exécutez la commande suivante :
```bash
kubectl get svc -n <your-cluster-name>
```

## <a id="upgrade"></a> Mise à niveau vers une nouvelle version

Actuellement, la seule façon de mettre à niveau un cluster de données volumineux vers une nouvelle version consiste à supprimer et recréer le cluster manuellement. Chaque version comporte une version unique de **mssqlctl** qui n’est pas compatible avec la version précédente. En outre, si un cluster plus anciens avait télécharger une image sur un nouveau nœud, la dernière image peut-être pas compatible avec les anciennes images sur le cluster. Pour mettre à niveau vers la dernière version, procédez comme suit :

1. Avant de supprimer l’ancien cluster, sauvegardez les données sur l’instance principale de SQL Server et sur HDFS. Pour l’instance principale de SQL Server, vous pouvez utiliser [sauvegarde et restauration SQL Server](data-ingestion-restore-database.md). Système de fichiers HDFS, vous [peut copier les données avec **curl**](data-ingestion-curl.md).

1. Supprimer l’ancien cluster avec le `mssqlctl delete cluster` commande.

   ```bash
    mssqlctl cluster delete --name <old-cluster-name>
   ```

   > [!Important]
   > Utilisez la version de **mssqlctl** qui correspond à votre cluster. Ne supprimez pas un cluster plus anciens avec la version la plus récente de **mssqlctl**.

1. Désinstaller les anciennes versions de **mssqlctl**.

   ```bash
   pip3 uninstall mssqlctl
   ```

   > [!IMPORTANT]
   > Vous ne devez pas installer la nouvelle version de **mssqlctl** sans désinstaller les anciennes versions tout d’abord.

1. Installez la dernière version de **mssqlctl**. 

   **Windows :**

   ```powershell
   pip3 install -r  https://private-repo.microsoft.com/python/ctp-2.4/mssqlctl/requirements.txt
   ```

   **Linux :**

   ```bash
   pip3 install -r  https://private-repo.microsoft.com/python/ctp-2.4/mssqlctl/requirements.txt --user
   ```

   > [!IMPORTANT]
   > Pour chaque version, le chemin d’accès à **mssqlctl** modifications. Même si vous avez installé précédemment **mssqlctl**, vous devez réinstaller à partir du chemin plus récent avant de créer le nouveau cluster.

1. Installer la dernière version en suivant les instructions dans le [déployer section](#deploy) de cet article. 

## <a id="troubleshoot"></a> Surveillance et dépannage

Pour surveiller et résoudre les problèmes d’un déploiement, utilisez **kubectl** pour inspecter l’état du cluster et pour détecter les problèmes potentiels. À tout moment pendant un déploiement, vous pouvez ouvrir une fenêtre de commande différentes pour exécuter les tests suivants.

1. Examiner l’état des pods dans votre cluster.

   ```cmd
   kubectl get pods -n <your-cluster-name>
   ```

   Au cours du déploiement, pods avec un **état** de **ContainerCreating** sont toujours démarrent. Si le déploiement se bloque pour une raison quelconque, cela peut vous donner une idée où il est possible. Examinez également le **prêt** colonne. Cela indique le nombre de conteneurs ont démarré dans le pod. Notez que les déploiements peuvent prendre trente minutes ou plus, selon votre configuration et votre réseau. Une grande partie de ce temps est consacré à télécharger les images de conteneur pour les différents composants. Le tableau suivant présente un exemple de modification de sortie de deux conteneurs lors d’un déploiement :

   ```output
   PS C:\> kubectl get pods -n sbdc8
   NAME                                     READY   STATUS              RESTARTS   AGE
   mssql-controller-h79ft                   4/4     Running             0          13m
   mssql-storage-pool-default-0             0/7     ContainerCreating   0          6m
   ```

1. Décrire un pod individuel pour plus d’informations. La commande suivante inspecte le `mssql-storage-pool-default-0` pod.

   ```cmd
   kubectl describe pod mssql-storage-pool-default-0 -n <your-cluster-name>
   ```

   Cette action génère des informations détaillées sur le pod, y compris les événements récents. Si une erreur s’est produite, vous pouvez parfois trouver l’erreur ici.

1. Récupérer les journaux pour les conteneurs en cours d’exécution dans un bloc. La commande suivante récupère les journaux de tous les conteneurs en cours d’exécution dans le bloc nommé `mssql-storage-pool-default-0` , puis les génère dans un fichier nommé `pod-logs.txt`:

   ```cmd
   kubectl logs mssql-storage-pool-default-0 --all-containers=true -n <your-cluster-name> > pod-logs.txt
   ```

1. Passez en revue les services de cluster pendant et après un déploiement avec la commande suivante :

   ```cmd
   kubectl get svc -n <your-cluster-name>
   ```

   Ces services prennent en charge les connexions internes et externes pour le cluster de données volumineux. Pour les connexions externes, les services suivants sont utilisés :

   | Service | Description |
   |---|---|
   | **endpoint-master-pool** | Fournit l’accès à l’instance principale.<br/>(**EXTERNAL-IP, 31433** et **SA** utilisateur) |
   | **endpoint-controller** | Prend en charge des outils et les clients qui gèrent le cluster. |
   | **endpoint-service-proxy** | Fournit l’accès à la [portail d’Administration de Cluster](cluster-admin-portal.md).<br/>(https://**EXTERNAL-IP**: 30777/portail)|
   | **endpoint-security** | Fournit l’accès à la passerelle HDFS/Spark.<br/>(**EXTERNAL-IP** et **racine** utilisateur) |

1. Utilisez le [portail d’Administration de Cluster](cluster-admin-portal.md) pour surveiller le déploiement sur le **déploiement** onglet. Vous devez attendre la **proxy de service de point de terminaison** démarrage avant d’accéder à ce portail, donc il n’est pas disponible au début d’un déploiement du service.

> [!TIP]
> Pour plus d’informations sur la résolution des problèmes de cluster, consultez [commandes Kubectl pour la surveillance et dépannage des clusters de données volumineuses de SQL Server](cluster-troubleshooting-commands.md).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez les ressources suivantes :

- [Quelles sont les clusters SQL Server 2019 big data ?](big-data-cluster-overview.md)
- [Atelier : Architecture de clusters de données volumineuses de Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)