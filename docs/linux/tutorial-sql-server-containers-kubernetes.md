---
title: Déployer un conteneur de SQL Server dans Kubernetes avec Azure Kubernetes Services (AKS)
description: Ce didacticiel montre comment déployer une solution de haute disponibilité de SQL Server avec Kubernetes sur Azure Kubernetes Service.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 01/10/2018
ms.topic: tutorial
ms.prod: sql
ms.custom: mvc
ms.technology: linux
ms.openlocfilehash: 2ae299553c700de7f22976917fa8556f93dbe61b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032054"
---
# <a name="deploy-a-sql-server-container-in-kubernetes-with-azure-kubernetes-services-aks"></a>Déployer un conteneur de SQL Server dans Kubernetes avec Azure Kubernetes Services (AKS)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Découvrez comment configurer une instance de SQL Server sur Kubernetes dans Azure Kubernetes Service (ACS), avec le stockage persistant pour la haute disponibilité (HA). La solution fournit la résilience. Si l’instance de SQL Server échoue, Kubernetes automatiquement recrée dans un nouveau module. Kubernetes fournit également la résilience contre une défaillance de nœud.

Ce didacticiel montre comment configurer une instance de SQL Server hautement disponible dans un conteneur sur AKS. Vous pouvez également créer [groupes de disponibilité Always On pour les conteneurs de SQL Server](sql-server-ag-kubernetes.md). Pour comparer les deux différentes solutions de Kubernetes, consultez [haute disponibilité pour les conteneurs de SQL Server](sql-server-linux-container-ha-overview.md).

> [!div class="checklist"]
> * Créer un mot de passe
> * Créer le stockage
> * Créer le déploiement
> * Se connecter avec SQL Server Management Studio (SSMS)
> * Vérifiez que la défaillance et récupération

## <a name="ha-solution-on-kubernetes-running-in-azure-kubernetes-service"></a>Solution de haute disponibilité sur Kubernetes s’exécutant dans Azure Kubernetes Service

