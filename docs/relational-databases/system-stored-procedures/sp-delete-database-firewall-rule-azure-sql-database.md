---
title: sp_delete_database_firewall_rule (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 08/04/2017
ms.service: sql-database
ms.reviewer: ''
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
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: b942b64b8d97ac69b03b9e1aef03056200f4eef4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750653"
---
# <a name="sp_delete_database_firewall_rule-azure-sql-database"></a>sp_delete_database_firewall_rule (Azure SQL Database)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  Supprime le paramètre de pare-feu de niveau base de données de votre [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] . Les règles de pare-feu de base de données peuvent être configurées et supprimées pour la base de données Master, ainsi que pour les bases de données utilisateur sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] .   
  
 
## <a name="syntax"></a>Syntaxe  
  
```    
sp_delete_database_firewall_rule [@name =] [N]'name'
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 `[@name =] [N]'name'`  
 Nom du paramètre de pare-feu de niveau base de données qui sera supprimé. *Name* est de type **nvarchar (128)** sans valeur par défaut. L’identificateur Unicode `N` est facultatif pour [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] . 
  
## <a name="permissions"></a>Autorisations  
 Seul le nom de connexion du principal au niveau du serveur créé par le processus de configuration ou un principal Azure Active Directory affecté en tant qu’administrateur peut supprimer les règles de pare-feu au niveau de la base de données.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant supprime le paramètre de pare-feu au niveau de la base de données nommé `Example DB Setting 1` .
  
```  
-- Remove database-level firewall setting  
EXECUTE sp_delete_database_firewall_rule N'Example DB Setting 1';  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Pare-feu Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Procédure : configurer les paramètres de pare-feu (Azure SQL Database)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_set_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)   
 [sys. database_firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  


