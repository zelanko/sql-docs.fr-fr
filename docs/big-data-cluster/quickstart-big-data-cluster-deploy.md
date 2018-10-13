---
title: Déployer le cluster de données volumineux de SQL Server | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: quickstart
ms.prod: sql
ms.openlocfilehash: 5781b3acfd2262b3a3be540abb331839dfcc56c6
ms.sourcegitcommit: 08b3de02475314c07a82a88c77926d226098e23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49120456"
---
# <a name="quickstart-deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Démarrage rapide : Déployer le cluster de données volumineux de SQL Server sur Azure Kubernetes Service (AKS)

Dans ce démarrage rapide, vous installerez cluster de données volumineux de SQL Server sur AKS dans une configuration par défaut appropriée pour les environnements de développement/test. En plus de l’instance SQL principale, le cluster inclura l’instance de calcul d’un pool, instance de pool de données et deux instances de pool de stockage. Données seront conservées à l’aide de volumes persistants Kubernetes qui sont configurées sur les classes de stockage par défaut AKS. Dans le [déploiement](deployment-guidance.md) rubrique, vous trouverez un ensemble de variables d’environnement que vous pouvez utiliser pour personnaliser davantage votre configuration.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>Prérequis

Ce démarrage rapide nécessite que vous avez déjà configuré un cluster AKS avec une version 1.10 d’edgeos minimale. Pour plus d’informations, consultez le [déployer sur AKS](deploy-on-aks.md) guide.

Sur l’ordinateur que vous utilisez pour exécuter les commandes pour installer le cluster de données volumineux de SQL Server, vous devez installer [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/). Cluster de données volumineux de SQL Server nécessite au minimum la version 1.10 pour Kubernetes, pour le serveur et le client (kubectl). Pour installer kubectl, consultez [installer kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). 

