---
title: Qu’est-ce que le déploiement d’applications?
titleSuffix: SQL Server 2019 big data clusters
description: Cet article décrit le déploiement d’applications sur un cluster SQL Server 2019 Big Data (version préliminaire).
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d8cc44862af21c54bdbd0e4adbb35db912c3f7c9
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419409"
---
# <a name="what-is-application-deployment-on-a-sql-server-2019-big-data-cluster"></a>Qu’est-ce que le déploiement d’application sur un cluster SQL Server 2019 Big Data?

Le déploiement d’applications permet le déploiement d’applications sur le cluster Big Data en fournissant des interfaces pour créer, gérer et exécuter des applications. Les applications déployées sur le cluster Big Data bénéficient de la puissance de calcul du cluster et peuvent accéder aux données disponibles sur le cluster. Cela augmente l’évolutivité et les performances des applications, tout en gérant les applications où résident les données.
Les sections suivantes décrivent l’architecture et les fonctionnalités du déploiement d’applications.

## <a name="application-deployment-architecture"></a>Architecture du déploiement d’applications

Le déploiement d’applications se compose d’un contrôleur et de gestionnaires d’exécution d’application. Lors de la création d’une application, un`spec.yaml`fichier de spécification () est fourni. Ce `spec.yaml` fichier contient tout ce que le contrôleur a besoin de savoir pour déployer correctement l’application. Voici un exemple du contenu de `spec.yaml`:

```yaml
#spec.yaml
name: add-app #name of your python script
version: v1  #version of the app
runtime: Python #the language this app uses (R or Python)
src: ./add.py #full path to the location of the app
entrypoint: add #the function that will be called upon execution
replicas: 1  #number of replicas needed
poolsize: 1  #the pool size that you need your app to scale
inputs:  #input parameters that the app expects and the type
  x: int
  y: int
output: #output parameter the app expects and the type
  result: int
```

Le contrôleur inspecte le `runtime` spécifié dans le `spec.yaml` fichier et appelle le gestionnaire d’exécution correspondant. Le gestionnaire d’exécution crée l’application. Tout d’abord, un ReplicaSet Kubernetes est créé contenant un ou plusieurs Pod, chacun contenant l’application à déployer. Le nombre de Pod est défini par le `replicas` jeu de paramètres dans `spec.yaml` le fichier de l’application. Chaque Pod peut avoir un ou plusieurs pools. Le nombre de pools est défini par `poolsize` le jeu de paramètres `spec.yaml` dans le fichier.

Ces paramètres ont un impact sur la quantité de requêtes que le déploiement peut traiter en parallèle. Le nombre maximal de demandes à un moment donné est égal à `replicas` plusieurs fois. `poolsize` Si vous avez 5 réplicas et 2 pools par réplica, le déploiement peut gérer 10 demandes en parallèle. Reportez-vous à l’image ci `replicas` - `poolsize`dessous pour obtenir une représentation graphique de et:

![Regrouper et réplicas](media/big-data-cluster-create-apps/poolsize-vs-replicas.png)

Une fois le ReplicaSet créé et les Pod démarrés, un travail cron est créé si un `schedule` a été défini dans le `spec.yaml` fichier. Enfin, un service Kubernetes est créé et peut être utilisé pour gérer et exécuter l’application (voir ci-dessous).

Lorsqu’une application est exécutée, le service Kubernetes pour l’application transmet les demandes à un réplica et retourne les résultats.

## <a name="how-to-work-with-application-deployment"></a>Comment utiliser le déploiement d’applications

Les deux interfaces principales pour le déploiement d’applications sont les suivantes: 
- [Interface de ligne de commande`azdata`](big-data-cluster-create-apps.md)
- [Extension Visual Studio Code et Azure Data Studio](app-deployment-extension.md)

Une application peut également être exécutée à l’aide d’un service Web RESTful. Pour plus d’informations, consultez [utiliser des applications sur des clusters Big Data](big-data-cluster-consume-apps.md).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur la création et l’exécution d’applications sur SQL Server Clusters Big Data, consultez les rubriques suivantes:

- [Déployer des applications à l’aide de azdata](big-data-cluster-create-apps.md)
- [Déployer des applications à l’aide de l’extension App deploy](app-deployment-extension.md)
- [Utiliser des applications sur des clusters Big Data](big-data-cluster-consume-apps.md)

Pour en savoir plus sur les clusters Big Data SQL Server, consultez la vue d’ensemble suivante:

- [Que sont les clusters SQL Server 2019 Big Data?](big-data-cluster-overview.md)
