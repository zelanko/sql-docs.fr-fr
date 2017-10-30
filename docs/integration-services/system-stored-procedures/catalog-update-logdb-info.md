---
title: "Catalog.update_logdb_info (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a898be08859230ab873fd8e358b892789aaed043
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="catalogupdatelogdbinfo-ssisdb-database"></a>Catalog.update_logdb_info (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

Mise à jour le [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] l’échelle à l’enregistrement des informations.

## <a name="syntax"></a>Syntaxe

```sql
catalog.update_logdb_info [@server_name = ] server_name, [@connection_string = ] connection_string
```

## <a name="arguments"></a>Arguments
[ @server_name =] *nom_serveur*  
 Le serveur Sql utilisé pour la journalisation de monter en charge. Le *nom_serveur* est **nvarchar**.  

 [ @connection_string =] *chaîne_connexion*  
 La chaîne de connexion utilisée pour la journalisation de monter en charge. Le *chaîne_connexion* est **nvarchar**.

 ## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  

## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
   
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
 

