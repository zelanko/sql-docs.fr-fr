---
title: Type d’enclave de chiffrement de colonne - Option de configuration de serveur | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
manager: jroth
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 1031bdfa3aa6c728d3e33b500fe942d5e52c5fdc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66799469"
---
# <a name="column-encryption-enclave-type-server-configuration-option"></a>Type d’enclave de chiffrement de colonne - Option de configuration de serveur
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Utilisez l’option **Type d’enclave de chiffrement de colonne** pour activer ou désactiver une enclave sécurisée pour Always Encrypted.  Pour plus d’informations, consultez [Always Encrypted avec enclaves sécurisées](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

 Le tableau suivant liste les valeurs possibles pour le **type d’enclave de chiffrement de colonne** :  
  
|Valeur|Description|  
|-------------------|-----------------|  
|0|**Aucune enclave sécurisée**. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] n’initialise pas l’enclave sécurisée pour Always Encrypted. Par conséquent, la fonctionnalité d’Always Encrypted avec enclaves sécurisées n’est pas disponible.|  
|1|**Sécurité basée sur la virtualisation**. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] initialise l’enclave sécurisée (enclave à mémoire sécurisée basée sur la virtualisation) pour Always Encrypted.|    

> [!IMPORTANT]
> Les modifications apportées au **type d’enclave de chiffrement de colonne** ne sont pas appliquées tant que vous n’avez pas redémarré l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
   
## <a name="examples"></a>Exemples  
 L’exemple suivant active l’enclave sécurisée :  

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

## <a name="see-also"></a>Voir aussi  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
