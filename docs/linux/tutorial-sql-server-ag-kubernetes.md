---
title: Configurer un groupe de disponibilité SQL Server Always On sur des conteneurs Docker dans Kubernetes | Microsoft Docs
description: Ce didacticiel montre comment déployer un serveur SQL toujours sur le groupe de disponibilité avec Kubernetes sur Azure Container Service.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: tutorial
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux,mvc
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6d21866f3f7004dff1ea86ca4f608580a79ab754
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049359"
---
# <a name="configure-a-sql-server-always-on-availability-group-on-docker-containers-in-kubernetes-with-azure-kubernetes-service-aks"></a>Configurer un groupe de disponibilité SQL Server Always On sur des conteneurs Docker dans Kubernetes avec Azure Kubernetes Service (AKS)

Ce didacticiel montre comment configurer une instance de SQL Server hautement disponible dans un conteneur sur AKS. Vous pouvez également [déployer un conteneur de SQL Server dans Kubernetes](tutorial-sql-server-containers-kubernetes.md). Pour comparer les deux différentes solutions de Kubernetes, consultez [haute disponibilité pour les conteneurs de SQL Server](sql-server-linux-container-ha-overview.md).

Dans ce didacticiel, vous allez découvrir comment :  

> [!div class="checklist"]
> * Créer le stockage
> * Déployer l’opérateur de SQL Server sur un cluster Kubernetes 
> * Créer des clés secrètes Kubernetes
> * Déployer des instances de SQL Server et les agents d’intégrité
> * Se connecter au réplica principal
> * Ajouter une base de données au groupe de disponibilité

