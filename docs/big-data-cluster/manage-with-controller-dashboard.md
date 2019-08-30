---
title: Gérer le cluster SQL Server Big Data avec le tableau de bord du contrôleur
titleSuffix: Manage SQL Server big data cluster with controller dashboard
description: Utilisez un notebook d’Azure Data Studio pour gérer et dépanner un cluster Big Data.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 08/29/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5fadb9b069e6f70cb780e6dc69295f63330a683a
ms.sourcegitcommit: 71fac5fee00e0eca57e555f44274dd7e08d47e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160721"
---
# <a name="manage-big-data-clusters-for-sql-server-controller-dashboard"></a>Gérer les clusters Big Data pour le tableau de bord du contrôleur SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

En plus de **azdata** et du bloc-notes État du cluster, il existe une autre façon d’afficher l’état d’un cluster SQL Server Big Data. Vous pouvez maintenant ajouter le SQL Server contrôleur de cluster Big Data via les **connexions** Viewlet. Cela vous permet de disposer d’un tableau de bord pour afficher l’intégrité du cluster.

![tableau de bord](media/manage-with-controller-dashboard/controller-dashboard.png)
## <a name="prerequisites"></a>Prérequis

Les conditions préalables suivantes sont requises pour lancer le bloc-notes:

* Version la plus récente de la [build Azure Data Studio Insiders](https://docs.microsoft.com/sql/big-data-cluster/deploy-big-data-tools?view=sqlallproducts-download-and-install-azure-data-studio-sql-server-2019-release-candidate-rc)
* Extension [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] installée dans Azure Data Studio

En plus des éléments ci-dessus, SQL Server Cluster Big Data de 2019 requiert également:

* **azdata**
    - [Gestionnaire de package Linux](deploy-install-azdata-linux-package.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Interface de ligne de commande Azure](/cli/azure/install-azure-cli)


## <a name="add-sql-server-big-data-cluster-controller"></a>Ajouter SQL Server Big Data contrôleur de cluster

1. Cliquez sur la vue connexions dans le volet gauche.
2. En bas de la vue connexions, cliquez sur **SQL Server Clusters Big Data** pour la développer.
3. Cliquez sur **ajouter SQL Server Big Data contrôleur de cluster**, une nouvelle boîte de dialogue s’ouvre.

## <a name="add-new-controller"></a>Ajouter un nouveau contrôleur

1. Ajoutez le nom de votre cluster.
2. Ajoutez l’URL de votre service de gestion de cluster. Vous pouvez le trouver dans la table points de terminaison de service de votre tableau de bord BDC ou demander à votre administrateur de cluster.
3. Ajoutez votre nom d’utilisateur et votre mot de passe.

## <a name="launch-controller-dashboard"></a>Lancer le tableau de bord du contrôleur

1. Une fois que vous avez ajouté votre contrôleur, vous pouvez l’afficher sous SQL Server Clusters Big Data.
2. Pour lancer le tableau de bord, cliquez avec le bouton droit sur le contrôleur, puis cliquez sur **gérer**.

## <a name="controller-dashboard"></a>Tableau de bord du contrôleur

1. Le tableau de bord du contrôleur contient 3 composants principaux:

    - **Barre d’outils** en haut qui contient des actions pour le tableau de bord.
    - **Volet de navigation** sur la gauche, qui passe aux différents affichages du tableau de bord.
    - **Vue** couvrant la majeure partie de la page.

2. Sur la page **vue d’ensemble du cluster Big Data** , vous pouvez voir:

    - **Propriétés de cluster** pour afficher des informations sur votre cluster.
    - **Vue** d’ensemble du cluster pour obtenir une vue d’ensemble générale de tous les composants de cluster et ceux qui ne sont pas intègres
    - **Points de terminaison de service** pour la copie ou l’accès à différents services au sein de votre cluster SQL Server Big Data.

3. Dans le **volet de navigation,** vous pouvez voir la liste des services, puis cliquer sur l’un d’entre eux pour afficher des détails supplémentaires sur le cluster. Il s’agit des mêmes affichages lorsque vous cliquez sur un service dans **vue d’ensemble du cluster.**

4. Chaque vue sous les **Détails du cluster** se compose des mêmes composants d’interface utilisateur:

    - **Détails** de l’état d’intégrité qui partagent l’État et l’état d’intégrité du composant.
    - **Les métriques et les journaux** pour afficher des métriques et des journaux supplémentaires via Grafana et Kibana.

1. Si vous affichez un composant qui n’est pas sain, cliquez sur dépanner dans la barre d’outils pour lancer un livre Jupyter contenant un bloc-notes pour vous aider à diagnostiquer le problème.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur le contrôleur, consultez [notre documentation](concept-controller.md)sur le contrôleur.