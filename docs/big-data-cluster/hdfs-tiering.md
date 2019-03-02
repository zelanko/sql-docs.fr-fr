---
title: Configurer la hiérarchisation HDFS
titleSuffix: SQL Server 2019 big data clusters
description: Cet article explique comment configurer HDFS la hiérarchisation pour monter un système de fichiers externe Azure Data Lake Storage dans HDFS sur un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: craigg
ms.date: 02/29/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 04f493109997d4b673a6a308de5c9ebee6eac7e4
ms.sourcegitcommit: 56fb7b648adae2c7b81bd969de067af1a2b54180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57239126"
---
# <a name="configure-hdfs-tiering-on-sql-server-2019-big-data-clusters"></a>Configurer HDFS hiérarchisation sur des clusters SQL Server 2019 big data

La hiérarchisation HDFS fournit la capacité à monter externe, le système de fichiers compatible HDFS dans HDFS. Cet article explique comment configurer HDFS réduits pour les clusters de données volumineuses de SQL Server 2019 (version préliminaire). À ce stade, CTP 2.3 prend en charge uniquement se connecter à Azure Data Lake Storage Gen2, qui est l’objectif de cet article.

## <a name="hdfs-tiering-overview"></a>Vue d’ensemble de la hiérarchisation HDFS

Avec une hiérarchisation, les applications peuvent accéder en toute transparence les données dans un large éventail de magasins externes comme si les données résident dans HDFS. Le montage est une opération de métadonnées, où les métadonnées qui décrivent l’espace de noms sur le système de fichiers externe sont copiée dans HDFS. Ces métadonnées incluent des informations sur les répertoires externes et les fichiers, ainsi que leurs autorisations et les ACL. Les données correspondantes sont uniquement copié à la demande, lorsque les données lui-même sont accessible. Les données de système de fichiers externe sont maintenant accessible à partir du cluster de données volumineuses de SQL Server. Vous pouvez exécuter Spark travaux et des requêtes SQL sur ces données dans la même façon que les exécuter sur toutes les données locales stockées dans HDFS sur le cluster.

