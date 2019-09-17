---
title: Déployer SQL Server Cluster Big Data avec une haute disponibilité
titleSuffix: Deploy SQL Server Big Data Cluster with high availability
description: Découvrez comment déployer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (version préliminaire) dans avec une haute disponibilité.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 307697f43fc1c2615f212ae5f433485814dd62d0
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874706"
---
# <a name="deploy-sql-server-big-data-cluster-with-high-availability"></a>Déployer SQL Server Cluster Big Data avec une haute disponibilité

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Au moment du déploiement d’un cluster Big Data (BDC), vous pouvez configurer SQL Server maître à déployer dans une configuration de groupe de disponibilité. Cette configuration augmente la fiabilité de SQL Server Master, en plus de ce que l’infrastructure de Kubernetes active avec ses mécanismes intégrés de surveillance de l’intégrité, de détection des défaillances et de basculement. Les groupes de disponibilité ajoutent de la redondance à l’instance SQL Server. Dans cette configuration, les tâches de surveillance, de détection des défaillances et de basculement sont gérées par Big Data Service de gestion de cluster, à savoir le service de contrôle.

En outre, d’autres tâches d’administration telles que la configuration des points de terminaison de mise en miroir de bases de données, la création du groupe de disponibilité et l’ajout de bases de données au groupe de disponibilité sont assurées par la plateforme de cluster Big Data.

Voici quelques-unes des fonctionnalités que les groupes de disponibilité activent :

1. Si les paramètres de haute disponibilité sont spécifiés dans le fichier de configuration de déploiement, un `containedag` seul groupe de disponibilité nommé est créé. Par défaut, `containedag` a trois réplicas, y compris le réplica principal. Toutes les opérations CRUD pour le groupe de disponibilité sont gérées en interne.
1. Toutes les bases de données sont automatiquement ajoutées au groupe de disponibilité `master` , `msdb`y compris et. Les bases de données de configuration Polybase ne sont pas incluses dans le groupe de disponibilité, car elles incluent des métadonnées au niveau de l’instance spécifiques à chaque réplica.
1. Un point de terminaison externe est automatiquement approvisionné pour la connexion aux bases de données GA. Ce point `master-svc-external` de terminaison joue le rôle de l’écouteur GA.
1. Un deuxième point de terminaison externe est configuré pour les connexions en lecture seule aux réplicas secondaires. 


# <a name="deploy"></a>Déployer

Pour déployer SQL Server maître dans un groupe de disponibilité :

1. Activer la `hadr` fonctionnalité
1. Spécifiez le nombre de réplicas pour le groupe de disponibilité (le minimum est 3)
1. Configurer les détails du deuxième point de terminaison externe créé pour les connexions aux réplicas secondaires en lecture seule

Les étapes suivantes montrent comment créer un fichier correctif qui comprend ces paramètres et comment l’appliquer à des profils de `aks-dev-test` configuration `kubeadm-dev-test` ou. Ces étapes décrivent un exemple de mise à jour corrective `aks-dev-test` du profil pour ajouter les attributs de haute disponibilité. Pour un déploiement sur un cluster kubeadm, un correctif similaire s’applique, mais assurez-vous que vous utilisez *deexclusion* pour le **serviceType** dans la section **points de terminaison** .

