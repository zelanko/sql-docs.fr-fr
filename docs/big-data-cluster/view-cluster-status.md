---
title: Afficher l’état du cluster
titleSuffix: SQL Server big data clusters
description: Cet article explique comment afficher l’état d’un cluster Big Data à l’aide de Azure Data Studio, de blocs-notes et de commandes azdata.
author: yualan
ms.author: alayu
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c6dca94b8bd7547222394d7809cb003b9e936982
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419289"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>Comment afficher l’état d’un cluster Big Data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment accéder aux points de terminaison de service et afficher l’état d’un cluster SQL Server Big Data (version préliminaire). Vous pouvez utiliser à la fois Azure Data Studio et **azdata**, et cet article aborde ces deux techniques.

## <a id="datastudio"></a>Utiliser Azure Data Studio

Après avoir téléchargé la **Build** Insiders la plus récente de [Azure Data Studio](https://aka.ms/azdata-insiders), vous pouvez afficher les points de terminaison de service et l’état d’un cluster Big Data avec le tableau de bord du cluster SQL Server Big Data. Notez que certaines des fonctionnalités ci-dessous ne sont disponibles que dans la version Insiders de Azure Data Studio.

1. Tout d’abord, créez une connexion à votre cluster Big Data dans Azure Data Studio. Pour plus d’informations, consultez [se connecter à un cluster SQL Server Big Data avec Azure Data Studio](connect-to-big-data-cluster.md).

1. Cliquez avec le bouton droit sur le point de terminaison du cluster Big Data, puis cliquez sur **gérer**.

   ![Cliquez avec le bouton droit sur gérer](media/view-cluster-status/right-click-manage.png)

1. Sélectionnez l’onglet **SQL Server Big Data cluster** pour accéder au tableau de bord du cluster Big Data.

   ![Tableau de bord du cluster Big Data](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>Points de terminaison de service

Il est important de pouvoir accéder facilement aux différents services au sein d’un cluster Big Data. Le tableau de bord du cluster Big Data fournit une table de points de terminaison de service qui vous permet de voir et de copier les points de terminaison de service.

![Points de terminaison de service](media/view-cluster-status/service-endpoints.png)

Les premières lignes exposent les services suivants:

- Proxy d’application
- Service de gestion de cluster
- HDFS et Spark
- Proxy de gestion

Ces services répertorient les points de terminaison qui peuvent être copiés et collés lorsque vous avez besoin du point de terminaison pour la connexion à ces services. Par exemple, vous pouvez cliquer sur l’icône de copie à droite du point de terminaison, puis la coller dans une fenêtre de texte demandant ce point de terminaison. Le point de terminaison du service de gestion de cluster est nécessaire pour exécuter le [Notebook État du cluster](#notebook).

### <a name="dashboards"></a>Tableaux de bord

Le tableau des points de terminaison de service expose également plusieurs tableaux de bord pour la surveillance:

- Mesures (Grafana)
- Journaux (Kibana)
- Surveillance des travaux Spark
- Gestion des ressources Spark

Vous pouvez cliquer sur ces liens directement. Deux fois, vous êtes invité à fournir votre nom d’utilisateur et votre mot de passe avant de vous connecter au service.

### <a id="notebook"></a>Bloc-notes d’État du cluster

1. Vous pouvez également afficher l’état du cluster Big Data en lançant le bloc-notes État du cluster. Pour lancer le bloc-notes, cliquez sur la tâche **État du cluster** .

    ![Lancer](media/view-cluster-status/cluster-status-launch.png)

2. Avant de commencer, vous aurez besoin des éléments suivants:

    - Nom du cluster Big Data
    - Nom d’utilisateur du contrôleur
    - Mot de passe du contrôleur
    - Points de terminaison de contrôleur

    Le nom du cluster Big Data par défaut est **MSSQL-cluster** , sauf si vous l’avez personnalisé au cours de votre déploiement. Vous pouvez trouver le point de terminaison du contrôleur à partir du tableau de bord Big Data du cluster dans le tableau des points de terminaison de service. Le point de terminaison est listé en tant que **service de gestion de cluster**. Si vous ne connaissez pas les informations d’identification, demandez à l’administrateur qui a déployé votre cluster.

3. Dans la barre d’outils supérieure, cliquez sur **exécuter les cellules** .

4. Suivez l’invite de commandes pour vos informations d’identification. Appuyez sur entrée après avoir tapé chaque information d’identification pour le nom du cluster Big Data, le nom d’utilisateur du contrôleur et le mot de passe du contrôleur.

    > [!Note]
    > Si vous n’avez pas configuré de fichier de configuration avec votre Big Data, vous êtes invité à indiquer le point de terminaison du contrôleur. Tapez ou collez-le, puis appuyez sur entrée pour continuer.

5. Si vous avez réussi à vous connecter, le reste du bloc-notes affiche la sortie de chaque composant du cluster Big Data. Lorsque vous souhaitez réexécuter une certaine cellule de code, pointez sur la cellule de code, puis cliquez sur l’icône **exécuter** .

## <a name="use-azdata"></a>Utiliser azdata

Vous pouvez également utiliser les commandes [azdata](deploy-install-azdata.md) pour afficher les deux points de terminaison et l’état du cluster.

### <a name="service-endpoints"></a>Points de terminaison de service

Vous pouvez obtenir les adresses IP des points de terminaison externes pour le cluster Big Data à l’aide des étapes suivantes.

1. Recherchez l’adresse IP du point de terminaison du contrôleur en regardant la sortie externe-IP de la commande **kubectl** suivante:

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Si vous n’avez pas modifié le nom par défaut lors du `-n mssql-cluster` déploiement, utilisez dans la commande précédente. **MSSQL-cluster** est le nom par défaut du cluster Big Data.

1. Connectez-vous au cluster Big Data avec la [connexion azdata](reference-azdata.md). Définissez le paramètre **--Endpoint-point de terminaison** sur l’adresse IP externe du point de terminaison du contrôleur.

   ```bash
   azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Spécifiez le nom d’utilisateur et le mot de passe que vous avez configurés pour le contrôleur (CONTROLLER_USERNAME et CONTROLLER_PASSWORD) au cours du déploiement.

1. Exécutez la [liste de points de terminaison azdata BDC](reference-azdata-bdc-endpoint.md) pour obtenir une liste avec une description de chaque point de terminaison, ainsi que les valeurs d’adresse IP et de port correspondantes. 

   ```bash
   azdata bdc endpoint list -o table
   ```

   La liste suivante affiche un exemple de sortie de cette commande:

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

Vous pouvez afficher l’état du cluster à l’aide de la commande [azdata BDC Status Show](reference-azdata-bdc-status.md) .

```bash
azdata bdc status show -o table
```

> [!TIP]
> Pour exécuter les commandes d’État, vous devez d’abord vous connecter à l’aide de la commande **azdata login** , qui était affichée dans la section points de terminaison précédents.

Le code suivant montre un exemple de sortie de cette commande:

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

Vous pouvez afficher l’état des pools au sein du cluster à l’aide de la commande azdata de l' [État du pool BDC](reference-azdata-bdc-pool-status.md) . Pour utiliser cette commande, spécifiez le type de pool avec `--kind` le paramètre. Les types de pool sont les suivants:

- Calcul
- data
- master
- Mousse
- storage

Par exemple, la commande suivante affiche l’état du pool de stockage:

```bash
azdata bdc pool status show --kind storage
```

Vous devez voir un texte similaire à la sortie suivante:

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

La `logsUrl` valeur est liée à un tableau de bord kibana avec les informations de journal:

![Tableau de bord Kibana](./media/view-cluster-status/kibana-dashboard.png)

Les `nodeMetricsUrl` valeurs `sqlMetricsUrl` et sont liées à un tableau de bord grafana pour surveiller l’intégrité des nœuds et les métriques SQL:

![Tableau de bord Grafana](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>Afficher l’état du contrôleur

Vous pouvez afficher l’état du contrôleur avec la commande [azdata BDC Control Status Show](reference-azdata-bdc-control-status.md) . Il fournit des liens similaires vers les tableaux de bord de surveillance liés aux nœuds de contrôleur du cluster Big Data.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [que sont les SQL Server Big Data les clusters](big-data-cluster-overview.md).
