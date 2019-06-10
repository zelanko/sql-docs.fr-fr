---
title: Effectuer une mise à niveau vers une nouvelle version
titleSuffix: SQL Server big data clusters
description: Découvrez comment mettre à niveau des clusters de données volumineuses de SQL Server 2019 (version préliminaire) vers une nouvelle version.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3af688d607e8ec2d9dad7efe0d2275840c48cba8
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66782235"
---
# <a name="how-to-upgrade-sql-server-big-data-clusters"></a>Comment mettre à niveau des clusters de données volumineuses de SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article fournit des conseils sur la mise à niveau un cluster de données volumineux de SQL Server vers une nouvelle version. Les étapes décrites dans cet article s’appliquent spécifiquement à la mise à niveau entre des versions préliminaires.

## <a name="backup-and-delete-the-old-cluster"></a>Sauvegardez et supprimez l’ancien cluster

Actuellement, la seule façon de mettre à niveau un cluster de données volumineux vers une nouvelle version consiste à supprimer et recréer le cluster manuellement. Chaque version comporte une version unique de **mssqlctl** qui n’est pas compatible avec la version précédente. En outre, si un cluster plus anciens avait télécharger une image sur un nouveau nœud, la dernière image peut-être pas compatible avec les anciennes images sur le cluster. Pour mettre à niveau vers la dernière version, procédez comme suit :

1. Avant de supprimer l’ancien cluster, sauvegardez les données sur l’instance principale de SQL Server et sur HDFS. Pour l’instance principale de SQL Server, vous pouvez utiliser [sauvegarde et restauration SQL Server](data-ingestion-restore-database.md). Système de fichiers HDFS, vous [peut copier les données avec **curl**](data-ingestion-curl.md).

1. Supprimer l’ancien cluster avec le `mssqlctl delete cluster` commande.

   ```bash
    mssqlctl cluster delete --name <old-cluster-name>
   ```

   > [!Important]
   > Utilisez la version de **mssqlctl** qui correspond à votre cluster. Ne supprimez pas un cluster plus anciens avec la version la plus récente de **mssqlctl**.

1. Si vous disposez de toutes les versions précédentes de **mssqlctl** installé, il est important de désinstaller **mssqlctl** premier avant d’installer la dernière version.

   Si vous désinstallez **mssqlctl** correspondant à CTP 2.2 ou exécution inférieur :

   ```powershell
   pip3 uninstall mssqlctl
   ```

   Pour CTP 2.3 ou version ultérieure, exécutez la commande suivante. Remplacez `ctp-2.5` dans la commande avec la version de **mssqlctl** que vous désinstallez :

   ```powershell
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp-2.5/mssqlctl/requirements.txt
   ```

1. Installez la dernière version de **mssqlctl**. Les commandes suivantes installent **mssqlctl** pour CTP 3.0 :

   **Windows :**

   ```powershell
   pip3 install -r  https://private-repo.microsoft.com/python/ctp3.0/mssqlctl/requirements.txt
   ```

   **Linux :**

   ```bash
   pip3 install -r  https://private-repo.microsoft.com/python/ctp3.0/mssqlctl/requirements.txt --user
   ```

   > [!IMPORTANT]
   > Pour chaque version, le chemin d’accès à **mssqlctl** modifications. Même si vous avez installé précédemment **mssqlctl**, vous devez réinstaller à partir du chemin plus récent avant de créer le nouveau cluster.

## <a id="mssqlctlversion"></a> Vérifier la version mssqlctl

Avant de déployer un nouveau cluster de données volumineuses, vérifiez que vous utilisez la dernière version de **mssqlctl** avec la `--version` paramètre :

```bash
mssqlctl --version
```

## <a name="install-the-new-release"></a>Installer la nouvelle version

Après avoir supprimé le précédent cluster big data et de l’installation de la dernière version **mssqlctl**, déployer le nouveau cluster de données volumineuses en suivant les instructions de déploiement actuel. Pour plus d’informations, consultez [comment déployer des données volumineuses de SQL Server clusters sur Kubernetes](deployment-guidance.md). Ensuite, restaurez les bases de données requises ou les fichiers.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses, consultez [que sont les clusters de données volumineuses de SQL Server](big-data-cluster-overview.md).
