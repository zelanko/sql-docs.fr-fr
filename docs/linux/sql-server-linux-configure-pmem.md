---
title: Comment configurer la mémoire persistante (PMEM) pour SQL Server sur Linux | Microsoft Docs
description: Cet article fournit une procédure pas à pas pour la configuration PMEM sur Linux.
author: DBArgenis
ms.author: argenisf
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 42b51f28682ea7c53b5aa6f33ac2e6aa61a121ed
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46714957"
---
# <a name="how-to-configure-persistent-memory-pmem-for-sql-server-on-linux"></a>Comment configurer la mémoire persistante (PMEM) pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article décrit comment configurer la mémoire persistante (PMEM) pour SQL Server sur Linux. Prise en charge PMEM sur Linux a été introduite dans SQL Server 2019 CTP 2.0.

## <a name="overview"></a>Vue d'ensemble

SQL Server 2016 introduit la prise en charge de barrettes DIMM Non Volatile, et une optimisation appelé [fin de la mise en cache du journal sur le dispositif NVDIMM]( https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/) qui réduit la quantité d’opérations nécessaires pour renforcer un tampon de journal vers le stockage persistant. Cela s’appuie sur les capacités de Windows Server pour accéder directement à un périphérique de mémoire persistante en mode DAX.

Version préliminaire de SQL Server 2019 s’étend la prise en charge de mémoire persistante appareils (PMEM) pour Linux, offrant révération complète des données et les fichiers journaux placés sur PMEM. Révération fait référence à la méthode d’accès au périphérique de stockage à l’aide d’opérations de memcpy espace utilisateur efficace. Au lieu de passer en revue la pile de stockage et de système de fichier, SQL Server s’appuie sur la prise en charge DAX sur Linux pour placer directement les données sur les appareils, encourir dans une latence minimale.

## <a name="enable-enlightenment-of-database-files"></a>Activer les connaissances des fichiers de base de données
Pour activer les connaissances de fichiers de base de données dans SQL Server sur Linux, suivez les étapes suivantes :

1. Configurer les appareils dans Linux, cette opération est effectuée à l’aide de la `ndctl` utilitaire.

  - Installer installation `ndctl` configurer pmem périphérique. Vous pouvez le trouver [ici](https://docs.pmem.io/getting-started-guide/installing-ndctl).
  - Utilisez [ndctl] pour créer un espace de noms.

  ```bash 
  ndctl create-namespace -f -e namespace0.0 --mode=fsdax* –map=mem
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

  - Créer et monter pmem appareil

    Par exemple, avec XFS

    ```bash
    mkfs.xfs -f /dev/pmem0
    mount –o dax,noatime /dev/pmem0 /mnt/dax
    xfs_io -c "extsize 2m" /mnt/dax
    ```

    Par exemple, avec EXT4

    ```bash
    mkfs.ext4 -b 4096 -E stride=512 -F /dev/pmem0
    mount –o dax,noatime /dev/pmem0 /mnt/dax
    ```

  Une fois que l’appareil a été configuré avec ndctl, formaté et monté, vous pouvez placer les fichiers de base de données qu’il contient. Vous pouvez également créer une nouvelle base de données 

1. Activer révération de fichier de base de données SQL Server à l’aide de l’indicateur de trace 3979. Cet indicateur de trace est un indicateur de trace de démarrage et doit être activé à l’aide de l’utilitaire mssql-conf.

1. Redémarrez SQL Server.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur SQL Server sur Linux, consultez [SQL Server sur Linux](sql-server-linux-overview.md).
