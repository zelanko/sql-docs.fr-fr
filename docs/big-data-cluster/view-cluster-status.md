---
title: Afficher l’état du cluster
titleSuffix: SQL Server big data clusters
description: Cet article explique comment afficher l’état d’un cluster Big Data à l’aide d’Azure Data Studio, de notebooks et de commandes azdata.
author: yualan
ms.author: alayu
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 45cf5461b9154d397ee5365fd275d2545a3cc376
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "73531586"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>Guide pratique pour afficher l’état d’un cluster Big Data 

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment accéder aux points de terminaison de service et afficher l’état des composants d’un cluster Big Data SQL Server. Il présente les deux techniques disponibles : Azure Data Studio et **azdata**.

## <a name="use-azure-data-studio"></a><a id="datastudio"></a> Utiliser Azure Data Studio

Après avoir téléchargé la dernière **build Insiders** d’[Azure Data Studio](https://aka.ms/getazuredatastudio), vous pouvez accéder au tableau de bord Cluster Big Data SQL Server pour afficher les points de terminaison de service et l’état d’un cluster Big Data. Certaines des fonctionnalités présentées ci-dessous ne sont disponibles que dans la build Insiders d’Azure Data Studio.

1. Commencez par créer une connexion à votre cluster Big Data dans Azure Data Studio. Pour plus d’informations, consultez [Se connecter à un cluster Big Data SQL Server avec Azure Data Studio](connect-to-big-data-cluster.md).

1. Cliquez avec le bouton droit sur le point de terminaison du cluster Big Data, puis cliquez sur **Manage** (Gérer).

   ![Clic droit, puis Manage](media/view-cluster-status/right-click-manage.png)

1. Sélectionnez l’onglet **Cluster Big Data SQL Server** pour accéder au tableau de bord du cluster Big Data.

   ![Tableau de bord du cluster Big Data](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>Points de terminaison de service

Il est important de pouvoir accéder facilement aux différents services au sein d’un cluster Big Data. Le tableau de bord du cluster Big Data fournit une table de points de terminaison de service qui vous permet de voir et de copier les points de terminaison de service.

![points de terminaison de service](media/view-cluster-status/service-endpoints.png)

Ces services listent les points de terminaison qui peuvent être copiés et collés quand vous avez besoin du point de terminaison pour vous connecter à ces services. Par exemple, vous pouvez cliquer sur l’icône de copie à droite du point de terminaison, puis la coller dans une fenêtre de texte demandant ce point de terminaison. Le point de terminaison Service de gestion de cluster est nécessaire pour exécuter le [notebook cluster status](#notebook).

### <a name="dashboards"></a>Tableaux de bord

La table des points de terminaison de service expose également plusieurs tableaux de bord de supervision :

- Metrics (Métriques) (Grafana)
- Logs (Journaux) (Kibana)
- Spark Job Monitoring (Supervision des travaux Spark)
- Spark Resource Management (Gestion des ressources Spark)

Vous pouvez cliquer directement sur ces liens. Vous serez invité à vous authentifier lors de l’accès à ces tableaux de bord. Pour les tableaux de bord des métriques et des journaux, fournissez les informations d’identification d’administrateur du contrôleur que vous avez définies au moment du déploiement à l’aide des variables d’environnement **AZDATA_USERNAME** et **AZDATA_PASSWORD**. Les tableaux de bord Spark utilisent des informations d’identification de passerelle (Knox) : l’identité Active Directory dans un cluster intégré à AD ou l’utilisateur **racine** et **AZDATA_PASSWORD** si l’authentification de base est utilisée dans votre cluster. 

### <a name="cluster-status-notebook"></a><a id="notebook"></a> Notebook Cluster Status

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

5. Si vous avez réussi à vous connecter, le reste du notebook montre la sortie de chaque composant du cluster Big Data. Quand vous souhaitez réexécuter une certaine cellule de code, pointez sur celle-ci, puis cliquez sur l’icône **Exécuter**.

## <a name="use-azdata"></a>Utiliser azdata

Vous pouvez également utiliser les commandes [azdata](deploy-install-azdata.md) pour afficher les points de terminaison et l’état du cluster.

### <a name="service-endpoints"></a>Points de terminaison de service

1. Connectez-vous au cluster Big Data avec [azdata login](reference-azdata.md). Affectez au paramètre **--controller-endpoint** l’adresse IP externe du point de terminaison du contrôleur.

   ```bash
   azdata login --endpoint https://<ip-address-of-controller-svc-external>:30080 --username <user-name>
   ```

   Spécifiez le nom d’utilisateur et le mot de passe que vous avez configurés pour le contrôleur (AZDATA_USERNAME et AZDATA_PASSWORD) durant le déploiement. 
   Pour l’authentification Active Directory, la commande est la suivante :

  ```bash
   azdata login --endpoint https://<control_domain_name>:30080 --auth ad
   ```

1. Exécutez [`azdata bdc endpoint list`](reference-azdata-bdc-endpoint.md) pour obtenir une liste comprenant la description de chaque point de terminaison ainsi que les adresses IP et valeurs de port correspondantes. 

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

Vous pouvez afficher l’état du cluster à l’aide de la commande [`azdata bdc status show`](reference-azdata-bdc-status.md).

```bash
azdata bdc status show
```

> [!TIP]
> Pour exécuter les commandes d’état, vous devez d’abord vous connecter à l’aide de la commande **azdata login** (présentée dans la section précédente sur les points de terminaison).

Voici un exemple de sortie de cette commande :

```output
 Bdc: ready                                                                                                                                                                                                          Health Status:  healthy
 ===========================================================================================================================================================================================================================================
 Services: ready                                                                                                                                                                                                     Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Servicename    State    Healthstatus    Details

 spark          ready    healthy         -
 sql            ready    healthy         -
 hdfs           ready    healthy         -
 control        ready    healthy         -
 gateway        ready    healthy         -
 app            ready    healthy         -


 Spark Services: ready                                                                                                                                                                                               Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 sparkhead       ready    healthy         StatefulSet sparkhead is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy


 Sql Services: ready                                                                                                                                                                                                 Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 master          ready    healthy         StatefulSet master is healthy
 compute-0       ready    healthy         StatefulSet compute-0 is healthy
 data-0          ready    healthy         StatefulSet data-0 is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy


 Hdfs Services: ready                                                                                                                                                                                                Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 nmnode-0        ready    healthy         StatefulSet nmnode-0 is healthy
 zookeeper       ready    healthy         StatefulSet zookeeper is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy
 sparkhead       ready    healthy         StatefulSet sparkhead is healthy


 Control Services: ready                                                                                                                                                                                             Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 controldb       ready    healthy         StatefulSet controldb is healthy
 control         ready    healthy         ReplicaSet control is healthy
 metricsdc       ready    healthy         DaemonSet metricsdc is healthy
 metricsui       ready    healthy         ReplicaSet metricsui is healthy
 metricsdb       ready    healthy         StatefulSet metricsdb is healthy
 logsui          ready    healthy         ReplicaSet logsui is healthy
 logsdb          ready    healthy         StatefulSet logsdb is healthy
 mgmtproxy       ready    healthy         ReplicaSet mgmtproxy is healthy
 controlwd       ready    healthy         ReplicaSet controlwd is healthy


 Gateway Services: ready                                                                                                                                                                                             Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 gateway         ready    healthy         StatefulSet gateway is healthy


 App Services: ready                                                                                                                                                                                                 Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 appproxy        ready    healthy         ReplicaSet appproxy is healthy
```

### <a name="view-specific-resource-status"></a>Afficher l’état d’une ressource spécifique

Vous pouvez afficher l’état d’une ressource spécifique au sein du cluster à l’aide de la commande [azdata bdc status show](reference-azdata-bdc-status.md). Lorsque vous utilisez cette commande, vous pouvez filtrer à l’aide du paramètre `--resource`. Voici quelques exemples d’entrées pour le paramètre `--resource` :

- master
- contrôle
- compute-0
- storage-0
- passerelle

Par exemple, la commande suivante affiche l’état du pool de stockage :

```bash
azdata bdc status show --all --resource storage-0
```

Pour afficher l’état de tous les composants qui exécutent un service spécifique, vous devez utiliser le groupe de commandes `azdata bdc <serviceName> status show` correspondant. Par exemple :

- azdata bdc sql status show --all
- azdata bdc hdfs status show --all
- azdata bdc spark status show --all

Voici un exemple de sortie :

```output
  Storage-0: ready                                                                                                                                                                                                    Health Status:  healthy
 ===========================================================================================================================================================================================================================================
 Instances: running                                                                                                                                                                                                  Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Instancename    State    Healthstatus    Details

 storage-0-0     running  healthy         Pod storage-0-0 is healthy
 storage-0-1     running  healthy         Pod storage-0-1 is healthy


 Dashboards
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Name            Url

 nodeMetricsUrl  https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/nodemetrics/ui
 sqlMetricsUrl   https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/sqlmetrics/ui
 logsUrl         https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/logs/ui
 ```

> [!TIP]
> Exécutez la commande d’état avec des paramètres `--all` pour obtenir des détails supplémentaires sur l’intégrité, dont des liens vers des tableaux de bord de métriques et de journaux correspondant à l’instance spécifique. Voici un exemple de sortie lorsque les paramètres `--all` sont utilisés :

```output
 Spark: ready                                                                                                                                                                                                        Health Status:  healthy
 ===========================================================================================================================================================================================================================================
 Resources: ready                                                                                                                                                                                                    Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 sparkhead       ready    healthy         StatefulSet sparkhead is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy


 Sparkhead Resources: running                                                                                                                                                                                        Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Instancename    State    Healthstatus    Details

 sparkhead-0     running  healthy         Pod sparkhead-0 is healthy
 sparkhead-1     running  healthy         Pod sparkhead-1 is healthy


      Dashboards
      --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      Name            Url

      nodeMetricsUrl  https://13.91.50.9:30777/api/v1/bdc/instances/sparkhead-1/status/nodemetrics/ui
      sqlMetricsUrl   https://13.91.50.9:30777/api/v1/bdc/instances/sparkhead-1/status/sqlmetrics/ui
      logsUrl         https://13.91.50.9:30777/api/v1/bdc/instances/sparkhead-1/status/logs/ui


 Storage-0 Resources: running                                                                                                                                                                                        Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Instancename    State    Healthstatus    Details

 storage-0-0     running  healthy         Pod storage-0-0 is healthy
 storage-0-1     running  healthy         Pod storage-0-1 is healthy


      Dashboards
      --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      Name            Url

      nodeMetricsUrl  https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/nodemetrics/ui
      sqlMetricsUrl   https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/sqlmetrics/ui
      logsUrl         https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/logs/ui
```

La valeur `logsUrl` est liée à un tableau de bord Kibana :

![Tableau de bord kibana](./media/view-cluster-status/kibana-dashboard.png)

> [!NOTE]
> L’(ancien) navigateur Microsoft Edge étant incompatible avec Kibana, vous devez utiliser le navigateur Chromium pour que le tableau de bord s’affiche correctement. Une page vide s’affiche lors du chargement des tableaux de bord à l’aide d’un navigateur non pris en charge. Examinez ici les navigateurs pris en charge pour Kibana.

Les valeurs `nodeMetricsUrl` et `sqlMetricsUrl` sont liées à un tableau de bord Grafana pour superviser les métriques de nœuds Kubernetes et les métriques de service de cluster Big Data :

![Tableau de bord Grafana](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>Afficher l’état du contrôleur

Vous pouvez afficher l’état du contrôleur avec la commande [`azdata bdc control status show`](reference-azdata-bdc-control-status.md). Celle-ci fournit des liens similaires vers les tableaux de bord de supervision associés aux composants de contrôleur du cluster Big Data.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] ?](big-data-cluster-overview.md).