Kubernetes 1.6 et versions ultérieures prend en charge [classes de stockage](https://kubernetes.io/docs/concepts/storage/storage-classes/), [les revendications de volume persistant](https://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims)et le [type de volume de disque Azure](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). Vous pouvez créer et gérer vos instances de SQL Server en mode natif dans Kubernetes. L’exemple dans cet article montre comment créer un [déploiement](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) pour obtenir une configuration de haute disponibilité similaire à une instance de cluster de basculement de disque partagé. Dans cette configuration, Kubernetes joue le rôle de l’orchestrateur de cluster. En cas d’échec d’une instance de SQL Server dans un conteneur, l’orchestrateur démarre une autre instance du conteneur qui s’attache à un même stockage persistant.

![Diagramme du cluster Kubernetes SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

Dans le diagramme précédent, `mssql-server` est un conteneur dans un [pod](https://kubernetes.io/docs/concepts/workloads/pods/pod/). Kubernetes orchestre les ressources du cluster. Un [jeu de réplicas](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) garantit que le pod est automatiquement récupéré après une défaillance de nœud. Applications se connectent au service. Dans ce cas, le service représente un équilibreur de charge qui héberge une adresse IP qui reste la même après l’échec de la `mssql-server`.

Dans le diagramme suivant, le `mssql-server` conteneur a échoué. Comme l’orchestrateur, Kubernetes garantit le nombre correct d’instances saines dans le réplica défini et crée un conteneur en fonction de la configuration. L’orchestrateur démarre un nouveau module sur le même nœud, et `mssql-server` se reconnecte à un même stockage persistant. Le service se connecte à la re-création `mssql-server`.

![Diagramme du cluster Kubernetes SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-pod-fail.png)

Dans le diagramme suivant, le nœud qui héberge le `mssql-server` conteneur a échoué. L’orchestrateur démarre le pod de nouveau sur un autre nœud, et `mssql-server` se reconnecte à un même stockage persistant. Le service se connecte à la re-création `mssql-server`.

![Diagramme du cluster Kubernetes SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-node-fail.png)

## <a name="prerequisites"></a>Prérequis

* **Cluster Kubernetes**
   - Ce didacticiel nécessite un cluster Kubernetes. Utilisent les étapes [kubectl](https://kubernetes.io/docs/user-guide/kubectl/) pour gérer le cluster. 

   - Consultez [déployer un cluster Azure Container Service (AKS)](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-deploy-cluster) pour créer et de se connecter à un cluster Kubernetes à nœud unique dans ACS avec `kubectl`. 

   >[!NOTE]
   >Pour vous protéger contre les défaillances de nœud, un cluster Kubernetes nécessite plusieurs nœuds.

* **Azure CLI 2.0.23**
   - Les instructions fournies dans ce didacticiel ont été validées par rapport à Azure CLI 2.0.23.

## <a name="create-an-sa-password"></a>Créer un mot de passe

Créer un mot de passe dans le cluster Kubernetes. Kubernetes peuvent gérer les informations de configuration sensibles, telles que les mots de passe en tant que [secrets](https://kubernetes.io/docs/concepts/configuration/secret/).

La commande suivante crée un mot de passe pour le compte SA :

   ```azurecli
   kubectl create secret generic mssql --from-literal=SA_PASSWORD="MyC0m9l&xP@ssw0rd"
   ```  

   Remplacez `MyC0m9l&xP@ssw0rd` avec un mot de passe complexe.

   Pour créer un secret dans Kubernetes nommé `mssql` qui contient la valeur `MyC0m9l&xP@ssw0rd` pour le `SA_PASSWORD`, exécutez la commande.


## <a name="create-storage"></a>Créer le stockage

Configurer un [volume persistant](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) et [revendication de volume persistant](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistent-volume-claim-protection) dans le cluster Kubernetes. Effectuez ensuite les tâches suivantes : 

1. Créer un manifeste pour définir la classe de stockage et du volume persistant revendication.  Le manifeste spécifie le fournisseur de stockage, paramètres, et [récupérer de la stratégie](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaiming). Le cluster Kubernetes utilise ce manifeste pour créer le stockage persistant. 

   L’exemple d’yaml suivant définit une classe de stockage et de la revendication de volume persistant. Le fournisseur de classe de stockage est `azure-disk`, car ce cluster Kubernetes dans Azure. Le type de compte de stockage est `Standard_LRS`. La revendication de volume persistant est nommée `mssql-data`. Les métadonnées de revendication de volume persistant incluent une annotation connexion refaites-le à la classe de stockage. 

   ```yaml
   kind: StorageClass
   apiVersion: storage.k8s.io/v1beta1
   metadata:
        name: azure-disk
   provisioner: kubernetes.io/azure-disk
   parameters:
     storageaccounttype: Standard_LRS
     kind: Managed
   ---
   kind: PersistentVolumeClaim
   apiVersion: v1
   metadata:
     name: mssql-data
     annotations:
       volume.beta.kubernetes.io/storage-class: azure-disk
   spec:
     accessModes:
     - ReadWriteOnce
     resources:
       requests:
         storage: 8Gi
   ```

   Enregistrez le fichier (par exemple, **pvc.yaml**).

1. Créer la revendication de volume persistant dans Kubernetes.

   ```azurecli
   kubectl apply -f <Path to pvc.yaml file>
   ```

   `<Path to pvc.yaml file>` est l’emplacement où vous avez enregistré le fichier.

   Le volume persistant est automatiquement créé en tant que compte de stockage Azure et lié à la revendication de volume persistant. 

    ![Capture d’écran de la commande de revendication de volume persistant](media/tutorial-sql-server-containers-kubernetes/02_pvc_cmd.png)

1. Vérifiez que la revendication de volume persistant.

   ```azurecli
   kubectl describe pvc <PersistentVolumeClaim>
   ```

   `<PersistentVolumeClaim>` est le nom de la revendication de volume persistant.

   Dans l’étape précédente, la revendication de volume persistant est nommée `mssql-data`. Pour afficher les métadonnées relatives à la revendication de volume persistant, exécutez la commande suivante :

   ```azurecli
   kubectl describe pvc mssql-data
   ```

   Les métadonnées retournées incluent une valeur appelée `Volume`. Cette valeur correspond au nom de l’objet blob.

   ![Capture d’écran de métadonnées retournées, notamment le Volume](media/tutorial-sql-server-containers-kubernetes/describe-volume.png)

   La valeur de volume correspond à la partie du nom de l’objet blob dans l’image suivante à partir du portail Azure : 

   ![Nom d’objet blob de portail de capture d’écran d’Azure](media/tutorial-sql-server-containers-kubernetes/describe-volume-portal.png)

1. Vérifiez que le volume persistant.

   ```azurecli
   kubectl describe pv
   ```

   `kubectl` Retourne les métadonnées du volume persistant qui a été automatiquement créé et lié à la revendication de volume persistant. 

## <a name="create-the-deployment"></a>Créer le déploiement

Dans cet exemple, le conteneur qui héberge l’instance de SQL Server est décrite comme un objet de déploiement Kubernetes. Le déploiement crée un jeu de réplicas. Le jeu de réplicas crée le pod. 

Dans cette étape, créez un manifeste pour décrire le conteneur basé sur le serveur SQL [mssql-server-linux](https://hub.docker.com/_/microsoft-mssql-server) image Docker. Le manifeste fait référence à la `mssql-server` revendication de volume persistant et le `mssql` secret que vous avez déjà appliqué au cluster Kubernetes. Le manifeste décrit également un [service](https://kubernetes.io/docs/concepts/services-networking/service/). Ce service est un équilibreur de charge. L’équilibreur de charge garantit que l’adresse IP persiste une fois que l’instance de SQL Server est récupérée. 

1. Créez un manifeste (fichier YAML) pour décrire le déploiement. L’exemple suivant décrit un déploiement, y compris un conteneur basé sur l’image de conteneur de SQL Server.

   ```yaml
   apiVersion: apps/v1beta1
   kind: Deployment
   metadata:
     name: mssql-deployment
   spec:
     replicas: 1
     template:
       metadata:
         labels:
           app: mssql
       spec:
         terminationGracePeriodSeconds: 10
         containers:
         - name: mssql
           image: mcr.microsoft.com/mssql/server:2017-latest
           ports:
           - containerPort: 1433
           env:
           - name: MSSQL_PID
             value: "Developer"
           - name: ACCEPT_EULA
             value: "Y"
           - name: MSSQL_SA_PASSWORD
             valueFrom:
               secretKeyRef:
                 name: mssql
                 key: SA_PASSWORD 
           volumeMounts:
           - name: mssqldb
             mountPath: /var/opt/mssql
         volumes:
         - name: mssqldb
           persistentVolumeClaim:
             claimName: mssql-data
   ---
   apiVersion: v1
   kind: Service
   metadata:
     name: mssql-deployment
   spec:
     selector:
       app: mssql
     ports:
       - protocol: TCP
         port: 1433
         targetPort: 1433
     type: LoadBalancer
   ```

   Copiez le code précédent dans un nouveau fichier nommé `sqldeployment.yaml`. Mettre à jour les valeurs suivantes : 

   * MSSQL_PID `value: "Developer"`: Définit le conteneur pour exécuter SQL Server Developer edition. Édition développeur n’est pas autorisée pour les données de production. Si le déploiement est pour la production, définissez l’édition appropriée (`Enterprise`, `Standard`, ou `Express`). 

      >[!NOTE]
      >Pour plus d’informations, consultez [comment obtenir la licence SQL Server](https://www.microsoft.com/sql-server/sql-server-2017-pricing).

   * `persistentVolumeClaim`: Cette valeur nécessite une entrée pour `claimName:` qui mappe au nom utilisé pour la revendication de volume persistant. Ce didacticiel utilise`mssql-data`. 

   * `name: SA_PASSWORD`: Configure l’image de conteneur pour définir le mot de passe SA, tel que défini dans cette section.

     ```yaml
     valueFrom:
       secretKeyRef:
         name: mssql
         key: SA_PASSWORD 
     ```

     Lorsque Kubernetes déploie le conteneur, il fait référence à la clé secrète nommée `mssql` pour obtenir la valeur pour le mot de passe. 

   >[!NOTE]
   >À l’aide de la `LoadBalancer` type de service, l’instance de SQL Server est accessible à distance (via internet) sur le port 1433.

   Enregistrez le fichier (par exemple, **sqldeployment.yaml**).

1. Créer le déploiement.

   ```azurecli
   kubectl apply -f <Path to sqldeployment.yaml file>
   ```

   `<Path to sqldeployment.yaml file>` est l’emplacement où vous avez enregistré le fichier.

   ![Capture d’écran de la commande de déploiement](media/tutorial-sql-server-containers-kubernetes/04_deploy_cmd.png)

   Le déploiement et le service sont créés. L’instance de SQL Server est dans un conteneur, connecté à un stockage persistant.

   Pour afficher l’état du pod, tapez `kubectl get pod`.

   ![Capture d’écran de la commande get pod](media/tutorial-sql-server-containers-kubernetes/05_get_pod_cmd.png)

   Dans l’image précédente, le pod a le statut `Running`. Cet état indique que le conteneur est prêt. Cette opération peut prendre plusieurs minutes.

   >[!NOTE]
   >Une fois le déploiement est créé, il peut prendre quelques minutes avant que le pod est visible. Le délai est parce que le cluster extrait la [mssql-server-linux](https://hub.docker.com/_/microsoft-mssql-server) image à partir du hub Docker. Une fois que l’image est extraite de la première fois, les déploiements suivants peuvent être plus rapides si le déploiement vers un nœud qui possède déjà l’image mis en cache sur ce dernier. 

1. Vérifiez que les services sont en cours d’exécution. Exécutez la commande suivante :

   ```azurecli
   kubectl get services 
   ```

   Cette commande renvoie les services qui sont en cours d’exécution, ainsi que les adresses IP internes et externes pour les services. Notez l’adresse IP externe pour le `mssql-deployment` service. Utilisez cette adresse IP pour se connecter à SQL Server. 

   ![Capture d’écran de la commande de service get](media/tutorial-sql-server-containers-kubernetes/06_get_service_cmd.png)

   Pour plus d’informations sur l’état des objets dans le cluster Kubernetes, exécutez :

   ```azurecli
   az aks browse --resource-group <MyResourceGroup> --name <MyKubernetesClustername>
   ```  

## <a name="connect-to-the-sql-server-instance"></a>Connectez-vous à l’instance de SQL Server

Si vous avez configuré le conteneur comme décrit, vous pouvez vous connecter à une application à partir de l’extérieur du réseau virtuel Azure. Utilisez le `sa` compte et l’adresse IP externe d’adresses pour le service. Utilisez le mot de passe que vous avez configuré en tant que le secret Kubernetes. 

Vous pouvez utiliser les applications suivantes pour vous connecter à l’instance de SQL Server. 

* [SSMS](https://docs.microsoft.com/sql/linux/sql-server-linux-manage-ssms)

* [SSDT](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-ssdt)

* sqlcmd
   
   Pour vous connecter avec `sqlcmd`, exécutez la commande suivante :

   ```cmd
   sqlcmd -S <External IP Address> -U sa -P "MyC0m9l&xP@ssw0rd"
   ```

   Remplacez les valeurs suivantes :
      
    - `<External IP Address>` avec l’adresse IP pour le `mssql-deployment` service 
    - `MyC0m9l&xP@ssw0rd` avec votre mot de passe

## <a name="verify-failure-and-recovery"></a>Vérifiez que la défaillance et récupération

Pour vérifier la défaillance et récupération, vous pouvez supprimer le pod. Procédez comme suit :

1. Répertorier le pod exécutant SQL Server.

   ```azurecli
   kubectl get pods
   ```

   Notez le nom du pod en cours d’exécution SQL Server.

1. Supprimer le pod.

   ```azurecli
   kubectl delete pod mssql-deployment-0
   ```
   `mssql-deployment-0` la valeur est retournée à partir de l’étape précédente pour le nom du pod. 

Kubernetes recrée automatiquement le pod pour récupérer une instance de SQL Server et vous connecter au stockage persistant. Utilisez `kubectl get pods` pour vérifier qu’un nouveau module est déployé. Utilisez `kubectl get services` pour vérifier que l’adresse IP pour le nouveau conteneur est le même. 

## <a name="summary"></a>Récapitulatif

Dans ce didacticiel, vous avez appris à déployer des conteneurs de SQL Server sur un cluster Kubernetes pour la haute disponibilité. 

> [!div class="checklist"]
> * Créer un mot de passe
> * Créer le stockage
> * Créer le déploiement
> * Se connecter avec SQL Server Management Studio (SSMS)
> * Vérifiez que la défaillance et récupération

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
>[Présentation de Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes)


