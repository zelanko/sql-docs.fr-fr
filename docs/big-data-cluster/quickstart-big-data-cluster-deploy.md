---
title: Démarrage rapide du déploiement
titleSuffix: SQL Server 2019 big data clusters
description: Procédure pas à pas un déploiement de clusters SQL Server 2019 données volumineuses (version préliminaire) sur Azure Kubernetes Service (AKS).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: quickstart
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: c760bd4c149a63de0335c6d6651036bba56533a0
ms.sourcegitcommit: edf7372cb674179f03a330de5e674824a8b4118f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53246758"
---
# <a name="quickstart-deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Démarrage rapide : Déployer le cluster de données volumineux de SQL Server sur Azure Kubernetes Service (AKS)

Dans ce démarrage rapide, vous allez déployer un cluster de données volumineuses de SQL Server 2019 (version préliminaire) sur AKS dans une configuration par défaut appropriée pour les environnements de développement/test.

> [!NOTE]
> AKS est simplement un emplacement à l’hôte Kubernetes. Les clusters de données volumineuses peuvent être déployés dans Kubernetes, quel que soit l’infrastructure sous-jacente. Pour plus d’informations, consultez [comment déployer des données volumineuses de SQL Server clusters sur Kubernetes](deployment-guidance.md).

En plus d’une instance SQL principale, le cluster comprend un seul pool instance de calcul, une instance de pool de données et deux instances de pool de stockage. Données sont conservées à l’aide de volumes persistants Kubernetes utilisant des classes de stockage par défaut AKS. Pour personnaliser davantage votre configuration, consultez les variables d’environnement dans le [déploiement](deployment-guidance.md).

