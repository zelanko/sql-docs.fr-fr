---
title: Utilisez curl pour charger des données dans HDFS | Microsoft Docs
titleSuffix: SQL Server big data clusters
description: Utilisez curl pour charger des données dans HDFS sur des clusters Big Data SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: aae991c6dfdade4145f1e5578273e3b6aeb83299
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958633"
---
# <a name="use-curl-to-load-data-into-hdfs-on-sql-server-big-data-clusters"></a>Utiliser curl pour charger des données dans HDFS sur des clusters Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment utiliser **curl** pour charger des données dans HDFS sur des clusters Big Data SQL Server 2019 (préversion).

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

Par exemple :

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>Lister un fichier

Pour lister le fichier sous **hdfs:///airlinedata**, utilisez la commande curl suivante :

```bash
curl -i -k -u root:root-password -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Placer un fichier local dans HDFS

Pour déplacer un nouveau fichier **test.csv** du répertoire local vers le répertoire airlinedata, utilisez la commande curl suivante (le paramètre **Content-Type** est obligatoire) :

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Créer un répertoire

Pour créer un répertoire **test** sous `hdfs:///`, utilisez la commande suivante :

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data SQL Server, consultez [Qu’est-ce qu’un cluster Big Data SQL Server ?](big-data-cluster-overview.md).
