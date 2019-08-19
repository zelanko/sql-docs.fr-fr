---
title: Déployer un groupe de disponibilité Always On SQL Server sur un cluster Kubernetes
description: Cet article explique les paramètres des exigences globales de l’opérateur de groupe de disponibilité Always On Kubernetes SQL Server
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 10/02/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1e8825336edd4e55812f6037bbb4479a3b225e3f
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028732"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-a-kubernetes-cluster"></a>Déployer un groupe de disponibilité Always On SQL Server sur un cluster Kubernetes

L’exemple de cet article déploie un groupe de disponibilité Always On SQL Server sur un cluster Kubernetes avec trois réplicas. Les réplicas secondaires sont en mode de validation synchrone.

Sur Kubernetes, le déploiement comprend un opérateur SQL Server, les conteneurs SQL Server et les services d’équilibrage de charge. L’opérateur orchestre automatiquement le groupe de disponibilité. Cet article explique comment :

- Déployer l’opérateur, les conteneurs SQL Server et les services d’équilibrage de charge.
- Se connecter au groupe de disponibilité avec les services.
- Ajouter une base de données au groupe de disponibilité.

## <a name="requirements"></a>Spécifications

- Un cluster AKS Kubernetes à la dernière version
- Au moins trois nœuds
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- Accès au référentiel GitHub [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files)

