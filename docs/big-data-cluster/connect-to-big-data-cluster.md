---
title: Se connecter à l’instance principale et à HDFS
titleSuffix: SQL Server big data clusters
description: Découvrez comment vous connecter à l’instance principale SQL Server et à la passerelle HDFS/Spark pour un cluster Big Data SQL Server 2019 (préversion).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1f09763b210427c84efe75d693fee302d7048db7
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958646"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Se connecter à un cluster Big Data SQL Server avec Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment se connecter à un cluster Big Data SQL Server 2019 (préversion) à partir d’Azure Data Studio.

## <a name="prerequisites"></a>Conditions préalables requises

- Un [cluster Big Data SQL Server 2019](deployment-guidance.md) déployé.
- [Outils de Big Data SQL Server 2019](deploy-big-data-tools.md) :
   - **Azure Data Studio**
   - **Extension SQL Server 2019**
   - **kubectl**

## <a id="master"></a> Se connecter au cluster

Pour vous connecter à un cluster Big Data avec Azure Data Studio, établissez une nouvelle connexion à l’instance principale SQL Server dans le cluster. Les étapes suivantes décrivent comment se connecter à l’instance principale avec Azure Data Studio.

1. À partir de la ligne de commande, recherchez l’adresse IP de votre instance principale avec la commande suivante :

   ```
   kubectl get svc master-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Le nom du cluster Big Data est par défaut **mssql-cluster**, sauf si vous avez personnalisé le nom dans un fichier de configuration du déploiement. Pour plus d’informations, consultez [Configurer les paramètres de déploiement de clusters Big Data](deployment-custom-configuration.md#clustername).

1. Dans Azure Data Studio, appuyez sur **F1** > **Nouvelle connexion**.

1. Dans **Type de connexion**, sélectionnez **Microsoft SQL Server**.

1. Tapez l’adresse IP de l’instance principale SQL Server dans **Nom du serveur** (par exemple : **\<Adresse IP\>,31433**).

1. Entrez un **Nom d’utilisateur** et un **Mot de passe** pour la connexion SQL.

   > [!TIP]
   > Par défaut, le nom d’utilisateur est **SA** et, sauf s’il a été changé, le mot de passe correspond à la variable d’environnement **MSSQL_SA_PASSWORD** utilisée lors du déploiement.

1. Remplacez le **Nom de la base de données** cible par une de vos bases de données relationnelles.

   ![Se connecter à l’instance principale](./media/connect-to-big-data-cluster/connect-to-cluster.png)

1. Appuyez sur **Se connecter** : le **Tableau de bord du serveur** doit apparaître.

Avec la version de février 2019 d’Azure Data Studio, la connexion à l’instance principale SQL Server vous permet également d’interagir avec la passerelle HDFS/Spark. Cela signifie que vous n’avez pas besoin d’utiliser une connexion distincte pour HDFS et Spark décrite dans la section suivante.

- L’Explorateur d’objets contient maintenant un nouveau nœud **Services de données** avec prise en charge du clic droit pour les tâches de cluster Big Data, comme la création de notebooks ou l’envoi de travaux Spark. 
- Le nœud **Services de données** contient également un dossier **HDFS** pour l’exploration de HDFS et l’exécution d’actions comme Créer une table externe ou Analyser dans le notebook.
- Le **Tableau de bord du serveur** pour la connexion contient également des onglets pour **Cluster Big Data SQL Server** et **SQL Server 2019 (préversion)** quand l’extension est installée.

   ![Nœud Services de données d’Azure Data Studio](./media/connect-to-big-data-cluster/connect-data-services-node.png)

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data SQL Server 2019, consultez [Présentation des clusters Big Data SQL Server 2019](big-data-cluster-overview.md).