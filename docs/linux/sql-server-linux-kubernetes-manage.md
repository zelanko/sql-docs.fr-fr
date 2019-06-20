---
title: Gérer un groupe de disponibilité SQL Server Always On Kubernetes
description: Cet article explique comment gérer un SQL Server groupe de disponibilité AlwaysOn dans Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 808f49ff5060ba6a6ffe9e864cfc2710fe6251e6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705526"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>Gérer SQL Server Always On Kubernetes du groupe de disponibilité

Pour gérer un groupe de disponibilité AlwaysOn sur Kubernetes, créez un manifeste et appliquez-le au cluster. Le manifeste est un `.yaml` fichier.  

Les exemples de cet article s’appliquent à tous les clusters Kubernetes. Les scénarios dans ces exemples sont appliquées sur un cluster sur Azure Kubernetes Service.

Voir un exemple du déploiement complet dans [déployer un SQL Server groupe de disponibilité AlwaysOn sur un Kubernetes Cluster](sql-server-linux-kubernetes-deploy.md).

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>Basculer - groupe de disponibilité de SQL Server sur Kubernetes

Pour effectuer un basculement ou déplacer un réplica principal vers un autre nœud dans un groupe de disponibilité, procédez comme suit :

1. Définir un travail dans un fichier manifeste.

  [`failover.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/failover.yaml) -dans le [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) référentiel github décrit un travail de basculement.

  Copiez le fichier manifeste sur votre terminal de l’administration.

  Mettre à jour le fichier pour votre environnement.

  - Remplacez `<containerName>` avec le nom du pod (par exemple, mssql2-0) de la cible de groupe de disponibilité attendu.
  - Si le groupe de disponibilité n’est pas dans le `ag1` espace de noms, remplacez `ag1` avec l’espace de noms.

  Ce fichier définit un travail de basculement nommé `manual-failover`.

1. Pour déployer le travail, utilisez `kubectl apply`. Le script suivant déploie le travail.

  ```azurecli
  kubectl apply -f failover.yaml
  ```

  Une fois le travail est déployé, kubernetes, avec l’opérateur de serveur SQL, effectue les tâches suivantes :
  
  - Rétrograde le réplica principal pour la base de données secondaire
  
  - Promeut le réplica spécifié vers le site principal
  
  Après avoir appliqué le fichier manifeste, Kubernetes exécute la tâche. La tâche permet de sélectionner un nouveau responsable le superviseur et déplace le réplica principal à l’instance de SQL Server du responsable.

1. Vérifiez que le travail est terminé.
  
  Une fois que Kubernetes exécute la tâche, vous pouvez consulter le journal.
  
  L’exemple suivant retourne l’état de la tâche nommée `manual-failover`.

  ```azurecli
  kubectl describe jobs/manual-failover --namespace ag1
  ```

1. Supprimer le travail de basculement manuel. 

  >[!IMPORTANT]
  >Vous devez supprimer manuellement le travail avant d’émettre un autre basculement manuel.
  > 
  >L’objet de traitement dans Kubernetes reste après la saisie semi-automatique afin que vous puissiez afficher son état. Vous devez supprimer manuellement les anciens travaux après noter leur état. La suppression de la tâche supprime également les journaux de Kubernetes. Si vous ne supprimez pas le travail, les tâches de basculement futures échoue, sauf si vous modifiez le nom du travail et le sélecteur de pod. Pour plus d’informations, consultez [travaux - s’exécute jusqu'à achèvement](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/).

  La commande suivante supprime la tâche.

  ```azurecli
  kubectl delete jobs manual-failover --namespace ag1
  ```

## <a name="rotate-credentials"></a>Faire pivoter les informations d’identification

Faire pivoter les informations d’identification pour réinitialiser le mot de passe pour le serveur SQL Server `sa` compte et le serveur SQL [clé principale du service](../relational-databases/security/encryption/service-master-key.md). 

Pour effectuer cette tâche, vous créer des clés secrètes dans le cluster Kubernetes et puis créer une tâche pour faire pivoter les informations d’identification.

Avant la rotation des informations d’identification, rendre un nouveau secret pour le mot de passe et la clé principale.

Le script suivant crée une clé secrète nommée `new-sql-secrets`. Avant d’exécuter le script, remplacez `<>` avec des mots de passe complexes pour le `sapassword` et `masterkeypassword`. Utiliser des mots de passe différents pour chaque valeur correspondante.

```azurecli
kubectl create secret generic new-sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
```

Effectuez les étapes suivantes pour chaque instance de SQL Server qui a besoin de la clé principale ou `sa` mot de passe.

1. Copie [ `rotate-creds.yaml` ](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) sur votre terminal de l’administration.

  [`rotate-creds.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) dans le [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/) référentiel github est un exemple d’un manifeste pour ce travail.

  Avant d’appliquer ce manifeste, mettre à jour le manifeste pour votre environnement. Passez en revue et modifier les paramètres suivants, en fonction des besoins.

  - Vérifiez l’espace de noms. Mise à jour si nécessaire. L’exemple suivant dans un manifeste s’applique à un espace de noms nommé `ag1`.

    ```yaml
    metadata:
      name: rotate-creds
      namespace: ag1
    ```

  - Vérifiez le nom de l’instance de SQL Server. Mise à jour si nécessaire. L’exemple suivant dans une spécification de manifeste s’applique à une instance de SQL Server nommée `mssql1`.

    ```yaml
    env:
      - name: MSSQL_K8S_SQL_SERVER_NAME
        value: mssql1
    ```

  Enregistrez le fichier de manifeste mis à jour sur votre station de travail.

1. Utilisez `kubectl` pour déployer la tâche.

  ```azurecli
  kubectl apply -f rotate-creds.yaml --namespace ag1
  ```

  Kubernetes met à jour la clé principale et `sa` mot de passe pour une instance de SQL Server dans un groupe de disponibilité.

1. Vérifiez que la tâche est terminée. Exécutez la commande suivante : Pour vérifier que la tâche est terminée, exécutez 

  ```azcli
  kubectl describe job rotate-creds --namespace ag1
  ```

  Après la réussite du travail, la clé principale et `sa` mot de passe pour une instance de SQL Server sont mises à jour.


1. Avant d’exécuter à nouveau le travail, supprimez le travail. Chaque nom de la tâche doit être unique.

  ```azurecli
  kubectl delete job rotate-creds --namespace ag1
  ```

Pour définir les mêmes `sa` mot de passe pour toutes les instances de SQL Server, répétez les étapes ci-dessus pour chaque instance de SQL Server.

## <a name="next-steps"></a>Étapes suivantes

[Accès du tableau de bord Kubernetes avec Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[Groupe de disponibilité de SQL Server sur un cluster Kubernetes](sql-server-ag-kubernetes.md)
