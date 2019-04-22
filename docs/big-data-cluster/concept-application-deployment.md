---
title: Quel est le déploiement d’applications ?
titleSuffix: SQL Server 2019 big data clusters
description: Cet article décrit le déploiement d’applications sur un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: jterh
ms.author: jroth
manager: craigg
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 44e0be15c9b9cc3abb8af3e8f2e7fc8049d385df
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58872362"
---
# <a name="what-is-application-deployment-on-a-sql-server-2019-big-data-cluster"></a>Qu’est le déploiement d’applications sur un cluster de données volumineuses de SQL Server 2019 ?

Déploiement d’applications permet le déploiement d’applications sur le cluster de données volumineuses en fournissant des interfaces pour créer, gérer et exécuter des applications. Les applications déployées sur le cluster de données volumineuses bénéficient de la puissance de calcul du cluster et peuvent accéder aux données qui sont disponibles sur le cluster. Cela augmente l’évolutivité et les performances des applications, tout en gérant les applications où les données résident.
Les sections suivantes décrivent l’architecture et les fonctionnalités de déploiement de l’Application.

## <a name="application-deployment-architecture"></a>Architecture de déploiement d’application

Déploiement de l’application se compose d’un contrôleur et des gestionnaires de runtime d’application. Lors de la création d’une application, un fichier de spécification (`spec.yaml`) est fourni. Cela `spec.yaml` fichier contient tout ce que le contrôleur a besoin pour déployer correctement l’application. Voici un exemple du contenu pour `spec.yaml`:

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

Inspecte le contrôleur le `runtime` spécifié dans le `spec.yaml` de fichiers et appelle le Gestionnaire de runtime correspondant. Le Gestionnaire de runtime crée l’application. Tout d’abord, un Kubernetes ReplicaSet est créé contenant un ou plusieurs pods, chacun d’eux contient l’application à déployer. Le nombre de pods est défini par le `replicas` paramètre défini le `spec.yaml` fichier pour l’application. Chaque bloc peut avoir un des pools plus. Le nombre de pools est défini par le `poolsize` paramètre défini le `spec.yaml` fichier.

Ces paramètres ont un impact sur le nombre de demandes que le déploiement peut gérer en parallèle. Le nombre maximal de demandes à un moment donné est égal à `replicas` fois `poolsize`. Si vous avez 5 réplicas et 2 pools par réplica le déploiement peut gérer 10 requêtes en parallèle. Voir l’image ci-dessous pour obtenir une représentation graphique de `replicas` et `poolsize`:

![Taiile_pool et réplicas](media/big-data-cluster-create-apps/poolsize-vs-replicas.png)

Après le ReplicaSet a été créé et les pods ont démarré, un travail cron est créé si un `schedule` a été défini dans le `spec.yaml` fichier. Enfin, un Kubernetes Service est créé qui peut être utilisé pour gérer et exécuter l’application (voir ci-dessous).

Quand une application est exécutée, le service Kubernetes pour les proxys d’application les demandes à un réplica et renvoie les résultats.

## <a name="how-to-work-with-application-deployment"></a>Comment travailler avec le déploiement d’applications

Les deux interfaces principales pour le déploiement d’Application sont : 
- [Interface de ligne de commande `mssqlctl`](big-data-cluster-create-apps.md)
- [Visual Studio Code et Azure Data Studio l’extension](app-deployment-extension.md)

Il est également possible pour une application doit être exécuté à l’aide d’un service web RESTful. Pour plus d’informations, consultez [consommer des applications sur des clusters de données volumineuses](big-data-cluster-consume-apps.md).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur la façon de créer et exécuter des applications sur des clusters de données volumineuses de SQL Server, consultez les rubriques suivantes :

- [Déployer des applications à l’aide de mssqlctl](big-data-cluster-create-apps.md)
- [Déployer des applications à l’aide de l’extension de l’application déployée](app-deployment-extension.md)
- [Utiliser les applications sur les clusters de données volumineuses](big-data-cluster-consume-apps.md)

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez la présentation suivante :

- [Quelles sont les clusters SQL Server 2019 big data ?](big-data-cluster-overview.md)
