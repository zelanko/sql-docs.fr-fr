---
title: sp_syscollector_set_warehouse_instance_name (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syscollector_set_warehouse_instance_name_TSQL
- sp_syscollector_set_warehouse_instance_name
dev_langs: TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_set_warehouse_instance_name
ms.assetid: 5320fcd4-bed1-468f-b784-a5e10fcfaeb6
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 569ad6a22134ae8da3568b56b2190ae9fbdf9645
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="spsyscollectorsetwarehouseinstancename-transact-sql"></a>sp_syscollector_set_warehouse_instance_name (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Spécifie le nom de l'instance pour la chaîne de connexion utilisée pour la connexion à l'entrepôt de données de gestion.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_syscollector_set_warehouse_instance_name [ @instance_name = ] 'instance_name'  
```  
  
## <a name="arguments"></a>Arguments  
 [ @instance_name =] '*nom_instance*'  
 Est le nom d’instance. *nom_instance* est **sysname** et valeurs par défaut à l’instance locale si elle est NULL.  
  
> **Remarque :***nom_instance* doit être le nom d’instance complet, constitué du nom de l’ordinateur et le nom d’instance sous la forme *Nom_Ordinateur*\\*instanceName*.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Vous devez désactiver le collecteur de données avant de modifier cette configuration. Cette procédure échoue si le collecteur de données est activé.  
  
 Pour afficher le nom de l’instance actuelle, interrogez la [syscollector_config_store](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md) vue système.  
  
## <a name="permissions"></a>Permissions  
 Requiert l'appartenance au rôle de base de données fixe dc_admin (avec autorisation EXECUTE) pour exécuter cette procédure.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant montre comment configurer le collecteur de données pour qu'il utilise une instance d'entrepôt de données de gestion sur un serveur distant. Dans cet exemple, le serveur distant est nommé `RemoteSERVER` et la base de données est installée sur l'instance par défaut.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_set_warehouse_instance_name N'RemoteSERVER'; -- the default instance is assumed on the remote server  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [syscollector_config_store &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md)  
  
  
