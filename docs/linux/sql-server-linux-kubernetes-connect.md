---
title: Se connecter à un groupe de disponibilité Always On SQL Server sur un cluster Kubernetes
description: Cet article explique comment se connecter à un groupe de disponibilité Always On
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f05bc51f587723414d3b0a4090fe2b27ad5fb837
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67952605"
---
# <a name="connect-to-a-sql-server-always-on-availability-group-on-kubernetes"></a>Se connecter à un groupe de disponibilité Always On SQL Server sur Kubernetes

Pour vous connecter à des instances SQL Server dans des conteneurs sur un cluster Kubernetes, créez un [service d’équilibrage de charge](https://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer). L’équilibreur de charge est un point de terminaison. Il détient une adresse IP et transfère les requêtes pour l’adresse IP au pod qui exécute l’instance SQL Server.

Pour vous connecter à un réplica de groupe de disponibilité, créez un service pour différents types de réplicas. Vous pouvez voir des exemples de services pour différents types de réplicas dans [sql-server-samples/ag-services.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

* `ag1-primary` pointe sur le réplica principal.
* `ag1-secondary` pointe vers n’importe quel réplica secondaire.

Dans le cas de plusieurs réplicas secondaires, Kubernetes route votre connexion aux différents réplicas en mode tourniquet (round robin).

## <a name="create-a-load-balancer-service"></a>Créer un service d’équilibrage de charge

Pour créer des services d’équilibrage de charge pour le réplica principal et les réplicas secondaires, copiez [`ag1-services.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) à partir de [sql-server-samples](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-file) et mettez-le à jour pour votre groupe de disponibilité.

La commande suivante applique la configuration du fichier `.yaml` au cluster:

```kubectl
kubectl apply -f ag1-services.yaml --namespace ag1
```

## <a name="get-the-ip-address-for-your-load-balancer-service"></a>Obtenir l’adresse IP de votre service d’équilibrage de charge

Pour obtenir l’adresse IP de l’équilibreur de charge de votre service d’équilibrage de charge, exécutez

```kubectl
kubectl get services
```

Identifiez l’adresse IP du service auquel vous souhaitez vous connecter.

## <a name="connect-to-primary-replica"></a>Se connecter au réplica principal

Pour vous connecter au réplica principal avec l’authentification SQL, utilisez le compte `sa`, la valeur de `sapassword` du secret que vous avez créé et cette adresse IP.

Par exemple :

```cmd
sqlcmd -S <0.0.0.0> -U sa -P "<MyC0m9l&xP@ssw0rd>"
```

## <a name="next-steps"></a>Étapes suivantes

[Gérer un groupe de disponibilité SQL Server sur un cluster Kubernetes](sql-server-linux-kubernetes-manage.md)

[Groupe de disponibilité SQL Server sur le cluster Kubernetes](sql-server-ag-kubernetes.md)