1. Créer un `patch.json` fichier

    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.resources.master.spec",
          "value": {
            "type": "Master",
            "replicas": 3,
            "endpoints": [
              {
                "name": "Master",
                "serviceType": "LoadBalancer",
                "port": 31433
              },
              {
                "name": "MasterSecondary",
                "serviceType": "LoadBalancer",
                "port": 31436
              }
            ],
            "settings": {
              "sql": {
                "hadr.enabled": "true"
              }
            }
          }
        }
      ]
    }
    ```

1. Cloner votre profil ciblé

    ```bash
    azdata bdc config init --source aks-dev-test --target custom-aks
    ```

1. Appliquer le fichier correctif à votre profil personnalisé

    ```bash
    azdata bdc config patch -c custom-aks/bdc.json --patch-file patch.json
    ```

## <a name="connect-to-sql-server-databases"></a>Se connecter à des bases de données SQL Server

Selon le type de charge de travail que vous souhaitez exécuter sur SQL Server maître, vous pouvez vous connecter à la base de données principale pour les charges de travail en lecture-écriture ou aux bases de données dans les réplicas secondaires pour le type de charges de travail en lecture seule. Voici un plan pour chaque type de connexion :

### <a name="connect-to-databases-on-the-primary-replica"></a>Se connecter aux bases de données sur le réplica principal

Pour les connexions au réplica principal, utilisez `sql-server-master` le point de terminaison. Ce point de terminaison est également l’écouteur du groupe de disponibilité. Toutes les connexions sont dans le contexte du groupe de disponibilité. Par exemple, une connexion par défaut utilisant ce point de terminaison entraînera la `master` connexion à la base de données dans le groupe `master` de disponibilité, et non dans la base de données d’instance SQL Server.

```bash
azdata bdc endpoint list -e sql-server-master -o table
```

`Description                           Endpoint             Name               Protocol`
`------------------------------------  -------------------  -----------------  ----------`
`SQL Server Master Instance Front-End  13.64.235.192,31433  sql-server-master  tds`

> [!NOTE]
> Des événements de basculement peuvent se produire lors d’une exécution de requête distribuée qui accède aux données à partir de sources de données distantes telles que HDFS ou le pool de données. En guise de meilleure pratique, les applications doivent être conçues pour avoir une logique de nouvelle tentative de connexion en cas de déconnexion causée par le basculement.  
>

### <a name="connect-to-databases-on-the-secondary-replicas"></a>Se connecter aux bases de données sur les réplicas secondaires

Pour les connexions en lecture seule aux bases de données dans les réplicas `sql-server-master-readonly` secondaires, utilisez le point de terminaison. Ce point de terminaison agit comme un équilibreur de charge sur tous les réplicas secondaires. Indiquez le contexte de la base de données utilisateur dans la chaîne de connexion.

```bash
azdata bdc endpoint list -e sql-server-master-readonly -o table
```

`Description                                    Endpoint            Name                        Protocol`
`---------------------------------------------  ------------------  --------------------------  ----------`
`SQL Server Master Readable Secondary Replicas  13.64.238.24,31436  sql-server-master-readonly  tds`

### <a id="instance-connect"></a>Se connecter à l’instance de SQL Server

Pour certaines opérations telles que la définition de configurations au niveau du serveur ou l’ajout manuel d’une base de données au groupe de disponibilité (dans le cas où la base de données a été créée avec un flux de travail de restauration), vous avez besoin d’une connexion à l’instance. Pour fournir cette connexion, exposez un point de terminaison externe. Voici un exemple qui montre comment exposer ce point de terminaison, puis ajouter la base de données créée avec un flux de travail de restauration au groupe de disponibilité.

- Déterminez le pod qui héberge le réplica principal en vous connectant au `sql-server-master` point de terminaison et exécutez :

    ```sql
    SELECT @@SERVERNAME
   ```

- Exposer le point de terminaison externe en créant un nouveau service Kubernetes

    Pour un cluster kubeadm, exécutez la commande ci-dessous. Remplacez `podName` par le nom du serveur retourné à l’étape précédente, `serviceName` avec le nom préféré pour le service Kubernetes créé et `namespaceName`* par le nom de votre cluster BDC.

    ```bash
    kubectl -n <namespaceName> expose pod <podName> --port=1533  --name=<serviceName> --type=NodePort
    ```

    Pour un cluster AKS, exécutez la même commande, sauf que le type du service créé sera `LoadBalancer`. Exemple : 

    ```bash
    kubectl -n <namespaceName> expose pod <podName> --port=1533  --name=<serviceName> --type=LoadBalancer
    ```

    Voici un exemple de cette commande exécutée sur AKS, où le pod hébergeant le serveur `master-0`principal est :

    ```bash
    kubectl -n mssql-cluster expose pod master-0 --port=1533  --name=master-sql-0 --type=LoadBalancer
    ```

    Récupérez l’adresse IP du service Kubernetes créé :

    ```bash
    kubectl get services -n <namespaceName>
    ```

> [!IMPORTANT]
> Comme meilleure pratique, vous devez effectuer un nettoyage en supprimant le service Kubernetes créé ci-dessus en exécutant la commande suivante :
>
>```bash
>kubectl delete svc master-sql-0 -n mssql-cluster
>```

- Ajoutez la base de données au groupe de disponibilité.

    Pour que la base de données soit ajoutée au groupe de disponibilité, elle doit s’exécuter en mode de récupération complète et une sauvegarde de fichier journal doit être effectuée. Utilisez l’adresse IP du service Kubernetes créé ci-dessus et connectez-vous à l’instance SQL Server, puis exécutez les instructions TSQL comme indiqué ci-dessous.

    ```sql
    ALTER DATABASE <databaseName> SET RECOVERY FULL;
    BACKUP DATABASE <databaseName> TO DISK='<filePath>'
    ALTER AVAILABILITY GROUP containedag ADD DATABASE <databaseName>
    ```

    L’exemple suivant ajoute une base de `sales` données nommée qui a été restaurée sur l’instance :

    ```sql
    ALTER DATABASE sales SET RECOVERY FULL;
    BACKUP DATABASE sales TO DISK='/var/opt/mssql/data/sales.bak'
    ALTER AVAILABILITY GROUP containedag ADD DATABASE sales
    ```

## <a name="known-limitations"></a>Limites connues

Il s’agit des problèmes connus et des limitations avec les groupes de disponibilité pour SQL Server maître dans Big Data cluster :

- Les bases de données créées à la suite de flux `CREATE DATABASE` de `RESTORE`travail `CREATE DATABASE FROM SNAPSHOT` autres que like, ne sont pas automatiquement ajoutées au groupe de disponibilité. [Connectez-vous à l’instance](#instance-connect) et ajoutez la base de données manuellement au groupe de disponibilité.
- Certaines opérations telles que l’exécution des paramètres `sp_configure` de configuration du serveur avec requièrent une connexion à l’instance principale. Vous ne pouvez pas utiliser le point de terminaison principal correspondant. Suivez [les instructions](#instance-connect) pour vous connecter à l’instance SQL Server et `sp_configure`exécutez.
- La configuration de haute disponibilité doit être créée lors du déploiement du BDC. Vous ne pouvez pas activer la configuration de haute disponibilité avec les groupes de disponibilité après le déploiement.

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur l’utilisation des fichiers de configuration dans Big Data les déploiements de cluster, voir [How to deploy [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] on Kubernetes](deployment-guidance.md#configfile).
- Pour plus d’informations sur la fonctionnalité des groupes de disponibilité pour SQL Server, consultez [vue d’ensemble des groupes de disponibilité Always on (SQL Server)](https://docs.microsoft.com/en-us/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server?view=sql-server-2017).
