---
title: Monter S3 pour la hiérarchisation HDFS
titleSuffix: SQL Server big data clusters
description: Cet article explique comment configurer la hiérarchisation HDFS pour monter un système de fichiers S3 externe dans HDFS sur un cluster SQL Server 2019 Big Data (version préliminaire).
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 28c80d6076f07c8a4f1605149f4b5c730c8349a1
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419341"
---
# <a name="how-to-mount-s3-for-hdfs-tiering-in-a-big-data-cluster"></a>Comment monter la hiérarchisation S3 pour HDFS dans un cluster Big Data

Les sections suivantes fournissent un exemple de configuration de la hiérarchisation HDFS avec une source de données de stockage S3.

## <a name="prerequisites"></a>Prérequis

- [Cluster Big Data déployé](deployment-guidance.md)
- [Outils Big Data](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**
- Créer et charger des données dans un compartiment S3 
  - Chargez les fichiers CSV ou parquet dans votre compartiment S3. Il s’agit des données HDFS externes qui seront montées sur HDFS dans le cluster Big Data.

## <a name="access-keys"></a>Clés d'accès

### <a name="set-environment-variable-for-access-key-credentials"></a>Définir la variable d’environnement pour les informations d’identification de la clé d’accès

Ouvrez une invite de commandes sur un ordinateur client qui peut accéder à votre cluster Big Data. Définissez une variable d’environnement en utilisant le format suivant. Notez que les informations d’identification doivent figurer dans une liste séparée par des virgules. La commande’Set’est utilisée sur Windows. Si vous utilisez Linux, utilisez’exporter’à la place.

   ```text
    set MOUNT_CREDENTIALS=fs.s3a.access.key=<Access Key ID of the key>,
    fs.s3a.secret.key=<Secret Access Key of the key>
   ```

   > [!TIP]
   > Pour plus d’informations sur la création de clés d’accès S3, consultez [clés d’accès S3](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

## <a id="mount"></a>Monter le stockage HDFS distant

Maintenant que vous avez préparé un fichier d’informations d’identification avec des clés d’accès, vous pouvez commencer le montage. Les étapes suivantes montent le stockage HDFS distant dans S3 dans le stockage HDFS local de votre cluster Big Data.

1. Utilisez **kubectl** pour trouver l’adresse IP du contrôleur de point de terminaison **-SVC-External** service dans votre cluster Big Data. Recherchez l' **adresse IP externe**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Connectez-vous avec **azdata** à l’aide de l’adresse IP externe du point de terminaison de contrôleur avec le nom d’utilisateur et le mot de passe de votre cluster:

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
   
1. Définir la variable d’environnement MOUNT_CREDENTIALS en suivant les instructions ci-dessus

1. Montez le stockage HDFS distant dans Azure à l’aide du **montage de pool de stockage azdata BDC Create**. Remplacez les valeurs d’espace réservé avant d’exécuter la commande suivante:

   ```bash
   azdata bdc storage-pool mount create --remote-uri s3a://<S3 bucket name> --mount-path /mounts/<mount-name>
   ```

   > [!NOTE]
   > La commande Mount Create est asynchrone. À ce stade, aucun message ne s’affiche pour indiquer si le montage a réussi. Consultez la section [État](#status) pour vérifier l’état de vos montages.

Si le montage réussit, vous devez être en mesure d’interroger les données HDFS et d’exécuter des travaux Spark sur celle-ci. Il apparaîtra dans le HDFS de votre cluster Big Data à l’emplacement spécifié par `--mount-path`.

## <a id="status"></a>Récupération de l’état des montages

Pour afficher l’état de tous les montages dans votre cluster Big Data, utilisez la commande suivante:

```bash
azdata bdc storage-pool mount status
```

Pour répertorier l’état d’un montage dans un chemin d’accès spécifique dans HDFS, utilisez la commande suivante:

```bash
azdata bdc storage-pool mount status --mount-path <mount-path-in-hdfs>
```

## <a name="refresh-a-mount"></a>Actualiser un montage

L’exemple suivant actualise le montage.

```bash
azdata bdc hdfs mount refresh --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a>Supprimer le montage

Pour supprimer le montage, utilisez la commande de **Suppression de pool de stockage azdata BDC** et spécifiez le chemin de montage dans HDFS:

```bash
azdata bdc storage-pool mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters SQL Server 2019 Big Data, consultez [que sont les clusters SQL Server 2019 Big Data?](big-data-cluster-overview.md).
