---
title: Comment configurer la mémoire persistante (PMEM) pour SQL Server sur Linux
description: Cet article fournit une procédure pas à pas pour la configuration PMEM sur Linux.
author: DBArgenis
ms.author: argenisf
ms.reviewer: vanto
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 4ed705b1b26193585a6278508ac98666d069418a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077562"
---
# <a name="how-to-configure-persistent-memory-pmem-for-sql-server-on-linux"></a>Comment configurer la mémoire persistante (PMEM) pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article décrit comment configurer la mémoire persistante (PMEM) pour SQL Server sur Linux. Prise en charge PMEM sur Linux a été introduite dans la version préliminaire de SQL Server 2019.

## <a name="overview"></a>Vue d'ensemble

SQL Server 2016 introduit la prise en charge de barrettes DIMM Non Volatile, et une optimisation appelé [fin de la mise en cache du journal sur le dispositif NVDIMM]( https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/). Ces optimisations réduit le nombre d’opérations nécessaires pour renforcer un tampon de journal vers le stockage persistant. Cela s’appuie sur Windows Server un accès direct à un périphérique de mémoire persistante en mode DAX.

Version préliminaire de SQL Server 2019 s’étend la prise en charge de mémoire persistante appareils (PMEM) pour Linux, offrant révération complète des données et les fichiers journaux placés sur PMEM. Révération fait référence à la méthode d’accès au périphérique de stockage à l’aide d’espace utilisateur efficace `memcpy()` operations. Au lieu de passer en revue la pile de stockage et de système de fichier, SQL Server s’appuie sur la prise en charge DAX sur Linux à placer directement les données dans les appareils, ce qui réduit la latence.

## <a name="enable-enlightenment-of-database-files"></a>Activer les connaissances des fichiers de base de données
Pour activer les connaissances de fichiers de base de données dans SQL Server sur Linux, suivez les étapes suivantes :

1. Configurer les appareils.

  Sous Linux, utilisez la `ndctl` utilitaire.

  - Installer `ndctl` configurer PMEM périphérique. Vous pouvez le trouver [ici](https://docs.pmem.io/getting-started-guide/installing-ndctl).
  - Utilisez [ndctl] pour créer un espace de noms.

  ```bash 
  ndctl create-namespace -f -e namespace0.0 --mode=fsdax* --map=mem
  ```

  >[!NOTE]
  >Si vous utilisez `ndctl` version inférieure à 59, utilisez `--mode=memory`.

  Utilisez `ndctl` pour vérifier l’espace de noms. Exemple de sortie suivant :

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

  - Créer et monter PMEM appareil

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

  Une fois que l’appareil a été configuré avec ndctl, formaté et monté, vous pouvez placer les fichiers de base de données qu’il contient. Vous pouvez également créer une nouvelle base de données 

1. Étant donné que les appareils PMEM sont O_DIRECT sans échec, activez l’indicateur de trace 3979 pour désactiver le mécanisme de vidage forcé. Cet indicateur de trace est un indicateur de trace de démarrage et doit être activé à l’aide de l’utilitaire mssql-conf. Veuillez noter qu’il s’agit d’une modification de configuration de l’échelle du serveur, et vous ne devez pas utiliser cet indicateur de trace si vous avez tous les appareils non conformes O_DIRECT nécessitant le mécanisme de vidage forcé pour garantir l’intégrité des données. Pour plus d’informations, consultez https://support.microsoft.com/en-us/help/4131496/enable-forced-flush-mechanism-in-sql-server-2017-on-linux

1. Redémarrez SQL Server.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur SQL Server sur Linux, consultez [SQL Server sur Linux](sql-server-linux-overview.md).
