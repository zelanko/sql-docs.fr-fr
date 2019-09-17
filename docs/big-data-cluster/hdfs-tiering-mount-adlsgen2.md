---
title: Monter ADLS Gen2 pour la hiérarchisation HDFS
titleSuffix: How to mount ADLS Gen2
description: Cet article explique comment configurer la hiérarchisation HDFS pour monter un système de fichiers Azure Data Lake Storage externe dans HDFS sur [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]un.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 08/27/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 679fbd63d77e21a84db315cf05adf112d122ad63
ms.sourcegitcommit: 243925311cc952dd455faea3c1156e980959d6de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70774216"
---
# <a name="how-to-mount-adls-gen2-for-hdfs-tiering-in-a-big-data-cluster"></a>Comment monter ADLS Gen2 pour la hiérarchisation HDFS dans un cluster Big Data

Les sections suivantes fournissent un exemple de configuration de la hiérarchisation HDFS avec une source de données Azure Data Lake Storage Gen2.

## <a name="prerequisites"></a>Prérequis

- [Cluster Big Data déployé](deployment-guidance.md)
- [Outils Big Data](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**

## <a id="load"></a> Charger des données dans Azure Data Lake Storage

La section suivante décrit comment configurer Azure Data Lake Storage Gen2 pour le test de la hiérarchisation HDFS. Si vous avez déjà des données stockées dans Azure Data Lake Storage, vous pouvez ignorer cette section pour utiliser vos propres données.

1. [Créer un compte de stockage avec des fonctionnalités de Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. [Créez un conteneur d’objets BLOB/système de fichiers](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal) dans ce compte de stockage pour vos données externes.

1. Chargez un fichier CSV ou Parquet dans le conteneur. Il s’agit de données HDFS externes qui vont être montées sur HDFS dans le cluster Big Data.

## <a name="credentials-for-mounting"></a>Informations d'identification pour le montage

### <a name="use-oauth-credentials-to-mount"></a>Utiliser les informations d’identification OAuth pour le montage

Pour pouvoir utiliser les informations d’identification OAuth pour le montage, vous devez suivre les étapes ci-dessous :

1. Allez au [Portail Azure](https://portal.azure.com)
1. Accédez à « Azure Active Directory ». Ce service doit s’afficher dans la barre de navigation de gauche.
1. Dans la barre de navigation de droite, sélectionnez « inscriptions d’applications » et créez une nouvelle inscription.
1. Créez une « application Web » et suivez l’Assistant. **N’oubliez pas le nom de l’application que vous créez ici**. Vous devrez ajouter ce nom à votre compte ADLS en tant qu’utilisateur autorisé. Notez également l’ID client de l’application dans la vue d’ensemble lorsque vous sélectionnez l’application.
1. Une fois l’application Web créée, accédez à « certificats & secrets » et créez une **nouvelle clé secrète client** et sélectionnez une durée de clé. **Ajoutez** la clé secrète.
1.  Revenez à la page inscriptions des applications, puis cliquez sur « points de terminaison » en haut. **Notez le point de terminaison de jeton OAuth (v2)** URL
1. Les éléments suivants doivent maintenant être signalés pour OAuth :

    - « ID client d’application » de l’application Web
    - La clé secrète client
    - Point de terminaison de jeton

### <a name="adding-the-service-principal-to-your-adls-account"></a>Ajout du principal du service à votre compte ADLS

1. Accédez de nouveau au portail et accédez à votre système de fichiers de compte de stockage ADLS, puis sélectionnez contrôle d’accès (IAM) dans le menu de gauche.
1. Sélectionnez « Ajouter une attribution de rôle » 
1. Sélectionner un rôle « collaborateur de données de stockage BLOB »
1. Recherchez le nom que vous avez créé ci-dessus (Notez qu’il n’apparaît pas dans la liste, mais qu’il sera trouvé si vous recherchez le nom complet).
1. Enregistrez le rôle.

Attendre 5 à 10 minutes avant d’utiliser les informations d’identification pour le montage

### <a name="set-environment-variable-for-oauth-credentials"></a>Définir la variable d’environnement pour les informations d’identification OAuth

Ouvrez une invite de commandes sur une machine client pouvant accéder à votre cluster Big Data. Définissez une variable d’environnement au format suivant : Notez que les informations d’identification doivent figurer dans une liste de valeurs séparées par des virgules. La commande « set » est utilisée sur Windows. Si vous êtes sur Linux, utilisez « export » à la place.

   ```text
    set MOUNT_CREDENTIALS=fs.azure.account.auth.type=OAuth,
    fs.azure.account.oauth.provider.type=org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider,
    fs.azure.account.oauth2.client.endpoint=[token endpoint],
    fs.azure.account.oauth2.client.id=[Application client ID],
    fs.azure.account.oauth2.client.secret=[client secret]
   ```

## <a name="use-access-keys-to-mount"></a>Utiliser des clés d’accès pour le montage

Vous pouvez également monter à l’aide des clés d’accès que vous pouvez obtenir pour votre compte ADLS sur le Portail Azure.

 > [!TIP]
   > Pour plus d’informations sur la recherche de la touche d'accès (`<storage-account-access-key>`) pour votre compte de stockage, consultez [Afficher les clés de compte et la chaîne de connexion](/azure/storage/common/storage-account-manage#view-account-keys-and-connection-string).

### <a name="set-environment-variable-for-access-key-credentials"></a>Définir la variable d’environnement pour les informations d’identification de la clé d’accès

1. Ouvrez une invite de commandes sur une machine client pouvant accéder à votre cluster Big Data.

1. Ouvrez une invite de commandes sur une machine client pouvant accéder à votre cluster Big Data. Définissez une variable d’environnement au format suivant. Notez que les informations d’identification doivent figurer dans une liste de valeurs séparées par des virgules. La commande « set » est utilisée sur Windows. Si vous êtes sur Linux, utilisez « export » à la place.

   ```text
   set MOUNT_CREDENTIALS=fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

## <a id="mount"></a> Monter le stockage HDFS distant

Maintenant que vous avez défini la variable d’environnement MOUNT_CREDENTIALS pour les clés d’accès ou à l’aide d’OAuth, vous pouvez commencer le montage. Les étapes suivantes permettent de monter le stockage HDFS distant dans Azure Data Lake vers le stockage HDFS local de votre cluster Big Data.

1. Utilisez **kubectl** pour rechercher l’adresse IP du service **controller-svc-external** du point de terminaison dans votre cluster Big Data. Recherchez **External-IP**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Connectez-vous à **azdata** en utilisant l’adresse IP externe du point de terminaison du contrôleur ainsi que votre nom d’utilisateur et votre mot de passe de cluster :

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
1. Définissez la variable d’environnement MOUNT_CREDENTIALS (faites défiler les instructions)

1. Montez le stockage HDFS distant dans Azure à l’aide de **azdata BDC HDFS Mount Create**. Remplacez les valeurs d’espace réservé avant d’exécuter la commande suivante :

   ```bash
   azdata bdc hdfs mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name>
   ```

   > [!NOTE]
   > La commande créer un montage est asynchrone. À ce stade, aucun message n’indique si le montage a réussi. Consultez la section [état](#status) pour vérifier l’état de vos montages.

Si le montage a été correctement effectué, vous devez pouvoir interroger les données HDFS et exécuter des tâches Spark sur ces dernières. Il apparaît dans le stockage HDFS de votre cluster Big Data à l’emplacement spécifié par `--mount-path`.

## <a id="status"></a> Obtenir l’état des montages

Pour répertorier l’état de tous les montages de votre cluster Big Data, utilisez la commande suivante :

```bash
azdata bdc hdfs mount status
```

Pour répertorier l’état d’un montage situé sur un chemin spécifique dans HDFS, utilisez la commande suivante :

```bash
azdata bdc hdfs mount status --mount-path <mount-path-in-hdfs>
```

## <a name="refresh-a-mount"></a>Actualiser un montage

L’exemple suivant actualise le montage. Cette actualisation efface également le cache de montage.

```bash
azdata bdc hdfs mount refresh --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> Supprimer le montage

Pour supprimer le montage, utilisez la commande **azdata BDC HDFS Mount Delete** et spécifiez le chemin de montage dans HDFS :

```bash
azdata bdc hdfs mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]sur, consultez [que [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]sont ?](big-data-cluster-overview.md).
