---
title: Utilisez curl pour charger des données dans HDFS | Microsoft Docs
titleSuffix: SQL Server big data clusters
description: Utilisez curl pour charger des données dans HDFS sur des clusters SQL Server 2019 big data.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 56bee3241427b9de9768e7bdd9e49646b51521d1
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860136"
---
# <a name="use-curl-to-load-data-into-hdfs-on-sql-server-big-data-clusters"></a>Utilisez curl pour charger des données dans HDFS sur les clusters de données volumineuses de SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment utiliser **curl** pour charger des données dans HDFS sur les clusters de données volumineuses de SQL Server 2019 (version préliminaire).

## <a name="obtain-the-service-external-ip"></a>Obtenir l’adresse IP externe de service

WebHDFS est démarré lorsque le déploiement est terminé et que son accès traverse Knox. Le point de terminaison Knox est exposée via un service Kubernetes appelé **-security du point de terminaison**.  Pour créer l’URL WebHDFS nécessaire pour télécharger des fichiers, vous devez le **-security du point de terminaison** adresse IP externe et le nom de votre cluster de service. Vous pouvez obtenir le **-security du point de terminaison** adresse IP externe de service en exécutant la commande suivante :

```bash
kubectl get service endpoint-security -n <cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> Le `<cluster name>` ici est le nom du cluster que vous avez fourni lors de l’exécution `mssqlctl cluster create --name <cluster name>`.

## <a name="construct-the-url-to-access-webhdfs"></a>Construire l’URL pour accéder à WebHDFS

Maintenant, vous pouvez construire l’URL pour accéder à la WebHDFS comme suit :

`https://<endpoint-security service external IP address>:30443/gateway/default/webhdfs/v1/`

Exemple :

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>Un fichier de liste

Au fichier de liste sous **hdfs : / / / airlinedata**, utilisez la commande curl suivante :

```bash
curl -i -k -u root:root-password -X GET 'https://<endpoint-security IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Placez un fichier local dans HDFS

Pour placer un nouveau fichier **test.csv** à partir d’un répertoire local au répertoire d’airlinedata, utilisez la commande curl suivante (le **Content-Type** paramètre est obligatoire) :

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<endpoint-security IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Créez un répertoire

Pour créer un répertoire **tester** sous `hdfs:///`, utilisez la commande suivante :

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<endpoint-security IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur le cluster de données volumineux de SQL Server, consultez [What ' s cluster de données volumineux de SQL Server ?](big-data-cluster-overview.md).
