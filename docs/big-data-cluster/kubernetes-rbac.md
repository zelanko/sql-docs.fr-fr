---
title: Contrôle RBAC Kubernetes
titleSuffix: SQL Server big data clusters
description: Cet article explique comment Clusters Big Data SQL Server utilise le contrôle RBAC avec Kubernetes.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5d2e3f379402f16f32020f9cd34103919f13a30c
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552974"
---
# <a name="kubernetes-rbac-model--impact-on-users-managing-bdc"></a>Modèle RBAC Kubernetes et impact sur les utilisateurs qui gèrent des clusters Big Data

La section suivante décrit les autorisations requises pour les utilisateurs qui gèrent des clusters Big Data.

> [!NOTE]
> Pour des ressources supplémentaires sur le modèle RBAC Kubernetes, consultez [Utilisation de l’autorisation RBAC – Kubernetes](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) et [Utilisation du contrôle RBAC pour définir et appliquer des autorisations – OpenShift](https://docs.openshift.com/container-platform/4.4/authentication/using-rbac.html).

## <a name="role-required-for-deployment"></a>Rôle nécessaire pour le déploiement

Clusters Big Data utilise des comptes de service (par exemple, `sa-mssql-controller` ou `master`) pour orchestrer le provisionnement des pods, des services, de la haute disponibilité, de la surveillance, etc. des clusters. Lorsque le déploiement Clusters Big Data démarre (par exemple, `azdata bdc create`), `azdata` effectue les opérations suivantes :

1. Il vérifie si l’espace de noms fourni existe.
2. S’il n’existe pas, il en crée un et applique l’étiquette `MSSQL_CLUSTER`.
3. Il crée le compte de service `sa-mssql-controller`.
4. Il crée un rôle de `<namespaced>-admin` possédant des autorisations complètes sur l’espace de noms ou le projet, mais pas d’autorisations au niveau du cluster.
5. Il crée une attribution au rôle pour ce compte de service.

Une fois ces étapes effectuées, les pods du plan de contrôle sont provisionnés et le compte de service déploie le reste du cluster Big Data.  

Par conséquent, l’utilisateur qui effectue le déploiement doit disposer des autorisations suivantes :

- Lister les espaces de noms dans le cluster (1)
- Corriger l’ancien ou le nouvel espace de noms avec l’étiquette (2)
- Créer le compte de service `sa-mssql-controller`, le rôle `<namespaced>-admin` et la liaison de rôle (3-5)

Dans la mesure où le rôle `admin` par défaut ne dispose pas de ces autorisations, l’utilisateur qui déploie le cluster Big Data doit posséder au moins des autorisations d’administrateur au niveau de l’espace de noms.

## <a name="cluster-role-required-for-pods-and-nodes-metrics-collection"></a>Rôle de cluster nécessaire pour la collecte de métriques sur les pods et les nœuds

À compter de SQL Server 2019 CU5, Telegraf exige un compte de service disposant d’autorisations de rôle à l’échelle du cluster pour collecter les métriques sur les pods et les nœuds. Lors du déploiement (ou de la mise à niveau de déploiements existants), nous tentons de créer le compte de service et le rôle de cluster nécessaires. Cependant, même si l’utilisateur qui déploie le cluster ou effectue la mise à niveau ne dispose pas d’autorisations suffisantes, le déploiement ou la mise à niveau continuera avec un avertissement et aboutira. Dans ce cas, les métriques sur les pods et les nœuds ne seront pas collectées. L’utilisateur qui déploie le cluster devra demander à un administrateur de cluster de créer le rôle et le compte de service (avant ou après le déploiement ou la mise à niveau). Clusters Big Data pourra alors les utiliser. 

Voici un script montrant comment créer les artefacts requis :

```console
export CLUSTER_NAME=mssql-cluster
kubectl create -f - <<EOF
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: ${CLUSTER_NAME}:cr-mssql-metricsdc-reader
rules:
- apiGroups:
  - '*'
  resources:
  - pods
  - nodes/stats
  verbs:
  - get
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: ${CLUSTER_NAME}:crb-mssql-metricsdc-reader
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: ${CLUSTER_NAME}:cr-mssql-metricsdc-reader
subjects:
- kind: ServiceAccount
  name: sa-mssql-metricsdc-reader
  namespace: ${CLUSTER_NAME}
EOF
```

Le compte de service, le rôle de cluster et la liaison de rôle de cluster peuvent être créés avant ou après le déploiement Clusters Big Data. Kubernetes met automatiquement à jour l’autorisation du compte de service Telegraf. En cas de création dans le cadre d’un déploiement de pod, un délai de quelques minutes se produit dans la collecte des métriques sur les pods et les nœuds.

> [!NOTE]
> SQL Server 2019 CU5 introduit deux commutateurs de fonctionnalités pour contrôler la collecte de métriques sur les pods et les nœuds. Par défaut, ces paramètres ont la valeur true dans toutes les environnements cibles, à l’exception d’OpenShift où la valeur par défaut est remplacée. 

Vous pouvez personnaliser ces paramètres dans la section security du fichier de configuration de déploiement `control.json` :

```json
  "security": {
    …
    "allowNodeMetricsCollection": false,
    "allowPodMetricsCollection": false
  }
```

Si ces paramètres sont définis sur `false`, le flux de travail de déploiement Clusters Big Data ne tente pas de créer le compte de service, le rôle de cluster ni la liaison pour Telegraf.
