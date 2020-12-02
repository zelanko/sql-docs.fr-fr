---
description: catalog.add_execution_worker (base de données SSISDB)
title: catalog.add_execution_worker (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d587cedd-6402-4d5c-9526-7cd25627a037
author: chugugrace
ms.author: chugu
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 102277139885379f4c2f75c912756e09131ec546
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96129957"
---
# <a name="catalogadd_execution_worker-ssisdb-database"></a>catalog.add_execution_worker (base de données SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE[sqlserver2017](../../includes/applies-to-version/sqlserver2017.md)]

Ajoute un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Worker à une instance d’exécution dans Scale Out.

## <a name="syntax"></a>Syntaxe

```sql
catalog.add_execution_worker [ @execution_id = ] execution_id, [ @workeragent_id = ] workeragent_id
```

## <a name="arguments"></a>Arguments
[ @execution_id = ] *execution_id*  
 Identificateur unique de l'instance d'exécution. *execution_id* est de type **bigint**.  
 
[@workeragent_id = ] *workeragent_id*  
ID d’agent de Worker d’un Scale Out Worker. *workeragent_id* est de type **uniqueIdentifier**.

## <a name="return-code-value"></a>Valeur du code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  

## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur l'instance d'exécution  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
 
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
 
- L’utilisateur n’a pas les autorisations appropriées.

- L’identificateur d’exécution n’est pas valide.

- L’ID d’agent de Worker n’est pas valide.

- L’exécution n’a pas lieu dans Scale Out.

## <a name="see-also"></a>Voir aussi
[Exécuter des packages dans Scale-out](~/integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md).

