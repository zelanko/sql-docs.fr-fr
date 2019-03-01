---
title: Portail d’administration du cluster
titleSuffix: SQL Server 2019 big data clusters
description: Découvrez comment utiliser le portail d’administration de cluster pour surveiller les clusters de données volumineuses de SQL Server 2019 (version préliminaire).
author: yualan
ms.author: alayu
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 9048de9c5f1a1241a6d7049f8eeb15efef87cabb
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017855"
---
# <a name="how-to-use-the-cluster-administration-portal-to-monitor-a-sql-server-big-data-cluster"></a>Comment utiliser le portail d’administration de cluster pour surveiller un cluster de données volumineux de SQL Server

Si vous souhaitez analyser ou résoudre les problèmes de votre cluster de données volumineux de SQL Server 2019 (version préliminaire), utilisez le portail d’administration de cluster.

Le portail d’administration de cluster vous permet de :
- Afficher rapidement le nombre de pods en cours d’exécution et les problèmes
- Surveiller le statut de déploiement
- Points de terminaison service disponible
- Contrôleur d’affichage et l’instance principale de SQL Server
- Explorer plus d’informations sur les pods, y compris l’accès aux journaux de Kibana et des tableaux de bord Grafana

## <a name="access-the-cluster-administration-portal"></a>Accéder au portail d’administration de cluster

Suivez le [Guide de démarrage rapide pour déployer votre cluster big data](quickstart-big-data-cluster-deploy.md) jusqu'à ce que vous arriviez à la **portail d’administration de cluster** section. Une fois que vous avez le cluster de données volumineux en cours d’exécution avec mssqlctl, suivez ces instructions :

Une fois que le pod de contrôleur est en cours d’exécution, vous pouvez utiliser le portail d’administration de cluster pour surveiller le déploiement. Vous pouvez accéder au portail à l’aide de l’externe IP adresse et numéro de port pour le `endpoint-service-proxy` (par exemple : **https://\<ip-address\>: 30777/portail**). Informations d’identification pour accéder au portail d’administration est les valeurs de `CONTROLLER_USERNAME` et `CONTROLLER_PASSWORD` variables d’environnement fournis ci-dessus.

> [!NOTE]
> Pour CTP 2.3, il est un avertissement de sécurité lorsque vous accédez à la page web dans la mesure où il est à l’aide de certificats SSL générés automatiquement.

## <a name="overview"></a>Vue d'ensemble

![vue d'ensemble](./media/cluster-admin-portal/portal-overview.png)

Lorsque vous entrez tout d’abord le portail, vous pouvez rapidement afficher le nombre de pods en cours d’exécution :
- Contrôleur
- Instance de master
- Pool de calcul
- Pool de stockage
- Pool de données

S’il existe des problèmes, vous pouvez ouvrir un lien vers les problèmes connus. Vous pouvez utiliser le volet de navigation de gauche pour accéder au pool spécifique, s’il existe un problème.

## <a name="deployment"></a>Déploiement

![Déploiement](./media/cluster-admin-portal/portal-deployment.png)

Pour surveiller votre déploiement, cliquez sur l’onglet déploiement sur la gauche. Vous pouvez afficher une arborescence de votre déploiement, et s’il existe des problèmes dans le déploiement.

## <a name="service-endpoints"></a>Points de terminaison de service

![points de terminaison](./media/cluster-admin-portal/portal-endpoints.png)

Vous pouvez afficher les points de terminaison de service disponible en cliquant sur l’onglet points de terminaison dans le volet de navigation de gauche.

Cela inclut des liens vers le point de terminaison de Spark, tableau de bord Grafana, et les journaux de Kibana.

## <a name="controller"></a>Contrôleur

![Contrôleur](./media/cluster-admin-portal/portal-controller.png)

Le contrôleur montre tous les pods liés au contrôleur. Plus d’informations sur le contrôleur [ici.](concept-controller.md)

Pour en savoir plus d’informations supplémentaires sur chaque bloc, vous pouvez cliquer sur **métriques** colonne afin d’afficher des tableaux de bord Grafana.

Pour en savoir plus sur les journaux pour des pods avec des problèmes, vous pouvez cliquer sur le **journaux** colonne.

## <a name="master-instance"></a>Instance de master

![points de terminaison](./media/cluster-admin-portal/portal-master.png)

L’Instance principale montre tous les pods liés à l’instance principale de SQL Server. Plus d’informations sur l’instance principale de SQL Server [ici.](concept-master-instance.md)

Pour en savoir plus d’informations supplémentaires sur chaque bloc, vous pouvez cliquer sur **métriques** colonne afin d’afficher des tableaux de bord Grafana.

Pour en savoir plus sur les journaux pour des pods avec des problèmes, vous pouvez cliquer sur le **journaux** colonne.

## <a name="pool-and-pod-pages"></a>Pool et les Pages de Pod

![Pool](./media/cluster-admin-portal/portal-data-pool.png)

Sur chaque page du pool (calcul, stockage et données), vous pouvez explorer chacune des pages de pod en cliquant sur **par défaut**

![pod](./media/cluster-admin-portal/portal-data-default-pool.png)

Cela indique un fil d’Ariane en haut de l’exploration de chemin d’accès.

Pour en savoir plus d’informations supplémentaires sur chaque bloc, vous pouvez cliquer sur **métriques** colonne afin d’afficher des tableaux de bord Grafana.

Pour en savoir plus sur les journaux pour des pods avec des problèmes, vous pouvez cliquer sur le **journaux** colonne.

Pour en savoir plus sur chaque pool :
- [pool de calcul](concept-compute-pool.md)
- [pool de stockage](concept-storage-pool.md)
- [pool de données](concept-data-pool.md)

## <a name="about-page"></a>Sur la Page

![à propos de](./media/cluster-admin-portal/portal-about.png)

Ici, vous pouvez afficher plus d’informations sur votre cluster telles que les numéros de version différents, les conteneurs et un lien vers la documentation.

## <a name="next-steps"></a>Étapes suivantes

En plus du portail d’administration de cluster, vous pouvez également exécuter plusieurs commandes Kubernetes utiles pour Explorer l’état et l’intégrité de votre cluster. Pour plus d’informations, consultez [commandes Kubectl pour la surveillance et dépannage des clusters de données volumineuses de SQL Server](cluster-troubleshooting-commands.md).

Pour en savoir plus sur les clusters de données volumineuses de SQL Server 2019, consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).