Si vous préférez exécuter un script pour créer votre cluster AKS et installer un cluster de données volumineux en même temps, consultez [déployer un serveur SQL Server sur Azure Kubernetes Service (ACS) de cluster de données volumineuses](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>Prérequis

Ce démarrage rapide nécessite que vous avez déjà configuré un cluster AKS avec une version 1.10 d’edgeos minimale. Pour plus d’informations, consultez le [déployer sur AKS](deploy-on-aks.md) guide.

- [Outils de données volumineuses de SQL Server 2019](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **Extension de SQL Server 2019**
   - **kubectl**
   - **mssqlctl**

## <a name="verify-aks-configuration"></a>Vérifier la configuration d’ACS

Une fois que vous avez le cluster AKS déployé, vous pouvez exécuter la commande kubectl pour afficher la configuration de cluster ci-dessous. Assurez-vous que kubectl pointe vers le contexte de cluster correct.

```bash
kubectl config view
```

## <a name="define-environment-variables"></a>Définir des variables d’environnement

Définition des variables d’environnement requises pour le déploiement de cluster de données volumineux légèrement diffère selon que vous utilisez un client Windows ou Linux/Mac OS.  Choisissez les étapes ci-dessous, selon le système d’exploitation que vous utilisez.

Avant de continuer, notez les instructions importantes suivantes :

- Dans le [fenêtre de commande](https://docs.microsoft.com/visualstudio/ide/reference/command-window), guillemets doubles sont inclus dans les variables d’environnement. Si vous utilisez des guillemets pour encapsuler un mot de passe, les guillemets sont inclus dans le mot de passe.
- Dans bash, les guillemets ne sont pas inclus dans la variable. Nos exemples utilisent des guillemets doubles `"`.
- Vous pouvez définir les variables d’environnement le mot de passe à comme vous le souhaitez, mais assurez-vous qu’ils sont suffisamment complexes et n’utilisent pas le `!`, `&`, ou `'` caractères.
- Pour la version CTP 2.2, ne modifiez pas les ports par défaut.
- Le `sa` compte est un administrateur système sur l’instance principale de SQL Server qui est créé pendant l’installation. Une fois le conteneur SQL Server créé, la variable d’environnement `MSSQL_SA_PASSWORD` que vous avez spécifiée peut être découverte en exécutant `echo $MSSQL_SA_PASSWORD` dans le conteneur. Pour des raisons de sécurité, vous devez modifier votre `sa` mot de passe conformément aux bonnes pratiques documentées [ici](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Initialiser les variables d’environnement suivantes.  Ils sont requis pour le déploiement d’un cluster de données volumineuses :

### <a name="windows"></a>Windows

À l’aide d’une fenêtre de commande (et pas PowerShell), configurer les variables d’environnement suivantes :

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=aks

SET CONTROLLER_USERNAME=<controller_admin_name - can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password - can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password - can be anything, password complexity compliant>
SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

SET DOCKER_REGISTRY=private-repo.microsoft.com
SET DOCKER_REPOSITORY=mssql-private-preview
SET DOCKER_USERNAME=<your username, credentials provided by Microsoft>
SET DOCKER_PASSWORD=<your password, credentials provided by Microsoft>
SET DOCKER_EMAIL=<your Docker email, use the username provided by Microsoft>
SET DOCKER_PRIVATE_REGISTRY="1"
```

### <a name="linuxmacos"></a>Linux/Mac OS

Initialiser les variables d’environnement suivantes :

```bash
export ACCEPT_EULA="Y"
export CLUSTER_PLATFORM="aks"

export CONTROLLER_USERNAME="<controller_admin_name - can be anything>"
export CONTROLLER_PASSWORD="<controller_admin_password - can be anything, password complexity compliant>"
export KNOX_PASSWORD="<knox_password - can be anything, password complexity compliant>"
export MSSQL_SA_PASSWORD="<sa_password_of_master_sql_instance, password complexity compliant>"

export DOCKER_REGISTRY="private-repo.microsoft.com"
export DOCKER_REPOSITORY="mssql-private-preview"
export DOCKER_USERNAME="<your username, credentials provided by Microsoft>"
export DOCKER_PASSWORD="<your password, credentials provided by Microsoft>"
export DOCKER_EMAIL="<your Docker email, use the username provided by Microsoft>"
export DOCKER_PRIVATE_REGISTRY="1"
```

> [!NOTE]
> Pendant la préversion publique limitée, les informations d’identification de Docker pour télécharger les images de cluster de données volumineuses de SQL Server sont fournies pour chaque client par Microsoft. Pour demander l’accès, vous devez inscrire [ici](https://aka.ms/eapsignup)et spécifiez votre intérêt pour essayer les clusters de données volumineuses de SQL Server.

## <a name="deploy-a-big-data-cluster"></a>Déployer un cluster de données volumineuses

Pour déployer un cluster de données volumineuses de SQL Server 2019 CTP 2.2 sur votre cluster Kubernetes, exécutez la commande suivante :

```bash
mssqlctl create cluster <your-cluster-name>
```

> [!NOTE]
> Le nom de votre cluster doit être uniquement alphanumériques minuscules, sans espaces. Tous les artefacts de Kubernetes pour le cluster de données volumineuses seront créées dans un espace de noms avec le même nom que le cluster de nom spécifié.

La fenêtre de commande ou l’interpréteur de commandes retourne l’état du déploiement. Vous pouvez également vérifier l’état du déploiement en exécutant ces commandes dans une fenêtre cmd différents :

```bash
kubectl get all -n <your-cluster-name>
kubectl get pods -n <your-cluster-name>
kubectl get svc -n <your-cluster-name>
```

Vous pouvez voir un état et configuration pour chaque pod plus granulaire en exécutant :
```bash
kubectl describe pod <pod name> -n <your-cluster-name>
```

> [!TIP]
> Pour plus d’informations sur la façon de surveiller et dépanner un déploiement, consultez le [la résolution des problèmes de déploiement](deployment-guidance.md#troubleshoot) section de l’article de conseils de déploiement.

## <a name="open-the-cluster-administration-portal"></a>Ouvrez le portail d’Administration de Cluster

Une fois que le pod de contrôleur est en cours d’exécution, vous pouvez utiliser le portail d’Administration de Cluster pour surveiller le déploiement. Vous pouvez accéder au portail à l’aide de l’externe IP adresse et numéro de port pour le `service-proxy-lb` (par exemple : **https://\<ip-address\>: 30777/portail**). Informations d’identification pour accéder au portail d’administration est les valeurs de `CONTROLLER_USERNAME` et `CONTROLLER_PASSWORD` variables d’environnement fournis ci-dessus.

Vous pouvez obtenir l’adresse IP du service de proxy-service-lb en exécutant cette commande dans une fenêtre bash ou cmd :

```bash
kubectl get svc service-proxy-lb -n <your-cluster-name>
```

> [!NOTE]
> Vous verrez un avertissement de sécurité lorsque vous accédez à la page web dans la mesure où nous utilisons des certificats SSL générés automatiquement. Dans les futures versions, nous fournirons la capacité de fournir vos propres certificats auto-signés.

## <a name="connect-to-the-big-data-cluster"></a>Connectez-vous au cluster big data

Une fois le script de déploiement terminée, vous pouvez obtenir l’adresse IP de l’instance principale de SQL Server et les points de terminaison Spark/HDFS à l’aide de la procédure décrite ci-dessous. Tous les points de terminaison de cluster sont affichés dans la section points de terminaison de Service dans le portail d’Administration de Cluster ainsi qu’à faciliter la référence.

Azure fournit le service de l’équilibreur de charge Azure pour AKS. Exécutez la commande dans une cmd suivante ou bash fenêtre :

```bash
kubectl get svc endpoint-master-pool -n <your-cluster-name>
kubectl get svc service-security-lb -n <your-cluster-name>
```

Recherchez le **External-IP** valeur assignée aux services. Se connecter à l’instance principale de SQL Server à l’aide de l’adresse IP pour le `endpoint-master-pool` au port 31433 (Ex :  **\<ip-address\>, 31433**) et pour le point de terminaison cluster de données SQL Server à l’aide de l’IP externe pour le `service-security-lb` service.   Que le point de terminaison de cluster big data est où vous pouvez interagir avec HDFS et envoyer des travaux Spark via Knox.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que le cluster de données volumineuses de SQL Server est déployé, essayez certaines des nouvelles fonctionnalités :

> [!div class="nextstepaction"]
> [Comment utiliser des blocs-notes en version préliminaire de SQL Server 2019](notebooks-guidance.md)
