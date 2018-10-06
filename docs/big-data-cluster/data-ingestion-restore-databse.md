---
title: Restaurer une base de données dans un cluster de données volumineux de SQL Server | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 04514fb0184fa28e0ba959f3dd33cb2e1ec945cb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796106"
---
# <a name="restore-a-database-into-the-sql-server-big-data-cluster-master-instance"></a>Restaurer une base de données dans l’instance principale de SQL Server des données big cluster

Pour importer une base de données SQL Server existant dans l’instance principale, nous vous recommandons d’utiliser une sauvegarde, copie et de restauration approche.  Dans cet exemple, nous allons montrer comment restaurer la base de données AdventureWorks, mais vous pouvez utiliser n’importe quelle sauvegarde de base de données dont vous disposez.  Vous pouvez télécharger la sauvegarde AdventureWorks [ici](https://www.microsoft.com/en-us/download/details.aspx?id=49502).

Tout d’abord, sauvegardez votre base de données SQL Server existante sur SQL Server sur Windows ou Linux à l’aide d’une des méthodes habituelles de création d’une sauvegarde de base de données.

Copiez le fichier de sauvegarde sur le conteneur de SQL Server dans le pod de l’instance principale du cluster Kubernetes.

```bash
kubectl cp <path to .bak file> mssql-data-pool-master-0:/tmp/ -c mssql-data-pool-data -n <name of your cluster>
```

Exemple :

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-data-pool-master-0:/tmp/ -c mssql-data-pool-data -n clustertest
```

Ensuite, vérifiez que le fichier de sauvegarde a été copié dans le conteneur de pod.

```bash
kubectl exec -it mssql-data-pool-master-0 -n <name of your cluster> -c mssql-data-pool-data -- bin/bash
root@mssql-data-pool-master-0:/# ls /tmp
root@mssql-data-pool-master-0:/# exit
```

Exemple :

```bash
kubectl exec -it mssql-data-pool-master-0 -n clustertest -c mssql-data-pool-data -- bin/bash
root@mssql-data-pool-master-0:/# ls /tmp
```

Ensuite, restaurez la sauvegarde de base de données master instance SQL Server.  Si vous restaurez une sauvegarde de base de données qui a été créée sur Windows, vous devrez obtenir les noms des fichiers.  Dans Studio Ops connecté à l’instance principale, exécutez ce script SQL :

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/<db file name>.bak'
```

Exemple :

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
```

![Liste des fichiers de sauvegarde](media/restore-database/database-restore-file-list.png)

À présent, restaurer la base de données avec un script comme celui-ci, en remplaçant les noms/chemins d’accès en fonction des besoins en fonction de votre sauvegarde de base de données.

```sql
RESTORE DATABASE AdventureWorks2016CTP3
FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
WITH MOVE 'AdventureWorks2016CTP3_Data' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Data.mdf',
        MOVE 'AdventureWorks2016CTP3_Log' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Log.ldf',
        MOVE 'AdventureWorks2016CTP3_mod' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_mod'
```

Maintenant, si vous souhaitez que votre base de données de valeur élevée pouvoir accéder aux pools de données que vous devez configurer le pool de données des procédures stockées en ouvrant et en exécutant les scripts à partir du référentiel GitHub.

Exécuter le **haute-valeur-db-configuration\data_pool_ddl_install. SQL** script.

- Les procédures de prise en charge stocké de paramétrage

Exécuter le **haute-valeur-db-configuration\supportability. SQL** script.
