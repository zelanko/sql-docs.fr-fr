---
title: sys. database_firewall_rules (Azure SQL Database) | Microsoft Docs
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
ms.openlocfilehash: 61402b762b7a6b4d944214d59e187e1457e93f93
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155770"
---
# <a name="sysdatabase_firewall_rules-azure-sql-database"></a>sys.database_firewall_rules (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les paramètres de pare-feu au niveau [!INCLUDE[msCoName](../../includes/msconame-md.md)] de la base de données associés à votre [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Les paramètres de pare-feu de niveau base de données sont particulièrement utiles lors de l’utilisation des utilisateurs de base de données autonome. Pour plus d’informations, voir [Utilisateurs de base de données autonome - Rendre votre base de données portable](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
 La vue `sys.database_firewall_rules` contient les colonnes suivantes :  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|id|**INTEGER**|Identificateur du paramètre de pare-feu de niveau base de données.|  
|name|**NVARCHAR(128)**|Nom que vous avez choisi pour décrire et distinguer le paramètre de pare-feu de niveau base de données.|  
|start_ip_address|**VARCHAR (45)**|Adresse IP la plus basse dans la plage de paramètres de pare-feu au niveau base de données. Les adresses IP supérieures ou égales à celle-ci peuvent essayer de se connecter à l'instance [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L"adresse IP la plus basse possible est `0.0.0.0`.|  
|end_ip_address|**VARCHAR (45)**|Adresse IP la plus élevée dans la plage du paramètre de pare-feu. Les adresses IP inférieures ou égales à celle-ci peuvent essayer de se connecter à l'instance [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L"adresse IP la plus élevée possible est `255.255.255.255`.<br /><br /> Remarque : Les tentatives de connexion Azure sont autorisées lorsque ce champ et le champ **start_ip_address** sont `0.0.0.0`égaux.|  
|create_date|**DATE/HEURE**|Date et heure UTC de création du paramètre de pare-feu de niveau base de données.|  
|modify_date|**DATE/HEURE**|Date et heure UTC de la dernière modification du paramètre de pare-feu de niveau base de données.|  
  
## <a name="remarks"></a>Notes  
 Pour renvoyer des informations sur les paramètres de pare-feu au niveau du serveur associés à votre Microsoft Azure SQL Database, utilisez [sys. firewall_rules (Azure SQL Database)](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md).  
  
## <a name="permissions"></a>Autorisations  
 Cette vue est disponible dans la base de données **Master** et dans chaque base de données utilisateur. L'accès en lecture seule à cette vue est disponible pour tous les utilisateurs autorisés à se connecter à la base de données.  
  
## <a name="see-also"></a>Voir aussi
[sp_set_database_firewall_rule &#40;Base de données Azure SQL&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)  
[sp_delete_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)  
[sp_set_firewall_rule &#40;Base de données Azure SQL&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)  
[sp_delete_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)   
[sys. firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)  
[Configurer un pare-feu Windows pour l’accès Moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)     
[Configurer un pare-feu pour l’accès FILESTREAM](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)  
[Configurer un pare-feu pour accéder au serveur de rapports](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
