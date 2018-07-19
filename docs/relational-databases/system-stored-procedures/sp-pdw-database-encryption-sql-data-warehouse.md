---
title: sp_pdw_database_encryption pour (SQL Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: system-objects
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f5ccb424-7a95-4557-b774-c69de33c1545
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6508d150df663a6e95437d0b6b3bfd0c8f65906f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38052227"
---
# <a name="sppdwdatabaseencryption-sql-data-warehouse"></a>sp_pdw_database_encryption pour (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Utilisez **sp_pdw_database_encryption pour** pour activer le chiffrement transparent des données pour un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] appliance. Lorsque **sp_pdw_database_encryption pour** défini sur 1, utilisez le **ALTER DATABASE** instruction pour chiffrer une base de données à l’aide du chiffrement transparent des données.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption [ [ @enabled = ] enabled ] ;  
```  
  
#### <a name="parameters"></a>Paramètres  
 [  **@enabled=** ] *activé*  
 Détermine si le chiffrement transparent des données est activé. *activé* est **int**, et peut prendre l’une des valeurs suivantes :  
  
-   0 = Désactivé  
  
-   1 = Activé  
  
 L’exécution de **sp_pdw_database_encryption pour** sans paramètres retourne l’état actuel du chiffrement transparent des données sur l’appliance comme un jeu de résultats scalaires : 0 pour désactivé ou 1 pour activé.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Lorsque la chiffrement transparent des données sont activée à l’aide de **sp_pdw_database_encryption pour**, la base de données tempdb est supprimé, recréé et chiffré. Pour cette raison, la chiffrement transparent des données ne peut pas être activée sur une appliance tandis que les autres sessions sont actives à l’aide de tempdb. L’activation ou désactivation de TDE sur une appliance est une action qui modifie l’état de l’appliance, dans la plupart des cas doit être effectuée qu’une seule fois dans la durée de vie du matériel et doit être exécutée lorsqu’il n’existe aucun trafic sur l’appliance.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’appartenance dans le **sysadmin** rôle de base de données fixe ou **CONTROL SERVER** autorisation.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant active le chiffrement transparent des données sur l’appliance.  
  
```sql  
EXEC sys.sp_pdw_database_encryption 1;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
