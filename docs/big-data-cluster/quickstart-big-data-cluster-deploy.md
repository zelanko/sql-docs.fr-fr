---
title: Script de déploiement
titleSuffix: SQL Server big data clusters
description: 'Procédure pas à pas: déploiement de SQL Server 2019 Big Data clusters (version préliminaire) sur Azure Kubernetes service (AKS).'
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7ff1ec3672fbcf101d98ad30913742186dea574d
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419402"
---
# <a name="deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Déployer SQL Server Cluster Big Data sur Azure Kubernetes service (AKS)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dans ce didacticiel, vous utilisez un exemple de script de déploiement pour déployer SQL Server 2019 Big Data cluster (version préliminaire) dans le service Kubernetes Azure (AKS). 

> [!TIP]
> AKS n’est qu’une option pour héberger des Kubernetes pour votre cluster Big Data. Pour en savoir plus sur les autres options de déploiement et sur la personnalisation des options de déploiement, consultez [comment déployer des clusters SQL Server Big Data sur Kubernetes](deployment-guidance.md).

Le déploiement de cluster Big Data par défaut utilisé ici se compose d’une instance SQL Master, d’une instance de pool de calcul, de deux instances de pool de données et de deux instances de pool de stockage. Les données sont conservées à l’aide de volumes persistants Kubernetes qui utilisent les classes de stockage par défaut AKS. La configuration par défaut utilisée dans ce didacticiel est adaptée aux environnements de développement et de test.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>Prérequis

- Un abonnement Azure.
- [Outils Big Data](deploy-big-data-tools.md):
   - **azdata**
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server extension 2019**
   - **Interface de ligne de commande Azure**

## <a name="log-in-to-your-azure-account"></a>Connectez-vous à votre compte Azure

Le script utilise Azure CLI pour automatiser la création d’un cluster AKS. Avant d’exécuter le script, vous devez vous connecter à votre compte Azure avec Azure CLI au moins une fois. Exécutez la commande suivante à partir d’une invite de commandes.

```
az login
```

## <a name="download-the-deployment-script"></a>Télécharger le script de déploiement

Ce didacticiel automatise la création du cluster Big Data sur AKS à l’aide d’un script Python **Deploy-SQL-Big-Data-AKS.py**. Si vous avez déjà installé python pour **azdata**, vous devriez pouvoir exécuter le script avec succès dans ce didacticiel. 

Dans une invite bash Windows PowerShell ou Linux, exécutez la commande suivante pour télécharger le script de déploiement à partir de GitHub.

```
curl -o deploy-sql-big-data-aks.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/aks/deploy-sql-big-data-aks.py"
```

## <a name="run-the-deployment-script"></a>Exécuter le script de déploiement

