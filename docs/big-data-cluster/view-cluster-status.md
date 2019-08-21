---
title: Afficher l’état du cluster
titleSuffix: SQL Server big data clusters
description: Cet article explique comment afficher l’état d’un cluster Big Data à l’aide d’Azure Data Studio, de notebooks et de commandes azdata.
author: yualan
ms.author: alayu
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 028864712658e35913fa04fb1a85e4ca960ad573
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653271"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>Guide pratique pour afficher l’état d’un cluster Big Data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment accéder aux points de terminaison de service et afficher l’état d’un cluster Big Data SQL Server (préversion). Il présente les deux techniques disponibles : Azure Data Studio et **azdata**.

## <a id="datastudio"></a> Utiliser Azure Data Studio

Après avoir téléchargé la dernière **build Insiders** d’[Azure Data Studio](https://aka.ms/azdata-insiders), vous pouvez accéder au tableau de bord Cluster Big Data SQL Server pour afficher les points de terminaison de service et l’état d’un cluster Big Data. Notez que certaines des fonctionnalités présentées ci-dessous ne sont disponibles que dans la build Insiders d’Azure Data Studio.

1. Commencez par créer une connexion à votre cluster Big Data dans Azure Data Studio. Pour plus d’informations, consultez [Se connecter à un cluster Big Data SQL Server avec Azure Data Studio](connect-to-big-data-cluster.md).

1. Cliquez avec le bouton droit sur le point de terminaison du cluster Big Data, puis cliquez sur **Manage** (Gérer).

   ![Clic droit, puis Manage](media/view-cluster-status/right-click-manage.png)

1. Sélectionnez l’onglet **Cluster Big Data SQL Server** pour accéder au tableau de bord du cluster Big Data.

   ![Tableau de bord du cluster Big Data](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>Points de terminaison de service

Il est important de pouvoir accéder facilement aux différents services au sein d’un cluster Big Data. Le tableau de bord du cluster Big Data fournit une table de points de terminaison de service qui vous permet de voir et de copier les points de terminaison de service.

![points de terminaison de service](media/view-cluster-status/service-endpoints.png)

Les premières lignes exposent les services suivants :

- Application Proxy (Proxy d’application)
- Cluster Management Service (Service de gestion de cluster)
- HDFS and Spark (HDFS et Spark)
- Management Proxy (Proxy de gestion)

Ces services listent les points de terminaison qui peuvent être copiés et collés quand vous avez besoin du point de terminaison pour vous connecter à ces services. Par exemple, vous pouvez cliquer sur l’icône de copie à droite du point de terminaison, puis la coller dans une fenêtre de texte demandant ce point de terminaison. Le point de terminaison Service de gestion de cluster est nécessaire pour exécuter le [notebook cluster status](#notebook).

### <a name="dashboards"></a>Tableaux de bord

La table des points de terminaison de service expose également plusieurs tableaux de bord de supervision :

- Metrics (Métriques) (Grafana)
- Logs (Journaux) (Kibana)
- Spark Job Monitoring (Supervision des travaux Spark)
- Spark Resource Management (Gestion des ressources Spark)

Vous pouvez cliquer directement sur ces liens. Avant d’être connecté au service, vous devez fournir votre nom d’utilisateur et votre mot de passe à deux reprises.

### <a id="notebook"></a> Notebook Cluster Status

1. Vous pouvez également voir l’état du cluster Big Data en lançant le notebook Cluster Status (État du cluster). Pour lancer le notebook, cliquez sur la tâche **Cluster Status**.

    ![lancer](media/view-cluster-status/cluster-status-launch.png)

2. Avant de commencer, vous avez besoin des éléments suivants :

    - Nom du cluster Big Data
    - Nom d’utilisateur du contrôleur
    - Mot de passe du contrôleur
    - Points de terminaison du contrôleur

    Le nom du cluster Big Data par défaut est **mssql-cluster**, sauf si vous l’avez personnalisé durant votre déploiement. Vous trouverez le point de terminaison du contrôleur dans la table des points de terminaison de service du tableau de bord du cluster Big Data. Le point de terminaison est listé comme **Cluster Management Service**. Si vous ne connaissez pas les informations d’identification, demandez-les à l’administrateur ayant déployé votre cluster.

3. Cliquez sur **Exécuter les cellules** dans la barre d’outils supérieure.

4. À l’invite, entrez vos informations d’identification. Appuyez sur Entrée après chaque information d’identification : nom du cluster Big Data, nom d’utilisateur du contrôleur et mot de passe du contrôleur.

    > [!Note]
    > Si vous ne disposez pas d’un fichier de configuration avec votre cluster Big Data, vous êtes invité à indiquer le point de terminaison du contrôleur. Tapez-le ou collez-le, puis appuyez sur Entrée pour continuer.

5. Si vous avez réussi à vous connecter, le reste du notebook montre la sortie de chaque composant du cluster Big Data. Quand vous souhaitez réexécuter une certaine cellule de code, pointez sur celle-ci, puis cliquez sur l’icône **Run**.

## <a name="use-azdata"></a>Utiliser azdata

Vous pouvez également utiliser les commandes [azdata](deploy-install-azdata.md) pour afficher les points de terminaison et l’état du cluster.

### <a name="service-endpoints"></a>Points de terminaison de service

Vous pouvez obtenir les adresses IP des points de terminaison externes du cluster Big Data en effectuant les étapes suivantes.

1. Recherchez l’adresse IP du point de terminaison du contrôleur. Pour cela, examinez la sortie EXTERNAL-IP de la commande **kubectl** suivante :

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Si vous n’avez pas changé le nom par défaut durant le déploiement, utilisez `-n mssql-cluster` dans la commande précédente. **mssql-cluster** est le nom par défaut du cluster Big Data.

1. Connectez-vous au cluster Big Data avec [azdata login](reference-azdata.md). Affectez au paramètre **--controller-endpoint** l’adresse IP externe du point de terminaison du contrôleur.

   ```bash
   azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Spécifiez le nom d’utilisateur et le mot de passe que vous avez configurés pour le contrôleur (CONTROLLER_USERNAME et CONTROLLER_PASSWORD) durant le déploiement.

1. Exécutez [azdata bdc endpoint list](reference-azdata-bdc-endpoint.md) pour obtenir une liste comprenant la description de chaque point de terminaison ainsi que les adresses IP et ports correspondants. 

   ```bash
   azdata bdc endpoint list -o table
   ```

   La liste suivante montre un exemple de sortie de cette commande :

   ```output
   Description                                             Endpoint                                                   Ip              Name               Port    Protocol
   ------------------------------------------------------  ---------------------------------------------------------  --------------  -----------------  ------  ----------
   Gateway to access HDFS files, Spark                     https://11.111.111.111:30443                               11.111.111.111  gateway            30443   https
   Spark Jobs Management and Monitoring Dashboard          https://11.111.111.111:30443/gateway/default/sparkhistory  11.111.111.111  spark-history      30443   https
   Spark Diagnostics and Monitoring Dashboard              https://11.111.111.111:30443/gateway/default/yarn          11.111.111.111  yarn-ui            30443   https
   Application Proxy                                       https://11.111.111.111:30778                               11.111.111.111  app-proxy          30778   https
   Management Proxy                                        https://11.111.111.111:30777                               11.111.111.111  mgmtproxy          30777   https
   Log Search Dashboard                                    https://11.111.111.111:30777/kibana                        11.111.111.111  logsui             30777   https
   Metrics Dashboard                                       https://11.111.111.111:30777/grafana                       11.111.111.111  metricsui          30777   https
   Cluster Management Service                              https://11.111.111.111:30080                               11.111.111.111  controller         30080   https
   SQL Server Master Instance Front-End                    11.111.111.111,31433                                       11.111.111.111  sql-server-master  31433   tcp
   HDFS File System Proxy                                  https://11.111.111.111:30443/gateway/default/webhdfs/v1    11.111.111.111  webhdfs            30443   https
   Proxy for running Spark statements, jobs, applications  https://11.111.111.111:30443/gateway/default/livy/v1       11.111.111.111  livy               30443   https
   ```

### <a name="view-cluster-status"></a>Afficher l’état du cluster

Vous pouvez afficher l’état du cluster à l’aide de la commande [azdata bdc status show](reference-azdata-bdc-status.md).

```bash
azdata bdc status show -o table
```

> [!TIP]
> Pour exécuter les commandes d’état, vous devez d’abord vous connecter à l’aide de la commande **azdata login** (présentée dans la section précédente sur les points de terminaison).

Voici un exemple de sortie de cette commande :

```output
Kind     Name           State
-------  -------------  -------
BDC      mssql-cluster  Ready
Control  default        Ready
Master   default        Ready
Compute  default        Ready
Data     default        Ready
Storage  default        Ready
```

### <a name="view-pool-status"></a>Afficher l’état du pool

Vous pouvez afficher l’état des pools au sein du cluster à l’aide de la commande [azdata bdc pool status show](reference-azdata-bdc-pool-status.md). Pour utiliser cette commande, spécifiez le type de pool avec le paramètre `--kind`. Les types de pools sont les suivants :

- compute
- data
- master
- spark
- storage

Par exemple, la commande suivante affiche l’état du pool de stockage :

```bash
azdata bdc pool status show --kind storage
```

Vous devez obtenir un texte similaire à la sortie suivante :

```output
[
  {
    "kind": "Pod",
    "logsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-0/logs/ui",
    "name": "storage-0-0",
    "nodeMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-0/nodemetrics/ui",
    "sqlMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-0/sqlmetrics/ui",
    "state": "Running"
  },
  {
    "kind": "Pod",
    "logsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-1/logs/ui",
    "name": "storage-0-1",
    "nodeMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-1/nodemetrics/ui",
    "sqlMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-1/sqlmetrics/ui",
    "state": "Running"
  }
]
```

La valeur `logsUrl` est liée à un tableau de bord kibana avec des informations de journal :

![Tableau de bord kibana](./media/view-cluster-status/kibana-dashboard.png)

Les valeurs `nodeMetricsUrl` et `sqlMetricsUrl` sont liées à un tableau de bord grafana qui permet de superviser l’intégrité des nœuds et les métriques SQL :

![Tableau de bord Grafana](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>Afficher l’état du contrôleur

Vous pouvez voir l’état du contrôleur à l’aide de la commande [azdata bdc control status show](reference-azdata-bdc-control-status.md). Celle-ci fournit des liens similaires vers les tableaux de bord de supervision liés aux nœuds de contrôleur du cluster Big Data.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]que sont les ](big-data-cluster-overview.md).
