---
title: Conseils pour le déploiement
titleSuffix: SQL Server big data clusters
description: Découvrez comment déployer des clusters SQL Server 2019 Big Data (version préliminaire) sur Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e6f2eefd37c45753e3051722448b80d88712df26
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419420"
---
# <a name="how-to-deploy-sql-server-big-data-clusters-on-kubernetes"></a>Comment déployer des clusters de Big Data SQL Server sur Kubernetes

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

SQL Server Cluster Big Data est déployé en tant que conteneurs d’ancrage sur un cluster Kubernetes. Voici une vue d’ensemble des étapes d’installation et de configuration:

- Configurez un cluster Kubernetes sur une seule machine virtuelle, un cluster de machines virtuelles ou un service Azure Kubernetes (AKS).
- Installez l’outil de configuration de cluster **azdata** sur votre ordinateur client.
- Déployez un cluster SQL Server Big Data dans un cluster Kubernetes.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-sql-server-2019-big-data-tools"></a>Installer les outils de Big Data SQL Server 2019

Avant de déployer un cluster SQL Server 2019 Big Data, commencez par [installer les outils Big Data](deploy-big-data-tools.md):

- **azdata**
- **kubectl**
- **Azure Data Studio**
- **SQL Server extension 2019**

## <a id="prereqs"></a>Conditions préalables de Kubernetes

SQL Server Clusters Big Data nécessitent une version minimale de Kubernetes au moins v 1.10 pour le serveur et le client (kubectl).

