---
title: sp_set_firewall_rule (base de données Azure SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/28/2016
ms.prod: ''
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_set_firewall_rule
- sp_set_firewall_rule_TSQL
- sys.sp_set_firewall_rule
- sys.sp_set_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_firewall_rule
- firewall_rules, setting server rules
ms.assetid: a974a561-5382-4039-8499-3a56767bcefe
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: c5ce548a1a1a982a363b9c79e7861f01474bdc18
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758407"
---
# <a name="spsetfirewallrule-azure-sql-database"></a>sp_set_firewall_rule (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  Crée ou met à jour les paramètres de pare-feu au niveau serveur du serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Cette procédure stockée est uniquement disponible dans la base de données master pour la connexion du principal au niveau du serveur ou le principal d’Azure Active Directory affecté.  
  
  
## <a name="syntax"></a>Syntaxe  
  
```
sp_set_firewall_rule [@name =] 'name', 
    [@start_ip_address =] 'start_ip_address', 
    [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 Le tableau suivant montre les arguments pris en charge et les options dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
|Nom   |Type de données|Description|  
|----------|--------------|-----------------|  
|[@name =] 'name'|**NVARCHAR (128)**|Le nom utilisé pour décrire et distinguer le paramètre de pare-feu au niveau serveur.|  
|[@start_ip_address =] 'start_ip_address'|**VARCHAR (50)**|Adresse IP la plus basse dans la plage de paramètres de pare-feu au niveau serveur. Les adresses IP supérieures ou égales à celle-ci peuvent essayer de se connecter au serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L"adresse IP la plus basse possible est `0.0.0.0`.|  
|[@end_ip_address =] 'end_ip_address'|**VARCHAR (50)**|Adresse IP la plus élevée dans la plage de paramètres de pare-feu au niveau serveur. Les adresses IP inférieures ou égales à celle-ci peuvent essayer de se connecter au serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L"adresse IP la plus élevée possible est `255.255.255.255`.<br /><br /> Remarque : Les tentatives de connexion Azure sont autorisées lorsque ce champ et le *start_ip_address* champ equals `0.0.0.0`.|  
  
## <a name="remarks"></a>Notes  
 Les noms des paramètres de pare-feu au niveau serveur doivent être uniques. Si le nom du paramètre de pare-feu spécifié pour la procédure stockée existe déjà dans le tableau des paramètres de pare-feu, les adresses IP de début et de fin sont mises à jour. Sinon, un nouveau paramètre de pare-feu au niveau serveur est créé.  
  
 Lorsque vous ajoutez un paramètre de pare-feu au niveau du serveur où le début et fin des adresses IP sont égaux à `0.0.0.0`, vous activez l’accès à votre [!INCLUDE[ssSDS](../../includes/sssds-md.md)] server à partir d’Azure. Spécifiez une valeur pour le *nom* n’oubliez pas de paramètre qui vous aideront à ce qui concerne le paramètre de pare-feu au niveau du serveur.  
  
 Dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)], les données de connexion exigées pour authentifier une connexion et les règles de pare-feu de niveau serveur sont temporairement mises en cache dans chaque base de données. Ce cache est régulièrement actualisé. Pour forcer une actualisation du cache d’authentification et garantir qu’une base de données a la version la plus récente de la table de connexions, exécutez [DBCC FLUSHAUTHCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Uniquement la connexion principale au niveau du serveur est créée par le processus d’approvisionnement ou une entité de sécurité Azure Active Directory affecté comme administrateur peut créer ou modifier des règles de pare-feu de niveau serveur. L’utilisateur doit être connecté à la base de données master pour exécuter sp_set_firewall_rule.  
  
## <a name="examples"></a>Exemples  
 Le code suivant crée un paramètre de pare-feu de niveau serveur `Allow Azure` qui permet l’accès à partir d’Azure. Exécutez le code suivant dans la base de données master virtuelle.  
  
```  
-- Enable Windows Azure connections.  
exec sp_set_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Le code suivant crée un paramètre de pare-feu au niveau serveur appelé `Example setting 1` uniquement pour l'adresse IP `0.0.0.2`. Ensuite, le `sp_set_firewall_rule` procédure stockée est appelée à nouveau pour mettre à jour l’adresse IP de fin pour `0.0.0.4`, dans ce paramètre de pare-feu. Cette opération crée une plage qui autorise les adresses IP `0.0.0.2`, `0.0.0.3`, et `0.0.0.4` pour accéder au serveur.  
  
```  
-- Create server-level firewall setting for only IP 0.0.0.2  
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.2';  
  
-- Update server-level firewall setting to create a range of allowed IP addresses
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.4';  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Pare-feu de base de données SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Comment : configurer les paramètres de pare-feu (base de données SQL Azure)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [Sys.firewall_rules &#40;base de données SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)
