---
title: Changer le compte pour la journalisation SSIS Scale Out| Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dcedbe0d2c2ef2c2089af1e2a8b31fbeb75ce2fc
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="change-the-account-for-scale-out-logging"></a>Changer le compte pour la journalisation Scale Out
Quand vous exécutez des packages dans Scale Out, les messages d’événement sont journalisés dans SSISDB avec un utilisateur créé automatiquement **##MS_SSISLogDBWorkerAgentLogin##**. La connexion de cet utilisateur utilise l’authentification SQL Server. Pour changer le compte, suivez les étapes ci-après :

## <a name="1-create-a-user-of-ssisdb"></a>1. Créer un utilisateur de SSISDB
Pour savoir comment créer un utilisateur de base de données, consultez [Créer un utilisateur de base de données](../../relational-databases/security/authentication-access/create-a-database-user.md).

## <a name="2-add-the-user-to-database-role-ssisclusterworker"></a>2. Ajouter l’utilisateur au rôle de base de données ssis_cluster_worker

Pour savoir comment joindre un rôle de base de données, consultez [Joindre un rôle](../../relational-databases/security/authentication-access/join-a-role.md).

## <a name="3-update-logging-information-in-ssisdb"></a>3. Mettre à jour les informations de journalisation dans SSISDB
Appelez la procédure stockée [catalog].[update_logdb_info] en utilisant le nom du serveur SQL Server et la chaîne de connexion comme paramètres.

#### <a name="example"></a>Exemple
```sql
SET @serverName = CONVERT(sysname, SERVERPROPERTY('servername'))
SET @connectionString = 'Data Source=' + @serverName + ';Initial Catalog=SSISDB;Integrated Security=SSPI;'
EXEC [internal].[update_logdb_info] @serverName, @connectionString
GO
```

## <a name="4-restart-scale-out-worker-service"></a>4. Redémarrer le service Scale Out Worker

> [!NOTE]
> Si vous utilisez un compte d’utilisateur Windows pour la journalisation, celui-ci doit correspondre au même compte qui exécute le service Scale Out Worker. Sinon, la connexion à SQL Server échoue.
