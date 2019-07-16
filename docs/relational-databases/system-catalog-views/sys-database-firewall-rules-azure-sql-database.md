---
title: Sys.database_firewall_rules (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.database_firewall_rules_TSQL
- database_firewall_rules_TSQL
- sys.database_firewall_rules
- database_firewall_rules
dev_langs:
- TSQL
helpviewer_keywords:
- database_firewall_rules
- sys.database_firewall_rules
ms.assetid: 2e821593-3b9f-43d6-a99b-1ceffe177faf
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 1681c3b245da5d1abded678d54b2b7694598077b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915022"
---
# <a name="sysdatabasefirewallrules-azure-sql-database"></a>sys.database_firewall_rules (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les paramètres de pare-feu au niveau de la base de données associé à votre [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Les paramètres de pare-feu de niveau base de données sont particulièrement utiles lors de l’utilisation des utilisateurs de base de données autonome. Pour plus d’informations, voir [Utilisateurs de base de données autonome - Rendre votre base de données portable](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
 La vue `sys.database_firewall_rules` contient les colonnes suivantes :  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|id|**INTEGER**|Identificateur du paramètre de pare-feu de niveau base de données.|  
|name|**NVARCHAR(128)**|Nom que vous avez choisi pour décrire et distinguer le paramètre de pare-feu de niveau base de données.|  
|start_ip_address|**VARCHAR(45)**|Adresse IP la plus basse dans la plage de paramètres de pare-feu au niveau base de données. Les adresses IP supérieures ou égales à celle-ci peuvent essayer de se connecter à l'instance [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L"adresse IP la plus basse possible est `0.0.0.0`.|  
|end_ip_address|**VARCHAR(45)**|Adresse IP la plus élevée dans la plage du paramètre de pare-feu. Les adresses IP inférieures ou égales à celle-ci peuvent essayer de se connecter à l'instance [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L"adresse IP la plus élevée possible est `255.255.255.255`.<br /><br /> Remarque : Tentatives de connexion de Windows Azure sont autorisées lorsque ce champ et le **start_ip_address** champ equals `0.0.0.0`.|  
|create_date|**DATE/HEURE**|Date et heure UTC de création du paramètre de pare-feu de niveau base de données.|  
|modify_date|**DATE/HEURE**|Date et heure UTC de la dernière modification du paramètre de pare-feu de niveau base de données.|  
  
## <a name="remarks"></a>Notes  
 Pour retourner des informations sur les paramètres de pare-feu de niveau serveur associés à votre base de données Microsoft Azure SQL, utilisez [sys.firewall_rules (Azure SQL Database)](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md).  
  
## <a name="permissions"></a>Autorisations  
 Cette vue est disponible dans le **master** base de données et dans chaque base de données utilisateur. L'accès en lecture seule à cette vue est disponible pour tous les utilisateurs autorisés à se connecter à la base de données.  
  
## <a name="see-also"></a>Voir aussi
[sp_set_database_firewall_rule &#40;Base de données Azure SQL&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)  
[sp_delete_database_firewall_rule &#40;base de données SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)  
[sp_set_firewall_rule &#40;Base de données Azure SQL&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)  
[sp_delete_firewall_rule &#40;base de données SQL Azure&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)   
[Sys.firewall_rules &#40;base de données SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)  
[Configurer un pare-feu Windows pour accéder au moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)     
[Configurer un pare-feu pour l’accès FILESTREAM](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)  
[Configurer un pare-feu pour accéder au serveur de rapports](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
