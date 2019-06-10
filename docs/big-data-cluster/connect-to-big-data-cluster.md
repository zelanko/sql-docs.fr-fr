---
title: Se connecter au maître et HDFS
titleSuffix: SQL Server big data clusters
description: Découvrez comment vous connecter à l’instance principale de SQL Server et de la passerelle HDFS/Spark pour un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 245e88034194a01908b69d545deb9fa717c19a4a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66782980"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Se connecter à un cluster SQL Server de données volumineux avec Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit comment se connecter à un cluster de données volumineuses de SQL Server 2019 (version préliminaire) à partir d’Azure Data Studio.

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
   kubectl get svc master-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Par défaut, nom de cluster les données big **mssql-cluster** , sauf si vous avez personnalisé le nom d’un fichier de configuration de déploiement. Pour plus d’informations, consultez [configurer les paramètres de déploiement pour les clusters de données volumineuses](deployment-custom-configuration.md#clustername).

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
- Le **tableau de bord Server** pour la connexion contient également des onglets pour **cluster de données volumineux de SQL Server** et **SQL Server 2019 (version préliminaire)** lorsque l’extension est installée.

   ![Nœud des Services de données Azure Data Studio](./media/connect-to-big-data-cluster/connect-data-services-node.png)

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses de SQL Server 2019, consultez [que sont les clusters de données volumineuses de SQL Server 2019](big-data-cluster-overview.md).