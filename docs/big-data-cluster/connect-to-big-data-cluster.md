---
title: Se connecter au maître et HDFS
titleSuffix: SQL Server 2019 big data clusters
description: Découvrez comment vous connecter à l’instance principale de SQL Server et de la passerelle HDFS/Spark pour un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/12/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 103e02d456f1176c3bb49c1e67f84215399ab5cd
ms.sourcegitcommit: 009bee6f66142c48477849ee03d5177bcc3b6380
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56231036"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Se connecter à un cluster SQL Server de données volumineux avec Azure Data Studio

Cet article décrit comment se connecter à un cluster de données volumineuses de SQL Server 2019 (version préliminaire) à partir d’Azure Data Studio. Il existe deux points de terminaison principales qui servent à interagir avec un cluster de données volumineuses :

| Point de terminaison | Description |
|---|---|
| Instance de SQL Server Master | L’instance principale de SQL Server dans le cluster contenant les bases de données relationnelles SQL Server. |
| Passerelle HDFS/Spark | Accès au stockage HDFS du cluster et la possibilité d’exécuter des tâches Spark. |

> [!TIP]
> Avec la version de février 2019 de Studio de données Azure, se connecter automatiquement à l’instance principale de SQL Server fournit l’accès de l’interface utilisateur à la passerelle HDFS/Spark.

## <a name="prerequisites"></a>Prérequis

- Un déployé [cluster de données volumineux de SQL Server 2019](deployment-guidance.md).
- [Outils de données volumineuses de SQL Server 2019](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **Extension de SQL Server 2019**
   - **kubectl**

## <a id="master"></a> Connectez-vous au cluster

Pour vous connecter à un cluster de données volumineux avec Azure Data Studio, effectuez une nouvelle connexion à l’instance principale de SQL Server dans le cluster. Les étapes suivantes décrivent comment vous connecter à l’instance principale à l’aide d’Azure Data Studio.

1. À partir de la ligne de commande, recherchez l’adresse IP de votre instance principale avec la commande suivante :

   ```
   kubectl get svc endpoint-master-pool -n <your-cluster-name>
   ```

1. Dans Azure Data Studio, appuyez sur **F1** > **nouvelle connexion**.

1. Dans **type de connexion**, sélectionnez **Microsoft SQL Server**.

1. Tapez l’adresse IP de l’instance principale de SQL Server dans **nom_serveur** (par exemple : **\<Adresse IP\>, 31433**).

1. Entrez un nom de connexion SQL **nom d’utilisateur** et **mot de passe**.

   > [!TIP]
   > Par défaut, le nom d’utilisateur est **SA** et, sauf si modifié, le mot de passe correspond à la **MSSQL_SA_PASSWORD** variable d’environnement utilisée au cours du déploiement.

1. Modifier la cible **nom de la base de données** à un de vos bases de données relationnelles.

   ![Se connecter à l’instance principale](./media/connect-to-big-data-cluster/connect-to-cluster.png)

1. Appuyez sur **Connect**et le **tableau de bord Server** doit apparaître.

Avec la version de février 2019 de Studio de données Azure, se connecter à l’instance principale de SQL Server vous permet également d’interagir avec la passerelle HDFS/Spark. Cela signifie que vous n’avez pas besoin d’utiliser une connexion distincte pour HDFS et Spark qui décrit la section suivante.

- L’Explorateur d’objets contient maintenant une nouvelle **Data Services** nœud avec prise en charge avec le bouton droit pour les tâches de cluster de données volumineuses, telles que la création de nouveaux ordinateurs portables ou en soumettant des travaux spark. 
- Le **Data Services** nœud contient également un **HDFS** dossier pour l’exploration de HDFS et effectuer des actions telles que Create External Table ou d’analyser dans le bloc-notes.
- Le **tableau de bord Server** pour la connexion contient également des onglets pour **Cluster Big Data de SQL Server** et **SQL Server 2019 (version préliminaire)** lorsque l’extension est installée.

   ![Nœud des Services de données Azure Data Studio](./media/connect-to-big-data-cluster/connect-data-services-node.png)

> [!IMPORTANT]
> Si vous voyez **erreur inconnue** dans l’interface utilisateur, vous devrez peut-être [vous connecter directement à la passerelle HDFS/Spark](#hdfs). Une des causes de cette erreur sont des mots de passe différents pour l’instance principale de SQL Server et de la passerelle HDFS/Spark. Azure Data Studio part du principe que le mot de passe est utilisé pour les deux.
  
## <a id="hdfs"></a> Se connecter à la passerelle HDFS/Spark

Dans la plupart des cas, connexion à l’instance principale de SQL Server vous permet d’accéder au HDFS et Spark également via le **Data Services** nœud. Toutefois, vous pouvez toujours de créer une connexion dédiée à la **passerelle HDFS/Spark** si nécessaire. Les étapes suivantes décrivent comment vous connecter avec Azure Data Studio.

1. À partir de la ligne de commande, recherchez l’adresse IP de votre passerelle HDFS/Spark avec l’une des commandes suivantes.
   
   **Déploiements de AKS :**

   ```
   kubectl get svc service-security-lb -n <your-cluster-name>
   ```

   **Les déploiements non-AKS**:

   ```
   kubectl get svc service-security-nodeport -n <your-cluster-name>
   ```
 
1. Dans Azure Data Studio, appuyez sur **F1** > **nouvelle connexion**.

1. Dans **type de connexion**, sélectionnez **cluster de données volumineux de SQL Server**.

   > [!TIP]
   > Si vous ne voyez pas le **cluster de données volumineux de SQL Server** connexion type, assurez-vous que vous avez installé le [extension de SQL Server 2019](../azure-data-studio/sql-server-2019-extension.md) et que vous avez redémarré Azure Data Studio après l’extension terminée l’installation.

1. Tapez l’adresse IP du cluster big data dans **nom_serveur** (ne spécifiez pas de port).

1. Entrez `root` pour le **utilisateur** et spécifiez le **mot de passe** à votre cluster big data.

   ![Se connecter à HDFS/Spark passerelle](./media/connect-to-big-data-cluster/connect-to-cluster-hdfs-spark.png)

   > [!TIP]
   > Par défaut, le nom d’utilisateur est **racine** et le mot de passe correspond à la **KNOX_PASSWORD** variable d’environnement utilisée au cours du déploiement.

1. Appuyez sur **Connect**et le **tableau de bord Server** doit apparaître.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses de SQL Server 2019, consultez [que sont les clusters de données volumineuses de SQL Server 2019](big-data-cluster-overview.md).