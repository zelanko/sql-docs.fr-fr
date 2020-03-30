---
title: Configurer le type d’enclave pour l’option de configuration de serveur Always Encrypted | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 4786c512850d161d9b7ab33f2a12cd0bd077b2bd
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "73593820"
---
# <a name="configure-the-enclave-type-for-always-encrypted-server-configuration-option"></a>Configurer le type d’enclave pour l’option de configuration de serveur Always Encrypted
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

Cet article explique comment activer ou désactiver une enclave sécurisée pour Always Encrypted avec enclaves sécurisées. Pour plus d’informations, consultez [Always Encrypted avec enclaves sécurisées](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

L’option de configuration de serveur **column encryption enclave type** contrôle le type d’une enclave sécurisée utilisée pour Always Encrypted. Vous pouvez affecter l’une des valeurs suivantes à cette option :  
  
|Valeur|Description|  
|-------------------|-----------------| 
|0|**Aucune enclave sécurisée**. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] n’initialise pas l’enclave sécurisée pour Always Encrypted. Par conséquent, la fonctionnalité d’Always Encrypted avec enclaves sécurisées n’est pas disponible.|  
|1|**Sécurité basée sur la virtualisation**. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] essaie d’initialiser une enclave de sécurité basée sur la virtualisation (VBS).

> [!IMPORTANT]
> Les modifications apportées à **column encryption enclave type** ne sont pas appliquées tant que l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas redémarrée.
   
Vous pouvez vérifier la valeur du type d’enclave configurée et la valeur du type d’enclave actuellement en vigueur en utilisant la vue [sys.configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md). 

Pour confirmer qu’une enclave du type (supérieur à 0) actuellement en vigueur a été correctement initialisée après le dernier redémarrage de [!INCLUDE [ssnoversion-md](../../includes/ssnoversion-md.md)], vérifiez la vue [sys.dm_column_encryption_enclave (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-column-encryption-enclave.md) :
 - Si la vue contient exactement une ligne, l’enclave est correctement initialisée. 
 - Si la vue ne contient pas de lignes, consultez le journal des erreurs SQL Server pour examiner les erreurs d’initialisation de l’enclave. Consultez [Afficher le journal des erreurs SQL Server (SQL Server Management Studio)](../../relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md).

Pour obtenir des instructions pas à pas sur la configuration d’une enclave VBS, consultez [Activer Always Encrypted avec enclaves sécurisées dans SQL Server](../../relational-databases/security/tutorial-getting-started-with-always-encrypted-enclaves.md#step-3-enable-always-encrypted-with-secure-enclaves-in-sql-server).

## <a name="examples"></a>Exemples  
 L’exemple suivant active l’enclave sécurisée et définit le type d’enclave VBS :

```sql  
sp_configure 'column encryption enclave type', 1;  
GO  
RECONFIGURE;  
GO  
```  

L’exemple suivant désactive l’enclave sécurisée :  

```sql  
sp_configure 'column encryption enclave type', 0;  
GO  
RECONFIGURE;  
GO  
```  

La requête suivante récupère le type d’enclave configuré et le type d’enclave actuellement en vigueur :

```sql  
USE [master];
GO
SELECT
[value]
, CASE [value] WHEN 0 THEN 'No enclave' WHEN 1 THEN 'VBS' ELSE 'Other' END AS [value_description]
, [value_in_use]
, CASE [value_in_use] WHEN 0 THEN 'No enclave' WHEN 1 THEN 'VBS' ELSE 'Other' END AS [value_in_use_description]
FROM sys.configurations
WHERE [name] = 'column encryption enclave type'; 
```  
## <a name="next-steps"></a>Étapes suivantes
 [Gérer des clés pour Always Encrypted avec enclaves sécurisées](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)

## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [sys.configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [sys.dm_column_encryption_enclave (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-column-encryption-enclave.md)   