> [!NOTE]
> Vous pouvez utiliser n’importe quel type de cluster Kubernetes. Pour créer un cluster Kubernetes sur Azure Kubernetes Service (AKS), consultez [Créer un cluster AKS](https://docs.microsoft.com/azure/aks/create-cluster).
>
> Utilisez la dernière version de Kubernetes. La version spécifique dépend de votre abonnement et de votre région. Voir [Versions de Kubernetes prises en charge dans AKS](https://docs.microsoft.com/azure/aks/supported-kubernetes-versions).  
>
> Le script suivant crée un cluster Kubernetes à quatre nœuds dans Azure. Avant d’exécuter le script, remplacez `<latest version>` par la dernière version disponible. Par exemple, `1.12.5`.
>
> ```azure-cli
> az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version <latest version> --generate-ssh-keys
> ```

## <a name="deploy-the-operator-sql-server-containers-and-load-balancing-services"></a>Déployer l’opérateur, les conteneurs SQL Server et les services d’équilibrage de charge

1. Créez un [espace de noms](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/).

      Cet exemple utilise un espace de noms appelé `ag1`. Exécutez la commande suivante pour créer l’espace de noms.
    
      ```azurecli
      kubectl create namespace ag1
      ```
    
      Tous les objets appartenant à cette solution se trouvent dans l’espace de noms `ag1`.

1. Configurez et déployez le manifeste d’opérateur SQL Server.

      Copiez le fichier [`operator.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml) de SQL Server depuis [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).
    
      Le fichier `operator.yaml` est le manifeste de déploiement pour l’opérateur Kubernetes.
    
      Appliquez le manifeste au cluster Kubernetes.
    
      ```azurecli
      kubectl apply -f operator.yaml --namespace ag1
      ```
    
1. Créez un secret pour Kubernetes avec des mots de passe pour le compte `sa`, et la clé principale de l’instance SQL Server.

      Créez le secret avec `kubectl`.
      
      L’exemple suivant crée une clé secrète nommée `sql-secrets` dans l’espace de noms `ag1`. Le secret stocke deux mots de passe :
      
      - `sapassword` stocke le mot de passe du compte SQL Server `sa`.
      - `masterkeypassword` stocke le mot de passe utilisé pour créer la clé principale de SQL Server. 
    
   Copiez le script sur votre terminal. Remplacez chaque `<>` par un mot de passe complexe, puis exécutez le script pour créer le secret.
    
   >[!NOTE]
   >Le mot de passe ne peut pas utiliser des caractères `&` ou `` ` ``.
    
   ```azurecli
   kubectl create secret generic sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
   ```

1. Déployez la ressource personnalisée SQL Server.

      Copiez le manifeste [`sqlserver.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml) de SQL Server depuis [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).
    
      >[!NOTE]
      >Le fichier `sqlserver.yaml` décrit les conteneurs SQL Server, les revendications de volume persistant, les volumes persistants et les services d’équilibrage de charge requis pour chaque instance de SQL Server.
    
      Appliquez le manifeste au cluster Kubernetes.
    
      ```azurecli
      kubectl apply -f sqlserver.yaml --namespace ag1
      ```
      
L’illustration suivante montre l’application réussie de `kubectl apply` pour cet exemple.

![Créer des conteneurs SQL Server](./media/sql-server-linux-kubernetes-deploy/create-sqlservers.png)

Une fois que vous avez appliqué le manifeste SQL Server, l’opérateur déploie les conteneurs SQL Server.

Kubernetes place les conteneurs dans des pods. Utilisez `kubectl get pods --namespace ag1` pour afficher l’état des pods. L’illustration suivante montre l’exemple de déploiement après le déploiement des pods SQL Server. 

![Pods construits](./media/sql-server-linux-kubernetes-deploy/builtpods.png)

### <a name="monitor-the-deployment"></a>Surveiller le déploiement

Vous pouvez utiliser le [tableau de bord Kubernetes avec le service Azure Kubernetes](https://docs.microsoft.com/azure/aks/kubernetes-dashboard) pour surveiller le déploiement.

Utilisez `az aks browse` pour lancer le tableau de bord. 

## <a name="connect-to-the-availability-group-with-the-services"></a>Se connecter au groupe de disponibilité avec les services

L' exemple [`ag-services.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) de [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) décrit les services d’équilibrage de charge qui peuvent se connecter aux réplicas de groupe de disponibilité. 

- `ag1-primary` fournit un point de terminaison pour se connecter au réplica principal.
- `ag1-secondary` fournit un point de terminaison pour se connecter à n’importe quel réplica secondaire.

Lorsque vous appliquez le fichier manifeste, Kubernetes crée les services d’équilibrage de charge pour chaque type de réplica. Le service d’équilibrage de charge comprend une adresse IP. Utilisez cette adresse IP pour vous connecter au type de réplica dont vous avez besoin.

Pour déployer les services, exécutez la commande suivante.

```azurecli
kubectl apply -f ag-services.yaml --namespace ag1
```

Une fois les services déployés, utilisez `kubectl get services --namespace ag1` pour identifier l’adresse IP des services.

Avec l’adresse IP, vous pouvez vous connecter à l’instance SQL Server qui héberge chaque type de réplica.

L'image suivante montre :

- La sortie de `kubectl get services` pour l’espace de noms `ag1`.

- Les services d’équilibrage de charge créés pour chaque conteneur SQL Server. Utilisez ces adresses IP en tant que points de terminaison pour vous connecter directement aux instances SQL Server du cluster.

- La connexion `sqlcmd` au réplica principal, avec le compte `sa` via le point de terminaison de l’équilibreur de charge.

![Se connecter](./media/sql-server-linux-kubernetes-deploy/connect.png)

## <a name="add-a-database-to-the-availability-group"></a>Ajouter une base de données au groupe de disponibilité

>[!NOTE]
>À ce stade, SQL Server Management Studio ne peut pas ajouter une base de données à un groupe de disponibilité. Utilisez Transact-SQL.

Une fois que Kubernetes a créé les conteneurs SQL Server, procédez comme suit pour ajouter une base de données au groupe de disponibilité.

1. [Connectez-vous](sql-server-linux-kubernetes-connect.md) à une instance SQL Server dans le cluster.

1. Créer une base de données.

      ```sql
      CREATE DATABASE [demodb]
      ```

1. À partir d’une sauvegarde complète de la base de données, démarrez la séquence de journaux de transactions consécutifs.

      ```sql
      USE MASTER
      GO
      BACKUP DATABASE [demodb] 
      TO DISK = N'/var/opt/mssql/data/demodb.bak'
      ```

1. Ajoutez la base de données au groupe de disponibilité.

      ```sql
      ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [demodb]
      ```
    
Le groupe de disponibilité est créé avec l’amorçage automatique afin que SQL Server crée automatiquement les réplicas secondaires.

Vous pouvez afficher l’état du groupe de disponibilité à partir du tableau de bord Groupes de disponibilité de SQL Server Management Studio.

![tableau de bord](./media/sql-server-linux-kubernetes-deploy/dashboard.png)

## <a name="next-steps"></a>Étapes suivantes

- [Se connecter à un groupe de disponibilité SQL Server sur un cluster Kubernetes](sql-server-linux-kubernetes-connect.md)

- [Gérer un groupe de disponibilité SQL Server sur un cluster Kubernetes](sql-server-linux-kubernetes-manage.md)

- [SQL Server prend en charge les groupes de disponibilité sur les conteneurs dans un cluster Kubernetes](sql-server-ag-kubernetes.md)
