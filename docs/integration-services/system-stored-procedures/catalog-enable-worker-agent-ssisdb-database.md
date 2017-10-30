---
title: "Catalog.enable_worker_agent (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6e5266b-c32d-49ff-aa69-f09664009fb4
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 3eb3f21b6a686c3013cdaaa3000038896edfbf94
ms.contentlocale: fr-fr
ms.lasthandoff: 10/20/2017

---
# <a name="catalogenableworkeragent-ssisdb-database"></a>Catalog.enable_worker_agent (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Activer un montée en puissance des processus de travail pour travailler avec cette mise à l’échelle Out maître [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalogue.

## <a name="syntax"></a>Syntaxe

```sql
catalog.enable_worker_agent [@WorkerAgentId =] WorkerAgentId
```
## <a name="arguments"></a>Arguments
[@WorkerAgentId =] *WorkerAgentId* l’agent de travailleur ID de montée en puissance des processus de travail. Le *WorkerAgentId* est **uniqueidentifier**.

## <a name="example"></a>Exemple
Cet exemple active Scale Out Worker sur MachineA.

```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[enable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```

## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  

## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur 

## <a name="errors-and-warnings"></a>Erreurs et avertissements
Si l’ID de l’agent de travailleur n’est pas valide, la procédure stockée renvoie une erreur.

