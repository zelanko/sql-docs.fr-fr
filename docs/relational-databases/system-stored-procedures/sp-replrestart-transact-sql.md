---
title: sp_replrestart (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_replrestart_TSQL
- sp_replrestart
helpviewer_keywords:
- sp_replrestart
ms.assetid: 111b3dbf-92f8-4670-b156-1468c63e4fc1
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a814699481f34510798bb0430fa3411bf5943ad3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spreplrestart-transact-sql"></a>sp_replrestart (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilisée par la réplication transactionnelle au cours de la sauvegarde et de la restauration pour que les données répliquées sur le serveur de distribution soient synchronisées avec celles du serveur de publication. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
> [!IMPORTANT]  
>  **sp_replrestart** est de réplication internes une procédure stockée et doit être utilisée uniquement lorsque la restauration d’une base de données publiée dans une topologie de réplication transactionnelle, comme indiqué dans la rubrique [stratégies de sauvegarde et restauration de capture instantanée et la réplication transactionnelle](../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replrestart  
```  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_replrestart** est utilisée lorsque la valeur de numéro séquentiel séquence de journal la plus élevée sur le serveur de distribution ne correspond pas à la valeur LSN la plus élevée sur le serveur de publication.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** du rôle de base de données fixe peut exécuter **sp_replrestart**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
