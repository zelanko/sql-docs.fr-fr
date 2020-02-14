---
title: Ajouter une mémoire tampon de journal persistante à une base de données
ms.custom: ''
ms.date: 10/30/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- PMEM
- persistent memory
- persisted log buffer
- add log file
- create log buffer
- remove log buffer
ms.assetid: 8ead516a-1334-4f40-84b2-509d0a8ffa45
author: briancarrig
ms.author: brcarrig
manager: amitban
ms.openlocfilehash: cc455ce62708f488224c4df6245f14eef8b2053d
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76832230"
---
# <a name="add-persisted-log-buffer-to-a-database"></a>Ajouter une mémoire tampon de journal persistante à une base de données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette rubrique explique comment ajouter une mémoire tampon de journal persistante à une base de données dans [!INCLUDE[sqlv15](../../includes/sssqlv15-md.md)] en utilisant [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="permissions"></a>Autorisations

Nécessite l'autorisation ALTER sur la base de données.  

## <a name="configure-persistent-memory-device-linux"></a>Configurer un module de mémoire persistante (Linux)

Pour configurer un module de mémoire persistante dans [Linux](../../linux/sql-server-linux-configure-pmem.md).

## <a name="configure-persistent-memory-device-windows"></a>Configurer un module de mémoire persistante (Windows)

Pour configurer un module de mémoire persistante dans [Windows](/windows-server/storage/storage-spaces/deploy-pmem/).
  
## <a name="add-a-persisted-log-buffer-to-a-database"></a>Ajouter une mémoire tampon de journal persistante à une base de données  

Les exemples suivants ajoutent une mémoire tampon de journal persistante.

```sql
ALTER DATABASE <MyDB> 
  ADD LOG FILE 
  (
    NAME = <DAXlog>, 
    FILENAME = '<Filepath to DAX Log File>', 
    SIZE = 20MB
  );
```

Le volume ou le montage sur lequel le nouveau fichier journal est placé doit être formaté avec DAX (NTFS) ou monté avec l’option DAX (XFS/EXT4).

## <a name="remove-a-persisted-log-buffer"></a>Supprimer une mémoire tampon de journal persistante

Pour supprimer de manière sécurisée une mémoire tampon de journal persistante, la base de données doit être placée en mode mono-utilisateur afin de vider la mémoire tampon de journal persistante.

L’exemple suivant supprime une mémoire tampon de journal persistante.

```sql
ALTER DATABASE <MyDB> SET SINGLE_USER;
ALTER DATABASE <MyDB> REMOVE FILE <DAXlog>;
ALTER DATABASE <MyDB> SET MULTI_USER;
```

## <a name="limitations"></a>Limites

[Transparent Data Encryption (TDE)](../security/encryption/transparent-data-encryption.md) n’est pas compatible avec la mémoire tampon de journal persistante.

Les [groupes de disponibilité](../../t-sql/statements/create-availability-group-transact-sql.md) ne peuvent utiliser cette fonctionnalité que sur des réplicas secondaires en raison du besoin d’une sémantique d’écriture de journal normale sur le réplica principal. Cependant, le petit fichier journal doit être créé sur tous les nœuds (idéalement sur des volumes ou des montages DAX).

## <a name="backup-and-restore-operations"></a>Opérations de sauvegarde et de restauration

Les conditions de restauration normales s’appliquent. Si la mémoire tampon de journal persistante est restaurée sur un volume ou un montage DAX, elle continue de fonctionner. Sinon, elle peut être supprimée de manière sécurisée.
  
## <a name="next-steps"></a>Étapes suivantes

- [How It Works (It Just Runs Faster): Non-Volatile Memory SQL Server Tail Of Log Caching on NVDIMM](https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/)
- [Data exposed: Latency and Durability with SQL Server 2016](https://channel9.msdn.com/Shows/Data-Exposed/Latency-and-Durability-with-SQL-Server-2016)
- [Accélération de la latence de validation des transactions en utilisant la mémoire de classe stockage dans Windows Server 2016/SQL Server 2016 SP1](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/12/02/transaction-commit-latency-acceleration-using-storage-class-memory-in-windows-server-2016sql-server-2016-sp1/)
