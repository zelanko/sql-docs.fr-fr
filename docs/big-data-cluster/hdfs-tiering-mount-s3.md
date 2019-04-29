---
title: Monter S3 pour la hiérarchisation HDFS
titleSuffix: SQL Server big data clusters
description: Cet article explique comment configurer HDFS la hiérarchisation pour monter un système de fichiers externe S3 dans HDFS sur un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: craigg
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cd4a5fc600a937b5cc29ea4356a7cc2eb14966b2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63317118"
---
# <a name="how-to-mount-s3-for-hdfs-tiering-in-a-big-data-cluster"></a>Comment S3 de montage de fichiers HDFS la hiérarchisation d’un cluster de données volumineuses

Les sections suivantes fournissent un exemple de configuration HDFS la hiérarchisation avec une source de données de stockage de S3.

## <a name="prerequisites"></a>Prérequis

- [Cluster de données volumineux déployé](deployment-guidance.md)
- [Outils de données volumineuses](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**
- Créer et charger des données dans un compartiment S3 
  - Charger un fichier CSV ou Parquet des fichiers à votre compartiment S3. Il s’agit de données HDFS externes qui seront montées à HDFS du cluster de données volumineuses.

## <a name="access-keys"></a>Clés d'accès

1. Ouvrez une invite de commandes sur un ordinateur client qui peut accéder à votre cluster de données volumineux.

1. Créez un fichier local nommé **filename.creds** qui contient vos informations d’identification du compte de S3 en utilisant le format suivant :

   ```text
    fs.s3a.access.key=<Access Key ID of the key>
    fs.s3a.secret.key=<Secret Access Key of the key>
   ```

   > [!TIP]
   > Pour plus d’informations sur la création de S3 clés d’accès (`<s3-access-key>`), consultez [clés d’accès S3](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

## <a id="mount"></a> Montage du stockage HDFS à distance

Maintenant que vous avez préparé un fichier d’informations d’identification avec des clés d’accès, vous pouvez commencer le montage. Les étapes suivantes monter le stockage HDFS à distance dans S3 vers le stockage HDFS local de votre cluster big data.

1. Utilisez **kubectl** pour rechercher l’adresse IP pour le **mgmtproxy-svc-external** service dans votre cluster de données volumineux. Recherchez le **External-IP**.

   ```bash
   kubectl get svc mgmtproxy-svc-external -n <your-cluster-name>
   ```

1. Se connecter avec **mssqlctl** à l’aide de l’adresse IP externe du point de terminaison de proxy de gestion avec votre nom d’utilisateur du cluster et le mot de passe :

   ```bash
   mssqlctl login -e https://<IP-of-mgmtproxy-svc-external>:30777/ -u <username> -p <password>
   ```

1. Montage du stockage HDFS à distance dans Azure à l’aide **créer de montage du stockage mssqlctl**. Remplacez les valeurs d’espace réservé avant d’exécuter la commande suivante :

   ```bash
   mssqlctl storage mount create --remote-uri s3a://<S3 bucket name> --mount-path /mounts/<mount-name> --credential-file <path-to-s3-credentials>/file.creds
   ```

   > [!NOTE]
   > Le montage de créer la commande est asynchrone. À ce stade, il n’existe aucun message indiquant si le montage a réussi. Consultez le [état](#status) section pour vérifier l’état de vos montages.

Si monté correctement, il se peut que vous devez être en mesure d’interroger les données HDFS et exécuter des tâches Spark contre lui. Il apparaît dans le HDFS pour votre cluster big data à l’emplacement spécifié par `--mount-path`.

## <a id="status"></a> Obtenir l’état de montages

Pour répertorier l’état de tous les montages dans votre cluster de données volumineux, utilisez la commande suivante :

```bash
mssqlctl storage mount status
```

Pour répertorier l’état d’un montage à un emplacement spécifique dans HDFS, utilisez la commande suivante :

```bash
mssqlctl storage mount status --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> Supprimer le montage

Pour supprimer le montage, utilisez le **mssqlctl stockage montage delete** commande et spécifiez le chemin d’accès de montage dans HDFS :

```bash
mssqlctl storage mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses de SQL Server 2019, consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).
