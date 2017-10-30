---
title: "Catalog.add_execution_worker (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d587cedd-6402-4d5c-9526-7cd25627a037
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8ce83f2678a1f3dcae6539f33beb33070b8e771b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="catalogaddexecutionworker-ssisdb-database"></a>Catalog.add_execution_worker (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

Ajoute un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] montée en puissance des processus de travail une instance d’exécution de monter en charge.

## <a name="syntax"></a>Syntaxe

```sql
catalog.add_execution_worker [@execution_id = ] execution_id, [@workeragent_id = ] workeragent_id
```

## <a name="arguments"></a>Arguments
[ @execution_id =] *execution_id*  
 Identificateur unique de l'instance d'exécution. Le *execution_id* est **bigint**.  
 
[@workeragent_id =] *workeragent_id*  
L’id de l’agent de travailleur d’un montée en puissance des processus de travail. Le *workeragent_id* est **uniqueIdentifier**.

## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  

## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur l'instance d'exécution  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
 
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
 
- L’utilisateur n’a pas les autorisations appropriées.

- L’identificateur d’exécution n’est pas valide.

- L’id de l’agent de travailleur n’est pas valide.

- L’exécution n’est pas de monter en charge.

## <a name="see-also"></a>Voir aussi
[Exécuter des packages de monter en charge](~/integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md).


