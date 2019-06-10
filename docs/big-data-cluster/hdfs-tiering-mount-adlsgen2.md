---
title: Monter ADLS Gen2 pour la hiérarchisation HDFS
titleSuffix: How to mount ADLS Gen2
description: Cet article explique comment configurer HDFS la hiérarchisation pour monter un système de fichiers externe Azure Data Lake Storage dans HDFS sur un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 504559fab3078b03ea3b8aea923035654f60ce47
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66782136"
---
# <a name="how-to-mount-adls-gen2-for-hdfs-tiering-in-a-big-data-cluster"></a>Comment Gen2 ADLS de montage de fichiers HDFS la hiérarchisation d’un cluster de données volumineuses

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

## <a name="credentials-for-mounting"></a>Informations d’identification pour le montage

## <a name="use-oauth-credentials-to-mount"></a>Utilisez les informations d’identification OAuth pour monter

Pour pouvoir utiliser les informations d’identification OAuth pour monter, vous devez suivre les étapes ci-dessous :

1. Accédez à la [portail Azure](https://portal.azure.com)
1. Accédez à « services » dans le volet de navigation gauche, puis sur « Azure Active Directory » de l’horloge
1. À l’aide de « Inscriptions d’application » dans le menu, créez un dossier « Application Web et suivez l’Assistant. **N’oubliez pas le nom que vous créez ici**. Vous devez ajouter ce nom à votre compte ADLS en tant qu’un utilisateur autorisé.
1. Une fois l’application web est créée, accédez à « clés » sous « paramètres » pour l’application.
1. Sélectionnez qu'une durée de clé et le, cliquez sur enregistrent. **Enregistrez la clé générée.**
1.  Revenez à la page des inscriptions d’application et cliquez sur le bouton « Points de terminaison » en haut. **Notez l’URL « Point de terminaison de jeton »**
1. Vous devez maintenant avoir les éléments suivants notées pour OAuth :

    - Le « ID » de l’application Web créé ci-dessus à l’étape 3
    - La clé que vous venez de générer à l’étape 5
    - Le point de terminaison de jeton à l’étape 6

### <a name="adding-the-service-principal-to-your-adls-account"></a>Ajout de principal du service à votre compte ADLS

1. Accédez au portail à nouveau et ouvrez votre compte ADLS et sélectionnez le contrôle d’accès (IAM) dans le menu de gauche.
1. Sélectionnez « Ajouter une attribution de rôle » et recherchez le nom que vous avez créé à l’étape 3 ci-dessus (Notez qu’il ne s’affiche pas dans la liste, mais sera trouvée si vous recherchez pour le nom complet).
1. Maintenant ajouter le rôle de « Stockage contributeur aux données Blob (version préliminaire) ».

Attendez 5 à 10 minutes avant d’utiliser les informations d’identification pour le montage

### <a name="create-credential-file"></a>Créer le fichier d’informations d’identification

Ouvrez une invite de commandes sur un ordinateur client qui peut accéder à votre cluster de données volumineux.

Créez un fichier local nommé **filename.creds** qui contient vos informations d’identification du compte Azure Data Lake Storage Gen2 en utilisant le format suivant :

   ```text
    fs.azure.account.auth.type=OAuth
    fs.azure.account.oauth.provider.type=org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider
    fs.azure.account.oauth2.client.endpoint=[token endpoint from step6 above]
    fs.azure.account.oauth2.client.id=[<Application ID> from step3 above]
    fs.azure.account.oauth2.client.secret=[<key> from step5 above]
   ```

## <a name="use-access-keys-to-mount"></a>Utilisez les touches d’accès pour monter

Vous pouvez également monter à l’aide de clés d’accès que vous pouvez obtenir pour votre compte ADLS sur le portail Azure.

 > [!TIP]
   > Pour plus d’informations sur la façon de trouver la clé d’accès (`<storage-account-access-key>`) pour votre compte de stockage, consultez [clés d’accès afficher et copier](https://docs.microsoft.com/azure/storage/common/storage-account-manage?#view-and-copy-access-keys).

### <a name="create-credential-file"></a>Créer le fichier d’informations d’identification

1. Ouvrez une invite de commandes sur un ordinateur client qui peut accéder à votre cluster de données volumineux.

1. Créez un fichier local nommé **filename.creds** qui contient vos informations d’identification du compte Azure Data Lake Storage Gen2 en utilisant le format suivant :

   ```text
   fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

## <a id="mount"></a> Montage du stockage HDFS à distance

Maintenant que vous avez préparé un fichier d’informations d’identification avec les clés d’accès ou à l’aide d’OAuth, vous pouvez commencer le montage. Les étapes suivantes monter le stockage HDFS à distance dans Azure Data Lake sur le stockage HDFS local de votre cluster big data.

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
   mssqlctl cluster storage-pool mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name> --credential-file <path-to-adls-credentials>/file.creds
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
