---
description: sys.service_contracts (Transact-SQL)
title: sys. service_contracts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- service_contracts_TSQL
- sys.service_contracts_TSQL
- sys.service_contracts
- service_contracts
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_contracts catalog view
ms.assetid: 787dd47e-4210-439d-9c4a-57a727a0dbd8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5c8a15b21c79cf8f27c8fcdc6c5f3cf88ac35235
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490121"
---
# <a name="sysservice_contracts-transact-sql"></a>sys.service_contracts (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Cet affichage catalogue contient une ligne pour chaque contrat de la base de données.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nom du contrat, unique dans la base de données. Cette colonne n'accepte pas la valeur NULL.|  
|**service_contract_id**|**int**|Identificateur du contrat. Cette colonne n'accepte pas la valeur NULL.|  
|**principal_id**|**int**|Identificateur du principal de base de données propriétaire de ce contrat. Accepte la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
