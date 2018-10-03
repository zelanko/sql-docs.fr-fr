---
title: Gérer un groupe de disponibilité SQL Server Always On Kubernetes
description: Cet article explique comment gérer un SQL Server groupe de disponibilité AlwaysOn dans Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8ad318c0f0967f26f5cfdf2c5ad9af2d94323bf0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622837"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>Gérer SQL Server Always On Kubernetes du groupe de disponibilité

Pour gérer un groupe de disponibilité AlwaysOn sur Kubernetes, créez un manifeste et appliquez-le au cluster. Le manifeste est un `.yaml` fichier.  

Les exemples de cet article s’appliquent à tous les clusters Kubernetes. Les scénarios dans ces exemples sont appliquées sur un cluster sur Azure Kubernetes Service.

Voir un exemple du déploiement de bout en bout dans [ce didacticiel](tutorial-sql-server-ag-kubernetes.md).

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>Basculer - groupe de disponibilité de SQL Server sur Kubernetes

Pour basculer sur un réplica principal de groupe de disponibilité vers un autre nœud dans Kubernetes, utilisez une tâche. Cet article identifie les variables d’environnement pour cette tâche.

L’exemple suivant d’un fichier manifeste décrit un travail pour basculer manuellement de travail pour un groupe de disponibilité sur un réplica de Kubernetes. Copiez le contenu de l’exemple dans un nouveau fichier appelé `failover.yaml`.

[Failover.yaml](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/templates/failover.yaml)

Pour déployer le travail, utilisez `Kubectl`.

```azurecli
kubectl apply -f failover.yaml
```

Lorsque vous appliquez le fichier manifeste, Kubernetes exécute la tâche. Lorsque le travail s’exécute, le superviseur choisit un nouveau leader et déplace le réplica principal à l’instance de SQL Server du responsable.

Après avoir exécuté le travail, supprimez-le. L’objet de traitement dans Kubernetes reste après la saisie semi-automatique afin que vous puissiez afficher son état. Vous devez supprimer manuellement les anciens travaux après noter leur état. La suppression de la tâche supprime également les journaux de Kubernetes. Si vous ne supprimez pas le travail, les tâches de basculement futures échoue, sauf si vous modifiez le nom du travail et le sélecteur de pod. Pour plus d’informations, consultez [travaux - s’exécute jusqu'à achèvement](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/).

## <a name="rotate-credentials"></a>Faire pivoter les informations d’identification

Faire pivoter les informations d’identification pour mettre à jour l’association de sécurité et la clé principale.

Copie le [creds.yaml pivoter](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script) utiliser localement `kubectl` pour l’appliquer à votre cluster.

```azurecli
kubectl apply -f rotate-creds.yaml
```

## <a name="next-steps"></a>Étapes suivantes

[Accès du tableau de bord Kubernetes avec Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[Groupe de disponibilité de SQL Server sur un cluster Kubernetes](sql-server-ag-kubernetes.md)
