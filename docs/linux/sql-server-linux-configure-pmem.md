---
title: Comment configurer la mémoire persistante (PMEM) pour SQL Server sur Linux
description: Cet article explique de façon détaillée comment configurer PMEM sur Linux.
author: briancarrig
ms.author: brcarrig
ms.reviewer: vanto
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 6f9a5d8c6b2db65bd237f0a3a267638a8cc16b68
ms.sourcegitcommit: 071065bc5433163ebfda4fdf6576349f9d195663
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71923829"
---
# <a name="how-to-configure-persistent-memory-pmem-for-sql-server-on-linux"></a>Comment configurer la mémoire persistante (PMEM) pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article décrit comment configurer la mémoire persistante (PMEM) pour SQL Server sur Linux. La prise en charge de PMEM sur Linux a été introduite dans la préversion de SQL Server 2019.

## <a name="overview"></a>Vue d’ensemble

SQL Server 2016 a introduit la prise en charge des DIMM non volatiles et une optimisation appelée [Fin de la mise en cache des journaux sur NVDIMM]( https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/). Ces optimisations ont réduit le nombre d’opérations nécessaires pour renforcer la mémoire tampon d’un journal dans un stockage persistant. Ceci est dû à l’accès direct de Windows Server à un appareil de mémoire persistante en mode DAX.

La préversion de SQL Server 2019 étend la prise en charge des appareils à mémoire persistante (PMEM) à Linux, fournissant un état d'éveil à la présence d'un environnement virtualisé des fichiers de données et de journaux de transactions placés sur PMEM. L’état d'éveil à la présence d'un environnement virtualisé fait référence à la méthode d’accès au dispositif de stockage à l’aide d'opérations d’espace utilisateur efficaces `memcpy()`. Au lieu de passer par le système de fichiers et la pile de stockage, SQL Server tire parti de la prise en charge de DAX sur Linux pour placer directement les données dans les appareils, ce qui réduit la latence.

## <a name="enable-enlightenment-of-database-files"></a>Activer l’état d'éveil à la présence d'un environnement virtualisé des fichiers de base de données
Pour activer l’état d'éveil à la présence d'un environnement virtualisé de fichiers de base de données dans SQL Server sur Linux, procédez comme suit :

1. Configurez les appareils.

  Dans Linux, utilisez l’utilitaire `ndctl`.

  - Installez `ndctl` pour configurer l’appareil PMEM. Vous pouvez le trouver [ici](https://docs.pmem.io/getting-started-guide/installing-ndctl).
  - Utilisez [ndctl] pour créer un espace de noms.

  ```bash 
  ndctl create-namespace -f -e namespace0.0 --mode=fsdax* --map=mem
  ```

  >[!NOTE]
  >Si vous utilisez une version de `ndctl` antérieure à 59, utilisez `--mode=memory`.

  Utilisez `ndctl` pour vérifier l’espace de noms. Un exemple est alors sorti :

```bash
ndctl list
[
  {
    "dev":"namespace0.0",
    "mode":"memory",
    "size":1099511627776,
    "blockdev":"pmem0",
    "numa_node":0
  }
]
```

  - Créez et montez un appareil PMEM

    Par exemple, avec XFS

    ```bash
    mkfs.xfs -f /dev/pmem0
    mount -o dax,noatime /dev/pmem0 /mnt/dax
    xfs_io -c "extsize 2m" /mnt/dax
    ```

    Par exemple, avec EXT4

    ```bash
    mkfs.ext4 -b 4096 -E stride=512 -F /dev/pmem0
    mount -o dax,noatime /dev/pmem0 /mnt/dax
    ```

  Une fois que l’appareil a été configuré avec ndctl, formaté et monté, vous pouvez y placer des fichiers de base de données. Vous pouvez également créer une nouvelle base de données 

1. Étant donné que les appareils PMEM sont O_DIRECT sécurisés, activez l’indicateur de trace 3979 pour désactiver le mécanisme de vidage forcé. Cet indicateur de trace est un indicateur de trace de démarrage qui doit être activé à l’aide de l’utilitaire mssql-conf. Notez qu’il s’agit d’une modification de la configuration qui concerne l’ensemble du serveur et que vous ne devez pas utiliser cet indicateur de trace si vous avez des appareils non conformes à O_DIRECT, qui ont besoin du mécanisme de vidage forcé pour garantir l’intégrité des données. Pour plus d'informations, consultez https://support.microsoft.com/en-us/help/4131496/enable-forced-flush-mechanism-in-sql-server-2017-on-linux

1. Redémarrez SQL Server.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur SQL Server sur Linux, consultez [SQL Server sur Linux](sql-server-linux-overview.md).