> [!NOTE]
> HDFS la hiérarchisation est une fonctionnalité développée par Microsoft, et une version antérieure de celui-ci a été publiée dans le cadre de la distribution d’Apache Hadoop 3.1. Pour plus d’informations, consultez [ https://issues.apache.org/jira/browse/HDFS-9806 ](https://issues.apache.org/jira/browse/HDFS-9806) pour plus d’informations.

Les sections suivantes fournissent un exemple de configuration HDFS la hiérarchisation avec une source de données Azure Data Lake Storage Gen2.

## <a name="prerequisites"></a>Prérequis

- [Cluster de données volumineux déployé](deployment-guidance.md)
- [Outils de données volumineuses](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**

## <a id="load"></a> Charger des données dans Azure Data Lake Storage

La section suivante décrit comment configurer le stockage Azure Data Lake Gen2 HDFS la hiérarchisation de test. Si vous avez déjà des données stockées dans Azure Data Lake Storage, vous pouvez ignorer cette section pour utiliser vos propres données.

1. [Créer un compte de stockage avec les fonctionnalités de Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. [Créer un conteneur d’objets blob](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal) dans ce compte de stockage pour vos données externes.

1. Téléchargez un fichier CSV ou Parquet dans le conteneur. Il s’agit de données HDFS externes qui seront montées à HDFS du cluster de données volumineuses.

## <a id="mount"></a> Montage du stockage HDFS à distance

Les étapes suivantes monter le stockage HDFS à distance dans Azure Data Lake dans le stockage HDFS local de votre cluster big data.

1. Ouvrez une invite de commandes sur un ordinateur client qui peut accéder à votre cluster de données volumineux.

1. Créez un fichier local nommé **files.creds** qui contient vos informations d’identification du compte Azure Data Lake Storage Gen2 en utilisant le format suivant :

   ```text
   fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

   > [!TIP]
   > Pour plus d’informations sur la façon de trouver la clé d’accès (`<storage-account-access-key>`) pour votre compte de stockage, consultez [clés d’accès afficher et copier](https://docs.microsoft.com/azure/storage/common/storage-account-manage?#view-and-copy-access-keys).

1. Utilisez **kubectl** pour rechercher l’adresse IP pour le **proxy de service de point de terminaison** service dans votre cluster de données volumineux. Recherchez le **External-IP**.

   ```bash
   kubectl get svc endpoint-service-proxy -n <your-cluster-name>
   ```

1. Se connecter avec **mssqlctl** à l’aide du point de terminaison de proxy de service avec votre nom d’utilisateur du cluster et le mot de passe :

   ```bash
   mssqlctl login -e https://<IP-of-endpoint-service-proxy>:30777/ -u <username> -p <password>
   ```

1. Montage du stockage HDFS à distance dans Azure à l’aide **créer de montage du stockage mssqlctl**. Remplacez les valeurs d’espace réservé avant d’exécuter la commande suivante :

   ```bash
   mssqlctl storage mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --local-path /mounts/<mount-name> --credential-file <path-to-adls-credentials>/file.creds
   ```

   > [!NOTE]
   > Le montage de créer la commande est asynchrone. À ce stade, il n’existe aucun message indiquant si le montage a réussi. Consultez le [état](#status) section pour vérifier l’état de vos montages.

Si monté correctement, il se peut que vous devez être en mesure d’interroger les données HDFS et exécuter des tâches Spark contre lui. Il apparaît dans le HDFS pour votre cluster big data à l’emplacement spécifié par `--local-path`.

## <a id="status"></a> Obtenir l’état de montages

Pour répertorier l’état de tous les montages dans votre cluster de données volumineux, utilisez la commande suivante :

```bash
mssqlctl storage mount status
```

Pour répertorier l’état d’un montage à un emplacement spécifique dans HDFS, utilisez la commande suivante :

```bash
mssqlctl storage mount status --local-path <mount-path-in-hdfs>
```

## <a id="delete"></a> Supprimer le montage

Pour supprimer le montage, utilisez le **mssqlctl stockage montage delete** commande et spécifiez le chemin d’accès de montage dans HDFS :

```bash
mssqlctl storage mount delete --local-path <mount-path-in-hdfs>
```

## <a id="issues"></a> Limitations et problèmes connus

La liste suivante fournit les problèmes connus et limitations actuelles lors de l’utilisation de HDFS la hiérarchisation dans les clusters de données volumineuses de SQL Server :

- Si la taille de l’annuaire externe qui est monté est supérieure à la capacité du cluster, le montage échoue.

- Si le montage est bloqué dans un `CREATING` état pendant une longue période, il a probablement échoué. Dans ce cas, annuler la commande et supprimer le montage si nécessaire. Vérifiez que vos paramètres et les informations d’identification sont correctes avant de réessayer.

- Montages ne peut pas être créés dans les répertoires existants.

- Impossible de créer les montages au sein de montages existants.

- Si un des ancêtres du point de montage n’existent pas, ils seront créés avec les autorisations par défaut la valeur r-xr-xr-x (555).

- La création de montage peut prendre un certain temps selon le nombre et la taille des fichiers qui est monté. Pendant ce processus, les fichiers sous le montage ne sont pas visibles aux utilisateurs. Pendant la création, le montage tous les fichiers seront ajoutés à un chemin d’accès temporaire, qui utilise par défaut `/_temporary/_mounts/<mount-location>`.

- La commande de création de montage est asynchrone. Une fois que la commande est exécutée, l’état de montage peut être vérifié à comprendre l’état du montage.

- Lorsque vous créez le montage, l’argument utilisé pour **--local-path** est essentiellement un identificateur unique du montage. La même chaîne (y compris la « / » en fin de compte, le cas échéant) doit être utilisée dans les commandes suivantes.

- Les montages sont en lecture seule. Impossible de créer les répertoires ou les fichiers sous un montage.

- Nous ne recommandons pas de fichiers et répertoires de montage qui peuvent changer. Une fois le montage est créé, les modifications ou les mises à jour vers l’emplacement distant seront répercutées dans le montage dans HDFS. Si les modifications se produisent dans l’emplacement distant, vous pouvez choisir de supprimer et recréer le montage pour refléter l’état mis à jour.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses de SQL Server 2019, consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).