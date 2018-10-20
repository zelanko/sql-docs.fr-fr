---
title: Se connecter à SQL Server groupe de disponibilité AlwaysOn sur un cluster Kubernetes
description: Cet article explique comment se connecter à un groupe de disponibilité AlwaysOn
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7fcad17522f4372e696a26a99d4ce1a4af92ea15
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356100"
---
# <a name="connect-to-a-sql-server-always-on-availability-group-on-kubernetes"></a>Se connecter à un serveur SQL Server Always On de groupe de disponibilité sur Kubernetes

Pour vous connecter aux instances de SQL Server dans des conteneurs sur un cluster Kubernetes, créez un [service d’équilibrage de charge](http://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer). L’équilibreur de charge est un point de terminaison. Il conserve une adresse IP et transfère les demandes pour l’adresse IP sur le pod qui exécute l’instance de SQL Server.

Pour vous connecter à un réplica de groupe de disponibilité, créez un service pour les types de réplicas différents. Vous pouvez voir des exemples de services pour différents types de réplicas dans [sql-server-samples/groupe de disponibilité-services.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

* `ag1-primary` pointe vers le réplica principal.
* `ag1-secondary` pointe vers un réplica secondaire.

Si plus d’un réplica secondaire, Kubernetes achemine votre connexion pour les différents réplicas de manière alternée.

## <a name="create-a-load-balancer-service"></a>Créer un service d’équilibrage de charge

Pour créer des services d’équilibrage de charge pour le serveur principal et les réplicas, copiez [ `ag1-services.yaml` ](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) de [sql-server-samples](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-file) et mettez-le à jour pour votre groupe de disponibilité.

La commande suivante applique la configuration de le `.yaml` fichier au cluster :

```kubectl
kubectl apply -f ag1-services.yaml --namespace ag1
```

## <a name="get-the-ip-address-for-your-load-balancer-service"></a>Obtenir l’adresse IP pour votre service d’équilibrage de charge

Pour obtenir l’adresse IP de l’équilibrage de charge pour votre service d’équilibrage de charge, exécutez

```kubectl
kubectl get services
```

Identifier l’adresse IP du service que vous souhaitez vous connecter.

## <a name="connect-to-primary-replica"></a>Se connecter au réplica principal

Pour vous connecter au réplica principal avec l’authentification SQL, utilisez la `sa` compte, la valeur de `sapassword` à partir de la clé secrète que vous avez créé et que cette adresse IP.

Exemple :

```cmd
sqlcmd -S <0.0.0.0> -U sa -P "<MyC0m9l&xP@ssw0rd>"
```

## <a name="next-steps"></a>Étapes suivantes

[Gérer le groupe de disponibilité de SQL Server sur un cluster Kubernetes](sql-server-linux-kubernetes-manage.md)

[Groupe de disponibilité de SQL Server sur un cluster Kubernetes](sql-server-ag-kubernetes.md)
