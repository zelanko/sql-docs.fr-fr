---
title: Monter S3 pour la hiérarchisation HDFS
titleSuffix: SQL Server big data clusters
description: Cet article explique comment configurer HDFS la hiérarchisation pour monter un système de fichiers externe S3 dans HDFS sur un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1f126620c4da759a4c56abad05bf2e989d7d1bc3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66782064"
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
   > Pour plus d’informations sur la création de clés d’accès S3, consultez [clés d’accès S3](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

## <a id="mount"></a> Montage du stockage HDFS à distance

Maintenant que vous avez préparé un fichier d’informations d’identification avec des clés d’accès, vous pouvez commencer le montage. Les étapes suivantes monter le stockage HDFS à distance dans S3 vers le stockage HDFS local de votre cluster big data.

1. Utilisez **kubectl** pour rechercher l’adresse IP du point de terminaison **contrôleur-svc-external** service dans votre cluster de données volumineux. Recherchez le **External-IP**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Se connecter avec **mssqlctl** à l’aide de l’adresse IP externe du point de terminaison contrôleur avec votre nom d’utilisateur du cluster et le mot de passe :

   ```bash
   mssqlctl login -e https://<IP-of-controller-svc-external>:30080/
   ```

1. Montage du stockage HDFS à distance dans Azure à l’aide **créer de montage du pool de stockage de clusters mssqlctl**. Remplacez les valeurs d’espace réservé avant d’exécuter la commande suivante :

   ```bash
   mssqlctl cluster storage-pool mount create --remote-uri s3a://<S3 bucket name> --mount-path /mounts/<mount-name> --credential-file <path-to-s3-credentials>/file.creds
   ```

   > [!NOTE]
   > Le montage de créer la commande est asynchrone. À ce stade, il n’existe aucun message indiquant si le montage a réussi. Consultez le [état](#status) section pour vérifier l’état de vos montages.

Si monté correctement, il se peut que vous devez être en mesure d’interroger les données HDFS et exécuter des tâches Spark contre lui. Il apparaît dans le HDFS pour votre cluster big data à l’emplacement spécifié par `--mount-path`.

## <a id="status"></a> Obtenir l’état de montages

Pour répertorier l’état de tous les montages dans votre cluster de données volumineux, utilisez la commande suivante :

```bash
mssqlctl cluster storage-pool mount status
```

Pour répertorier l’état d’un montage à un emplacement spécifique dans HDFS, utilisez la commande suivante :

```bash
mssqlctl cluster storage-pool mount status --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> Supprimer le montage

Pour supprimer le montage, utilisez le **delete de montage de pool de stockage de cluster mssqlctl** commande et spécifiez le chemin d’accès de montage dans HDFS :

```bash
mssqlctl cluster storage-pool mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses de SQL Server 2019, consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).