Procédez comme suit pour exécuter le script de déploiement. Ce script crée un service AKS dans Azure, puis déploie un cluster SQL Server 2019 Big Data sur AKS. Vous pouvez également modifier le script avec d’autres [variables d’environnement](deployment-guidance.md#configfile) pour créer un déploiement personnalisé.

1. Exécutez le script avec la commande suivante :

   ```
   python deploy-sql-big-data-aks.py
   ```

   > [!NOTE]
   > Si vous avez à la fois Python3 et python2 sur votre machine cliente et dans le chemin d’accès, vous devez exécuter la `python3 deploy-sql-big-data-aks.py`commande à l’aide de Python3:.

1. Lorsque vous y êtes invité, entrez les informations suivantes:

   | Value | Description |
   |---|---|
   | **ID d’abonnement Azure** | ID d’abonnement Azure à utiliser pour AKS. Vous pouvez répertorier tous vos abonnements et leurs ID en `az account list` exécutant à partir d’une autre ligne de commande. |
   | **Groupe de ressources Azure** | Nom du groupe de ressources Azure à créer pour le cluster AKS. |
   | **Région Azure** | Région Azure pour le nouveau cluster AKS (ouest de l' **Ouest**par défaut). |
   | **Taille de la machine** | Taille de l' [ordinateur](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) à utiliser pour les nœuds du cluster AKS (par défaut **Standard_L8s**). |
   | **Nœuds Worker** | Nombre de nœuds Worker dans le cluster AKS (par défaut, **1**). |
   | **Nom du cluster** | Nom du cluster AKS et du cluster Big Data. Le nom de votre cluster Big Data ne doit contenir que des caractères alphanumériques minuscules et aucun espace. ( **sqlbigdata**par défaut). |
   | **Mot de passe** | Mot de passe pour le contrôleur, la passerelle HDFS/Spark et l’instance principale ( **MySQLBigData2019**par défaut). |
   | **Utilisateur du contrôleur** | Nom d’utilisateur de l’utilisateur contrôleur (par défaut: **admin**). |

Les paramètres suivants étaient requis pour les participants au programme early adopter SQL Server 2019 Big Data cluster: **Nom d’utilisateur**et **mot de passe**de l’ancrage. À partir de CTP 3,2, ils ne sont plus nécessaires.

   > [!IMPORTANT]
   > La taille de machine **Standard_L8s** par défaut n’est peut-être pas disponible dans toutes les régions Azure. Si vous sélectionnez une autre taille de machine, assurez-vous que le nombre total de disques pouvant être attachés entre les nœuds du cluster est supérieur ou égal à 24. Chaque revendication de volume persistant dans le cluster nécessite un disque attaché. Actuellement, Big Data cluster requiert 24 revendications de volume persistantes. Par exemple, la taille de machine [Standard_L8s](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-storage#lsv2-series) prend en charge 32 disques attachés. vous pouvez donc évaluer Big Data clusters avec un seul nœud de cette taille de machine.

   > [!NOTE]
   > Le `sa` compte est un administrateur système sur l’instance SQL Server Master qui est créée lors de l’installation. Après la création du déploiement `MSSQL_SA_PASSWORD` , la variable d’environnement est détectable en `echo $MSSQL_SA_PASSWORD` exécutant dans le conteneur de l’instance principale. Pour des raisons de sécurité, `sa` modifiez votre mot de passe sur l’instance principale après le déploiement. Pour plus d’informations, consultez [modifier le mot de passe sa](../linux/quickstart-install-connect-docker.md#sapassword).

1. Le script commence par créer un cluster AKS à l’aide des paramètres que vous avez spécifiés. Cette étape prend plusieurs minutes.

   <img src="./media/quickstart-big-data-cluster-deploy/script-parameters.png" width="800px" alt="Script parameters and AKS cluster creation"/>

## <a name="monitor-the-status"></a>Surveiller l’État

Une fois que le script a créé le cluster AKS, il continue de définir les variables d’environnement nécessaires avec les paramètres que vous avez spécifiés précédemment. Il appelle ensuite **azdata** pour déployer le cluster Big Data sur AKS.

La fenêtre de commande du client génère l’état du déploiement. Pendant le processus de déploiement, vous devez voir une série de messages dans laquelle il attend le pod du contrôleur:

```output
2018-11-15 15:42:02.0209 UTC | INFO | Waiting for controller pod to be up...
```

Après 10 à 20 minutes, vous devez être informé que le pod du contrôleur est en cours d’exécution:

```output
2018-11-15 15:50:50.0300 UTC | INFO | Controller pod is running.
2018-11-15 15:50:50.0585 UTC | INFO | Controller Endpoint: https://111.111.111.111:30080
```

> [!IMPORTANT]
> L’ensemble du déploiement peut prendre beaucoup de temps en raison du temps nécessaire au téléchargement des images conteneur pour les composants du cluster Big Data. Toutefois, il ne doit pas prendre plusieurs heures. Si vous rencontrez des problèmes avec votre déploiement, consultez [surveillance et résolution des problèmes SQL Server les clusters Big Data](cluster-troubleshooting-commands.md).

## <a name="inspect-the-cluster"></a>Inspecter le cluster

À tout moment pendant le déploiement, vous pouvez utiliser **kubectl** ou **azdata** pour inspecter l’État et les détails relatifs au cluster en cours d’exécution Big Data.

### <a name="use-kubectl"></a>Utiliser kubectl

Ouvrez une nouvelle fenêtre de commande pour utiliser **kubectl** pendant le processus de déploiement.

1. Exécutez la commande suivante pour obtenir un résumé de l’état de l’ensemble du cluster:

   ```
   kubectl get all -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Si vous n’avez pas modifié le nom du cluster Big Data, le script est par défaut **sqlbigdata**.

1. Examinez les services kubernetes et leurs points de terminaison internes et externes avec la commande **kubectl** suivante:

   ```
   kubectl get svc -n <your-big-data-cluster-name>
   ```

1. Vous pouvez également inspecter l’état des gousses kubernetes à l’aide de la commande suivante:

   ```
   kubectl get pods -n <your-big-data-cluster-name>
   ```

1. Pour plus d’informations sur un pod spécifique, consultez la commande suivante:

   ```
   kubectl describe pod <pod name> -n <your-big-data-cluster-name>
   ```

> [!TIP]
> Pour plus d’informations sur la surveillance et la résolution des problèmes d’un déploiement, consultez [surveillance et résolution des problèmes de SQL Server des clusters Big Data](cluster-troubleshooting-commands.md).

## <a name="connect-to-the-cluster"></a>Connexion au cluster

Une fois le script de déploiement terminé, la sortie vous avertit de la réussite:

```output
2018-11-15 16:10:25.0583 UTC | INFO | Cluster state: Ready
2018-11-15 16:10:25.0583 UTC | INFO | Cluster deployed successfully.
```

Le cluster SQL Server Big Data est maintenant déployé sur AKS. Vous pouvez maintenant utiliser Azure Data Studio pour vous connecter au cluster. Pour plus d’informations, consultez [se connecter à un cluster SQL Server Big Data avec Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="clean-up"></a>Nettoyer

Si vous testez SQL Server Clusters Big Data dans Azure, vous devez supprimer le cluster AKS lorsque vous avez terminé pour éviter des frais inattendus. Ne supprimez pas le cluster si vous envisagez de continuer à l’utiliser.

> [!WARNING]
> Les étapes suivantes décomposent le cluster AKS qui supprime également le cluster Big Data SQL Server. Si vous souhaitez conserver des bases de données ou des données HDFS, sauvegardez-les avant de supprimer le cluster.

Exécutez la commande Azure CLI suivante pour supprimer le cluster Big Data et le service AKS dans Azure (à `<resource group name>` remplacer par le **groupe de ressources Azure** que vous avez spécifié dans le script de déploiement):

```azurecli
az group delete -n <resource group name>
```

## <a name="next-steps"></a>Étapes suivantes

Le script de déploiement a configuré le service Azure Kubernetes et a également déployé un cluster SQL Server 2019 Big Data. Vous pouvez également choisir de personnaliser les futurs déploiements par le biais d’installations manuelles. Pour en savoir plus sur la façon dont Big Data les clusters sont déployés, ainsi que sur la personnalisation des déploiements, consultez [comment déployer des clusters Big Data SQL Server sur Kubernetes](deployment-guidance.md).

Maintenant que le cluster SQL Server Big Data est déployé, vous pouvez charger les exemples de données et explorer les didacticiels:

> [!div class="nextstepaction"]
> [Tutoriel : Charger des exemples de données dans un cluster SQL Server 2019 Big Data](tutorial-load-sample-data.md)