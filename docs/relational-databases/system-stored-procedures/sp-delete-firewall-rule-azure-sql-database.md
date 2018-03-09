---
title: "sp_delete_firewall_rule (base de données de SQL Azure) | Documents Microsoft"
ms.custom: 
ms.date: 07/27/2016
ms.prod: 
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: 
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_delete_firewall_rule_TSQL
- sp_delete_firewall_rule
- sys.sp_delete_firewall_rule
- sys.sp_delete_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_firewall_rule procedure
ms.assetid: cf93eed1-ba97-4850-9fcc-b9c5a9317908
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aa2815c27668bc680ce5da72b6713e29b517f43b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spdeletefirewallrule-azure-sql-database"></a>sp_delete_firewall_rule (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  Supprime des paramètres de pare-feu de niveau serveur de votre serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Cette procédure stockée est uniquement disponible dans la base de données master à la connexion du principal au niveau du serveur.  

  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_delete_firewall_rule [@name =] 'name' 
[ ; ] 
```  
  
## <a name="arguments"></a>Arguments  
 L'argument de la procédure stockée est le suivant :  
  
 [@name =] '*nom*'  
 Nom du paramètre de pare-feu de niveau serveur qui sera supprimé. *nom* est **nvarchar (128)** sans valeur par défaut.  
  
## <a name="remarks"></a>Notes  
 Dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)], les données de connexion requises pour authentifier une connexion et les règles de pare-feu de niveau serveur sont temporairement mis en cache dans chaque base de données. Ce cache est actualisé régulièrement. Pour forcer une actualisation du cache d’authentification et assurez-vous qu’une base de données a la version la plus récente de la table de connexions, exécutez [DBCC FLUSHAUTHCACHE &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Seul le nom de connexion du principal au niveau du serveur créé par le processus de déploiement peut supprimer les règles de pare-feu côté serveur. L’utilisateur doit être connecté à la base de données master pour exécuter sp_delete_firewall_rule.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant supprime le paramètre de pare-feu de niveau serveur nommé « Example setting 1 ». Exécutez l’instruction dans la base de données master virtuelle.  
  
```   
EXEC sp_delete_firewall_rule N'Example setting 1';   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Pare-feu de base de données SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Comment : configurer les paramètres de pare-feu (base de données SQL Azure)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40; Base de données SQL Azure &#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [Sys.firewall_rules &#40; Base de données SQL Azure &#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)  
  
  


