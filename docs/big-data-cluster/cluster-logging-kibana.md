---
title: Extraire les journaux de cluster avec le tableau de bord Kibana
titleSuffix: SQL Server Big Data Clusters
description: Analyse du cluster avec le tableau de bord Kibana sur le cluster Big Data SQL Server 2019.
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 10/01/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 66b405f020728c0ed7040a712d56bcadc3180e38
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92378414"
---
# <a name="check-out-cluster-logs--with-kibana-dashboard"></a>Extraire les journaux de cluster avec le tableau de bord Kibana

Cet article explique comment surveiller une application à l’intérieur d’un cluster Big Data SQL Server.

## <a name="prerequisites"></a>Prérequis

- [Cluster Big Data SQL Server 2019](deployment-guidance.md)
- [Utilitaire de ligne de commande azdata](deploy-install-azdata.md)

## <a name="capabilities"></a>Fonctionnalités

Dans SQL Server 2019, vous pouvez créer, supprimer, décrire, initialiser, exécuter et mettre à jour votre application. Le tableau suivant décrit les commandes de déploiement d’application que vous pouvez utiliser avec **azdata** .

|Commande |Description |
|:---|:---|
|`azdata bdc endpoint list` | Lister les points de terminaison du cluster Big Data. |


Vous pouvez utiliser l’exemple suivant pour répertorier le point de terminaison du **tableau de bord Kibana** :

```bash
azdata bdc endpoint list --endpoint-name logsui 
```

La sortie vous donnera le point de terminaison, que vous pouvez utiliser pour vous connecter en utilisant le nom d’utilisateur et le mot de passe de votre cluster. 

![Tableau de bord Kibana](media/big-data-cluster-monitor-cluster/kibana-dashboard-endpoint.png)


Le lien vers un tableau de bord Kibana :

![Tableau de bord kibana](./media/view-cluster-status/kibana-dashboard.png)

> [!NOTE]
> L’(ancien) navigateur Microsoft Edge étant incompatible avec Kibana, vous devez utiliser le navigateur Chromium pour que le tableau de bord s’affiche correctement. Une page vide s’affiche lors du chargement des tableaux de bord à l’aide d’un navigateur non pris en charge. Examinez ici les navigateurs pris en charge pour Kibana.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ?](big-data-cluster-overview.md).
