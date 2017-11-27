---
title: Modifier le compte pour la journalisation SSIS monter en charge | Documents Microsoft
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ec785459e5f9585776d83cde3f460c1e79367e46
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="change-the-account-for-scale-out-logging"></a>Modifier le compte pour la journalisation de monter en charge
Lors de l’exécution des packages de monter en charge, les messages d’événement sont journalisés dans SSISDB avec un utilisateur créées automatiquement **MS_SSISLogDBWorkerAgentLogin ## ##**. La connexion de cet utilisateur utilise l’authentification SQL Server. Pour modifier le compte, suit les étapes ci-dessous :

## <a name="1-create-a-user-of-ssisdb"></a>1. Créer un utilisateur de SSISDB
Pour obtenir des instructions de création d’un utilisateur de base de données, consultez [créer un utilisateur de base de données](../../relational-databases/security/authentication-access/create-a-database-user.md).

## <a name="2-add-the-user-to-database-role-ssisclusterworker"></a>2. Ajoutez l’utilisateur à ssis_cluster_worker de rôle de base de données

Pour obtenir des instructions de jointure d’un rôle de base de données, consultez [joindre un rôle](../../relational-databases/security/authentication-access/join-a-role.md).

## <a name="3-update-logging-information-in-ssisdb"></a>3. Mettre à jour les informations de journalisation dans SSISDB
Appelez la procédure stockée [catalogue]. [update_logdb_info] avec la chaîne de nom et une connexion Sql Server en tant que paramètres.

#### <a name="example"></a>Exemple
```sql
SET @serverName = CONVERT(sysname, SERVERPROPERTY('servername'))
SET @connectionString = 'Data Source=' + @serverName + ';Initial Catalog=SSISDB;Integrated Security=SSPI;'
EXEC [internal].[update_logdb_info] @serverName, @connectionString
GO
```

## <a name="4-restart-scale-out-worker-service"></a>4. Redémarrez le service de mise à l’échelle des processus de travail

> [!NOTE]
> Si vous utilisez un compte d’utilisateur Windows pour la journalisation, elle doit être le même compte de service de mise à l’échelle des processus de travail en cours d’exécution. Sinon, la connexion à SQL Server échoue.

