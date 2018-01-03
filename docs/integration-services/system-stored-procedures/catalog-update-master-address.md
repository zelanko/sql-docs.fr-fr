---
title: "catalog.update_master_address (base de données SSISDB) | Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 52aef94f67ef1697731a1844f44f83ddaf0c4ccc
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="catalogupdatemasteraddress-ssisdb-database"></a>catalog.update_master_address (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Met à jour le point de terminaison [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Master.

## <a name="syntax"></a>Syntaxe

```sql
catalog.update_master_address [@MasterAddress = ] masterAddress
```

## <a name="arguments"></a>Arguments
[ @MasterAddress = ] *masterAddress*  
Point de terminaison Scale Out Master. *masterAddress* est de type **nvarchar**.  

 ## <a name="return-code-value"></a>Valeur du code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  

## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
   
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
 
