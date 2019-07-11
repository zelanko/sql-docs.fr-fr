---
title: Conseils pour le déploiement
titleSuffix: SQL Server big data clusters
description: Découvrez comment déployer des clusters de données volumineuses de SQL Server 2019 (version préliminaire) sur Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e04986691b52149f0918b1559f1f3db1d99cab38
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728794"
---
# <a name="how-to-deploy-sql-server-big-data-clusters-on-kubernetes"></a>Comment déployer des clusters de données volumineuses de SQL Server sur Kubernetes

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cluster de données volumineux de SQL Server est déployé en tant que conteneurs docker sur un cluster Kubernetes. Il s’agit d’une vue d’ensemble des étapes d’installation et de configuration :

- Configurer un cluster Kubernetes sur une machine virtuelle unique, un cluster de machines virtuelles, ou dans Azure Kubernetes Service (ACS).
- Installer l’outil de configuration de cluster **mssqlctl** sur votre ordinateur client.
- Déployer un cluster de données volumineuses de SQL Server dans un cluster Kubernetes.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-sql-server-2019-big-data-tools"></a>Installer les outils de données volumineuses de SQL Server 2019

Avant de déployer un cluster de données volumineux SQL Server 2019, tout d’abord [installer les outils de données volumineuses](deploy-big-data-tools.md):

- **mssqlctl**
- **kubectl**
- **Azure Data Studio**
- **Extension de SQL Server 2019**

## <a id="prereqs"></a> Conditions préalables de Kubernetes

Clusters de données volumineuses de SQL Server nécessitent au minimum Kubernetes d’au moins 1.10 d’edgeos pour le serveur et le client (kubectl).

