---
title: Utilisez curl pour charger des données dans HDFS sur SQL Server 2019 CTP 2.0 | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 05ce2d4d848b7c244d672f6ab43cbcf09224e63f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796175"
---
# <a name="use-curl-to-load-data-into-hdfs-on-sql-server-2019-ctp-20"></a>Utilisez curl pour charger des données dans HDFS sur SQL Server 2019 CTP 2.0

Cet article explique comment utiliser **curl** pour charger des données dans HDFS sur SQL Server 2019 CTP 2.0.

## <a name="obtain-the-service-external-ip"></a>Obtenir l’adresse IP externe de service

WebHDFS est démarré lorsque le déploiement est terminé et que son accès traverse Knox. Le point de terminaison Knox est exposé via un service Kubernetes appelée (pour l’instant) **service-sécurité-lb**.  Pour créer l’URL WebHDFS dont vous aurez besoin à utiliser CURL pour charger/télécharger des fichiers, vous devez le **service-sécurité-lb** adresse IP externe et le nom de votre cluster de service. Vous pouvez obtenir l’adresse IP externe de service-sécurité-lb service en exécutant cette commande :

```bash
kubectl get service service-security-lb -n <cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> Le `<cluster name>` ici est le nom du cluster que vous avez fourni lorsque vous avez exécuté mssqlctl créer le cluster `<cluster name>`.

## <a name="construct-the-url-to-access-webhdfs"></a>Construire l’URL pour accéder à WebHDFS

Maintenant, vous pouvez construire l’URL pour accéder à la WebHDFS comme suit :

`https://<service-security-lb service external IP address>:30433/gateway/default/webhdfs/v1/`

Exemple :

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>Un fichier de liste

Au fichier de liste sous **hdfs : / / / airlinedata** utilisez la commande curl suivante :

```bash
curl -i -k -u root:root-password -X GET 'https://<service-security-lb IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Placez un fichier local dans HDFS

Pour placer un nouveau fichier **test.csv** à partir du répertoire local dans le répertoire d’airlinedata (**Content-Type** paramètre est obligatoire) utilisez la commande curl suivante :

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<service-security-lb IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Créez un répertoire

Pour créer un répertoire **tester** sous `hdfs:///` utilisez la commande suivante :

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<service-security-lb IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur le cluster de données volumineux de SQL Server, consultez [What ' s cluster de données volumineux de SQL Server ?](big-data-cluster-overview.md).