> [!NOTE]
> Notez que les versions client et serveur Kubernetes doivent se trouver dans une version mineure + 1 ou-1. Pour plus d’informations, consultez [notes de publication Kubernetes et stratégie de version distorsion des références SKU)](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

### <a id="kubernetes"></a>Configuration du cluster Kubernetes

Si vous disposez déjà d’un cluster Kubernetes qui répond aux conditions préalables ci-dessus, vous pouvez passer directement à l' [étape de déploiement](#deploy). Cette section suppose une compréhension de base des concepts de Kubernetes.  Pour plus d’informations sur Kubernetes, consultez la [documentation de Kubernetes](https://kubernetes.io/docs/home).

Vous pouvez choisir de déployer Kubernetes de trois manières:

| Déployer Kubernetes sur: | Description | Lien |
|---|---|---|
| **Services Azure Kubernetes (AKS)** | Service de conteneur Kubernetes géré dans Azure. | [Instructions](deploy-on-aks.md) |
| **Plusieurs ordinateurs (kubeadm)** | Un cluster Kubernetes déployé sur des ordinateurs physiques ou virtuels à l’aide de **kubeadm** | [Instructions](deploy-with-kubeadm.md) |
| **Minikube** | Cluster Kubernetes à nœud unique dans une machine virtuelle. | [Instructions](deploy-on-minikube.md) |

> [!TIP]
> Pour obtenir un exemple de script Python qui déploie à la fois AKS et un cluster SQL Server Big Data en [une seule étape, consultez démarrage rapide: Déployez SQL Server Cluster Big Data sur Azure Kubernetes service (AKS](quickstart-big-data-cluster-deploy.md)).

### <a name="verify-kubernetes-configuration"></a>Vérifier la configuration de Kubernetes

Exécutez la commande **kubectl** pour afficher la configuration du cluster. Vérifiez que kubectl pointe vers le contexte de cluster correct.

```bash
kubectl config view
```

Une fois que vous avez configuré votre cluster Kubernetes, vous pouvez procéder au déploiement d’un nouveau cluster SQL Server Big Data. Si vous effectuez une mise à niveau à partir d’une version précédente, consultez [Comment mettre à niveau SQL Server clusters Big Data](deployment-upgrade.md).

## <a id="deploy"></a>Présentation du déploiement

La plupart des paramètres de cluster Big Data sont définis dans un fichier de configuration de déploiement JSON. Vous pouvez utiliser un profil de déploiement par défaut pour `kubeadm`AKS, `minikube` ou ou vous pouvez personnaliser votre propre fichier de configuration de déploiement à utiliser pendant l’installation. Pour des raisons de sécurité, les paramètres d’authentification sont transmis via des variables d’environnement.

Les sections suivantes fournissent plus d’informations sur la configuration de vos déploiements de cluster Big Data, ainsi que des exemples de personnalisations courantes. En outre, vous pouvez toujours modifier le fichier de configuration de déploiement personnalisé à l’aide d’un éditeur comme VS Code par exemple.

## <a id="configfile"></a>Configurations par défaut

Les options de déploiement de cluster Big Data sont définies dans les fichiers de configuration JSON. Il existe trois profils de déploiement standard avec des paramètres par défaut pour les environnements de développement et de test:

| Profil de déploiement | Environnement Kubernetes |
|---|---|
| **aks-dev-test** | Service Azure Kubernetes (AKS) |
| **kubeadm-dev-test** | Plusieurs ordinateurs (kubeadm) |
| **minikube-dev-test** | Minikube |

Vous pouvez déployer un cluster Big Data en exécutant **azdata BDC Create**. Vous êtes alors invité à choisir l’une des configurations par défaut, puis vous guide tout au long du déploiement.

La première fois que vous `azdata` exécutez, vous `--accept-eula` devez inclure pour accepter le contrat de licence utilisateur final (CLUF).

```bash
azdata bdc create --accept-eula
```

Dans ce scénario, vous êtes invité à fournir tous les paramètres qui ne font pas partie de la configuration par défaut, tels que les mots de passe. 

> [!NOTE]
> À partir de SQL Server 2019 CTP 3,2, vous n’êtes plus membre de la version de SQL Server 2019, le [programme d’adoption précoce](https://aka.ms/eapsignup) pour découvrir les versions préliminaires de Big Data cluster.

> [!IMPORTANT]
> Le nom par défaut du cluster Big Data est **MSSQL-cluster**. Il est important de savoir si vous souhaitez exécuter l’une des commandes **kubectl** qui spécifient l’espace de noms `-n` Kubernetes avec le paramètre.

## <a id="customconfig"></a>Configurations personnalisées

Il est également possible de personnaliser votre propre profil de configuration de déploiement. Pour ce faire, procédez comme suit:

1. Commencez avec l’un des profils de déploiement standard qui correspondent à votre environnement Kubernetes. Vous pouvez utiliser la commande **azdata BDC config List** pour les répertorier:

   ```bash
   azdata bdc config list
   ```

1. Pour personnaliser votre déploiement, créez une copie du profil de déploiement avec la commande **azdata BDC config init** . Par exemple, la commande suivante crée une copie des fichiers de configuration de déploiement **AKS-dev-test** dans un répertoire cible `custom`nommé:

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

   azdata
   > Spécifie un répertoire qui contient les fichiers de configuration, **cluster. JSON** et **Control. JSON**, en fonction `--source` du paramètre. `--target`

1. Pour personnaliser les paramètres dans votre profil de configuration de déploiement, vous pouvez modifier le fichier de configuration de déploiement dans un outil adapté à la modification des fichiers JSON, par exemple VS Code. Pour l’automatisation par script, vous pouvez également modifier le profil de déploiement personnalisé à l’aide de la commande de **configuration azdata BDC** . Par exemple, la commande suivante modifie un profil de déploiement personnalisé pour remplacer le nom par défaut du cluster déployé (**MSSQL-cluster**) par **test-cluster**:  

   ```bash
   azdata bdc config replace --config-file custom/cluster.json --json-values "metadata.name=test-cluster"
   ```

   > L' [évaluateur JSONPath Online](https://jsonpath.com/)est un outil utile pour rechercher des chemins d’accès JSON.

   En plus de passer des paires clé-valeur, vous pouvez également fournir des valeurs JSON inline ou passer des fichiers de correctif JSON. Pour plus d’informations, consultez [configurer les paramètres de déploiement pour les clusters Big Data](deployment-custom-configuration.md).

1. Ensuite, transmettez le fichier de configuration personnalisé à **azdata BDC Create**. Notez que vous devez définir les [variables d’environnement](#env)requises. dans le cas contraire, vous serez invité à entrer les valeurs:

   ```bash
   azdata bdc create --config-profile custom --accept-eula yes
   ```

> Pour plus d’informations sur la structure d’un fichier de configuration de déploiement, consultez la documentation de référence sur le [fichier de configuration de déploiement](reference-deployment-config.md). Pour obtenir d’autres exemples de configuration, consultez [configurer les paramètres de déploiement pour les clusters Big Data](deployment-custom-configuration.md).

## <a id="env"></a>Variables d’environnement

Les variables d’environnement suivantes sont utilisées pour les paramètres de sécurité qui ne sont pas stockés dans un fichier de configuration de déploiement. Notez que les paramètres de l’ancrage, à l’exception des informations d’identification, peuvent être définis dans le fichier de configuration.

| Variable d'environnement | Prérequis |Description |
|---|---|---|
| **CONTROLLER_USERNAME** | Obligatoire |Nom d’utilisateur de l’administrateur de cluster. |
| **CONTROLLER_PASSWORD** | Obligatoire |Mot de passe de l’administrateur de cluster. |
| **MSSQL_SA_PASSWORD** | Obligatoire |Mot de passe de l’utilisateur SA pour l’instance SQL Master. |
| **KNOX_PASSWORD** | Obligatoire |Mot de passe de l’utilisateur Knox. |
| **ACCEPT_EULA**| Requis pour la première utilisation de`azdata`| Aucune valeur n’est requise. Lorsqu’il est défini en tant que variable d’environnement, il applique le `azdata`CLUF à SQL Server et. S’il n’est pas défini en tant que variable `--accept-eula` d’environnement, vous pouvez `azdata` inclure dans la première utilisation de la commande.|
| **DOCKER_USERNAME** | Facultatif | Nom d’utilisateur pour accéder aux images de conteneur si elles sont stockées dans un dépôt privé. Pour plus d’informations sur l’utilisation d’un référentiel d’ancrage privé pour le déploiement de clusters Big Data, consultez la rubrique [déploiements hors connexion](deploy-offline.md) .|
| **DOCKER_PASSWORD** | Facultatif |Mot de passe pour accéder au référentiel privé ci-dessus. |

Ces variables d’environnement doivent être définies avant d’appeler **azdata BDC Create**. Si une variable n’est pas définie, vous êtes invité à le faire.

L’exemple suivant montre comment définir les variables d’environnement pour Linux (bash) et Windows (PowerShell):

```bash
export CONTROLLER_USERNAME=admin
export CONTROLLER_PASSWORD=<password>
export MSSQL_SA_PASSWORD=<password>
export KNOX_PASSWORD=<password>
```

```PowerShell
SET CONTROLLER_USERNAME=admin
SET CONTROLLER_PASSWORD=<password>
SET MSSQL_SA_PASSWORD=<password>
SET KNOX_PASSWORD=<password>
```

Après avoir défini les variables d’environnement, vous `azdata bdc create` devez exécuter pour déclencher le déploiement. Cet exemple utilise le profil de configuration de cluster créé ci-dessus:

```bash
azdata bdc create --config-profile custom --accept-eula yes
```

Veuillez noter les instructions suivantes:

- Veillez à inclure le mot de passe entre guillemets doubles s’il contient des caractères spéciaux. Vous pouvez définir le **MSSQL_SA_PASSWORD** comme vous le souhaitez, mais assurez-vous que le mot de passe est suffisamment `!`complexe `&` et `'` n’utilisez pas les caractères ou. Notez que les séparateurs de guillemets doubles fonctionnent uniquement dans les commandes bash.
- La connexion **sa** est un administrateur système sur l’instance SQL Server Master qui est créée lors de l’installation. Après avoir créé votre conteneur SQL Server, la variable d’environnement **MSSQL_SA_PASSWORD** que vous avez spécifiée est détectable `echo $MSSQL_SA_PASSWORD` en exécutant dans le conteneur. Pour des raisons de sécurité, modifiez votre mot de passe d’administrateur système en suivant les meilleures pratiques décrites [ici](../linux/quickstart-install-connect-docker.md#sapassword).

## <a id="unattended"></a>Installation sans assistance

Pour un déploiement sans assistance, vous devez définir toutes les variables d’environnement requises, utiliser un fichier de configuration et `azdata bdc create` appeler la commande `--accept-eula yes` avec le paramètre. Les exemples de la section précédente illustrent la syntaxe d’une installation sans assistance.

## <a id="monitor"></a>Surveiller le déploiement

Lors du démarrage du cluster, la fenêtre de commande du client génère l’état du déploiement. Pendant le processus de déploiement, vous devez voir une série de messages dans laquelle il attend le pod du contrôleur:

```output
Waiting for cluster controller to start.
```

En 15 à 30 minutes, vous devez être informé que le pod du contrôleur est en cours d’exécution:

```output
Cluster controller endpoint is available at 11.111.111.11:30080.
Cluster control plane is ready.
```

> [!IMPORTANT]
> L’ensemble du déploiement peut prendre beaucoup de temps en raison du temps nécessaire au téléchargement des images conteneur pour les composants du cluster Big Data. Toutefois, il ne doit pas prendre plusieurs heures. Si vous rencontrez des problèmes avec votre déploiement, consultez [surveillance et résolution des problèmes SQL Server les clusters Big Data](cluster-troubleshooting-commands.md).

Une fois le déploiement terminé, la sortie vous avertit de la réussite:

```output
Cluster deployed successfully.
```

> [!TIP]
> Le nom par défaut du cluster Big Data déployé est `mssql-cluster` , sauf s’il est modifié par une configuration personnalisée.

## <a id="endpoints"></a>Récupérer des points de terminaison

Une fois que le script de déploiement s’est terminé avec succès, vous pouvez obtenir les adresses IP des points de terminaison externes pour le cluster Big Data à l’aide des étapes suivantes.

1. Après le déploiement, recherchez l’adresse IP du point de terminaison du contrôleur à partir de la sortie standard du déploiement ou en examinant la sortie externe-IP de la commande **kubectl** suivante:

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Si vous n’avez pas modifié le nom par défaut lors du `-n mssql-cluster` déploiement, utilisez dans la commande précédente. **MSSQL-cluster** est le nom par défaut du cluster Big Data.

1. Connectez-vous au cluster Big Data avec la [connexion azdata](reference-azdata.md). Définissez le paramètre **--Endpoint-point de terminaison** sur l’adresse IP externe du point de terminaison du contrôleur.

   ```bash
   azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Spécifiez le nom d’utilisateur et le mot de passe que vous avez configurés pour le contrôleur (CONTROLLER_USERNAME et CONTROLLER_PASSWORD) au cours du déploiement.

1. Exécutez la [liste de points de terminaison azdata BDC](reference-azdata-bdc-endpoint.md) pour obtenir une liste avec une description de chaque point de terminaison, ainsi que les valeurs d’adresse IP et de port correspondantes. 

   ```bash
   azdata bdc endpoint list -o table
   ```

   La liste suivante affiche un exemple de sortie de cette commande:

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

Vous pouvez également obtenir tous les points de terminaison de service déployés pour le cluster en exécutant la commande **kubectl** suivante:

```bash
kubectl get svc -n <your-big-data-cluster-name>
```

### <a name="minikube"></a>Minikube

Si vous utilisez minikube, vous devez exécuter la commande suivante pour récupérer l’adresse IP à laquelle vous devez vous connecter. En plus de l’adresse IP, spécifiez le port du point de terminaison auquel vous devez vous connecter.

```bash
minikube ip
```

## <a id="status"></a>Vérifier l’état du cluster

Après le déploiement, vous pouvez vérifier l’état du cluster à l’aide de la commande [azdata BDC Status Show](reference-azdata-bdc-status.md) .

```bash
azdata bdc status show -o table
```

> [!TIP]
> Pour exécuter les commandes d’État, vous devez d’abord vous connecter à l’aide de la commande **azdata login** , qui était affichée dans la section points de terminaison précédents.

Le code suivant montre un exemple de sortie de cette commande:

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

Dans ce résumé, vous pouvez également obtenir un État plus détaillé avec les commandes suivantes:

- [État du contrôle BDC azdata](reference-azdata-bdc-control-status.md)
- [État du pool BDC azdata](reference-azdata-bdc-pool-status.md)

La sortie de ces commandes contient des URL pour les tableaux de bord Kibana et Grafana pour une analyse plus détaillée.

Outre l’utilisation de **azdata**, vous pouvez également utiliser Azure Data Studio pour rechercher les points de terminaison et les informations d’État. Pour plus d’informations sur l’affichage de l’état du cluster avec **azdata** et Azure Data Studio, consultez [How to View the Status of a Big Data cluster](view-cluster-status.md).

## <a id="connect"></a>Se connecter au cluster

Pour plus d’informations sur la façon de se connecter au cluster Big Data, consultez [se connecter à un cluster SQL Server Big Data avec Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur le déploiement d’un cluster Big Data, consultez les ressources suivantes:

- [Configurer les paramètres de déploiement pour les clusters Big Data](deployment-custom-configuration.md)
- [Effectuer un déploiement hors connexion d’un cluster SQL Server Big Data](deploy-offline.md)
- [Atelier Architecture des clusters de Big Data Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