> [!NOTE]
> Notez que les versions Kubernetes client et le serveur ne doivent pas dépasser la version mineure + 1 ou -1. Pour plus d’informations, consultez [Kubernetes pris en charge les versions et composant de décalage](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

### <a id="kubernetes"></a> Configuration du cluster Kubernetes

Si vous avez déjà un cluster Kubernetes qui remplit les conditions préalables ci-dessus, vous pouvez passer directement à la [étape de déploiement](#deploy). Cette section suppose une compréhension élémentaire des concepts de Kubernetes.  Pour plus d’informations sur Kubernetes, consultez le [documentation Kubernetes](https://kubernetes.io/docs/home).

Vous pouvez choisir de déployer Kubernetes dans une des trois manières :

| Déploiement Kubernetes sur : | Description | Lien |
|---|---|---|
| **Services de Azure Kubernetes (AKS)** | Un service de conteneur Kubernetes géré dans Azure. | [Instructions](deploy-on-aks.md) |
| **Plusieurs ordinateurs (kubeadm)** | Un cluster Kubernetes déployé sur des ordinateurs physiques ou virtuels à l’aide de **kubeadm** | [Instructions](deploy-with-kubeadm.md) |
| **Minikube** | Un cluster Kubernetes à nœud unique dans une machine virtuelle. | [Instructions](deploy-on-minikube.md) |

> [!TIP]
> Pour un exemple de script python qui déploie AKS et un serveur SQL Server du cluster big data en une seule étape, consultez [Guide de démarrage rapide : Déployer SQL Server sur Azure Kubernetes Service (ACS) de cluster de données volumineuses](quickstart-big-data-cluster-deploy.md).

### <a name="verify-kubernetes-configuration"></a>Vérifier la configuration de Kubernetes

Exécutez le **kubectl** commande pour afficher la configuration du cluster. Assurez-vous que kubectl pointe vers le contexte de cluster correct.

```bash
kubectl config view
```

Une fois que vous avez configuré votre cluster Kubernetes, vous pouvez poursuivre le déploiement d’un nouveau cluster de données volumineuses de SQL Server. Si vous mettez à niveau depuis une version précédente, consultez [la mise à niveau des clusters de données volumineuses de SQL Server](deployment-upgrade.md).

## <a id="deploy"></a> Vue d’ensemble du déploiement

À partir de CTP 2.5, la plupart des paramètres de cluster de données volumineuses sont définis dans un fichier de configuration de déploiement JSON. Vous pouvez utiliser un profil de déploiement par défaut pour AKS, kubeadm, ou minikube ou vous pouvez personnaliser votre propre fichier de configuration de déploiement à utiliser pendant l’installation. Pour des raisons de sécurité, les paramètres d’authentification sont passés par le biais de variables d’environnement.

Les sections suivantes fournissent plus d’informations sur la configuration de vos données Big Data de cluster déploiements, ainsi que des exemples de personnalisations. En outre, vous pouvez toujours modifier le fichier de configuration de déploiement personnalisé à l’aide d’un éditeur comme VSCode par exemple.

## <a id="configfile"></a> Configurations par défaut

Options sont définies dans les fichiers de configuration JSON de déploiement du cluster de données volumineuses. Il existe trois profils de déploiement standard avec les paramètres par défaut pour les environnements de développement/test :

| Profil de déploiement | Environnement Kubernetes |
|---|---|
| **aks-dev-test** | Service Azure Kubernetes (AKS) |
| **kubeadm-dev-test** | Plusieurs ordinateurs (kubeadm) |
| **minikube-dev-test** | minikube |

Vous pouvez déployer un cluster de données volumineux en exécutant **mssqlctl bdc créer**. Cela vous invite à choisir une des configurations par défaut et vous guide ensuite dans le déploiement.

```bash
mssqlctl bdc create
```

Dans ce scénario, vous êtes invité pour tous les paramètres qui ne font pas partie de la configuration par défaut, tels que les mots de passe. Notez que les informations de Docker sont fournies pour vous par Microsoft dans le cadre de la 2019 de serveur SQL [programme d’Adoption anticipée](https://aka.ms/eapsignup).

> [!IMPORTANT]
> Le nom par défaut du cluster big data est **mssql-cluster**. Il est important de connaître pour exécuter un de la **kubectl** commandes qui spécifient l’espace de noms Kubernetes avec le `-n` paramètre.

## <a id="customconfig"></a> Configurations personnalisées

Il est également possible de personnaliser votre propre profil de configuration de déploiement. Vous pouvez le faire avec les étapes suivantes :

1. Démarrer avec l’un des profils de déploiement standard qui correspondent à votre environnement Kubernetes. Vous pouvez utiliser la **mssqlctl bdc configuration liste** commande pour répertorier les :

   ```bash
   mssqlctl bdc config list
   ```

1. Pour personnaliser votre déploiement, créez une copie du profil de déploiement avec le **mssqlctl bdc config init** commande. Par exemple, la commande suivante crée une copie de la **aks-dev-test** fichier de configuration de déploiement dans le répertoire cible `custom`:

   ```bash
   mssqlctl bdc config init --source aks-dev-test --target custom
   ```

   > [!TIP]
   > Le `--target` spécifie un répertoire qui contient le fichier de configuration basé sur le `--source` paramètre.

1. Pour personnaliser les paramètres dans votre profil de configuration de déploiement, vous pouvez modifier le fichier de configuration de déploiement dans un outil qui convient pour la modification des fichiers JSON, tels que Visual Studio Code. Pour l’automatisation de l’aide de scripts, vous pouvez également modifier le profil de déploiement personnalisé à l’aide **mssqlctl bdc configuration section défini** commande. Par exemple, la commande suivante modifie un profil de déploiement personnalisé pour modifier le nom du cluster déployé à partir de la valeur par défaut (**mssql-cluster**) à **test-cluster**:  

   ```bash
   mssqlctl bdc config section set --config-profile custom --json-values "metadata.name=test-cluster"
   ```

   > [!TIP]
   > Le `--config-profile` spécifie un nom de répertoire pour votre profil de déploiement personnalisé, mais les modifications se produisent sur le fichier JSON de configuration de déploiement de ce répertoire. Est un outil utile pour rechercher les chemins d’accès JSON le [évaluateur en ligne JSONPath](https://jsonpath.com/).

   En plus de transmettre des paires clé-valeur, vous pouvez également fournir des valeurs JSON en ligne ou transmettre les fichiers du correctif JSON. Pour plus d’informations, consultez [configurer les paramètres de déploiement pour les clusters de données volumineuses](deployment-custom-configuration.md).

1. Puis passez le fichier de configuration personnalisée à **mssqlctl bdc créer**. Notez que vous devez définir le texte requis [variables d’environnement](#env), sinon vous demandera les valeurs :

   ```bash
   mssqlctl bdc create --config-profile custom --accept-eula yes
   ```

> [!TIP]
> Pour plus d’informations sur la structure d’un fichier de configuration de déploiement, consultez le [référence de fichier de configuration de déploiement](reference-deployment-config.md). Pour obtenir des exemples de configuration, consultez [configurer les paramètres de déploiement pour les clusters de données volumineuses](deployment-custom-configuration.md).

## <a id="env"></a> Variables d’environnement

Les variables d’environnement suivantes sont utilisées pour les paramètres de sécurité qui ne sont pas stockées dans un fichier de configuration de déploiement. Notez que les paramètres de Docker à l’exception des informations d’identification peuvent être définis dans le fichier de configuration.

| Variable d'environnement | Description |
|---|---|---|---|
| **DOCKER_USERNAME** | Le nom d’utilisateur pour accéder aux images de conteneur dans le cas où ils sont stockés dans un référentiel privé. |
| **DOCKER_PASSWORD** | Le mot de passe pour accéder au référentiel privé ci-dessus. |
| **CONTROLLER_USERNAME** | Le nom d’utilisateur pour l’administrateur de cluster. |
| **CONTROLLER_PASSWORD** | Le mot de passe pour l’administrateur de cluster. |
| **KNOX_PASSWORD** | Le mot de passe utilisateur de Knox. |
| **MSSQL_SA_PASSWORD** | Le mot de passe de l’utilisateur d’association de sécurité pour l’instance principale de SQL. |

Ces variables d’environnement doivent être définies avant d’appeler **mssqlctl bdc créer**. Si n’importe quelle variable n’est pas définie, vous êtes invité pour celui-ci.

L’exemple suivant montre comment définir les variables d’environnement pour Linux (bash) et Windows (PowerShell) :

```bash
export CONTROLLER_USERNAME=admin
export CONTROLLER_PASSWORD=<password>
export MSSQL_SA_PASSWORD=<password>
export KNOX_PASSWORD=<password>
export DOCKER_USERNAME=<docker-username>
export DOCKER_PASSWORD=<docker-password>
```

```PowerShell
SET CONTROLLER_USERNAME=admin
SET CONTROLLER_PASSWORD=<password>
SET MSSQL_SA_PASSWORD=<password>
SET KNOX_PASSWORD=<password>
SET DOCKER_USERNAME=<docker-username>
SET DOCKER_PASSWORD=<docker-password>
```

Après avoir défini les variables d’environnement, vous devez exécuter `mssqlctl bdc create` pour déclencher le déploiement. Cet exemple utilise le profil de configuration de cluster créé ci-dessus :

```
mssqlctl bdc create --config-profile custom --accept-eula yes
```

Veuillez noter les recommandations suivantes :

- À ce stade, les informations d’identification du Registre Docker privé vous être fournies lors de triage votre [l’inscription du programme d’Adoption anticipée](https://aka.ms/eapsignup). Inscription de programme d’Adoption anticipée est requise pour tester les clusters de données volumineuses de SQL Server.
- Assurez-vous que vous encapsulez les mots de passe entre guillemets s’il contient des caractères spéciaux. Vous pouvez définir le **MSSQL_SA_PASSWORD** à comme vous le souhaitez, mais assurez-vous que le mot de passe est suffisamment complexe et n’utilisez pas le `!`, `&` ou `'` caractères. Notez que les délimiteurs de guillemets doubles ne fonctionnent que dans les commandes bash.
- Le **SA** connexion est un administrateur système sur l’instance principale de SQL Server qui est créé pendant l’installation. Après avoir créé votre conteneur de SQL Server, le **MSSQL_SA_PASSWORD** variable d’environnement que vous avez spécifié est détectable en exécutant echo MSSQL_SA_PASSWORD $ dans le conteneur. Pour des raisons de sécurité, modifier votre mot de passe SA conformément aux bonnes pratiques documentées [ici](../linux/quickstart-install-connect-docker.md#sapassword).

## <a id="unattended"></a> Installation sans assistance

Pour un déploiement sans assistance, vous devez définir toutes les variables d’environnement requises, utilisez un fichier de configuration et appeler `mssqlctl bdc create` commande avec le `--accept-eula yes` paramètre. Les exemples dans la section précédente illustrent la syntaxe pour une installation sans assistance.

## <a id="monitor"></a> Surveiller le déploiement

Pendant l’amorçage de cluster, la fenêtre de commande client affiche l’état du déploiement. Pendant le processus de déploiement, vous devez voir une série de messages où il attend que le pod de contrôleur :

```output
Waiting for cluster controller to start.
```

En moins de 15 à 30 minutes, vous devez averti que le pod de contrôleur est en cours d’exécution :

```output
Cluster controller endpoint is available at 11.111.111.11:30080.
Cluster control plane is ready.
```

> [!IMPORTANT]
> La totalité du déploiement peut prendre beaucoup de temps en raison du temps nécessaire pour télécharger les images de conteneur pour les composants du cluster de données volumineuses. Toutefois, il ne doit pas prendre plusieurs heures. Si vous rencontrez des problèmes avec votre déploiement, consultez [analyse et résoudre les problèmes de clusters de données volumineuses de SQL Server](cluster-troubleshooting-commands.md).

Une fois le déploiement terminé, la sortie vous informe de réussite :

```output
Cluster deployed successfully.
```

> [!TIP]
> Le nom par défaut pour le cluster déployé des données volumineuses est `mssql-cluster` sauf modification par une configuration personnalisée.

## <a id="endpoints"></a> Récupérer les points de terminaison

Une fois le script de déploiement terminée, vous pouvez obtenir les adresses IP des points de terminaison externes pour le cluster de données volumineuses en procédant comme suit.

1. Après le déploiement, recherchez l’adresse IP du point de terminaison de contrôleur en examinant la sortie de l’adresse IP externe des éléments suivants **kubectl** commande :

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Si vous n’avez pas modifié le nom par défaut au cours du déploiement, utilisez `-n mssql-cluster` dans la commande précédente. **MSSQL-cluster** est le nom par défaut pour le cluster de données volumineuses.

1. Connectez-vous au cluster big data avec [mssqlctl connexion](reference-mssqlctl.md). Définir le **--contrôleur de point de terminaison** paramètre à l’adresse IP externe du point de terminaison de contrôleur.

   ```bash
   mssqlctl login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Spécifiez le nom d’utilisateur et le mot de passe que vous avez configuré pour le contrôleur (CONTROLLER_USERNAME et CONTROLLER_PASSWORD) au cours du déploiement.

1. Exécutez [liste de point de terminaison mssqlctl bdc](reference-mssqlctl-bdc-endpoint.md) pour obtenir une liste avec une description de chaque point de terminaison et leurs valeurs d’adresse et le port IP correspondantes. 

   ```bash
   mssqlctl bdc endpoint list -o table
   ```

   La liste suivante illustre le résultat de cette commande :

   ```output
   Description                                             Endpoint                                                   Ip              Name               Port    Protocol
   ------------------------------------------------------  ---------------------------------------------------------  --------------  -----------------  ------  ----------
   Gateway to access HDFS files, Spark                     https://11.111.111.111:30443                               11.111.111.111  gateway            30443   https
   Spark Jobs Management and Monitoring Dashboard          https://11.111.111.111:30443/gateway/default/sparkhistory  11.111.111.111  spark-history      30443   https
   Spark Diagnostics and Monitoring Dashboard              https://11.111.111.111:30443/gateway/default/yarn          11.111.111.111  yarn-ui            30443   https
   Application Proxy                                       https://11.111.111.111:30778                               11.111.111.111  app-proxy          30778   https
   Management Proxy                                        https://11.111.111.111:30777                               11.111.111.111  mgmtproxy          30777   https
   Log Search Dashboard                                    https://11.111.111.111:30777/kibana                        11.111.111.111  logsui             30777   https
   Metrics Dashboard                                       https://11.111.111.111:30777/grafana                       11.111.111.111  metricsui          30777   https
   Cluster Management Service                              https://11.111.111.111:30080                               11.111.111.111  controller         30080   https
   SQL Server Master Instance Front-End                    11.111.111.111,31433                                       11.111.111.111  sql-server-master  31433   tcp
   HDFS File System Proxy                                  https://11.111.111.111:30443/gateway/default/webhdfs/v1    11.111.111.111  webhdfs            30443   https
   Proxy for running Spark statements, jobs, applications  https://11.111.111.111:30443/gateway/default/livy/v1       11.111.111.111  livy               30443   https
   ```

Vous pouvez également obtenir tous les points de terminaison service déployés pour le cluster en exécutant la commande suivante **kubectl** commande :

```bash
kubectl get svc -n <your-big-data-cluster-name>
```

### <a name="minikube"></a>Minikube

Si vous utilisez minikube, vous devez exécuter la commande suivante pour obtenir l’adresse IP, que vous devez vous connecter à. En plus de l’adresse IP, spécifiez le port pour le point de terminaison que vous avez besoin pour vous connecter à.

```bash
minikube ip
```

## <a id="status"></a> Vérifier l’état du cluster

Après le déploiement, vous pouvez vérifier l’état du cluster avec le [afficher d’état mssqlctl bdc](reference-mssqlctl-bdc-status.md) commande.

```bash
mssqlctl bdc status show -o table
```

> [!TIP]
> Pour exécuter les commandes d’état, vous devez tout d’abord vous connecter avec le **mssqlctl connexion** commande, qui a été indiqué dans la section précédente de points de terminaison.

Voici un exemple de sortie de cette commande :

```output
Kind     Name           State
-------  -------------  -------
BDC      mssql-cluster  Ready
Control  default        Ready
Master   default        Ready
Compute  default        Ready
Data     default        Ready
Storage  default        Ready
```

En plus de ce résumé de l’état, vous pouvez également obtenir un état plus détaillé avec les commandes suivantes :

- [mssqlctl bdc control status](reference-mssqlctl-bdc-control-status.md)
- [mssqlctl bdc pool status](reference-mssqlctl-bdc-pool-status.md)

La sortie de ces commandes comprennent des URL vers des tableaux de bord Kibana et Grafana pour une analyse plus détaillée. 

Outre l’utilisation de **mssqlctl**, vous pouvez également utiliser Azure Data Studio pour rechercher des points de terminaison et les informations d’état. Pour plus d’informations sur l’affichage État du cluster avec **mssqlctl** et Azure Data Studio, consultez [comment afficher l’état d’un cluster de données volumineuses](view-cluster-status.md).

## <a id="connect"></a> Connectez-vous au cluster

Pour plus d’informations sur la façon de se connecter au cluster big data, consultez [se connecter à SQL Server cluster big data avec Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur le déploiement de cluster de données volumineuses, consultez les ressources suivantes :

- [Configurer les paramètres de déploiement pour les clusters de données volumineuses](deployment-custom-configuration.md)
- [Effectuer un déploiement hors connexion d’un cluster de données volumineuses de SQL Server](deploy-offline.md)
- [Atelier : Architecture de clusters de données volumineuses de Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
