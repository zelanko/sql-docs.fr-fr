---
title: Déployer un groupe de disponibilité SQL Server Always On sur un cluster Kubernetes
description: Cet article présente les différents paramètres pour les SQL Server Kubernetes Always On groupe opérateur globales exigences de disponibilité
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 10/02/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 117faab160c512f4732b0709b0b2e1024a196893
ms.sourcegitcommit: ef15fa253d98c62538bf9b6fe191af7f8ef8f6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49991182"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-a-kubernetes-cluster"></a>Déployer un groupe de disponibilité SQL Server Always On sur un cluster Kubernetes

L’exemple dans cet article déploie un groupe de disponibilité SQL Server Always On sur un cluster Kubernetes avec trois réplicas. Les réplicas secondaires sont en mode de validation synchrone.

Sur Kubernetes, le déploiement inclut un opérateur de SQL Server, les conteneurs de SQL Server et charge les services d’équilibrage. L’opérateur orchestre automatiquement le groupe de disponibilité. Cet article explique comment :

- Déployer l’opérateur, les conteneurs de SQL Server et les services d’équilibrage de charge.
- Se connecter au groupe de disponibilité avec les services.
- Ajouter une base de données au groupe de disponibilité.

## <a name="requirements"></a>Spécifications

- Un cluster Kubernetes
- Kubernetes version 1.11.0 ou une version ultérieure
- Au moins trois nœuds
- [kubectl](http://kubernetes.io/docs/tasks/tools/install-kubectl/)
- L’accès à la [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) référentiel GitHub

>[!NOTE]
>Vous pouvez utiliser n’importe quel type de cluster Kubernetes. Pour créer un cluster Kubernetes sur Azure Kubernetes Service (AKS), consultez [créer un cluster AKS](http://docs.microsoft.com/azure/aks/create-cluster).
> Le script suivant crée un cluster à quatre nœuds Kubernetes dans Azure.
>```azure-cli
az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version 1.11.3 --generate-ssh-keys
>```

## <a name="deploy-the-operator-sql-server-containers-and-load-balancing-services"></a>Déployer l’opérateur, les conteneurs de SQL Server et les services d’équilibrage de charge

1. Créer un [espace de noms](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/).

      Cet exemple utilise un espace de noms appelé `ag1`. Exécutez la commande suivante pour créer l’espace de noms.
    
      ```azurecli
      kubectl create namespace ag1
      ```
    
      Tous les objets appartenant à cette solution sont dans le `ag1` espace de noms.

1. Configurez et déployez le manifeste d’opérateur de SQL Server.

      Copiez le serveur SQL Server [ `operator.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml) à partir de fichiers [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).
    
      Le `operator.yaml` fichier est le manifeste de déploiement pour l’opérateur de Kubernetes.
    
      Appliquer le manifeste au cluster Kubernetes.
    
      ```azurecli
      kubectl apply -f operator.yaml --namespace ag1
      ```
    
1. Créer une clé secrète pour Kubernetes avec des mots de passe pour le `sa` compte et la clé principale d’instance SQL Server.

      Créer la clé secrète avec `kubectl`.
      
      L’exemple suivant crée une clé secrète nommée `sql-secrets` dans le `ag1` espace de noms. La clé secrète stocke deux mots de passe :
      
      - `sapassword` stocke le mot de passe pour le serveur SQL `sa` compte.
      - `masterkeypassword` stocke le mot de passe utilisé pour créer la clé principale de SQL Server. 
    
   Copiez le script vers votre terminal. Remplacez chaque `<>` avec un mot de passe complexe, puis exécutez le script pour créer le secret.
    
   >[!NOTE]
   >Le mot de passe ne peut pas utiliser `&` ou `` ` `` caractères.
    
   ```azurecli
   kubectl create secret generic sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
   ```

1. Déployer la ressource personnalisée de SQL Server.

      Copiez le manifeste de SQL Server [ `sqlserver.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml) de [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).
    
      >[!NOTE]
      >Le `sqlserver.yaml` fichier décrit le SQL Server pour les conteneurs, les revendications de volume persistant, volumes persistants et services d’équilibrage de charge qui sont requises pour chaque instance de SQL Server.
    
      Appliquer le manifeste au cluster Kubernetes.
    
      ```azurecli
      kubectl apply -f sqlserver.yaml --namespace ag1
      ```
      
L’illustration suivante montre une application réussie de `kubectl apply` pour cet exemple.

![créer sqlservers](./media/sql-server-linux-kubernetes-deploy/create-sqlservers.png)

Après avoir appliqué le manifeste de SQL Server, l’opérateur déploie les conteneurs de SQL Server.

Kubernetes place les conteneurs dans pods. Utilisez `kubectl get pods --namespace ag1` pour connaître l’état des blocs. L’illustration suivante montre l’exemple de déploiement une fois que les blocs de SQL Server sont déployés. 

![construit des pods](./media/sql-server-linux-kubernetes-deploy/builtpods.png)

### <a name="monitor-the-deployment"></a>Surveiller le déploiement

Vous pouvez utiliser la [tableau de bord Kubernetes avec Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/kubernetes-dashboard) pour surveiller le déploiement.

Utilisez `az aks browse` pour lancer le tableau de bord. 

## <a name="connect-to-the-availability-group-with-the-services"></a>Se connecter au groupe de disponibilité avec les services

Le [ `ag-services.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) de [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) exemple décrit les services d’équilibrage de charge qui peuvent se connecter aux réplicas de groupe de disponibilité. 

- `ag1-primary` fournit un point de terminaison pour se connecter au réplica principal.
- `ag1-secondary` fournit un point de terminaison pour se connecter à n’importe quel réplica secondaire.

Lorsque vous appliquez le fichier manifeste, Kubernetes crée les services d’équilibrage de charge pour chaque type de réplica. Le service d’équilibrage de charge inclut une adresse IP. Utilisez cette adresse IP pour se connecter au type de réplica que vous avez besoin.

Pour déployer les services, exécutez la commande suivante.

```azurecli
kubectl apply -f ag-services.yaml --namespace ag1
```

Après avoir déployé les services, utilisez `kubectl get services --namespace ag1` pour identifier l’adresse IP pour les services.

Avec l’adresse IP, vous pouvez vous connecter à l’instance de SQL Server qui héberge chaque type de réplica.

L’illustration suivante montre :

- La sortie de `kubectl get services` pour l’espace de noms `ag1`.

- Les services de l’équilibrage de charge qui sont créés pour chaque conteneur de SQL Server. Utilisez ces adresses IP en tant que points de terminaison pour se connecter directement aux instances de SQL Server dans le cluster.

- Le `sqlcmd` connexion au réplica principal, avec le `sa` compte via le point de terminaison d’équilibrage de charge.

![Connection](./media/sql-server-linux-kubernetes-deploy/connect.png)

## <a name="add-a-database-to-the-availability-group"></a>Ajouter une base de données au groupe de disponibilité

>[!NOTE]
>À ce stade, SQL Server Management Studio ne peut pas ajouter une base de données à un groupe de disponibilité. Utiliser Transact-SQL.

Une fois que Kubernetes crée les conteneurs de SQL Server, procédez comme suit pour ajouter une base de données au groupe de disponibilité.

1. [Se connecter](sql-server-linux-kubernetes-connect.md) à une instance de SQL Server dans le cluster.

1. Créer une base de données.

      ```sql
      CREATE DATABASE [demodb]
      ```

1. Effectuez une sauvegarde complète de la base de données pour démarrer la séquence de journaux.

      ```sql
      USE MASTER
      GO
      BACKUP DATABASE [demodb] 
      TO DISK = N'/var/opt/mssql/data/demodb.bak'
      ```

1. Ajouter la base de données au groupe de disponibilité.

      ```sql
      ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [demodb]
      ```
    
Le groupe de disponibilité est créé avec l’amorçage automatique afin que SQL Server crée automatiquement les réplicas secondaires.

Vous pouvez afficher l’état du groupe de disponibilité à partir du tableau de bord de groupes de disponibilité de SQL Server Management Studio.

![tableau de bord](./media/sql-server-linux-kubernetes-deploy/dashboard.png)

## <a name="next-steps"></a>Étapes suivantes

- [Se connecter à un groupe de disponibilité de SQL Server sur un cluster Kubernetes](sql-server-linux-kubernetes-connect.md)

- [Gérer un groupe de disponibilité de SQL Server sur un cluster Kubernetes](sql-server-linux-kubernetes-manage.md)

- [SQL Server prend en charge les groupes de disponibilité sur des conteneurs dans un cluster Kubernetes](sql-server-ag-kubernetes.md)