Pour installer le `mssqlctl` outil CLI pour gérer les données volumineuses de SQL Server du cluster sur votre ordinateur client, vous devez d’abord installer [Python](https://www.python.org/downloads/) v3.0 de version minimale et [pip3](https://pip.pypa.io/en/stable/installing/). Notez que pip est déjà installé si vous utilisez une version de Python au moins les 3.4 téléchargés à partir de [python.org](https://www.python.org/).

Si votre installation Python manque le `requests` package, vous devez installer `requests` à l’aide de `python -m pip install requests`. Si vous avez déjà un `requests` package à niveau vers la dernière version à l’aide `python -m pip install requests --upgrade`.

## <a name="verify-aks-configuration"></a>Vérifier la configuration d’ACS

Une fois que vous avez le cluster AKS déployé, vous pouvez exécuter la commande kubectl pour afficher la configuration de cluster ci-dessous. Assurez-vous que kubectl pointe vers le contexte de cluster correct.

```bash
kubectl config view
```

## <a name="install-mssqlctl-cli-management-tool"></a>Installer l’outil de gestion mssqlctl CLI

Exécutez la commande ci-dessous pour installer `mssqlctl` outil sur votre ordinateur client. Même commande fonctionne à partir d’un Windows et un client Linux, mais assurez-vous que vous l’exécutez à partir d’une fenêtre cmd qui s’exécute avec des privilèges d’administrateur sur Windows ou faites-le précéder `sudo` sur Linux :

```
pip3 install --index-url https://private-repo.microsoft.com/python/ctp-2.0 mssqlctl  
```

## <a name="define-environment-variables"></a>Définir des variables d’environnement

Définition des variables d’environnement requises pour le déploiement de cluster de données volumineux légèrement diffère selon que vous utilisez un client Windows ou Linux/Mac OS.  Choisissez les étapes ci-dessous, selon le système d’exploitation que vous utilisez.

Avant de continuer, notez les instructions importantes suivantes :

- Assurez-vous que vous encapsulez les mots de passe entre guillemets s’il contient des caractères spéciaux. Notez que les délimiteurs de guillemets doubles ne fonctionnent que dans les commandes bash.
- Vous pouvez définir les variables d’environnement le mot de passe à comme vous le souhaitez, mais assurez-vous qu’ils sont suffisamment complexes et n’utilisent pas le `!`, `&`, ou `‘` caractères.
- Pour la version CTP 2.0, ne modifiez pas les ports par défaut.
- Le **SA** compte est un administrateur système sur l’instance principale de SQL Server qui est créé pendant l’installation. Après que la création de votre conteneur de SQL Server, la variable d’environnement MSSQL_SA_PASSWORD que vous avez spécifié est détectable en exécutant l’écho MSSQL_SA_PASSWORD $ dans le conteneur. Pour des raisons de sécurité, modifier votre mot de passe SA conformément aux bonnes pratiques documentées [ici](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Initialiser les variables d’environnement suivantes.  Ils sont requis pour le déploiement d’un cluster de données volumineuses :

### <a name="windows"></a>Windows

À l’aide d’une fenêtre CMD (pas PowerShell), configurer les variables d’environnement suivantes :

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=aks

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

### <a name="linuxmacos"></a>Linux/Mac OS

Initialiser les variables d’environnement suivantes :

```bash
export ACCEPT_EULA=Y
export CLUSTER_PLATFORM=aks

export CONTROLLER_USERNAME=<controller_admin_name – can be anything>
export CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
export KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
export MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

export DOCKER_REGISTRY=private-repo.microsoft.com
export DOCKER_REPOSITORY=mssql-private-preview
export DOCKER_USERNAME=<your username, credentials provided by Microsoft>
export DOCKER_PASSWORD=<your password, credentials provided by Microsoft>
export DOCKER_EMAIL=<your Docker email, use the username provided by Microsoft>
export DOCKER_PRIVATE_REGISTRY="1"
```

> [!NOTE]
> Pendant la préversion publique limitée, les informations d’identification de Docker pour télécharger les images de cluster SQL Server Big Data sont fournies pour chaque client par Microsoft. Pour demander l’accès, vous devez inscrire [ici](https://aka.ms/eapsignup)et spécifiez votre intérêt pour essayer les clusters de données volumineuses de SQL Server.

## <a name="deploy-a-big-data-cluster"></a>Déployer un cluster de données volumineuses

Pour déployer un cluster SQL Server 2019 CTP 2.0 de données volumineux sur votre cluster Kubernetes, exécutez la commande suivante :

```bash
mssqlctl create cluster <name of your cluster>
```

> [!NOTE]
> Le nom de votre cluster doit être uniquement alphanumériques minuscules, sans espaces. Tous les artefacts de Kubernetes pour le cluster de données volumineuses seront créées dans un espace de noms avec le même nom que le cluster de nom spécifié.


La fenêtre de commande affiche l’état du déploiement. Vous pouvez également vérifier l’état du déploiement en exécutant ces commandes dans une fenêtre cmd différents :

```bash
kubectl get all -n <name of your cluster>
kubectl get pods -n <name of your cluster>
kubectl get svc -n <name of your cluster>
```

Vous pouvez voir un état et configuration pour chaque pod plus granulaire en exécutant :
```bash
kubectl describe pod <pod name> -n <name of your cluster>
```

Une fois que le pod de contrôleur est en cours d’exécution, vous pouvez utiliser le portail d’Administration de Cluster pour surveiller le déploiement. Vous pouvez accéder au portail à l’aide de l’externe IP adresse et numéro de port pour le `service-proxy-lb` (par exemple : **https://\<ip-address\>: 30777**). Informations d’identification pour accéder au portail d’administration est les valeurs de `CONTROLLER_USERNAME` et `CONTROLLER_PASSWORD` variables d’environnement fournis ci-dessus.

Vous pouvez obtenir l’adresse IP du service de proxy-service-lb en exécutant cette commande dans une fenêtre bash ou cmd :

```bash
kubectl get svc service-proxy-lb -n <name of your cluster>
```

> [!NOTE]
> Vous verrez un avertissement de sécurité lorsque vous accédez à la page web dans la mesure où nous utilisons des certificats SSL générés automatiquement. Dans les futures versions, nous fournirons la capacité de fournir vos propres certificats auto-signés.
 

## <a name="connect-to-the-big-data-cluster"></a>Connectez-vous au cluster big data

Une fois le script de déploiement terminée, vous pouvez obtenir l’adresse IP de l’instance principale de SQL Server et les points de terminaison Spark/HDFS à l’aide de la procédure décrite ci-dessous. Tous les points de terminaison de cluster sont affichés dans la section points de terminaison de Service dans le portail d’Administration de Cluster ainsi qu’à faciliter la référence.

Azure fournit le service de l’équilibreur de charge Azure pour AKS. Exécutez la commande dans une cmd suivante ou bash fenêtre :

```bash
kubectl get svc service-master-pool-lb -n <name of your cluster>
kubectl get svc service-security-lb -n <name of your cluster>
```

Recherchez le **External-IP** valeur assignée aux services. Se connecter à l’instance principale de SQL Server à l’aide de l’adresse IP pour le `service-master-pool-lb` au port 31433 (Ex :  **\<ip-address\>, 31433**) et pour le point de terminaison cluster de données SQL Server à l’aide de l’IP externe pour le `service-security-lb` service.   Que le point de terminaison de cluster big data est où vous pouvez interagir avec HDFS et envoyer des travaux Spark via Knox.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que le cluster de données volumineuses de SQL Server est déployé, essayez certaines des nouvelles fonctionnalités :

> [!div class="nextstepaction"]
> [Comment utiliser des blocs-notes en version préliminaire de SQL Server 2019](notebooks-guidance.md)
