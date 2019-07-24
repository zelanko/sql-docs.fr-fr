---
title: Effectuer une mise à niveau vers une nouvelle version
titleSuffix: SQL Server big data clusters
description: Découvrez comment mettre à niveau des clusters SQL Server 2019 Big Data (version préliminaire) vers une nouvelle version.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7bdb1eb59fd36d065df9dba0f6d6879c1a294914
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419384"
---
# <a name="how-to-upgrade-sql-server-big-data-clusters"></a>Comment mettre à niveau des clusters SQL Server Big Data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article fournit des conseils sur la façon de mettre à niveau un cluster SQL Server Big Data vers une nouvelle version. Les étapes décrites dans cet article s’appliquent spécifiquement à la mise à niveau entre les versions préliminaires.

## <a name="backup-and-delete-the-old-cluster"></a>Sauvegarder et supprimer l’ancien cluster

Actuellement, la seule façon de mettre à niveau un cluster Big Data vers une nouvelle version consiste à supprimer manuellement le cluster et à le recréer. Chaque version a une version unique de **azdata** qui n’est pas compatible avec la version précédente. En outre, si un cluster plus ancien devait télécharger une image sur un nouveau nœud, la dernière image risque de ne pas être compatible avec les anciennes images sur le cluster. Pour effectuer une mise à niveau vers la dernière version, procédez comme suit:

1. Avant de supprimer l’ancien cluster, sauvegardez les données sur l’instance principale de SQL Server et sur HDFS. Pour l’instance SQL Server Master, vous pouvez utiliser [SQL Server la sauvegarde et la restauration](data-ingestion-restore-database.md). Pour HDFS, vous [pouvez copier les données avec l' **accolade**](data-ingestion-curl.md).

1. Supprimez l’ancien cluster à `azdata delete cluster` l’aide de la commande.

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > Utilisez la version de **azdata** qui correspond à votre cluster. Ne supprimez pas un cluster plus ancien avec la version plus récente de **azdata**.

1. Avant CTP 3,2, **azdata** était appelé **mssqlctl**. Si vous avez installé des versions précédentes de **mssqlctl** ou **azdata** , il est important de commencer par désinstaller avant d’installer la dernière version de **azdata**.

   Pour la version CTP 2,3 ou une version ultérieure, exécutez la commande suivante. Remplacez `ctp3.1` dans la commande par la version de **mssqlctl** que vous désinstallez. Si la version est antérieure à CTP 3,1, ajoutez un tiret avant le numéro de version (par exemple `ctp-2.5`,).

   ```powershell
   pip3 uninstall -r https://mcr.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Installez la dernière version de **azdata**. Les commandes suivantes installent **azdata** pour CTP 3,2:

   **Windows**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **Linux**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > Pour chaque version, le chemin d’accès à **azdata** change. Même si vous avez déjà installé **azdata** ou **mssqlctl**, vous devez réinstaller à partir du chemin d’accès le plus récent avant de créer le nouveau cluster.

## <a id="azdataversion"></a>Vérifier la version de azdata

Avant de déployer un nouveau cluster Big Data, vérifiez que vous utilisez la dernière version de **azdata** avec le `--version` paramètre:

```bash
azdata --version
```

## <a name="install-the-new-release"></a>Installer la nouvelle version

Après avoir supprimé le cluster Big Data précédent et installé la dernière version de **azdata**, déployez le nouveau cluster Big Data à l’aide des instructions de déploiement actuelles. Pour plus d’informations, consultez [comment déployer des clusters SQL Server Big Data sur Kubernetes](deployment-guidance.md). Ensuite, restaurez les bases de données ou les fichiers requis.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [que sont les SQL Server Big Data les clusters](big-data-cluster-overview.md).
