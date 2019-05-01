---
title: Conseils pour le déploiement
titleSuffix: SQL Server big data clusters
description: Découvrez comment déployer des clusters de données volumineuses de SQL Server 2019 (version préliminaire) sur Kubernetes.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: a2ace569180006f54461631848ecbf5342b2c1e3
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63472042"
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
| **aks-dev-test.json** | Azure Kubernetes Service (AKS) |
| **kubeadm-dev-test.json** | Plusieurs ordinateurs (kubeadm) |
| **minikube-dev-test.json** | minikube |

Vous pouvez déployer un cluster de données volumineux en exécutant **de création du cluster mssqlctl**. Cela vous invite à choisir une des configurations par défaut et vous guide ensuite dans le déploiement.

```bash
mssqlctl cluster create
```

> [!TIP]
> Dans cet exemple, vous êtes invité pour tous les paramètres qui ne font pas partie de la configuration par défaut, tels que les mots de passe. Notez que les informations de Docker sont fournies pour vous par Microsoft dans le cadre de la 2019 de serveur SQL [programme d’Adoption anticipée](https://aka.ms/eapsignup).

## <a id="customconfig"></a> Configurations personnalisées

Il est également possible de personnaliser votre propre fichier de configuration de déploiement. Vous pouvez le faire avec les étapes suivantes :

1. Démarrer avec l’un des profils de déploiement standard qui correspondent à votre environnement Kubernetes. Vous pouvez utiliser la **liste de configuration de cluster mssqlctl** commande pour répertorier les :

   ```bash
   mssqlctl cluster config list
   ```

1. Pour personnaliser votre déploiement, créez une copie du profil de déploiement avec le **mssqlctl cluster config init** commande. Par exemple, la commande suivante crée une copie de la **aks-dev-test.json** fichier de configuration de déploiement dans le répertoire actif :

   ```bash
   mssqlctl cluster config init --src aks-dev-test.json --target custom.json
   ```

1. Pour personnaliser les paramètres dans votre fichier de configuration de déploiement, vous pouvez le modifier dans un outil qui convient pour la modification des documents json comme Visual Studio Code. Pour l’automatisation de l’aide de scripts, vous pouvez modifier le fichier de configuration personnalisée à l’aide **ensemble de section de configuration de cluster mssqlctl** commande. Par exemple, la commande suivante modifie un fichier de configuration personnalisée pour modifier le nom du cluster déployé à partir de la valeur par défaut (**mssql-cluster**) à **test-cluster**:  

   ```bash
   mssqlctl cluster config section set --config-file custom.json --json-values "metadata.name=test-cluster"
   ```

   > [!TIP]
   > Est un outil utile pour rechercher les chemins d’accès JSON le [évaluateur en ligne JSONPath](https://jsonpath.com/).

   En plus de transmettre des paires clé-valeur, vous pouvez également fournir des valeurs JSON en ligne ou transmettre les fichiers du correctif JSON. Pour plus d’informations, consultez [configurer les paramètres de déploiement pour les clusters de données volumineuses](deployment-custom-configuration.md).

1. Puis passez le fichier de configuration personnalisée à **de création du cluster mssqlctl**. Notez que vous devez définir le texte requis [variables d’environnement](#env), sinon vous demandera les valeurs :

   ```bash
   mssqlctl cluster create --config-file custom.json --accept-eula yes
   ```

> [!TIP]
> Pour plus d’informations sur la structure d’un fichier de configuration de déploiement, consultez le [référence de fichier de configuration de déploiement](reference-deployment-config.md). Pour obtenir des exemples de configuration, consultez [configurer les paramètres de déploiement pour les clusters de données volumineuses](deployment-custom-configuration.md).

## <a id="env"></a> Variables d’environnement

Les variables d’environnement suivantes sont utilisées pour les paramètres de sécurité qui ne sont pas stockées dans un fichier de configuration de déploiement.

| Variable d'environnement | Description |
|---|---|---|---|
| **DOCKER_REGISTRY** | Le Registre privé où sont stockées les images utilisées pour déployer le cluster. |
| **DOCKER_REPOSITORY** | Le dépôt privé au sein de la sous-clé de Registre ci-dessus où les images sont stockées. |
| **DOCKER_USERNAME** | Le nom d’utilisateur pour accéder aux images de conteneur dans le cas où ils sont stockés dans un référentiel privé. |
| **DOCKER_PASSWORD** | Le mot de passe pour accéder au référentiel privé ci-dessus. |
| **DOCKER_IMAGE_TAG** | L’étiquette utilisée pour marquer les images. Valeur par défaut est **dernière**, mais nous recommandons l’utilisation de la balise correspondant à la version pour éviter les problèmes d’incompatibilité de version. |
| **CONTROLLER_USERNAME** | Le nom d’utilisateur pour l’administrateur de cluster. |
| **CONTROLLER_PASSWORD** | Le mot de passe pour l’administrateur de cluster. |
| **KNOX_PASSWORD** | Le mot de passe utilisateur de Knox. |
| **MSSQL_SA_PASSWORD** | Le mot de passe de l’utilisateur d’association de sécurité pour l’instance principale de SQL. |

Ces variables d’environnement doivent être définies avant d’appeler **de création du cluster mssqlctl**. Si n’importe quelle variable n’est pas définie, vous êtes invité pour celui-ci.

L’exemple suivant montre comment définir les variables d’environnement pour Linux (bash) et Windows (PowerShell) :

```bash
export CONTROLLER_USERNAME=<controller_user>
export CONTROLLER_PASSWORD=<password>
export DOCKER_REGISTRY=<docker-registry>
export DOCKER_REPOSITORY=<docker-repository>
export MSSQL_SA_PASSWORD=<password>
export KNOX_PASSWORD=<password>
export DOCKER_USERNAME=<docker-username>
export DOCKER_PASSWORD=<docker-password>
export DOCKER_IMAGE_TAG=ctp2.5
```

```PowerShell
SET CONTROLLER_USERNAME=admin
SET CONTROLLER_PASSWORD=<password>
SET DOCKER_REGISTRY=<docker-registry>
SET DOCKER_REPOSITORY=<docker-repository>
SET MSSQL_SA_PASSWORD=<password>
SET KNOX_PASSWORD=<password>
SET DOCKER_USERNAME=<docker-username>
SET DOCKER_PASSWORD=<docker-password>
SET DOCKER_IMAGE_TAG=ctp2.5
```

Lors de la configuration des variables d’environnement, vous devez exécuter `mssqlctl cluster create` pour déclencher le déploiement. Cet exemple utilise le fichier de configuration de cluster créé ci-dessus :

```
mssqlctl cluster create --config-file custom.json --accept-eula yes
```

Veuillez noter les recommandations suivantes :

- À ce stade, les informations d’identification du Registre Docker privé vous être fournies lors de triage votre [l’inscription du programme d’Adoption anticipée](https://aka.ms/eapsignup). Inscription de programme d’Adoption anticipée est requise pour tester les clusters de données volumineuses de SQL Server.
- Assurez-vous que vous encapsulez les mots de passe entre guillemets s’il contient des caractères spéciaux. Vous pouvez définir le **MSSQL_SA_PASSWORD** à comme vous le souhaitez, mais assurez-vous que le mot de passe est suffisamment complexe et n’utilisez pas le `!`, `&` ou `'` caractères. Notez que les délimiteurs de guillemets doubles ne fonctionnent que dans les commandes bash.
- Le **SA** connexion est un administrateur système sur l’instance principale de SQL Server qui est créé pendant l’installation. Après avoir créé votre conteneur de SQL Server, le **MSSQL_SA_PASSWORD** variable d’environnement que vous avez spécifié est détectable en exécutant echo MSSQL_SA_PASSWORD $ dans le conteneur. Pour des raisons de sécurité, modifier votre mot de passe SA conformément aux bonnes pratiques documentées [ici](../linux/quickstart-install-connect-docker.md#sapassword).
- Le **DOCKER_IMAGE_TAG** dans cet exemple sont l’installation de contrôles qui vous libérer. Dans cet exemple, il est la version CTP 2.5.

## <a id="unattended"></a> Installation sans assistance

Pour un déploiement sans assistance, vous devez définir toutes les variables d’environnement requises, utilisez un fichier de configuration et appeler `mssqlctl cluster create` commande avec le `--accept-eula yes` paramètre. Les exemples dans la section précédente illustrent la syntaxe pour une installation sans assistance.

## <a id="monitor"></a> Surveiller le déploiement

Pendant l’amorçage de cluster, la fenêtre de commande client affiche l’état du déploiement. Pendant le processus de déploiement, vous devez voir une série de messages où il attend que le pod de contrôleur :

```output
2019-04-12 14:40:10.0129 UTC | INFO | Waiting for controller pod to be up...
```

En moins de 15 à 30 minutes, vous devez averti que le pod de contrôleur est en cours d’exécution :

```output
2019-04-12 15:01:10.0809 UTC | INFO | Waiting for controller pod to be up. Checkthe mssqlctl.log file for more details.
2019-04-12 15:01:40.0861 UTC | INFO | Controller pod is running.
2019-04-12 15:01:40.0884 UTC | INFO | Controller Endpoint: https://<ip-address>:30080
```

> [!IMPORTANT]
> La totalité du déploiement peut prendre beaucoup de temps en raison du temps nécessaire pour télécharger les images de conteneur pour les composants du cluster de données volumineuses. Toutefois, il ne doit pas prendre plusieurs heures. Si vous rencontrez des problèmes avec votre déploiement, consultez [analyse et résoudre les problèmes de clusters de données volumineuses de SQL Server](cluster-troubleshooting-commands.md).

Une fois le déploiement terminé, la sortie vous informe de réussite :

```output
2019-04-12 15:37:18.0271 UTC | INFO | Monitor and track your cluster at the Portal Endpoint: https://<ip-address>:30777/portal/
2019-04-12 15:37:18.0271 UTC | INFO | Cluster deployed successfully.
```

Notez l’URL de la **portail le point de terminaison** dans la sortie précédente pour une utilisation dans la section suivante.

> [!TIP]
> Le nom par défaut pour le cluster déployé des données volumineuses est `mssql-cluster` sauf modification par une configuration personnalisée.

## <a id="endpoints"></a> Récupérer les points de terminaison

Une fois le script de déploiement terminée, vous pouvez obtenir les adresses IP des points de terminaison externes pour le cluster de données volumineuses en procédant comme suit.

1. À partir de la sortie du déploiement, copiez la **portail le point de terminaison** et supprimer le `/portal/` à la fin. Voici l’URL du Proxy de gestion (par exemple, `https://<ip-address>:30777`).

   > [!TIP]
   > Si vous n’avez pas de sortie de votre déploiement, vous pouvez obtenir l’adresse IP pour le Proxy de gestion en examinant la sortie de l’adresse IP externe des éléments suivants **kubectl** commande :
   >
   > ```bash
   > kubectl get svc mgmtproxy-svc-external -n <your-cluster-name>
   > ```

1. Connectez-vous au cluster big data avec **mssqlctl connexion**. Définir le **--point de terminaison** paramètre vers le Proxy de gestion.

   ```bash
   mssqlctl login --endpoint https://<ip-address>:30777
   ```

   Spécifiez le nom d’utilisateur et le mot de passe que vous avez configuré pour le contrôleur (CONTROLLER_USERNAME et CONTROLLER_PASSWORD) au cours du déploiement.

1. Exécutez **liste de points de terminaison de cluster mssqlctl** pour obtenir une liste avec une description de chaque point de terminaison et leurs valeurs d’adresse et le port IP correspondantes. Par exemple, ce qui suit affiche la sortie pour le point de terminaison du portail de gestion :

   ```output
   {
     "description": "Management Portal",
     "endpoint": "https://<ip-address>:30777/portal",
     "ip": "<ip-address>",
     "name": "portal",
     "port": 30777,
     "protocol": "https"
   },
   ```

1. Tous les points de terminaison de cluster sont également présentées dans le **points de terminaison de Service** onglet dans le portail d’Administration de Cluster. Vous pouvez accéder au portail à l’aide du point de terminaison du portail de gestion à l’étape précédente (par exemple, `https://<ip-address>:30777/portal`). Les informations d’identification pour accéder au portail d’administration sont les valeurs pour le nom d’utilisateur du contrôleur et le mot de passe que vous avez spécifié au cours du déploiement. Vous pouvez également utiliser le portail d’Administration de Cluster pour surveiller le déploiement.

### <a name="minikube"></a>Minikube

Si vous utilisez minikube, vous devez exécuter la commande suivante pour obtenir l’adresse IP, que vous devez vous connecter à. En plus de l’adresse IP, spécifiez le port pour le point de terminaison que vous avez besoin pour vous connecter à.

```bash
minikube ip
```

Quelle que soit la plateforme vous s’exécutent votre cluster Kubernetes, pour obtenir tous les points de terminaison service déployés pour le cluster, exécutez la commande suivante :

```bash
kubectl get svc -n <your-cluster-name>
```

## <a id="connect"></a> Connectez-vous au cluster

Pour plus d’informations sur la façon de se connecter au cluster big data, consultez [se connecter à SQL Server cluster big data avec Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur le déploiement de cluster de données volumineuses, consultez les ressources suivantes :

- [Configurer les paramètres de déploiement pour les clusters de données volumineuses](deployment-custom-configuration.md)
- [Effectuer un déploiement hors connexion d’un cluster de données volumineuses de SQL Server](deploy-offline.md)
- [Atelier : Architecture de clusters de données volumineuses de Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
