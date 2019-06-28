---
title: Afficher l’état de cluster
titleSuffix: SQL Server big data clusters
description: Cet article explique comment afficher l’état d’un cluster de données volumineux à l’aide d’Azure Data Studio, les ordinateurs portables et les commandes de mssqlctl.
author: yualan
ms.author: alayu
manager: jroth
ms.date: 06/27/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2edd49c37655d420cf8022677c0d0287028a0b93
ms.sourcegitcommit: 0a4879dad09c6c42ad1ff717e4512cfea46820e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67413966"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>Comment afficher l’état d’un cluster de données volumineuses

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit comment accéder aux points de terminaison de service et d’afficher l’état d’un cluster de données volumineuses de SQL Server (version préliminaire). Vous pouvez utiliser les deux Studio de données Azure et **mssqlctl**, et cet article aborde ces deux techniques.

## <a id="datastudio"></a> Utiliser Azure Data Studio

Après avoir téléchargé la dernière version **insiders build** de [Azure Data Studio](https://aka.ms/azdata-insiders), vous pouvez afficher les points de terminaison de service et l’état d’une donnée big cluster avec le tableau de bord du cluster volumineuses de données SQL Server. Notez que certaines des fonctionnalités ci-dessous ne sont tout d’abord disponibles dans la build insiders de Studio de données Azure.

1. Tout d’abord, créez une connexion à votre cluster big data dans Azure Data Studio. Pour plus d’informations, consultez [se connecter à SQL Server cluster big data avec Azure Data Studio](connect-to-big-data-cluster.md).

1. Avec le bouton droit sur le point de terminaison de cluster de données volumineuses, puis cliquez sur **gérer**.

   ![clic droit Gérer](media/view-cluster-status/right-click-manage.png)

1. Sélectionnez le **Cluster Big Data de SQL Server** tab pour accéder à bord du cluster de données volumineuses.

   ![Tableau de bord de cluster Big data](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>points de terminaison de service

Il est important de pouvoir accéder facilement aux différents services au sein d’un cluster de données volumineux. Le tableau de bord de cluster de données volumineuses fournit une table de points de terminaison de service qui vous permet de voir et de copier les points de terminaison de service.

![points de terminaison de service](media/view-cluster-status/service-endpoints.png)

Les premières lignes exposent les services suivants :

- Proxy d’application
- Service de gestion de cluster
- HDFS et Spark
- Proxy de gestion

Ces services répertorient les points de terminaison qui peuvent être copiés et collés lorsque vous avez besoin du point de terminaison pour la connexion à ces services. Par exemple, vous pouvez cliquez sur l’icône de copie à droite du point de terminaison et puis collez-la dans une fenêtre de texte demandant ce point de terminaison. Le point de terminaison de Service de gestion de Cluster est nécessaire d’exécuter le [bloc-notes d’état de cluster](#notebook).

### <a name="dashboards"></a>Tableaux de bord

Le tableau de points de terminaison de service expose également plusieurs tableaux de bord de surveillance :

- Mesures (Grafana)
- Journaux (Kibana)
- Surveillance des travaux Spark
- Gestion des ressources Spark

Vous pouvez cliquer directement sur ces liens. Vous êtes invité à deux reprises pour fournir votre nom d’utilisateur et le mot de passe avant de vous connecter au service.

### <a id="notebook"></a> Bloc-notes d’état de cluster

1. Vous pouvez également afficher l’état du cluster du cluster de données volumineuses en lançant le bloc-notes de l’état du Cluster. Pour lancer le bloc-notes, cliquez sur le **état du Cluster** tâche.

    ![lancement](media/view-cluster-status/cluster-status-launch.png)

2. Avant de commencer, vous avez besoin des éléments suivants :

    - Nom de cluster de données volumineuses
    - Nom d’utilisateur du contrôleur
    - Mot de passe de contrôleur
    - Points de terminaison de contrôleur

    Le nom de cluster de données volumineuses par défaut est **mssql-cluster** , sauf si vous le personnalisé pendant votre déploiement. Vous pouvez trouver le point de terminaison du contrôleur à partir du tableau de bord du cluster big data dans le tableau de points de terminaison de Service. Le point de terminaison est répertorié en tant que **Service de gestion de Cluster**. Si vous ne connaissez pas les informations d’identification, demandez à l’administrateur qui a déployé votre cluster.

3. Cliquez sur **cellules exécuter** sur la barre d’outils supérieure.

4. Suivez les instructions pour vos informations d’identification. Appuyez sur en appuyant sur ENTRÉE après vous tapez chaque information d’identification pour le nom de cluster de données volumineuses, le nom d’utilisateur du contrôleur et le mot de passe de contrôleur.

    > [!Note]
    > Si vous n’avez pas un programme d’installation du fichier de configuration avec vos données Big Data, il vous sera demandé pour le point de terminaison du contrôleur. Tapez ou collez, puis appuyez sur ENTRÉE pour continuer.

5. Si vous connecté avec succès, le reste du bloc-notes affichera la sortie de chaque composant du cluster big data. Lorsque vous souhaitez exécuter à nouveau certaines une cellule de code, placez le curseur sur la cellule de code et cliquez sur le **exécuter** icône.

## <a name="use-mssqlctl"></a>Utiliser mssqlctl

Vous pouvez également utiliser [mssqlctl](deploy-install-mssqlctl.md) commandes pour afficher les points de terminaison et l’état du cluster.

### <a name="service-endpoints"></a>points de terminaison de service

Vous pouvez obtenir les adresses IP des points de terminaison externes pour le cluster de données volumineuses en procédant comme suit.

1. Rechercher l’adresse IP du point de terminaison de contrôleur en examinant la sortie de l’adresse IP externe des éléments suivants **kubectl** commande :

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Si vous n’avez pas modifié le nom par défaut au cours du déploiement, utilisez `-n mssql-cluster` dans la commande précédente. **MSSQL-cluster** est le nom par défaut pour le cluster de données volumineuses.

1. Connectez-vous au cluster big data avec [mssqlctl connexion](reference-mssqlctl.md). Définir le **--contrôleur de point de terminaison** paramètre à l’adresse IP externe du point de terminaison de contrôleur.

   ```bash
   mssqlctl login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Spécifiez le nom d’utilisateur et le mot de passe que vous avez configuré pour le contrôleur (CONTROLLER_USERNAME et CONTROLLER_PASSWORD) au cours du déploiement.

1. Exécutez [liste de point de terminaison mssqlctl bdc](reference-mssqlctl-bdc-endpoint.md) pour obtenir une liste avec une description de chaque point de terminaison et leurs valeurs d’adresse et le port IP correspondantes. 

   ```bash
   mssqlctl bdc endpoint list -o table
   ```

   La liste suivante illustre le résultat de cette commande :

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

### <a name="view-cluster-status"></a>Afficher l’état de cluster

Vous pouvez afficher l’état du cluster avec le [afficher d’état mssqlctl bdc](reference-mssqlctl-bdc-status.md) commande.

```bash
mssqlctl bdc status show -o table
```

> [!TIP]
> Pour exécuter les commandes d’état, vous devez tout d’abord vous connecter avec le **mssqlctl connexion** commande, qui a été indiqué dans la section précédente de points de terminaison.

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

### <a name="view-pool-status"></a>Afficher l’état de pool

Vous pouvez afficher l’état des pools au sein du cluster avec le [afficher d’état mssqlctl bdc pool](reference-mssqlctl-bdc-pool-status.md) commande. Pour utiliser cette commande, spécifiez le type du pool avec la `--kind` paramètre. Les types de pool sont :

- Calcul
- data
- master
- Spark
- Stockage

Par exemple, la commande suivante affiche l’état du pool du pool de stockage :

```bash
mssqlctl bdc pool status show --kind storage
```

Vous devez voir le texte similaire à la sortie suivante :

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

Le `logsUrl` valeur des liens vers un tableau de bord kibana avec les informations du journal :

![tableau de bord kibana](./media/view-cluster-status/kibana-dashboard.png)

Le `nodeMetricsUrl` et `sqlMetricsUrl` valeurs lier à un tableau de bord grafana pour l’analyse d’intégrité de nœud et métriques SQL :

![Tableau de bord Grafana](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>Afficher l’état de contrôleur

Vous pouvez afficher l’état du contrôleur avec le [mssqlctl bdc contrôle état show](reference-mssqlctl-bdc-control-status.md) commande. Il fournit des liens similaires pour les tableaux de bord de surveillance associées aux nœuds de contrôleur du cluster de données volumineuses.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses, consultez [que sont les clusters de données volumineuses de SQL Server](big-data-cluster-overview.md).
