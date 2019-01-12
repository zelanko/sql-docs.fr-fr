---
title: Démarrage rapide du déploiement
titleSuffix: SQL Server 2019 big data clusters
description: Procédure pas à pas un déploiement de clusters SQL Server 2019 données volumineuses (version préliminaire) sur Azure Kubernetes Service (AKS).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/17/2018
ms.topic: quickstart
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 39c79c39c04d64656b83004425d476896cbc75db
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241700"
---
# <a name="quickstart-deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Démarrage rapide : Déployer le cluster de données volumineux de SQL Server sur Azure Kubernetes Service (AKS)

Dans ce démarrage rapide, vous utilisez un exemple de script de déploiement pour déployer le cluster de données volumineux SQL Server 2019 (version préliminaire) pour Azure Kubernetes Service (AKS). 

> [!TIP]
> ACS n'est qu’une seule option pour l’hébergement de Kubernetes pour votre cluster de données volumineux. Pour en savoir plus sur les autres options de déploiement, ainsi que la manière dont les options pour personnaliser le déploiement, consultez [comment déployer des données volumineuses de SQL Server clusters sur Kubernetes](deployment-guidance.md).

Le déploiement de cluster de données volumineuses par défaut utilisé ici se compose d’une instance SQL principale, instance de pool d’un calcul, deux instances de pool de données et deux instances de pool de stockage. Données sont conservées à l’aide de volumes persistants Kubernetes qui utilisent les classes de stockage par défaut AKS. La configuration par défaut utilisée dans ce démarrage rapide est adaptée aux environnements de développement/test.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>Prérequis

- Un abonnement Azure.
- [Outils de Big data](deploy-big-data-tools.md):
   - **mssqlctl**
   - **kubectl**
   - **Azure Data Studio**
   - **Extension de SQL Server 2019**
   - **Azure CLI**

## <a name="log-in-to-your-azure-account"></a>Connectez-vous à votre compte Azure

Le script utilise Azure CLI pour automatiser la création d’un cluster AKS. Avant d’exécuter le script, vous devez vous connecter à votre compte Azure avec Azure CLI au moins une fois. Exécutez la commande suivante à partir d’une invite de commandes.

```
az login
```

## <a name="download-the-deployment-script"></a>Télécharger le script de déploiement

Ce démarrage rapide automatise la création du cluster big data sur AKS à l’aide d’un script python **déployer-sql-big-data-aks.py**. Si vous avez déjà installé python pour **mssqlctl**, vous devez être en mesure d’exécuter le script avec succès dans ce démarrage rapide. 

Dans une invite de l’interpréteur de commandes Windows PowerShell ou Linux, exécutez la commande suivante pour télécharger le script de déploiement à partir de GitHub.

```
curl -o deploy-sql-big-data-aks.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/aks/deploy-sql-big-data-aks.py"
```

## <a name="run-the-deployment-script"></a>Exécutez le script de déploiement