Ce didacticiel illustre l’architecture dans [Azure Kubernetes Service (AKS)](http://docs.microsoft.com/azure/aks/). Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) avant de commencer.

Ce diagramme représente la solution que vous apportez dans ce didacticiel :

![cluster kubernetes-groupe de disponibilité](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

### <a name="deployment-methodology-for-kubernetes"></a>Méthodologie de déploiement pour Kubernetes

Plusieurs des étapes de cet article créer un manifeste et ensuite déploiement le manifeste sur le cluster. Le manifeste est un fichier .yaml avec la description des objets Kubernetes que vous déployez.

Les fichiers .yaml dans cet exemple sont disponibles au [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability).

Les objets incluent le stockage, les opérateurs, les pods, les conteneurs et les services.

## <a name="prerequisites"></a>Prérequis

* Déjà familiarisé avec ces technologies

  * [Kubernetes](http://kubernetes.io) version 1.8
  * [Azure Kubernetes Service (AKS)](http://docs.microsoft.com/azure/aks/)
  * [SQL Server sur Docker](quickstart-install-connect-docker.md)
  * [Groupe de disponibilité SQL Server Always On](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

* Un cluster Kubernetes avec quatre nœuds.

  Pour obtenir des instructions, reportez-vous à [didacticiel : déployer un cluster Azure Kubernetes Service (AKS)](http://docs.microsoft.com/azure/aks/tutorial-kubernetes-deploy-cluster).

* Installer [ `kubectl` ](https://docs.microsoft.com/en-us/azure/aks/tutorial-kubernetes-deploy-cluster#install-the-kubectl-cli).

## <a name="configuration-and-deployment-procedures"></a>Procédures de configuration et de déploiement

Le didacticiel explique comment appliquer les fichiers .yaml à votre cluster Kubernetes.

## <a name="create-the-secrets"></a>Créer les clés secrètes

Pour créer des clés secrètes Kubernetes pour stocker les mots de passe pour le compte SA de SQL Server et la clé principale de SQL Server, exécutez la commande suivante.

```azurecli
kubectl create secret generic sql-secrets --from-literal=sapassword="MyC0m9l&xP@ssw0rd" --from-literal=masterkeypassword="MyC0m9l&xP@ssw0rd2"
```

Dans un environnement de production, utilisez un autre mot de passe complexe.

## <a name="deploy-the-operator"></a>Déployer l’opérateur

Un opérateur Kubernetes déploie les instances de SQL Server et configure le groupe de disponibilité dans le cluster Kubernetes. 

Consultez un opérateur d’exemple à [`operator.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml)

Télécharger `operator.yaml` de [sql-server-samples](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/)

Déployer l’opérateur en tant que réplica d’un déploiement Kubernetes.

Pour déployer l’opérateur :

Déployer l’opérateur avec la `kubectl apply` commande.

```azurecli
kubectl apply -f operator.yaml
```

## <a name="create-the-sql-server-ag-deployment"></a>Créer le déploiement de groupe de disponibilité de SQL Server

L’étape suivante crée les instances de SQL Server et le groupe de disponibilité dans un déploiement Kubernetes. Après avoir appliqué ce déploiement vers le cluster, l’opérateur déploiera les instances de SQL Server en tant que conteneurs Docker. Ce déploiement génère trois StatefulSets avec un pod. Chaque pod inclut deux conteneurs :

* Instance de SQL Server basée sur le `mssql-server` image
* Superviseur de haute disponibilité

En outre, le déploiement décrit un service d’équilibrage de charge pour l’écouteur de groupe de disponibilité

Pour déployer mssql-server :

1. Copie [sqlserver.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml) sur votre ordinateur.
2. Mise à jour `sqlserver.yaml` pour votre environnement.


Pour déployer les instances de SQL Server et créer le groupe de disponibilité, exécutez la commande suivante.

```azurecli
kubectl apply -f sqlserver.yaml
```

## <a name="deploy-ag-services"></a>Services de déployer le groupe de disponibilité

Créer des services équilibreur de charge pour les appels directs aux réplicas dans le groupe de disponibilité dans le cluster Kubernetes.

[groupe de disponibilité-services.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) crée quatre services.

* AG1 principal se connecte au réplica principal.
* synchronisation de base de données secondaire AG1 se connecte à un réplica secondaire synchrone.
* AG1-base de données secondaire-async se connecte à un réplica secondaire asynchrone.
* configuration de base de données secondaire AG1 se connecte à un réplica en configuration seule. 

  >[!NOTE]
  >Ces services d’équilibrage de charge sont fournis comme exemples. Dans ce didacticiel, il est non réplica en configuration seule.


Déployer les services d’équilibrage de charge afin que vous pouvez vous connecter au groupe de disponibilité.

Pour déployer les services, exécutez la commande suivante.

```azurecli
kubectl apply -f ag-services.yaml
```

### <a name="monitor-the-deployment"></a>Surveiller le déploiement

Vous pouvez utiliser [tableau de bord Kubernetes avec Azure Kubernetes Service (AKS)](https://docs.microsoft.com/en-us/azure/aks/kubernetes-dashboard) pour surveiller le déploiement. 

Utilisez `az aks browse` pour lancer le tableau de bord. 

Après le déploiement, vous pouvez mettre à jour uniquement AG appartenance liste et post-init script T-SQL. Autres propriétés ne peuvent pas être mis à jour : la ressource doit être supprimée et recréée. Informations d’identification pour les utilisateurs générée automatiquement peuvent être pivotées à l’aide un `mssql-server-k8s-rotate-creds` travail.

## <a name="connect-to-the-sql-server-instance-hosting-the-primary-replica"></a>Connectez-vous à l’instance de SQL Server qui héberge le réplica principal

Le `ag-services.yaml` décrit un nom de service Kubernetes `ag1-primary`. `ag1-primary` Crée un équilibreur de charge Azure qui pointent de l’instance de SQL Server qui héberge le réplica principal. Utiliser l’adresse IP externe du service en tant que serveur cible, `sa` en tant que compte et le mot de passe que vous avez créée dans le `mssql secret` pour le mot de passe.

Utilisez `kubectl get services` pour obtenir cette adresse IP.

Exemple :

![Obtenir l’exemple de service](media\tutorial-sql-server-ag-containers-kubernetes\KubernetesGetServices.png)

Dans l’image ci-dessus, `ag1-primary` service a une adresse IP externe de `104.42-50.138`. 

Pour vous connecter à SQL Server avec l’authentification SQL, utilisez la `sa` compte, la valeur de `sapassword` à partir de la clé secrète que vous avez créé et que cette adresse IP.

Exemple :

```cmd
sqlcmd -S 104.42.50.138 -U sa -P "MyC0m9l&xP@ssw0rd"
```

![Se connecter avec sqlcmd](./media/tutorial-sql-server-ag-containers-kubernetes/sqlcmdConnect.png)

Vous pouvez également vous connecter avec [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md).

Pour vérifier votre connexion, à l’instance de SQL Server qui héberge le réplica principal, exécutez la requête suivante :

```sql
SELECT @@SERVERNAME;
```

La requête retourne le nom de l’instance de SQL Server qui héberge le réplica principal.

À ce stade, le cluster Kubernetes a trois instances de SQL Server dans des conteneurs docker. Un groupe de disponibilité s’étend sur les trois instances de SQL Server, mais aucune base de données n’est dans le groupe de disponibilité. L’étape suivante consiste à ajouter une base de données au groupe de disponibilité.

## <a name="add-a-database-to-the-availability-group"></a>Ajouter une base de données au groupe de disponibilité

Pour ajouter une base de données au groupe de disponibilité :

1. création d'une base de données ;

  ```sql
  CREATE DATABASE [DemoDB]
  ```

1. Effectuez une sauvegarde de la base de données pour démarrer la chaîne de journaux de transaction complète

  ```sql
  BACKUP DATABASE [DemoDB] 
  TO  DISK = N'/var/opt/mssql/data/DemoDB.bak' 
    WITH NOFORMAT, 
    NOINIT,  
    NAME = N'DemoDB-Full Database Backup', 
    SKIP, 
    NOREWIND, 
    NOUNLOAD,  
    STATS = 10;
  GO
  ```

1. Ajouter la base de données au groupe de disponibilité

  ```sql
  ALTER AVAILABILITY GROUP ag1 ADD DATABASE [DemoDB]; 
  ```

Le réplica est automatiquement configuré avec le mode d’amorçage automatique pour le groupe de disponibilité amorce la base de données sur les réplicas secondaires.

Dans SQL Server Management Studio, vous pouvez vous connecter au réplica principal et voir le groupe de disponibilité dans le tableau de bord.

L’exemple suivant montre le groupe de disponibilité avec des réplicas sur trois nœuds configurés dans le tableau de bord.

![Tableau de bord AG1](./media/tutorial-sql-server-ag-containers-kubernetes/ssms_AG1.png)

## <a name="verify-failure-and-recovery"></a>Vérifiez que la défaillance et récupération

Pour vérifier la détection des défaillances et basculement, vous pouvez supprimer le pod qui héberge le réplica principal. Kubernetes sera élire un nouveau réplica principal et rediriger l’écouteur. Puis il recrée le pod supprimé. 

Pour illustrer ce processus, procédez comme suit :

1. Répertorier le pod exécutant SQL Server.

   ```azurecli
   kubectl get pods
   ```

2. Identifiez le pod en cours d’exécution le réplica principal.

   Soit vous connecter au réplica principal à l’aide de l’adresse IP et la requête externe `@@servername` ou utilisez `kubectl` pour obtenir le pod approprié. Cette commande renvoie le nom du pod qui inclut le conteneur en cours d’exécution le réplica principal du groupe de disponibilité :

   ```azurecli
   kubectl get pods --selector="role.ag.mssql.microsoft.com/ag1"="primary" --output=jsonpath={.items..metadata.name}
   ```

3. Supprimer le pod.

   ```azurecli
   kubectl delete pod <podName>
   ```

Remplacez `<podName>` avec la valeur retournée à partir de l’étape précédente pour le nom du pod. 

Kubernetes automatiquement bascule vers un des réplicas secondaires de synchronisation disponibles ainsi que recrée le pod supprimé.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Lorsque vous n’en avez plus besoin, supprimez le groupe de ressources et toutes les ressources associées. Exécutez la commande suivante :
>[!WARNING]
>Cette commande supprime complètement tous les éléments dans le groupe de ressources. Aucun des composants du cluster Kubernetes sera disponible une fois que vous supprimez le groupe de ressources.

```azurecli
az group delete --name <MyResourceGroup>
```

Pour exécuter la commande ci-dessus, remplacez `<MyResourceGroup>` par le nom de votre groupe de ressources. 

Azure supprime le groupe de ressources.

## <a name="summary"></a>Résumé

Dans ce didacticiel, vous avez appris comment :  

> [!div class="checklist"]
> * Créer le stockage
> * Déployer l’opérateur de SQL Server sur un cluster Kubernetes 
> * Créer des clés secrètes Kubernetes
> * Déployer des instances de SQL Server et les agents d’intégrité
> * Se connecter au réplica principal
> * Ajouter une base de données au groupe de disponibilité

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
>[Introduction à Kubernetes](http://docs.microsoft.com/azure/aks/intro-kubernetes)
>[gérer SQL Server sur Kubernetes](sql-server-linux-kubernetes-manage.md)