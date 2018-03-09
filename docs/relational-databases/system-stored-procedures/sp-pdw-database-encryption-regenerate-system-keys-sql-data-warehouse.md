---
title: sp_pdw_database_encryption_regenerate_system_keys (SQL Data Warehouse) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: system-stored-procedures
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: bb13e323-a984-4462-8b6d-6019c38ddd9d
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 967ed1282db9b17ebc4a3c942ad6f6d4d9c58d61
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sppdwdatabaseencryptionregeneratesystemkeys-sql-data-warehouse"></a>sp_pdw_database_encryption_regenerate_system_keys (entrepôt de données SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Utilisez **sp_pdw_database_encryption_regenerate_system_keys** pour faire pivoter la clé de chiffrement de certificat et de la base de données pour les bases de données internes qui sont chiffrées lorsque TDE est activé sur l’appareil. Cela comprend `tempdb`. Cela réussira uniquement si le chiffrement transparent des données sont activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption_regenerate_system_keys  ;  
```  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 La procédure n’a aucun paramètre.  
  
 Cette procédure doit être utilisée lorsque le trafic de l’application est faible.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’appartenance dans le **sysadmin** rôle de base de données fixe ou **CONTROL SERVER** autorisation.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant régénère les clés de chiffrement de base de données.  
  
```sql  
EXEC sys.sp_pdw_database_encryption_regenerate_system_keys;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_pdw_database_encryption pour &#40; Entrepôt de données SQL &#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