Utilisez les étapes suivantes pour exécuter le script de déploiement. Ce script crée un service AKS dans Azure et puis déployer un cluster de données volumineuses de SQL Server 2019 sur AKS. Vous pouvez également modifier le script avec d’autres [variables d’environnement](deployment-guidance.md#env) pour créer un déploiement personnalisé.

1. Exécutez le script avec la commande suivante :

   ```
   python deploy-sql-big-data-aks.py
   ```

   > [!NOTE]
   > Si vous avez python3 et python2 sur votre ordinateur client et dans le chemin d’accès, vous devez exécuter la commande à l’aide de python3 : `python3 deploy-sql-big-data-aks.py`.

1. Lorsque vous y êtes invité, entrez les informations suivantes :

   | Value | Description |
   |---|---|
   | **ID d’abonnement Azure** | ID d’abonnement Azure à utiliser pour AKS. Vous pouvez répertorier tous vos abonnements et leurs ID en exécutant `az account list` à partir d’une autre ligne de commande. |
   | **Groupe de ressources Azure** | Le nom de groupe de ressources Azure pour créer le cluster AKS. |
   | **Nom d’utilisateur docker** | Le nom d’utilisateur Docker fourni dans le cadre de la version préliminaire publique limitée. |
   | **Mot de passe docker** | Le mot de passe Docker fourni dans le cadre de la version préliminaire publique limitée. |
   | **Région Azure** | La région Azure pour le nouveau cluster AKS (par défaut **westus**). |
   | **Taille de machine** | Le [taille de la machine](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) à utiliser pour les nœuds du cluster AKS (par défaut **Standard_L4s**). |
   | **Nœuds de travail** | Le nombre de nœuds de travail dans le cluster AKS (par défaut **3**). |
   | **Nom du cluster** | Le nom de cluster AKS et le cluster de données volumineux. Le nom de votre cluster doit être uniquement des caractères alphanumériques minuscules et sans espaces. (par défaut **sqlbigdata**). |
   | **Mot de passe** | Mot de passe pour le contrôleur, une passerelle HDFS/Spark et une instance principale (par défaut **MySQLBigData2019**). |
   | **Utilisateur du contrôleur** | Nom d’utilisateur pour l’utilisateur du contrôleur (par défaut : **administrateur**). |

   > [!IMPORTANT]
   > Chaque revendication de volume persistant dans le cluster nécessite un disque attaché. Actuellement, cluster big data nécessite 21 revendications de volume persistant. Lorsque vous choisissez une taille de machine virtuelle et le nombre de nœuds, assurez-vous que le nombre total de disques pouvant être connectés entre les nœuds est supérieure ou égale à 21. Par exemple, le [Standard_L4s](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-storage#ls-series) taille de l’ordinateur prend en charge 16 disques attachés, trois nœuds signifie que les 48 disques peuvent être attachés.

   > [!NOTE]
   > Le `sa` compte est un administrateur système sur l’instance principale de SQL Server qui est créé pendant l’installation. Après avoir créé le déploiement, la `MSSQL_SA_PASSWORD` variable d’environnement est détectable en exécutant `echo $MSSQL_SA_PASSWORD` dans le conteneur de l’instance principale. Pour des raisons de sécurité, vous devez modifier votre `sa` mot de passe sur l’instance principale après le déploiement. Pour plus d’informations, consultez [modifier le mot de passe SA](../linux/quickstart-install-connect-docker.md#sapassword).

1. Le script démarre en créant un cluster ACS en utilisant les paramètres que vous avez spécifié. Cette étape prend plusieurs minutes.

   <img src="./media/quickstart-big-data-cluster-deploy/script-parameters.png" width="800px" alt="Script parameters and AKS cluster creation"/>

## <a name="monitor-the-status"></a>Surveiller l’état

Une fois le script crée le cluster AKS, il se poursuit pour définir les variables d’environnement nécessaires avec les paramètres que vous avez spécifié précédemment. Il appelle ensuite **mssqlctl** pour déployer le cluster de données volumineuses sur AKS.

La fenêtre de commande client affiche l’état du déploiement. Pendant le processus de déploiement, vous devez voir une série de messages où il attend que le pod de contrôleur :

```output
2018-11-15 15:42:02.0209 UTC | INFO | Waiting for controller pod to be up...
```

Au bout de 10 à 20 minutes, vous devez averti que le pod de contrôleur est en cours d’exécution :

```output
2018-11-15 15:50:50.0300 UTC | INFO | Controller pod is running.
2018-11-15 15:50:50.0585 UTC | INFO | Controller Endpoint: https://111.222.222.222:30080
```

> [!IMPORTANT]
> La totalité du déploiement peut prendre beaucoup de temps en raison du temps nécessaire pour télécharger les images de conteneur pour les composants du cluster de données volumineuses. Toutefois, il ne doit pas prendre plusieurs heures. Si vous rencontrez des problèmes avec votre déploiement, consultez le [la résolution des problèmes de déploiement](deployment-guidance.md#troubleshoot) section de l’article de conseils de déploiement.

## <a name="inspect-the-cluster"></a>Inspecter le cluster

À tout moment au cours du déploiement, vous pouvez utiliser kubectl ou le portail d’Administration de Cluster pour inspecter l’état et les détails sur le cluster de données volumineux en cours d’exécution.

### <a name="use-kubectl"></a>Utiliser kubectl

Ouvrez une nouvelle fenêtre de commande à utiliser **kubectl** pendant le processus de déploiement.

1. Exécutez la commande suivante pour obtenir un résumé de l’état de l’ensemble du cluster :

   ```
   kubectl get all -n <your-cluster-name>
   ```

1. Vérifiez que les services kubernetes et leurs points de terminaison internes et externes par le code suivant **kubectl** commande :

   ```
   kubectl get svc -n <your-cluster-name>
   ```

1. Vous pouvez également examiner l’état des pods kubernetes avec la commande suivante :

   ```
   kubectl get pods -n <your-cluster-name>
   ```

1. Découvrez plus d’informations sur un pod spécifique avec la commande suivante :

   ```
   kubectl describe pod <pod name> -n <your-cluster-name>
   ```

> [!TIP]
> Pour plus d’informations sur comment surveiller et résoudre les problèmes d’un déploiement, consultez le [la résolution des problèmes de déploiement](deployment-guidance.md#troubleshoot) section de l’article de conseils de déploiement.

### <a name="use-the-cluster-administration-portal"></a>Utilisez le portail d’Administration de Cluster

Une fois que le pod de contrôleur est en cours d’exécution, vous pouvez également utiliser le portail d’Administration de Cluster pour surveiller le déploiement. Vous pouvez accéder au portail à l’aide de l’externe IP adresse et numéro de port pour le `service-proxy-lb` (par exemple : **https://\<ip-address\>: 30777/portail**). Les informations d’identification utilisées pour se connecter au portail correspondent aux valeurs pour **utilisateur du contrôleur** et **mot de passe** que vous avez spécifié dans le script de déploiement.

Vous pouvez obtenir l’adresse IP de la **proxy-service-lb** service en exécutant cette commande dans une fenêtre bash ou cmd :

```bash
kubectl get svc service-proxy-lb -n <your-cluster-name>
```

> [!NOTE]
> Dans CTP 2.2, vous verrez un avertissement de sécurité lorsque vous accédez à la page web, car les clusters de données volumineuses est actuellement à l’aide de certificats SSL générés automatiquement. En outre, dans CTP 2.2, il n’affiche pas l’état de l’instance principale de SQL Server.

## <a name="connect-to-the-cluster"></a>Connectez-vous au cluster

Une fois le script de déploiement, la sortie vous informe de réussite :

```output
2018-11-15 16:10:25.0583 UTC | INFO | Cluster state: Ready
2018-11-15 16:10:25.0583 UTC | INFO | Cluster deployed successfully.
```

Le cluster de données volumineux de SQL Server est désormais déployé sur AKS. Vous pouvez maintenant utiliser Azure Data Studio pour vous connecter à l’instance principale de SQL Server et les points de terminaison HDFS/Spark à l’aide d’Azure Data Studio.

### <a id="master"></a> Instance principale

L’instance principale de SQL Server est une instance de SQL Server traditionnelle contenant les bases de données relationnelles SQL Server. Les étapes suivantes décrivent comment vous connecter à l’instance principale à l’aide d’Azure Data Studio.

1. À partir de la ligne de commande, recherchez l’adresse IP de votre instance principale avec la commande suivante :

   ```
   kubectl get svc endpoint-master-pool -n <your-cluster-name>
   ```

1. Dans Azure Data Studio, appuyez sur **F1** > **nouvelle connexion**.

1. Dans **type de connexion**, sélectionnez **Microsoft SQL Server**.

1. Tapez l’adresse IP de l’instance principale de SQL Server dans **nom_serveur** (par exemple : **\<Adresse IP\>, 31433**).

1. Entrez un nom de connexion SQL **nom d’utilisateur** (`SA`) et **mot de passe** (mot de passe que vous avez entré dans le script de déploiement).

1. Modifier la cible **nom de la base de données** à un de vos bases de données relationnelles.

   ![Se connecter à l’instance principale](./media/quickstart-big-data-cluster-deploy/connect-to-cluster.png)

1. Appuyez sur **Connect**et le **tableau de bord Server** doit apparaître.

### <a id="hdfs"></a> Passerelle HDFS/Spark

Le **passerelle HDFS/Spark** vous permet de se connecter pour pouvoir fonctionner avec le pool de stockage HDFS et à exécuter des tâches Spark. Les étapes suivantes décrivent comment vous connecter avec Azure Data Studio.

1. À partir de la ligne de commande, recherchez l’adresse IP de votre passerelle HDFS/Spark avec la commande suivante :

   ```
   kubectl get svc service-security-lb -n <your-cluster-name>
   ```
 
1. Dans Azure Data Studio, appuyez sur **F1** > **nouvelle connexion**.

1. Dans **type de connexion**, sélectionnez **cluster de données volumineux de SQL Server**.
   
   > [!TIP]
   > Si vous ne voyez pas le **cluster de données volumineux de SQL Server** connexion type, assurez-vous que vous avez installé le [extension de SQL Server 2019](../azure-data-studio/sql-server-2019-extension.md) et que vous avez redémarré Azure Data Studio après l’extension terminée l’installation.

1. Tapez l’adresse IP du cluster big data dans **nom_serveur** (ne spécifiez pas de port).

1. Entrez `root` pour le **utilisateur** et spécifiez le **mot de passe** à votre cluster big data que vous avez entré dans le script de déploiement.

   ![Se connecter à HDFS/Spark passerelle](./media/quickstart-big-data-cluster-deploy/connect-to-cluster-hdfs-spark.png)

1. Appuyez sur **Connect**et le **tableau de bord Server** doit apparaître.

## <a name="clean-up"></a>Nettoyer

Si vous testez des clusters de données volumineuses de SQL Server dans Azure, vous devez supprimer le cluster AKS lorsque terminée pour éviter des frais inattendus. Ne supprimez pas le cluster si vous envisagez de continuer à l’utiliser.

> [!WARNING]
> Les étapes suivantes renverse le cluster AKS, ce qui supprime également le cluster de données volumineuses SQL Server. Si vous avez les bases de données ou les données HDFS que vous souhaitez conserver, sauvegardez ces données avant de supprimer le cluster.

Exécutez la commande Azure CLI suivante pour supprimer le cluster de données volumineux et le service ACS dans Azure (remplacez `<resource group name>` avec la **groupe de ressources Azure** vous avez spécifié dans le script de déploiement) :

```azurecli
az group delete -n <resource group name>
```

## <a name="next-steps"></a>Étapes suivantes

Maintenant que le cluster de données volumineuses de SQL Server est déployé, vous pouvez charger des exemples de données et explorez les didacticiels :

> [!div class="nextstepaction"]
> [Didacticiel : Charger des exemples de données dans un cluster de données volumineux de SQL Server 2019](tutorial-load-sample-data.md)