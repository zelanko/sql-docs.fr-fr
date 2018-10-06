---
title: Surveillance de Cluster à l’aide du portail d’Administration de Cluster | Microsoft Docs
description: ''
author: yualan
ms.author: alayu
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 3ae85c9e9078b91589b828d1bee9d3218b5316cc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796090"
---
# <a name="introduction-to-the-cluster-administration-portal"></a>Introduction au portail d’Administration de Cluster
Si vous souhaitez analyser ou résoudre les problèmes de votre cluster de données volumineux de SQL Server, utilisez le portail d’administration de cluster. 

Le portail d’administration de cluster vous permet de :
- Afficher rapidement le nombre de pods en cours d’exécution et les problèmes
- Surveiller le statut de déploiement
- Points de terminaison service disponible
- Contrôleur d’affichage et l’instance principale de SQL Server
- Explorer plus d’informations sur les pods, y compris l’accès aux journaux de Kibana et des tableaux de bord Grafana

## <a name="access-the-cluster-administration-portal"></a>Accéder au portail d’administration de cluster
Suivez le [Guide de démarrage rapide pour déployer votre cluster big data](quickstart-big-data-cluster-deploy.md) jusqu'à ce que vous arriviez à la **portail d’administration de cluster** section. Une fois que vous avez le cluster de données volumineux en cours d’exécution avec mssqlctl, suivez ces instructions :

Une fois que le pod de contrôleur est en cours d’exécution, vous pouvez utiliser le portail d’administration de cluster pour surveiller le déploiement. Vous pouvez accéder au portail à l’aide de l’externe IP adresse et numéro de port pour le `service-proxy-lb` (par exemple : **https://\<ip-address\>: 30777**). Informations d’identification pour accéder au portail d’administration est les valeurs de `CONTROLLER_USERNAME` et `CONTROLLER_PASSWORD` variables d’environnement fournis ci-dessus.
> [!NOTE]
> Il va être un avertissement de sécurité lorsque vous accédez à la page web dans la mesure où nous utilisons des certificats SSL générés automatiquement. Dans les futures versions, nous fournirons la capacité de fournir vos propres certificats auto-signés.

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

![POD](./media/cluster-admin-portal/portal-data-default-pool.png)

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
