---
title: sp_set_firewall_rule (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 07/28/2016
ms.service: sql-database
ms.reviewer: ''
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
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 9bc37626879b743eb3a5d0864490dc3543a8d8a9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "70152061"
---
# <a name="sp_set_firewall_rule-azure-sql-database"></a>sp_set_firewall_rule (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  Crée ou met à jour les paramètres de pare-feu au niveau serveur du serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Cette procédure stockée est uniquement disponible dans la base de données Master à la connexion du principal au niveau du serveur ou à l’Azure Active Directory principal.  
  
  
## <a name="syntax"></a>Syntaxe  
  
```
sp_set_firewall_rule [@name =] 'name', 
    [@start_ip_address =] 'start_ip_address', 
    [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 Le tableau suivant montre les arguments et les options pris [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]en charge dans.  
  
|Nom|Type de données|Description|  
|----------|--------------|-----------------|  
|[@name =] nomme|**NVARCHAR (128)**|Le nom utilisé pour décrire et distinguer le paramètre de pare-feu au niveau serveur.|  
|[@start_ip_address =] 'start_ip_address'|**VARCHAR (50)**|Adresse IP la plus basse dans la plage de paramètres de pare-feu au niveau serveur. Les adresses IP supérieures ou égales à celle-ci peuvent essayer de se connecter au serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L"adresse IP la plus basse possible est `0.0.0.0`.|  
|[@end_ip_address =] 'end_ip_address'|**VARCHAR (50)**|Adresse IP la plus élevée dans la plage de paramètres de pare-feu au niveau serveur. Les adresses IP inférieures ou égales à celle-ci peuvent essayer de se connecter au serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L"adresse IP la plus élevée possible est `255.255.255.255`.<br /><br /> Remarque : les tentatives de connexion Azure sont autorisées lorsque ce champ et le champ *start_ip_address* est `0.0.0.0`égal à.|  
  
## <a name="remarks"></a>Notes  
 Les noms des paramètres de pare-feu au niveau serveur doivent être uniques. Si le nom du paramètre de pare-feu spécifié pour la procédure stockée existe déjà dans le tableau des paramètres de pare-feu, les adresses IP de début et de fin sont mises à jour. Sinon, un nouveau paramètre de pare-feu au niveau serveur est créé.  
  
 Lorsque vous ajoutez un paramètre de pare-feu de niveau serveur et que les adresses IP de début et de fin sont égales à `0.0.0.0`, vous activez l'accès à votre serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] à partir de Azure. Spécifiez une valeur pour le paramètre de *nom* qui vous aidera à vous souvenir de la fonction du paramètre de pare-feu au niveau du serveur.  
  
 Dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)], les données de connexion exigées pour authentifier une connexion et les règles de pare-feu de niveau serveur sont temporairement mises en cache dans chaque base de données. Ce cache est régulièrement actualisé. Pour forcer une actualisation du cache d’authentification et garantir qu’une base de données a la version la plus récente de la table de connexions, exécutez [DBCC FLUSHAUTHCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Seul le nom de connexion du principal au niveau du serveur créé par le processus de configuration ou un principal Azure Active Directory affecté en tant qu’administrateur peut créer ou modifier des règles de pare-feu au niveau du serveur. L’utilisateur doit être connecté à la base de données Master pour exécuter sp_set_firewall_rule.  
  
## <a name="examples"></a>Exemples  
 Le code suivant crée un paramètre de pare-feu de niveau serveur nommé `Allow Azure` qui active l'accès à partir de Azure. Exécutez la commande suivante dans la base de données Master virtuelle.  
  
```  
-- Enable Azure connections.  
exec sp_set_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Le code suivant crée un paramètre de pare-feu au niveau serveur appelé `Example setting 1` uniquement pour l'adresse IP `0.0.0.2`. Ensuite, la `sp_set_firewall_rule` procédure stockée est de nouveau appelée pour mettre à jour l' `0.0.0.4`adresse IP de fin, dans ce paramètre de pare-feu. Cela permet de créer une plage qui autorise `0.0.0.2`les `0.0.0.3`adresses IP `0.0.0.4` , et à accéder au serveur.  
  
```  
-- Create server-level firewall setting for only IP 0.0.0.2  
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.2';  
  
-- Update server-level firewall setting to create a range of allowed IP addresses
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.4';  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Pare-feu Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Procédure : configurer les paramètres de pare-feu (Azure SQL Database)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sys. firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)
