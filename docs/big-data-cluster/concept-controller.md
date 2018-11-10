---
title: Qu’est le contrôleur de cluster de données volumineuses de SQL Server ? | Microsoft Docs
description: Cet article décrit le contrôleur d’un cluster de données volumineuses de SQL Server 2019.
author: mihaelablendea
ms.author: mihaelab
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: abf8c174379ad444cd29b5115240ad7c404b2c4b
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221515"
---
# <a name="what-is-the-sql-server-big-data-clusters-controller"></a>Qu’est le contrôleur de clusters de données volumineuses de SQL Server ?

Le contrôleur héberge la logique de base pour déployer et gérer un cluster de données volumineux. Il s’occupe de toutes les interactions avec Kubernetes, les instances de SQL Server qui font partie du cluster et d’autres composants tels que HDFS et Spark. 

Le service de contrôleur fournit les fonctionnalités principales suivantes :

- Gérer le cycle de vie du cluster : bootstrap du cluster & Supprimer, mettre à jour des configurations
- Gérer les instances de SQL Server maîtres
- Gérer des pools de stockage, de données et de calcul
- Exposer des outils de surveillance pour observer l’état du cluster
- Exposer des outils de dépannage pour détecter et corriger les problèmes inattendus
- Gérer la sécurité du cluster : Vérifiez les points de terminaison de cluster sécurisé, gérer les utilisateurs et les rôles, configurez les informations d’identification pour la communication intra-cluster
- Gérer le flux de travail des mises à niveau afin qu’ils sont implémentés en toute sécurité (non disponible dans les CTP 2.1)
- Gérer une haute disponibilité et récupération d’urgence pour les services avec état dans le cluster (non disponible dans les CTP 2.1)

## <a name="deploying-the-controller-service"></a>Déploiement du service de contrôleur

Le contrôleur est déployé et hébergé dans le même espace de noms Kubernetes où le client souhaite créer un cluster de données volumineux. Ce service est installé par un administrateur de Kubernetes au cours de bootstrap du cluster, à l’aide de l’utilitaire de ligne de commande mssqlctl :

```bash
mssqlctl create cluster <name of your cluster>
```

Le flux de travail buildout sera à disposition sur Kubernetes un cluster de données volumineuses de SQL Server entièrement fonctionnel qui inclut tous les composants décrits dans le [vue d’ensemble](big-data-cluster-overview.md) article. Le flux de travail d’amorçage crée tout d’abord le service de contrôleur et une fois que cela est déployé, le service de contrôleur coordonne l’installation et la configuration du reste de la partie de services de pools de stockage, calcul, données et master.

## <a name="managing-the-cluster-through-the-controller-service"></a>La gestion du cluster via le service de contrôleur
Vous pouvez gérer le cluster purement via le service de contrôleur à l’aide `mssqlctl` API ou le portail d’administration de cluster qui est hébergé au sein du cluster. Si vous déployez des objets supplémentaires comme pods Kubernetes dans le même espace de noms, ils ne sont pas gérés ou surveillées par le service de contrôleur.

Le contrôleur et les objets Kubernetes (jeux avec état, pods, secrets, etc.) créés pour un cluster de données volumineux se trouvent dans un espace de noms Kubernetes dédié. Le service du contrôleur sera être autorisé par l’administrateur de cluster Kubernetes pour gérer toutes les ressources au sein de cet espace de noms.  La stratégie RBAC pour ce scénario est configurée automatiquement dans le cadre du déploiement initial du cluster à l’aide `mssqlctl`. 

### <a name="mssqlctl"></a>mssqlctl

`mssqlctl` est un utilitaire de ligne de commande écrit dans Python qui permet aux administrateurs de cluster à démarrer et gérer des clusters de données volumineuses via les API REST exposées par le service de contrôleur.

### <a name="cluster-administration-portal"></a>Portail d’administration du cluster

Une fois que le service de contrôleur est en cours d’exécution, l’administrateur de cluster permettre utiliser le portail d’administration de Cluster pour surveiller la progression du déploiement, de détecter et de résoudre les problèmes avec les services au sein du cluster. 

## <a name="monitoring-and-troubleshooting-the-controller-service"></a>Surveillance et dépannage du service de contrôleur

À venir...

## <a name="controller-service-security"></a>Sécurité du contrôleur de service
Toutes les communications vers le service de contrôleur sont effectuée via l’API REST sur HTTPS. Un certificat auto-signé sera automatiquement généré pour vous au moment de l’amorçage. 

Authentification pour le point de terminaison de service de contrôleur est basée sur le nom d’utilisateur et mot de passe. Ces informations d’identification sont approvisionnées au moment de démarrage du cluster à l’aide de l’entrée pour les variables d’environnement `CONTROLLER_USERNAME` et `CONTROLLER_PASSWORD`.
```

> [!NOTE]
> You must provide a password that is in compliance with [SQL Server password complexity requirements](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017).

## Next steps

To learn more about the SQL Server big data clusters, see the following overview:

- [What are SQL Server 2019 big data clusters?](big-data-cluster-overview.md)
