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
ms.openlocfilehash: 6092f15fe64c96ed004d352408ae6cdac034def9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47852157"
---
# <a name="connect-to-a-sql-server-always-on-availability-group-on-kubernetes"></a>Se connecter à un serveur SQL Server Always On de groupe de disponibilité sur Kubernetes

Pour vous connecter aux instances de SQL Server dans des conteneurs sur un cluster Kubernetes, créez un [service d’équilibrage de charge](http://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer). L’équilibreur de charge transmet les demandes pour l’adresse IP sur le pod qui exécute l’instance de SQL Server.

Pour vous connecter à un réplica de groupe de disponibilité, créez un service pour les types de réplicas différents. Vous pouvez voir des exemples de services pour différents types de réplicas dans [sql-server-samples](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml).

* `ag1-primary` pointe vers le réplica principal.
* `ag1-secondary-sync` pointe vers le réplica secondaire synchrone.
* `ag1-secondary-async` pointe vers un réplica secondaire asynchrone.

Si plusieurs réplicas secondaires du même type existe, Kubernetes achemine votre connexion pour les différents réplicas de manière alternée.

## <a name="create-a-load-balancer-service"></a>Créer un service d’équilibrage de charge

Pour créer un service d’équilibrage de charge pour le réplica principal, copiez `ag1-primary.yaml` de [sql-server-samples]()et mettez-le à jour pour votre groupe de disponibilité.

La commande suivante s’applique le fichier .yaml à votre cluster :

```kubectl
kubectl apply -f ag1-primary.yaml
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
