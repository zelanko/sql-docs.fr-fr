---
title: Qu’est-ce que le contrôleur?
titleSuffix: SQL Server big data clusters
description: Cet article décrit le contrôleur d’un cluster SQL Server 2019 Big Data (version préliminaire).
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e984c3dced4bde713ac98d67c22481e54491cd68
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419539"
---
# <a name="what-is-the-controller-on-a-sql-server-big-data-cluster"></a>Qu’est-ce que le contrôleur sur un cluster SQL Server Big Data?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Le contrôleur héberge la logique principale pour le déploiement et la gestion d’un cluster Big Data. Elle prend en charge toutes les interactions avec Kubernetes, SQL Server instances qui font partie du cluster et d’autres composants tels que HDFS et Spark.

Le service de contrôleur fournit les fonctionnalités de base suivantes:

- Gérer le cycle de vie du cluster: démarrage du cluster & supprimer, mettre à jour les configurations
- Gérer les instances de SQL Server principales
- Gérer les pools de calcul, de données et de stockage
- Exposer les outils de surveillance pour observer l’état du cluster
- Exposer les outils de dépannage pour détecter et réparer les problèmes inattendus
- Gérer la sécurité du cluster:
  - Garantir la sécurité des points de terminaison de cluster
  - Gérer les utilisateurs et les rôles
  - Configurer les informations d’identification pour la communication intra-cluster

## <a name="deploying-the-controller-service"></a>Déploiement du service de contrôleur

Le contrôleur est déployé et hébergé dans le même espace de noms Kubernetes où le client veut créer un cluster Big Data. Ce service est installé par un administrateur Kubernetes lors du démarrage du cluster, à l’aide de l’utilitaire de ligne de commande **azdata** . Pour plus d’informations, consultez [prise en main des clusters de SQL Server Big Data](deploy-get-started.md).

Le flux de travail structure sera mis en page par-dessus Kubernetes un cluster SQL Server entièrement fonctionnel Big Data qui comprend tous les composants décrits dans l’article [vue d’ensemble](big-data-cluster-overview.md) . Le flux de travail de démarrage crée d’abord le service de contrôleur et, une fois celui-ci déployé, le service de contrôleur coordonne l’installation et la configuration du reste des services dans les pools de stockage, de calcul, de données et de maître.

## <a name="managing-the-cluster-through-the-controller-service"></a>Gestion du cluster par le biais du service de contrôleur

Vous pouvez gérer le cluster par le biais du service de contrôleur à l’aide des commandes **azdata** . Si vous déployez des objets Kubernetes supplémentaires comme des Pod dans le même espace de noms, ils ne sont pas gérés ou contrôlés par le service de contrôleur. Vous pouvez également utiliser des commandes **kubectl** pour gérer le cluster au niveau Kubernetes. Pour plus d’informations, consultez [surveillance et résolution des problèmes de SQL Server des clusters Big Data](cluster-troubleshooting-commands.md).

Le contrôleur et les objets Kubernetes (ensembles avec état, gousses, secrets, etc.) créés pour un cluster Big Data résident dans un espace de noms Kubernetes dédié. Le service de contrôleur sera autorisé par l’administrateur de cluster Kubernetes à gérer toutes les ressources au sein de cet espace de noms.  La stratégie RBAC pour ce scénario est configurée automatiquement dans le cadre du déploiement initial du cluster à l’aide de **azdata**.

### <a name="azdata"></a>azdata

**azdata** est un utilitaire de ligne de commande écrit en Python qui permet aux administrateurs de clusters de démarrer et de gérer des clusters Big Data via les API REST exposées par le service de contrôleur.

## <a name="controller-service-security"></a>Sécurité du service de contrôleur

Toutes les communications vers le service de contrôleur sont effectuées via une API REST sur HTTPs. Un certificat auto-signé est automatiquement généré pour vous au moment de l’amorçage. 

L’authentification auprès du point de terminaison du service de contrôleur est basée sur le nom d’utilisateur et le mot de passe. Ces informations d’identification sont approvisionnées au moment de l’amorçage du cluster à l’aide `CONTROLLER_USERNAME` de `CONTROLLER_PASSWORD`l’entrée pour les variables d’environnement et.

> [!NOTE]
> Vous devez fournir un mot de passe qui est conforme aux [exigences de complexité du mot de SQL Server](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters SQL Server Big Data, consultez les ressources suivantes:

- [Que sont les clusters SQL Server 2019 Big Data?](big-data-cluster-overview.md)
- [Atelier Architecture des clusters de Big Data Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
