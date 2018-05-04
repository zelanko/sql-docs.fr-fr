---
title: sp_delete_database_firewall_rule (base de données de SQL Azure) | Documents Microsoft
ms.custom: ''
ms.date: 08/04/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_database_firewall_rule
- sp_delete_database_firewall_rule_TSQL
- sys.sp_delete_database_firewall_rule
- sys.sp_delete_database_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_database_firewall_rule procedure
ms.assetid: ed295312-e586-4fc2-9e80-806b490ee7bd
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: a2d8ba7a1b0068b3a5321e530e6b7755aa2c5f87
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="spdeletedatabasefirewallrule-azure-sql-database"></a>sp_delete_database_firewall_rule (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Supprime un paramètre de pare-feu de niveau base de données de votre [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Les règles de pare-feu de base de données peuvent être configurés et supprimés de la base de données master et pour les bases de données utilisateur sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].   
  
 
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_delete_database_firewall_rule [@name =] [N]'name'
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@name =**] **'***nom***'**  
 Nom du paramètre de pare-feu de niveau base de données qui sera supprimé. *nom* est **nvarchar (128)** sans valeur par défaut. L’identificateur Unicode `N` est facultatif pour [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]. 
  
## <a name="permissions"></a>Autorisations  
 Uniquement au niveau du serveur principale connexion créée par le processus de déploiement ou d’une entité de sécurité Azure Active Directory désigné comme administrateur peut supprimer les règles de pare-feu de niveau base de données.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant supprime le paramètre nommé de pare-feu de niveau base de données `Example DB Setting 1`.
  
```  
-- Remove database-level firewall setting  
EXECUTE sp_delete_database_firewall_rule N'Example DB Setting 1';  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Pare-feu de base de données SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Comment : configurer les paramètres de pare-feu (base de données SQL Azure)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;base de données SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_set_database_firewall_rule &#40;base de données SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)   
 [Sys.database_firewall_rules &#40;base de données SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  


