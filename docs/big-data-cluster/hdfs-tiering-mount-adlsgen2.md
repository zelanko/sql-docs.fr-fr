---
title: Monter ADLS Gen2 pour la hiérarchisation HDFS
titleSuffix: How to mount ADLS Gen2
description: Cet article explique comment configurer la hiérarchisation HDFS pour monter un système de fichiers Azure Data Lake Storage externe dans HDFS sur un cluster SQL Server 2019 Big Data (version préliminaire).
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d7d8a6dd53452700853dca9774ed0196ed7546fe
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419346"
---
# <a name="how-to-mount-adls-gen2-for-hdfs-tiering-in-a-big-data-cluster"></a>Comment monter ADLS Gen2 pour la hiérarchisation HDFS dans un cluster Big Data

Les sections suivantes fournissent un exemple de configuration de la hiérarchisation HDFS avec une source de données Azure Data Lake Storage Gen2.

## <a name="prerequisites"></a>Prérequis

- [Cluster Big Data déployé](deployment-guidance.md)
- [Outils Big Data](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**

## <a id="load"></a>Charger des données dans Azure Data Lake Storage

La section suivante décrit comment configurer Azure Data Lake Storage Gen2 pour le test de la hiérarchisation HDFS. Si vous avez déjà des données stockées dans Azure Data Lake Storage, vous pouvez ignorer cette section pour utiliser vos propres données.

1. [Créez un compte de stockage avec des fonctionnalités de Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. [Créez un conteneur d’objets BLOB](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal) dans ce compte de stockage pour vos données externes.

1. Chargez un fichier CSV ou parquet dans le conteneur. Il s’agit des données HDFS externes qui seront montées sur HDFS dans le cluster Big Data.

## <a name="credentials-for-mounting"></a>Informations d’identification pour le montage

## <a name="use-oauth-credentials-to-mount"></a>Utiliser les informations d’identification OAuth pour le montage

Pour pouvoir utiliser les informations d’identification OAuth à monter, vous devez suivre les étapes ci-dessous:

1. Accédez au [portail Azure](https://portal.azure.com)
1. Accédez à «services» dans le volet de navigation gauche et à l’horloge «Azure Active Directory»
1. À l’aide de «inscriptions d’application» dans le menu, créez une «application Web et suivez l’Assistant. **N’oubliez pas le nom que vous créez ici**. Vous devez ajouter ce nom à votre compte ADLS en tant qu’utilisateur autorisé.
1. Une fois l’application Web créée, accédez à «clés» sous «paramètres» pour l’application.
1. Sélectionnez une durée de clé, puis cliquez sur Enregistrer. **Enregistrez la clé générée.**
1.  Revenez à la page inscriptions des applications, puis cliquez sur le bouton «points de terminaison» en haut. **Notez l’URL du point de terminaison de jeton**
1. Les éléments suivants doivent maintenant être signalés pour OAuth:

    - L' «ID d’application» de l’application Web que vous avez créée précédemment à l’étape 3
    - Clé que vous venez de générer à l’étape 5
    - Le point de terminaison de jeton de l’étape 6

### <a name="adding-the-service-principal-to-your-adls-account"></a>Ajout du principal du service à votre compte ADLS

1. Accédez de nouveau au portail, ouvrez votre compte ADLS et sélectionnez contrôle d’accès (IAM) dans le menu de gauche.
1. Sélectionnez «Ajouter une attribution de rôle» et recherchez le nom que vous avez créé dans step3 ci-dessus (Notez qu’il n’apparaît pas dans la liste, mais qu’il sera trouvé si vous recherchez le nom complet).
1. Ajoutez maintenant le rôle «contributeur pour le stockage des données BLOB (préversion)».

Attendre 5-10 minutes avant d’utiliser les informations d’identification pour le montage

### <a name="set-environment-variable-for-oauth-credentials"></a>Définir la variable d’environnement pour les informations d’identification OAuth

Ouvrez une invite de commandes sur un ordinateur client qui peut accéder à votre cluster Big Data. Définissez une variable d’environnement en utilisant le format suivant: Notez que les informations d’identification doivent figurer dans une liste séparée par des virgules. La commande’Set’est utilisée sur Windows. Si vous utilisez Linux, utilisez’exporter’à la place.

   ```text
    set MOUNT_CREDENTIALS=fs.azure.account.auth.type=OAuth,
    fs.azure.account.oauth.provider.type=org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider,
    fs.azure.account.oauth2.client.endpoint=[token endpoint from step6 above],
    fs.azure.account.oauth2.client.id=[<Application ID> from step3 above],
    fs.azure.account.oauth2.client.secret=[<key> from step5 above]
   ```

## <a name="use-access-keys-to-mount"></a>Utiliser des clés d’accès pour le montage

Vous pouvez également monter à l’aide des clés d’accès que vous pouvez obtenir pour votre compte ADLS sur le Portail Azure.

 > [!TIP]
   > Pour plus d’informations sur la recherche de la touche d'`<storage-account-access-key>`accès () pour votre compte de stockage, consultez [afficher les clés de compte et la chaîne de connexion](/azure/storage/common/storage-account-manage#view-account-keys-and-connection-string).

### <a name="set-environment-variable-for-access-key-credentials"></a>Définir la variable d’environnement pour les informations d’identification de la clé d’accès

1. Ouvrez une invite de commandes sur un ordinateur client qui peut accéder à votre cluster Big Data.

1. Ouvrez une invite de commandes sur un ordinateur client qui peut accéder à votre cluster Big Data. Définissez une variable d’environnement en utilisant le format suivant. Notez que les informations d’identification doivent figurer dans une liste séparée par des virgules. La commande’Set’est utilisée sur Windows. Si vous utilisez Linux, utilisez’exporter’à la place.

   ```text
   set MOUNT_CREDENTIALS=fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

## <a id="mount"></a>Monter le stockage HDFS distant

Maintenant que vous avez défini la variable d’environnement MOUNT_CREDENTIALS pour les clés d’accès ou à l’aide d’OAuth, vous pouvez commencer le montage. Les étapes suivantes montent le stockage HDFS distant dans Azure Data Lake dans le stockage HDFS local de votre cluster Big Data.

1. Utilisez **kubectl** pour trouver l’adresse IP du contrôleur de point de terminaison **-SVC-External** service dans votre cluster Big Data. Recherchez l' **adresse IP externe**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Connectez-vous avec **azdata** à l’aide de l’adresse IP externe du point de terminaison de contrôleur avec le nom d’utilisateur et le mot de passe de votre cluster:

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
1. Définir la variable d’environnement MOUNT_CREDENTIALS (faire défiler vers le haut pour obtenir des instructions)

1. Montez le stockage HDFS distant dans Azure à l’aide du **montage de pool de stockage azdata BDC Create**. Remplacez les valeurs d’espace réservé avant d’exécuter la commande suivante:

   ```bash
   azdata bdc storage-pool mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name>
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
