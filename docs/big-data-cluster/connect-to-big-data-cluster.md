---
title: Se connecter aux clusters Big Data HDFS et principal
description: Découvrez comment vous connecter à l’instance principale SQL Server et à la passerelle HDFS/Spark pour un [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0717226ee785df568d4cea75511e65acb728c592
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532241"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Se connecter à un cluster Big Data SQL Server avec Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment se connecter à un [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] à partir d’Azure Data Studio.

## <a name="prerequisites"></a>Conditions préalables requises

- Un [cluster Big Data SQL Server 2019](deployment-guidance.md) déployé.
- [Outils de Big Data SQL Server 2019](deploy-big-data-tools.md) :
   - **Azure Data Studio**
   - **Extension SQL Server 2019**
   - **kubectl**
   - **azdata**

## <a id="master"></a> Se connecter au cluster

Pour vous connecter à un cluster Big Data avec Azure Data Studio, établissez une nouvelle connexion à l’instance principale SQL Server dans le cluster. Les étapes suivantes décrivent comment se connecter à l’instance principale avec Azure Data Studio.

1. Recherchez le point de terminaison de l’instance principale SQL Server :

   ```
   azdata bdc endpoint list -e sql-server-master
   ```

   > [!TIP]
   > Pour plus d’informations sur la façon de récupérer des points de terminaison, consultez [Récupérer des points de terminaison](deployment-guidance.md#endpoints).

1. Dans Azure Data Studio, appuyez sur **F1** > **Nouvelle connexion**.

1. Dans **Type de connexion**, sélectionnez **Microsoft SQL Server**.

1. Tapez le nom du point de terminaison que vous avez trouvé pour l’instance principale SQL Server dans la zone de texte **Nom du serveur** (par exemple : **\<IP_Address\>,31433**). 

1. Choisissez votre type d’authentification. Pour une instance principale SQL Server s’exécutant dans des clusters Big Data, seules l’**authentification Windows** et la **connexion SQL** sont prises en charge. 

1. Entrez le **nom d’utilisateur** et le **mot de passe** de la connexion SQL. Si vous utilisez l’authentification Windows, ceci n’est pas nécessaire.

   > [!TIP]
   > Par défaut, le nom d’utilisateur **SA** est désactivé durant le déploiement de clusters Big Data. Un nouvel utilisateur sysadmin est provisionné lors du déploiement avec le nom correspondant à la variable d’environnement **AZDATA_USERNAME** et le mot de passe correspondant à la variable d’environnement **AZDATA_PASSWORD** utilisée pendant le déploiement.

1. Remplacez le **Nom de la base de données** cible par une de vos bases de données relationnelles.

   ![Se connecter à l’instance principale](./media/connect-to-big-data-cluster/connect-to-cluster.png)

1. Appuyez sur **Se connecter** : le **Tableau de bord du serveur** doit apparaître.

Avec la version de février 2019 d’Azure Data Studio, la connexion à l’instance principale SQL Server vous permet également d’interagir avec la passerelle HDFS/Spark. Cela signifie que vous n’avez pas besoin d’utiliser une connexion distincte pour HDFS et Spark décrite dans la section suivante.

- L’Explorateur d’objets contient maintenant un nouveau nœud **Services de données** avec prise en charge du clic droit pour les tâches de cluster Big Data, comme la création de notebooks ou l’envoi de travaux Spark. 
- Le nœud **Services de données** contient également un dossier **HDFS** pour l’exploration de HDFS et l’exécution d’actions comme Créer une table externe ou Analyser dans le notebook.
- Le **Tableau de bord du serveur** pour la connexion contient également des onglets pour **Cluster Big Data SQL Server** et **SQL Server 2019 (préversion)** quand l’extension est installée.

   ![Nœud Services de données d’Azure Data Studio](./media/connect-to-big-data-cluster/connect-data-services-node.png)

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)], consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ?](big-data-cluster-overview.md).
