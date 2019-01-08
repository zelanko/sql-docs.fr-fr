---
title: Se connecter au maître et HDFS
titleSuffix: SQL Server 2019 big data clusters
description: Découvrez comment vous connecter à l’instance principale de SQL Server et de la passerelle HDFS/Spark pour un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 8bccadd8fbce9fe2a8cc6f16db75dbd09f3d1ed0
ms.sourcegitcommit: edf7372cb674179f03a330de5e674824a8b4118f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53264361"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Se connecter à un cluster SQL Server de données volumineux avec Azure Data Studio

Cet article décrit comment se connecter à un cluster de données volumineuses de SQL Server 2019 (version préliminaire) à partir d’Azure Data Studio.

## <a name="prerequisites"></a>Prérequis

- Un déployé [cluster de données volumineux de SQL Server 2019](deployment-guidance.md).
- [Outils de données volumineuses de SQL Server 2019](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **Extension de SQL Server 2019**
   - **kubectl**

## <a name="connect-to-the-cluster"></a>Connectez-vous au cluster

Lorsque vous vous connectez à un cluster de données volumineux, vous pouvez vous connecter à SQL Server [instance principale](concept-master-instance.md) ou à la passerelle HDFS/Spark. Les sections suivantes montrent comment se connecter à chacun.

## <a id="master"></a> Instance principale

L’instance principale de SQL Server est une instance de SQL Server traditionnelle contenant les bases de données relationnelles SQL Server. Les étapes suivantes décrivent comment vous connecter à l’instance principale à l’aide d’Azure Data Studio.

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

## <a id="hdfs"></a> Passerelle HDFS/Spark

Le **passerelle HDFS/Spark** vous permet de se connecter pour pouvoir fonctionner avec le pool de stockage HDFS et à exécuter des tâches Spark. Les étapes suivantes décrivent comment vous connecter avec Azure Data Studio.

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

1. Tapez l’adresse IP du cluster big data dans **nom_serveur** (ne spécifiez pas de port).

1. Entrez `root` pour le **utilisateur** et spécifiez le **mot de passe** à votre cluster big data.

   ![Se connecter à HDFS/Spark passerelle](./media/connect-to-big-data-cluster/connect-to-cluster-hdfs-spark.png)

   > [!TIP]
   > Par défaut, le nom d’utilisateur est **racine** et le mot de passe correspond à la **KNOX_PASSWORD** variable d’environnement utilisée au cours du déploiement.

1. Appuyez sur **Connect**et le **tableau de bord Server** doit apparaître.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses de SQL Server 2019, consultez [que sont les clusters de données volumineuses de SQL Server 2019](big-data-cluster-overview.md).