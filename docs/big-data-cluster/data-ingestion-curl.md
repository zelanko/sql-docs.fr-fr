---
title: Utilisez curl pour charger des données dans HDFS | Microsoft Docs
titleSuffix: SQL Server big data clusters
description: Utilisez l’boucle pour charger des données dans HDFS sur [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c65ce7fb6752240f0dd23a6dab195539146e7933
ms.sourcegitcommit: 4fb6bc7c81a692a2df706df063d36afad42816af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73049876"
---
# <a name="use-curl-to-load-data-into-hdfs-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Utilisez l’boucle pour charger des données dans HDFS sur [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment utiliser l' **boucle** pour charger des données dans HDFS sur [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (version préliminaire).

## <a id="prereqs"></a> Prérequis

- [Charger des exemples de données dans votre cluster Big Data](tutorial-load-sample-data.md)

## <a name="obtain-the-service-external-ip"></a>Obtenir l’adresse IP externe du service

WebHDFS démarre lorsque le déploiement est terminé et que son accès est passé par Knox. Le point de terminaison Knox est exposé via un service Kubernetes nommé **gateway-svc-external**.  Pour créer l’URL WebHDFS nécessaire au téléchargement et au chargement des fichiers, vous avez besoin de l’adresse IP externe du service **gateway-svc-external** et du nom du cluster Big Data. Vous pouvez récupérer l’adresse IP externe du service **gateway-svc-external** en exécutant la commande suivante :

```bash
kubectl get service gateway-svc-external -n <big data cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> `<big data cluster name>` correspond au nom du cluster que vous avez spécifié dans le fichier de configuration du déploiement. Le nom par défaut est `mssql-cluster`.

## <a name="construct-the-url-to-access-webhdfs"></a>Construire l’URL pour accéder à WebHDFS

Vous pouvez maintenant construire l’URL pour accéder à WebHDFS de la façon suivante :

`https://<gateway-svc-external service external IP address>:30443/gateway/default/webhdfs/v1/`

Par exemple:

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>Lister un fichier

Pour afficher le fichier sous **HDFS:///product_review_data**, utilisez la commande bouclé suivante :

```bash
curl -i -k -u root:root-password -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Placer un fichier local dans HDFS

Pour placer un nouveau fichier **test. csv** à partir du répertoire local dans le répertoire product_review_data, utilisez la commande bouclé suivante (le paramètre **Content-type** est obligatoire) :

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Créer un répertoire

Pour créer un répertoire **test** sous `hdfs:///`, utilisez la commande suivante :

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data SQL Server, consultez [Qu’est-ce qu’un cluster Big Data SQL Server ?](big-data-cluster-overview.md).
