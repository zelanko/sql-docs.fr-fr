---
title: Déployer SQL Server Always On de groupe de disponibilité sur un Cluster Kubernetes
description: Cet article présente les différents paramètres pour les SQL Server Kubernetes Always On groupe opérateur globales exigences de disponibilité
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fe736fa57ea85e92b69d12f44fca35f4097cd3d6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48160059"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-kubernetes-cluster"></a>Déployer un serveur SQL Server Always On de groupe de disponibilité sur un Cluster Kubernetes

## <a name="requirements"></a>Spécifications

- Un cluster Kubernetes
- Kubernetes version 1.11.0 ou une version ultérieure
- Quatre nœuds ou plus
- [kubectl](http://kubernetes.io/docs/tasks/tools/install-kubectl/).

  >[!NOTE]
  >Vous pouvez utiliser n’importe quel type de cluster Kubernetes. Pour créer un cluster Kubernetes sur Azure Kubernetes Service (AKS), consultez [créer un cluster AKS](http://docs.microsoft.com/azure/aks/create-cluster).
  > Le script suivant crée un cluster à quatre nœuds Kubernetes dans Azure.
  >```azure-cli
  az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version 1.11.1
  >```

## <a name="steps"></a>Étapes

1. Configuration du stockage

  Dans les environnements de cloud comme Azure, configurer [volumes persistants](http://kubernetes.io/docs/concepts/storage/persistent-volumes/) pour chaque instance de SQL Server.

  Pour créer des volumes persistants dans Azure, consultez `pv.yaml` et `pvc.yaml` dans [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/templates).

  Pour créer le stockage, exécutez la commande suivante :

  ```azurecli
  kubectl apply -f <pv.yaml>
  ```

1. Créer des clés secrètes Kubernetes pour le mot de passe SA et la clé principale.

  L’exemple suivant crée deux secrets. `sapassword` est le mot de passe SA et `masterkeypassword` est pour la clé principale. Avant d’exécuter ce script à remplacer `<MyC0mp13xP@55w04d!>` avec un autre mot de passe complexe pour chaque clé secrète.

   ```azurecli
   kubectl create secret generic sql-secrets --from-literal='sapassword=<MyC0mp13xP@55w04d!>' --from-literal='masterkeypassword=<MyC0mp13xP@55w04d!>'
   ```

1. Configurez et déployez le manifeste d’opérateur de SQL Server.

  Copier l’opérateur de SQL Server `operator.yaml` à partir de fichiers [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

  Le `operator.yaml` fichier est le manifiest de déploiement pour l’opérateur de Kubernetes.

  Pour configurer le manifeste, mettre à jour le `operator.yaml` fichier pour votre environnement.

  Appliquer le manifeste au cluster Kubernetes.

  ```azurecli
  kubectl apply -f operator.yaml
  ```

1. Déployer la ressource personnalisée de SQL Server.

  Copiez le manifeste de SQL Server `sqlserver.yaml` de [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

  Appliquer le manifeste au cluster Kubernetes.

  ```azurecli
  kubectl apply -f sqlserver.yaml
  ```

Après avoir déployé le manifeste de SQL Server, l’opérateur déploie les instances de SQL Server en tant que nombre de pods dans des conteneurs.

Une fois le script terminé, l’opérateur Kubernetes créera le stockage, les instances de SQL Server, les services d’équilibrage de charge. Vous pouvez surveiller le déploiement avec [tableau de bord Kubernetes](http://docs.microsoft.com/azure/aks/kubernetes-dashboard).

Une fois que Kubernetes crée les conteneurs SQL Server procédez comme suit pour ajouter une base de données au groupe de disponibilité :

1. [Se connecter](sql-server-linux-kubernetes-connect.md) à une instance de SQL Server dans le cluster.

1. Créer une base de données.

1. Effectuez une sauvegarde complète de la base de données pour démarrer la séquence de journaux.

1. Ajouter la base de données au groupe de disponibilité.

Le groupe de disponibilité est créé avec l’amorçage automatique pour SQL Server crée automatiquement les réplicas secondaires.

## <a name="next-steps"></a>Étapes suivantes

[Se connecter à un groupe de disponibilité de SQL Server sur un cluster Kubernetes](sql-server-linux-kubernetes-connect.md)

[Gérer le groupe de disponibilité de SQL Server sur un cluster Kubernetes](sql-server-linux-kubernetes-manage.md)

[Groupe de disponibilité de SQL Server sur un cluster Kubernetes](sql-server-ag-kubernetes.md)
