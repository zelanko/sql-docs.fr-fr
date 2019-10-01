---
title: Effectuer une mise à niveau vers une nouvelle version
titleSuffix: SQL Server big data clusters
description: Découvrez comment mettre à niveau [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (version préliminaire) vers une nouvelle version.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bb1bf33c9ccb342e6afc4d22d67463791c0d67b6
ms.sourcegitcommit: 36c3ead6f2a3628f58040acf47f049f0b0957b8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71688274"
---
# <a name="how-to-upgrade-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Procédure de mise à niveau de [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article fournit des conseils sur la façon de mettre à niveau un cluster Big Data SQL Server vers une nouvelle version. Les étapes décrites dans cet article s’appliquent spécifiquement à la mise à niveau entre des préversions.

## <a name="backup-and-delete-the-old-cluster"></a>Sauvegarder et supprimer l’ancien cluster

La seule façon de mettre à niveau un cluster Big Data vers une nouvelle version consiste à supprimer le cluster et à le recréer manuellement. Chaque version a une version unique de `azdata` qui n’est pas compatible avec la version précédente. En outre, si un cluster plus ancien devait télécharger une image sur un nouveau nœud, la dernière image risquerait de ne pas être compatible avec les anciennes images sur le cluster. Pour effectuer une mise à niveau vers la dernière version, procédez comme suit :

1. Avant de supprimer l’ancien cluster, sauvegardez les données sur l’instance maître SQL Server et sur HDFS. Pour l’instance maître SQL Server, vous pouvez utiliser [Sauvegarde et restauration d’une base de données SQL Server](data-ingestion-restore-database.md). Pour HDFS, vous [pouvez copier les données avec `curl`](data-ingestion-curl.md).

1. Supprimez l’ancien cluster à l’aide de la commande `azdata delete cluster`.

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > Utilisez la version de `azdata` qui correspond à votre cluster. Ne supprimez pas un cluster plus ancien avec la version plus récente de `azdata`.

   > [!Note]
   > L’émission d’une commande `azdata bdc delete` entraînera la suppression de tous les objets créés dans l’espace de noms identifié par le nom du cluster Big Data, mais pas de l’espace de noms lui-même. L’espace de noms peut être réutilisé pour les déploiements suivants, à condition qu’il soit vide et qu’aucune autre application n’ait été créée dans.

1. Avant CTP 3,2, `azdata` était appelé `mssqlctl`. Si vous avez installé des versions antérieures de `mssqlctl` ou `azdata`, il est important de commencer par désinstaller avant d’installer la dernière version de `azdata`.

   Pour CTP  version 2.3 ou ultérieure, exécutez la commande suivante. Remplacez `ctp3.1` dans la commande par la version de `mssqlctl` que vous désinstallez. Si la version est antérieure à CTP 3.1, ajoutez un tiret avant le numéro de version (par exemple, `ctp-2.5`).

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Installez la dernière version de `azdata`. Les commandes suivantes installent `azdata` pour la version Release candidate :

   **Windows :**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **Linux :**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > Pour chaque version, le chemin d’accès à `azdata` change. Même si vous avez déjà installé `azdata` ou `mssqlctl`, vous devez réinstaller à partir du chemin le plus récent avant de créer le nouveau cluster.

## <a id="azdataversion"></a> Vérifier la version d’azdata

Avant de déployer un nouveau cluster Big Data, vérifiez que vous utilisez la dernière version de `azdata` avec le paramètre `--version` :

```bash
azdata --version
```

## <a name="install-the-new-release"></a>Installer la nouvelle version

Après avoir supprimé le cluster Big Data précédent et installé la dernière version de `azdata`, déployez le nouveau cluster Big Data à l’aide des instructions de déploiement actuelles. Pour plus d’informations, consultez [comment déployer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] sur Kubernetes](deployment-guidance.md). Ensuite, restaurez les bases de données ou les fichiers requis.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, voir [qu’est-ce que [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](big-data-cluster-overview.md).
