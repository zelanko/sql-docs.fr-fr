---
title: Qu’est le contrôleur ?
titleSuffix: SQL Server 2019 big data clusters
description: Cet article décrit le contrôleur d’un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: mihaelablendea
ms.author: mihaelab
manager: craigg
ms.date: 12/07/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 84162981b68a309f4a21efc0c0610837be308ddb
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241280"
---
# <a name="what-is-the-controller-on-a-sql-server-2019-big-data-cluster"></a>Qu’est le contrôleur sur un cluster de données volumineux de SQL Server 2019 ?

Le contrôleur héberge la logique de base pour déployer et gérer un cluster de données volumineux. Il s’occupe de toutes les interactions avec Kubernetes, les instances de SQL Server qui font partie du cluster et d’autres composants tels que HDFS et Spark. 

Le service de contrôleur fournit les fonctionnalités principales suivantes :

- Gérer le cycle de vie du cluster : bootstrap du cluster & Supprimer, mettre à jour des configurations
- Gérer les instances de SQL Server maîtres
- Gérer des pools de stockage, de données et de calcul
- Exposer des outils de surveillance pour observer l’état du cluster
- Exposer des outils de dépannage pour détecter et corriger les problèmes inattendus
- Gérer la sécurité du cluster : Vérifiez les points de terminaison de cluster sécurisé, gérer les utilisateurs et les rôles, configurez les informations d’identification pour la communication intra-cluster
- Gérer le flux de travail des mises à niveau afin qu’ils sont implémentés en toute sécurité (non disponible dans les CTP 2.2)
- Gérer une haute disponibilité et récupération d’urgence pour les services avec état dans le cluster (non disponible dans les CTP 2.2)

## <a name="deploying-the-controller-service"></a>Déploiement du service de contrôleur

Le contrôleur est déployé et hébergé dans le même espace de noms Kubernetes où le client souhaite créer un cluster de données volumineux. Ce service est installé par un administrateur de Kubernetes au cours de bootstrap du cluster, à l’aide de l’utilitaire de ligne de commande mssqlctl :

```bash
mssqlctl create cluster <name of your cluster>
```

Le flux de travail buildout sera à disposition sur Kubernetes un cluster de données volumineuses de SQL Server entièrement fonctionnel qui inclut tous les composants décrits dans le [vue d’ensemble](big-data-cluster-overview.md) article. Le flux de travail d’amorçage crée tout d’abord le service de contrôleur et une fois que cela est déployé, le service de contrôleur coordonne l’installation et la configuration du reste de la partie de services de pools de master, de calcul, de données et de stockage.

## <a name="managing-the-cluster-through-the-controller-service"></a>La gestion du cluster via le service de contrôleur

Vous pouvez gérer le cluster purement via le service de contrôleur à l’aide `mssqlctl` API ou le portail d’administration de cluster qui est hébergé au sein du cluster. Si vous déployez des objets supplémentaires comme pods Kubernetes dans le même espace de noms, ils ne sont pas gérés ou surveillées par le service de contrôleur.

Le contrôleur et les objets Kubernetes (jeux avec état, pods, secrets, etc.) créés pour un cluster de données volumineux se trouvent dans un espace de noms Kubernetes dédié. Le service du contrôleur sera être autorisé par l’administrateur de cluster Kubernetes pour gérer toutes les ressources au sein de cet espace de noms.  La stratégie RBAC pour ce scénario est configurée automatiquement dans le cadre du déploiement initial du cluster à l’aide `mssqlctl`. 

### <a name="mssqlctl"></a>mssqlctl

`mssqlctl` est un utilitaire de ligne de commande écrit dans Python qui permet aux administrateurs de cluster à démarrer et gérer des clusters de données volumineuses via les API REST exposées par le service de contrôleur.

### <a name="cluster-administration-portal"></a>Portail d’Administration de cluster

Une fois que le service de contrôleur est en cours d’exécution, l’administrateur de cluster peut utiliser le [portail d’Administration de Cluster](cluster-admin-portal.md) pour surveiller la progression du déploiement, détecter et résoudre les problèmes avec les services au sein du cluster.

## <a name="controller-service-security"></a>Sécurité du contrôleur de service

Toutes les communications vers le service de contrôleur sont effectuée via l’API REST sur HTTPS. Un certificat auto-signé sera automatiquement généré pour vous au moment de l’amorçage. 

Authentification pour le point de terminaison de service de contrôleur est basée sur le nom d’utilisateur et mot de passe. Ces informations d’identification sont approvisionnées au moment de démarrage du cluster à l’aide de l’entrée pour les variables d’environnement `CONTROLLER_USERNAME` et `CONTROLLER_PASSWORD`.

> [!NOTE]
> Vous devez fournir un mot de passe qui est en conformité avec [exigences de complexité de mot de passe SQL Server](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez la présentation suivante :

- [Quelles sont les clusters SQL Server 2019 big data ?](big-data-cluster-overview.md)
