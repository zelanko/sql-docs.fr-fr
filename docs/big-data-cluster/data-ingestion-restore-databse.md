---
title: Restaurer une base de données
titleSuffix: SQL Server 2019 big data clusters
description: Cet article explique comment restaurer une base de données sur l’instance principale d’un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: 854f31f6ac04e9767ff1fc12cfb04f5d28c2aa13
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030823"
---
# <a name="restore-a-database-into-the-sql-server-2019-big-data-cluster-master-instance"></a>Restaurer une base de données dans l’instance principale de SQL Server 2019 big data cluster

Cet article décrit comment restaurer une base de données existante sur l’instance principale d’un cluster de données volumineuses de SQL Server 2019 (version préliminaire). La méthode recommandée consiste à utiliser une copie de sauvegarde et restaurer l’approche.

## <a name="backup-your-existing-database"></a>Sauvegarder votre base de données existante

Tout d’abord, sauvegardez votre base de données SQL Server existante à partir de SQL Server sur Windows ou Linux. Utilisez les techniques de sauvegarde standard avec Transact-SQL ou un outil comme SQL Server Management Studio (SSMS).

Cet article explique comment restaurer la base de données AdventureWorks, mais vous pouvez utiliser n’importe quelle sauvegarde de base de données. 

> [!TIP]
> Vous pouvez télécharger la sauvegarde AdventureWorks [ici](https://www.microsoft.com/download/details.aspx?id=49502).

## <a name="copy-the-backup-file"></a>Copiez le fichier de sauvegarde

Copiez le fichier de sauvegarde sur le conteneur de SQL Server dans le pod de l’instance principale du cluster Kubernetes.

```bash
kubectl cp <path to .bak file> mssql-master-pool-0:/tmp -c mssql-server -n <name of your cluster>
```

Exemple :

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-master-pool-0:/tmp -c mssql-server -n clustertest
```

Ensuite, vérifiez que le fichier de sauvegarde a été copié dans le conteneur de pod.

```bash
kubectl exec -it mssql-master-pool-0 -n <name of your cluster> -c mssql-server -- bin/bash
cd /var/
ls /tmp
exit
```

Exemple :

```bash
kubectl exec -it mssql-master-pool-0 -n clustertest -c mssql-server -- bin/bash
ls /tmp
exit
```

## <a name="restore-the-backup-file"></a>Restaurer le fichier de sauvegarde

Ensuite, restaurez la sauvegarde de base de données master instance SQL Server.  Si vous restaurez une sauvegarde de base de données qui a été créée sur Windows, vous devrez obtenir les noms des fichiers.  Dans Azure Data Studio, connectez-vous à l’instance principale et exécutez ce script SQL :

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/<db file name>.bak'
```

Exemple :

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
```

![Liste des fichiers de sauvegarde](media/restore-database/database-restore-file-list.png)

À présent, restaurez la base de données. Le script suivant est un exemple. Remplacez les noms/chemins d’accès en fonction des besoins en fonction de votre sauvegarde de base de données.

```sql
RESTORE DATABASE AdventureWorks2016CTP3
FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
WITH MOVE 'AdventureWorks2016CTP3_Data' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Data.mdf',
        MOVE 'AdventureWorks2016CTP3_Log' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Log.ldf',
        MOVE 'AdventureWorks2016CTP3_mod' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_mod'
```

## <a name="configure-data-pool-and-hdfs-access"></a>Configurer le pool de données et des accès HDFS

Maintenant, pour l’instance principale de SQL Server pour les pools de données access et HDFS, exécutez les procédures stockée de pool pool et le stockage des données. Exécutez les scripts Transact-SQL suivants sur votre base de données nouvellement restaurée :

```sql
USE AdventureWorks2016CTP3
GO 
IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
    CREATE EXTERNAL DATA SOURCE SqlDataPool
    WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');

IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
    CREATE EXTERNAL DATA SOURCE SqlStoragePool
    WITH (LOCATION = 'sqlhdfs://service-mssql-controller:8080');
GO
```

> [!NOTE]
> Vous devrez exécuter ces scripts d’installation uniquement pour les bases de données restaurées à partir de versions antérieures de SQL Server. Si vous créez une nouvelle base de données dans l’instance principale de SQL Server, les procédures de magasin pool pool et le stockage des données sont déjà configurés pour vous.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez la présentation suivante :

- [Quelles sont les clusters SQL Server 2019 big data ?](big-data-cluster-overview.md)
