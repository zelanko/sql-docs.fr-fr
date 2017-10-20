---
title: "Catalog.update_master_address (base de données SSISDB) | Documents Microsoft"
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
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e5e560d6011370b3d56ba13c86608d2be3d0dc6e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="catalogupdatemasteraddress-ssisdb-database"></a>Catalog.update_master_address (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

Mise à jour le [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] point de terminaison de mise à l’échelle des Master.

## <a name="syntax"></a>Syntaxe

```sql
update_master_address [@MasterAddress = ] masterAddress
```

## <a name="arguments"></a>Arguments
[ @MasterAddress =] *masterAddress*  
Le point de terminaison de mise à l’échelle des Master. Le *masterAddress* est **nvarchar**.  

 ## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  

## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
   
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
 
