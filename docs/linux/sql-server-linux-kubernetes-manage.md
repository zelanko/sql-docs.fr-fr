---
title: Gérer un groupe de disponibilité SQL Server Always On Kubernetes
description: Cet article explique comment gérer un groupe de disponibilité SQL Server Always On dans Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 893e502c35ae33ce6ff87efd88049db97a40f875
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67952544"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>Gérer un groupe de disponibilité SQL Server Always On Kubernetes

Pour gérer un groupe de disponibilité Always On sur Kubernetes, créez un manifeste et appliquez-le au cluster. Le manifeste est un fichier `.yaml`.  

Les exemples de cet article s’appliquent à tous les clusters Kubernetes. Les scénarios de ces exemples sont appliqués à un cluster sur Azure Kubernetes Service.

Consultez l’exemple de déploiement complet dans [Déployer un groupe de disponibilité Always On SQL Server sur le cluster Kubernetes](sql-server-linux-kubernetes-deploy.md).

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>Basculement - Groupe de disponibilité SQL Server sur Kubernetes

Pour basculer un réplica principal ou le déplacer vers un autre nœud dans un groupe de disponibilité, procédez comme suit :

1. Définissez un travail dans un fichier manifeste.

  [`failover.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/failover.yaml) dans le référentiel GitHub [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) décrit un travail de basculement.

  Copiez le fichier manifeste sur votre terminal d’administration.

  Mettez à jour le fichier en fonction de votre environnement.

  - Remplacez `<containerName>` par le nom du pod (par exemple mssql2-0) de la cible de groupe de disponibilité attendue.
  - Si le groupe de disponibilité n’est pas dans l'espace de noms `ag1`, remplacez `ag1` par l’espace de noms.

  Ce fichier définit une tâche de basculement nommée `manual-failover`.

1. Pour déployer le travail, utilisez `kubectl apply`. Le script suivant déploie le travail.

  ```azurecli
  kubectl apply -f failover.yaml
  ```

  Une fois le travail déployé, Kubernetes, avec l’opérateur SQL Server, effectue les tâches suivantes :
  
  - Rétrograde le réplica principal en réplica secondaire
  
  - Promeut le réplica spécifié en principal
  
  Une fois que vous avez appliqué le fichier manifeste, Kubernetes exécute le travail. Le travail permet au superviseur de sélectionner un nouveau responsable et de déplacer le réplica principal vers l’instance SQL Server du responsable.

1. Vérifiez que le travail est terminé.
  
  Une fois que Kubernetes a exécuté le travail, vous pouvez consulter le journal.
  
  L’exemple suivant retourne l’état du travail nommé `manual-failover`.

  ```azurecli
  kubectl describe jobs/manual-failover --namespace ag1
  ```

1. Supprimez le travail de basculement manuel. 

  >[!IMPORTANT]
  >Vous devez supprimer la tâche manuellement avant d’émettre un autre basculement manuel.
  > 
  >L’objet de travail dans Kubernetes reste après l’achèvement. Vous pouvez ainsi afficher son état. Vous devez supprimer manuellement les anciens travaux après avoir noté leur état. La suppression du travail entraîne également la suppression des journaux Kubernetes. Si vous ne supprimez pas le travail, les tâches de basculement futures échoueront, sauf si vous modifiez le nom du travail et le sélecteur pod. Pour plus d’informations, consultez [Travaux - Exécuter jusqu'à la fin](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/).

  La commande suivante supprime le travail.

  ```azurecli
  kubectl delete jobs manual-failover --namespace ag1
  ```

## <a name="rotate-credentials"></a>Faire pivoter les informations d'identification

Faites pivoter les informations d’identification pour réinitialiser le mot de passe du compte SQL Server `sa` et la [clé principale du service](../relational-databases/security/encryption/service-master-key.md) SQL Server. 

Pour effectuer cette tâche, vous allez créer des secrets dans le cluster Kubernetes, puis créer un travail pour faire pivoter les informations d’identification.

Avant de faire pivoter les informations d’identification, créez un nouveau secret pour le mot de passe et la clé principale.

Le script suivant crée une clé secrète nommée `new-sql-secrets`. Avant d’exécuter le script, remplacez `<>` par des mots de passe complexes pour `sapassword` et `masterkeypassword`. Utilisez des mots de passe différents pour chaque valeur respective.

```azurecli
kubectl create secret generic new-sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
```

Effectuez les étapes suivantes pour chaque instance de SQL Server qui a besoin de la clé principale ou du mot de passe `sa`.

1. Copiez [`rotate-creds.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) sur votre terminal d’administration.

  [`rotate-creds.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) dans le référentiel GitHub [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/) est un exemple de manifeste pour ce travail.

  Avant d’appliquer ce manifeste, mettez à jour le manifeste pour votre environnement. Passez en revue et modifiez les paramètres suivants, si nécessaire.

  - Vérifiez l’espace de noms. Mettez-le à jour si nécessaire. L’exemple suivant dans un manifeste s’applique à un espace de noms nommé `ag1`.

    ```yaml
    metadata:
      name: rotate-creds
      namespace: ag1
    ```

  - Vérifiez le nom de l’instance SQL Server cible. Mettez-le à jour si nécessaire. L’exemple suivant dans une spécification de manifeste s’applique à une instance SQL Server nommée `mssql1`.

    ```yaml
    env:
      - name: MSSQL_K8S_SQL_SERVER_NAME
        value: mssql1
    ```

  Enregistrez le fichier manifeste mis à jour sur votre station de travail.

1. Utilisez `kubectl` pour déployer le travail.

  ```azurecli
  kubectl apply -f rotate-creds.yaml --namespace ag1
  ```

  Kubernetes met à jour la clé principale et le mot de passe `sa` pour une instance de SQL Server dans un groupe de disponibilité.

1. Vérifiez que le travail est terminé. Exécutez la commande suivante : Pour vérifier que le travail est terminé, exécutez 

  ```azcli
  kubectl describe job rotate-creds --namespace ag1
  ```

  Une fois le travail effectué, la clé principale et le mot de passe `sa` d’une instance de SQL Server sont mis à jour.


1. Avant de réexécuter le travail, supprimez le travail. Chaque nom de tâche doit être unique.

  ```azurecli
  kubectl delete job rotate-creds --namespace ag1
  ```

Pour définir le même mot de passe `sa` pour toutes les instances de SQL Server, répétez les étapes ci-dessus pour chaque instance de SQL Server.

## <a name="next-steps"></a>Étapes suivantes

[Accéder au tableau de bord Kubernetes avec Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[Groupe de disponibilité SQL Server sur le cluster Kubernetes](sql-server-ag-kubernetes.md)
