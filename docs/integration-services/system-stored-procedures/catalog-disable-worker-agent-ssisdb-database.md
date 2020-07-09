---
title: catalog.disable_worker_agent (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3f19dc4c-a000-4318-8fe1-e80d56720e66
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc3aae082a59cf122971798739e5add2b1886689
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053692"
---
# <a name="catalogdisable_worker_agent-ssisdb-database"></a>catalog.disable_worker_agent (base de données SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Désactive un Scale Out Worker pour Scale Out Master utilisant ce catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].

## <a name="syntax"></a>Syntaxe

```sql
catalog.disable_worker_agent [ @WorkerAgentId = ] WorkerAgentId
```
## <a name="arguments"></a>Arguments
[@WorkerAgentId =] *WorkerAgentId* ID d’agent de Worker de Scale Out Worker. *WorkerAgentId* est de type **uniqueidentifier**.

## <a name="example"></a>Exemple
Cet exemple désactive Scale Out Worker sur MachineA.

```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[disable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```

## <a name="return-code-value"></a>Valeur du code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  

## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin** 

## <a name="errors-and-warnings"></a>Erreurs et avertissements
Si l’ID d’agent de Worker n’est pas valide, la procédure stockée retourne une erreur.
